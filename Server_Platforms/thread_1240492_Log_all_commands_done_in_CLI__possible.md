---
title: "Log all commands done in CLI ? possible?"
date: 2009-08-14
forum: Server Platforms
---

### Post by starr0stealer on 2009-08-14
Is it at all possible to log every command entered in CLI on Ubuntu Server 9.04.

There are several users in the company that uses the OpenSSH connection and does several things on the two servers. despite the fact I have many times requested that they log these commands in a flat file, as I do, they still have yet to do so.

I want to log any command done, so that when something isn't working, I can trace it back to the command line that may have triggered this flaw.

---

### Post by andrewc6l on 2009-08-14
Some shells put things in a file - bash uses ~/.bash_history. But you'll never be able to get around a malicious user - they just need to build a shell that doesn't record history and they can bypass it.

Not to mention that works only for shells - once you get into something like mysql it won't get logged.

---

