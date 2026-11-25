# GitHub Batch Promotion POC

## Objective

Automate the promotion of multiple PRs from Develop to Master.

Instead of manually creating promotion branches, cherry-picking changes, and creating release PRs, GitHub Actions performs these tasks automatically.

---

## Labels

### queued-for-master

PR is ready for the next promotion.

### promote-to-master

Triggers the automation.

### promoted-to-master

PR has already been promoted to master.

---

## Flow

Developer PR
↓
Merge into Develop
↓
Add queued-for-master
↓
Apply promote-to-master on one PR
↓
Workflow starts
↓
Find all eligible queued PRs
↓
Create Promotion Branch
↓
Cherry-pick Merge Commits
↓
Create Promotion PR
↓
Review and Merge
↓
Update Labels
↓
promoted-to-master

---

## Repository Setup

Branches:

master
develop

Example Feature Branches:

US238589_dev_api_fix

US238590_dev_order_fix

US238591_dev_customer_fix

---

## Demo Scenario

### PR 1

customer.txt

Merge to develop

Add label:

queued-for-master

---

### PR 2

orders.txt

Merge to develop

Add label:

queued-for-master

---

### PR 3

accounts.txt

Merge to develop

Add label:

queued-for-master

---

## Trigger Promotion

Add label:

promote-to-master

to any queued PR.

Example:

PR #101

---

## Automation

Workflow automatically:

1. Finds all queued PRs for the same developer
2. Creates promotion branch from master
3. Cherry-picks merge commits
4. Pushes branch
5. Creates Promotion PR

Example:

[AUTO] Promotion Bundle

---

## Finalization

Once Promotion PR merges into master:

queued-for-master -> removed

promote-to-master -> removed

promoted-to-master -> added

---

## Benefits

- Eliminates manual cherry-picking
- Reduces release effort
- Creates repeatable promotion process
- Improves traceability
- Supports batch releases