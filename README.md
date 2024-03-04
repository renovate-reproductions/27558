# Renovate Composer Update Issue Reproduction

## Overview
This repository serves as a minimal reproduction for an issue encountered with Renovate Bot when updating Composer dependencies. [Discussion link](https://github.com/renovatebot/renovate/discussions/27558)

## Current Behavior
When Renovate attempts to update dependencies specified in `composer.json`, it leads to PR creation with an error stating that the requirements could not be resolved to an installable set of packages.

## Expected Behavior
Renovate should have the capability to suppress PRs for specific errors identified by configurable regex patterns. If an error matches a defined pattern, the PR creation is suppressed to reduce noise. The system should retain the branch for possible re-evaluation, only retrying updates when there are significant changes like git conflicts or new versions. This approach aims to manage update attempts efficiently while waiting for underlying package conflicts to resolve naturally over time.

## Steps to Reproduce
1. Observe the `composer.json` and `composer.lock` in this repository.
2. Run Renovate on this repository.
3. Notice PR "Update dependency nesbot/carbon to v3" which can't be solved at the moment because maclof/kubernetes-client 0.29.0 requires illuminate/support, which explicitly requires nesbot/carbon ^2.67

