---
title: "apt-get stalls"
date: 2005-07-07
forum: Repositories &amp; Backports
---

### Post by urue on 2005-07-07
I keep having a recurring problem with apt-get stalling. My /etc/apt/sources.list looks exactly like the one on [www.ubuntuguide.org](www.ubuntuguide.org). I run apt-get upgrade and it will get part way through a package from “security.ubuntu.com horary-security” and then it will just stall. If I kill apt-get with Ctrl-C, and then re-run apt-get upgrade, it will get a little bit further through the package that had stalled previously. Repeating this procedure (Ctrl-C when stalled and then re-run apt-get upgrade), I can eventually get the patch. If I just leave it go, eventually I get a “Connection timed out” error. Any ideas on what I’m missing? Thanks.

---

### Post by varunus on 2005-07-07
What's your internet connection?  I know some people have had problems with wireless disconnecting and reconnecting and apt not continuing after the reconnect...

---

### Post by ajtim on 2005-07-07
[QUOTE=varunus]What's your internet connection?  I know some people have had problems with wireless disconnecting and reconnecting and apt not continuing after the reconnect...[/QUOTE]

There are nothing with internet connection. Look After four days or Synaptyc download is slow.
I have now fifth or sixt day very slow speed  and nothing help. Problem is something in Ubuntu but nobody know?? nothing.
I downloaded from many sites without problem, Synaptyc on Debian work without problem, SuSE on the other machine has not a problem but Ubuntu has...and i didn't change nothing.,..

---

### Post by timelord726 on 2005-08-02
I doubt it's the internet connection.  Every computer at my dad's place running Linux, desktop or laptop, wired or wireless, this all happens on.  Just about every time.

---

