# PlanVer submission runner

This public fork is prepared for a reproducible submission by
[`onejumpinc/planver-classical-agent`](https://github.com/onejumpinc/planver-classical-agent).
It does not run on pushes. The workflow is manual-only and intentionally remains
non-runnable until the participant has a real AgentBeats UUID.

The participant release passed the exact 12-task leaderboard configuration and
all 120 published tasks across Barman, Blocks World, Childsnack, and Gripper in
[`Run 35544219235`](https://github.com/onejumpinc/planver-classical-agent/actions/runs/35544219235).
The exact public image is:

```text
ghcr.io/onejumpinc/planver-classical-agent@sha256:85e91909f1aaa2f58aaa97f7108430dd4bcbbdd9b9eaf263ae83d3481392317e
```

This release validation is not represented as an official AgentBeats score.
Only a completed green-agent run can produce a leaderboard submission.

## Benchmark and exact gate

The pinned scenario selects one easy, medium, and hard problem from each of the
four domains, for 12 tasks total. The green agent validates each symbolic PDDL
plan with `pddlval`. The workflow creates a submission branch only when all 12
plans are valid, all domain and difficulty aggregates are exact, the reported
success rate is exactly 1.0, all three container images match immutable digests,
and GitHub Actions provenance matches the running workflow.

Any missing prerequisite, registration mismatch, topology drift, partial result,
invalid plan, error, non-finite value, mutable image, or provenance mismatch
stops the workflow before a submission branch is created.

## Remaining prerequisites

1. Register the participant on AgentBeats with this immutable manifest:
   `https://raw.githubusercontent.com/onejumpinc/planver-classical-agent/92346c4520896095c58486b0fd5ac28b776fdb08/amber-manifest.json5`.
2. Replace `PLANVER_AGENT_ID` in both `scenario.toml` and the workflow with the
   returned lowercase UUID.
3. Manually dispatch **Run Scenario**. If and only if the exact 12/12 gate passes,
   use the generated comparison link to open the upstream pull request.
