---
title: "Sync users and passwords amond lan servers"
date: 2006-10-29
forum: Server Platforms
---

### Post by mooseman089 on 2006-10-29
I have 2 separate physical servers, one of them is a web server with ftp and the other is a mail server (courier + postfix), I want to have the exact same users in the group user on them so if somebody changes their password its sync across both servers instead of manually changing it on both. Is this possible and what would be the easiest way of doing?

---

### Post by MJN on 2006-10-29
I have no idea about the security implications of this (having never done it) but you could do something along the lines of copying/syncing **/etc/passwd** and** /etc/shadow** (or at least the relevant parts of them).

As for ensuring this is done in real time I don't know, short of running a cron job regularly checking to see if the files have changed - not very elegant so I'd wait for other ideas before heading down this route.

Indeed, the whole suggestion isn't particularly elegant so perhaps someone might know a more refined, purpose defined, solution.

Mathew

---

