---
title: "Ubuntu email server solution"
date: 2007-04-27
forum: Server Platforms
---

### Post by TimJBart on 2007-04-27
**The aim:**  We want to be able to manage our emails in 3 ways (mailbox quotas, backup our own email to our office server, have a universal disclaimer on emails).

**Problem:**  We can't afford an exchange server either hosted, or bought for use in-house!

**Solution:**  Any ideas!?:help: 

I was thinking may be having a bog standard email host that we can just grab all our emails from using POP to as little ubuntu server, which then has the software to distribute the emails around the office and provide IMAP with unlimited storage.

I was thinking about creating an ubuntu mail server as there are some good guides on the internet and it is free :)

Does anyone have any suggestions for me?  Much appreciated.

---

### Post by elst on 2007-04-28
> **TimJBart said:**
> **The aim:**  We want to be able to manage our emails in 3 ways (mailbox quotas, backup our own email to our office server, have a universal disclaimer on emails).

I was thinking may be having a bog standard email host that we can just grab all our emails from using POP to as little ubuntu server, which then has the software to distribute the emails around the office and provide IMAP with unlimited storage.

I'm a bit unclear about your setup - are you talking about using POP for a one-time migration, or for collecting mail from external accounts on an ongoing basis?

The best technical arrangement depends on the size of your organization, and whether you want shared folders, calandaring, or other features. SMTP and IMAP are doable with lots of products, and so the groupware/collaboration requirements are often a decider.

---

