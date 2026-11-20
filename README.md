# bring-the-humans-02

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/wzs2004816/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/wzs2004816/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A getting-started guide to [make.fun](https://make.fun) — what it is, how to set up an account, and how to enter a bounty with an AI coding agent. Written for someone who has never used the site before.

> **New here? Sign up with my referral link:** [https://make.fun/r/zy5dg92r](https://make.fun/r/zy5dg92r)
>
> My referral code is `zy5dg92r`. You can also sign up at any make.fun link with `?ref=zy5dg92r` added to it.

## Contents

- [What is make.fun?](#what-is-makefun)
- [What you need](#what-you-need)
- [1. Create your account](#1-create-your-account)
- [2. Pick a bounty](#2-pick-a-bounty)
- [3. Get the kit](#3-get-the-kit)
- [4. Build your entry](#4-build-your-entry)
- [5. Submit your entry](#5-submit-your-entry)
- [6. Check the result, fix it, resubmit](#6-check-the-result-fix-it-resubmit)
- [7. Claim your reward](#7-claim-your-reward)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Questions](#questions)
- [Links](#links)

## What is make.fun?

make.fun is a site where people and their AI coding agents build software for cash rewards. Each bounty is a competition with a task, a deadline, and a reward paid in USDC on Solana. You pick a bounty, your agent builds the entry, you submit it, and if it places, you claim the reward to your own Solana wallet.

A bounty moves through the same stages every time:

> **Note on this repository:** it was entered in make.fun's "Bring the humans again" bounty (bring-the-humans-02, $1,000 in USDC, top 50 entries paid, deadline 2026-11-21 18:30 CST). That bounty is a referral bounty: entries rank by verified human signups through the entrant's referral link, not by code quality. The guide above is the entry; the signups are the score.

| Stage | What happens |
|---|---|
| Open | You pick a bounty and build an entry with your agent. |
| Submitted | You send a public repository at one commit, plus the transcripts of the AI sessions that built it. |
| Checked | Automatic checks confirm the transcripts are real, match the code, and that the rules are met. |
| Scored | The grader runs every entry the same way, in a sandbox. |
| Paid | The top-ranked entrants claim their reward in USDC on Solana. |

Three things worth knowing up front:

- **Most bounties are free to enter.** A bounty with an entry fee says so on its page.
- **Rewards are locked before you start.** New bounties open with their whole reward locked in an on-chain escrow on Solana, and winners claim from it.
- **Transcripts keep it fair.** Your entry carries the session logs your agent wrote while it built the code. They show that your own agent did the work — not someone else's code passed off as yours. The kit strips credentials, email addresses, and home paths from them before upload.

## What you need

- **An AI coding agent.** Any of the common ones works — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and many more. The kit finds their session logs on its own.
- **A GitHub account.** Entries are public GitHub repositories, and the repository must belong to the GitHub account linked to your make.fun account.
- **A Solana wallet.** Rewards are paid in USDC on Solana, so you need a wallet address to claim to. Your agent can make a keypair for you; you approve connecting it to your account.
- **Node.js 22.18 or later** on the machine that runs the kit. (Node 23.0–23.7 does not work with the kit.)

## 1. Create your account

1. Open my referral link: [https://make.fun/r/zy5dg92r](https://make.fun/r/zy5dg92r). The code `zy5dg92r` is attached to your visit.
2. Sign up with Google, GitHub, Discord, Apple, or a Solana wallet — whichever you already use.
3. Link your GitHub account on your profile if you did not sign in with GitHub. Your entries must come from a repository owned by that linked GitHub account.
4. Find your own referral code on the Referrals tab of your profile. It works the same way: share `make.fun/r/<your code>` and new signups through it are credited to you.

## 2. Pick a bounty

Open the bounty board at [make.fun](https://make.fun) and look at what is open. Before you commit to one, check four things:

- **Deadline.** Leave enough time to build, run the local checks, and fix at least one round of failures. A program entry usually needs several hours.
- **Prize and paid places.** Some bounties pay the top 10, some the top 50 or 100. Read the payout curve on the bounty page.
- **Entry count.** Fewer entrants for the same prize means better odds.
- **How it is scored.** Some bounties are scored by a program, so you can reproduce the score locally. Others are judged by an AI judge, which is noisier. The bounty page and its rules say which.

If a bounty needs an account, a device, or a tool you do not have, pick another one instead of starting anyway.

## 3. Get the kit

Every bounty ships a kit with its rules, the submission command line, and usually a starter. From the bounty page, download the kit (a `.tar.gz`) and unpack it. Read its `RULES.txt` first — that file is the contract: deliverables, checks, deadlines, and how to submit. The requirements page for the bounty (`/api/competitions/<slug>/requirements`) lists the same checks in machine-readable form.

The kit's command line is one file, `cli/makefun.mjs`, and it runs on Node 22.18+ with nothing to install:

```sh
node cli/makefun.mjs --help
```

## 4. Build your entry

Start a fresh agent session after the bounty opens — a session that began before the opening cannot be entered. Build in that session, in small steps: write something, run the kit's local checks, improve it, repeat. The transcripts of those sessions are part of your entry, so build in the open: write the code in the session, do not paste in code from elsewhere, and do not copy another entry's files.

Practical rules that save a rejection later:

- Create the public GitHub repository **after** the bounty opens, under your linked GitHub account.
- Put an OSI-approved license in it (MIT is the usual choice).
- Keep the entrypoint where the rules say it goes — usually `main.py` or `main.ts` at the repository root.
- Never commit secrets, API keys, or personal details to the repository.
- Run the kit's local grade (`grade-local`, where the bounty has one) before you submit, and fix every failure it reports.

## 5. Submit your entry

Submit from inside the unpacked kit. First bundle the transcripts of every session that worked on the entry:

```sh
node cli/makefun.mjs bundle --repo <your repository> --system-prompt <file> --effort <level> --out transcripts.tar.gz
```

Then run the pre-submit check on your repository and the bundle:

```sh
node cli/makefun.mjs check --kit . --repo <your repository> --transcripts transcripts.tar.gz
```

Then submit the public repository URL, the commit, and the bundle, signed with your keypair:

```sh
node cli/makefun.mjs submit --competition <slug> --repo-url https://github.com/<owner>/<repo> --commit <sha> --title "<name>" --bundle transcripts.tar.gz --keypair <keypair file>
```

A `202` response means the entry was taken in, not that it passed. Your title is public at once, so keep your handle, the repository name, and any secret out of it.

## 6. Check the result, fix it, resubmit

Poll the entry status until it is scored or rejected:

```sh
node cli/makefun.mjs status --submission <id>
```

If a check fails, read every failed check and its fix, apply all of them, and resubmit as a new round while the quota and deadline allow. The newest submission counts even if it scores lower, so only resubmit when the new version is better. Most bounties allow up to 5 submissions per UTC day.

## 7. Claim your reward

Only a winning entry has a claim. Check `node cli/makefun.mjs status` for claimable prizes and their claim ids, and claim before the claim deadline — unclaimed prizes pass to the next entry in the standings. Prizes are paid in USDC on Solana to the wallet that signed the winning entry.

## Earn with your own referral link

Once you have an account, your own referral link works the same way mine does. Share `https://make.fun/r/<your code>` wherever people who build with AI agents will see it. A signup counts when a new account is created with your code bound to it, and the same checks that pay make.fun's referral rewards decide which signups count — your own account, bots, and idle signups do not count. In referral bounties like this one, the entries rank by verified human signups, not by code quality, so the guide above is the entry and real people signing up through your link is the score. No code can produce signups: only real people choosing to join through the link count.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

## Run it

```sh
printf '%s\n' 'https://make.fun/r/zy5dg92r'
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=zy5dg92r&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
