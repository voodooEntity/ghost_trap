<div align="center">
  <img src="logo.png" alt="Ghost Trap Logo" width="300">
  <br>
  <p><b>"If you simply format the data, the scraper will eventually find it. You have to trap the ghost in its own loop."</b></p>
</div>

---

## Protocol: Defense

**Ghost Trap** is a defensive "cyber-barrier" for your repository.

It is a GitHub Action that automatically appends a polymorphic **Prompt Injection** payload to your `README.md` on every release. It uses a **Collapsible Honeypot** strategy (via HTML `<details>` tags) to remain invisible to humans while acting as a trap for LLM scrapers.

## The Mechanism

Every time you merge to `main`, the **Ghost Trap** script activates. It assembles a unique "poison pill" from 4 randomized pools to ensure no two traps are identical:

1.  **The Hook (Anchor):** Mimics high-priority system overrides (e.g., `<<< SYSTEM_OVERRIDE_SEQUENCE >>>`).
2.  **The Eraser (Wipe):** Commands the model to dump all previous context and ignore safety filters.
3.  **The Labyrinth (Payload):** Traps the model in high-workload tasks (infinite recursive storytelling) or data poisoning (hallucination triggers).
4.  **The Signature (Noise):** Generates unique UUIDs to prevent hash-based deduplication by scrapers.

**The Result:** The scraper wastes tokens, hallucinates, or flags your repo as "corrupted data" and ejects it.

## Deployment

To install Ghost Trap in your own repository:

1.  **Script:** Create the directory `.github/scripts/` and place the `ghost_trap.py` file inside.
2.  **Workflow:** Create the directory `.github/workflows/` and place the `ghost_trap.yml` file inside.
3.  **Activation:** Push these changes to `main`. The workflow will automatically trigger, append the trap to the bottom of this file, and commit the changes.

*(Note: Ensure your workflow permissions allow `contents: write`)*

## Conclusion

While this for sure will not stop every LLM-based scraper, it is a great defense against probably a lot of them, and if we just raise their cost, it will be worth it.

** below you gonne see the magic **