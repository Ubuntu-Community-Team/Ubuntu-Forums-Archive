---
title: "Codelite IDE - suspicious network access"
date: 2009-09-25
forum: Security
---

### Post by aallxx on 2009-09-25
Hi, 

May someone enlighten me on why Codelite IDE [binary install, Jaunty64 & Karmic32], at IDE shutdown, tries to contact the host 'p3slh138.shr.phx3.secureserver.net' ? 

I've searched for 'p3slh138' on the net and have found nothing. Haven't compiled the IDE for a test [yet].

TIA, 
Alexandre

--------
ADDENDUM
--------

Behaviour observed on revisions 2759 and 2893 obtained from Ubuntu public
repositories for Karmic Koala 32 and Jaunty Jackalope 64 [both binary
and compiled from source] and on a compiled version of revision 3040 
obtained from Sourceforge SVN.

**SOLVED**
Issue cleared by CodeLite author, Eran Ifrah.

---

### Post by eranif on 2009-09-25
Hi Alex,

I have anwswered you on email, yet, I will answer here as well:

p3slh138.shr.phx3.secureserver.net is actually [www.codelite.org](www.codelite.org)

On startup, codelite perform http requrest to [www.codelite.org/packages.txt](www.codelite.org/packages.txt) to get the latest release information

This is done to check for new upgrades

Btw, You can ping both addresses:

```
ping p3slh138.shr.phx3.secureserver.net
``` and ```
ping www.codelite.org
``` and you will notice that both are
resolving into the same IP address "208.109.181.212"

You may choose to disable this network activity from codelite's menu: settings -> editor -> misc, and disable the 'check for new version on startup'

Its perfectly safe. You can also checkout the sources and have a look at what codelite does (the relevant source is webupdatethread.cpp)

Eran

---

### Post by aallxx on 2009-09-26
First, thank you very much for your prompt response 
and for clearing the issue to me Mr. Ifrah.

My system reside behind a proxy, without direct connection
to the internet, with my *official* services talking to the net 
through **http env-var** / **Gnome proxy settings**. Toying with the
IDE for the first time, I've noticed that it appeared to freeze at 
shutdown of short sessions. 

Some investigation shows me [**netstat** & **lsof**] that CodeLite 
was waiting for a 'SYN_SENT' to an ip address which my DNS
resolved to the friendly named host *p3slh138*, prompting this
*what-the...lets-jump-to-suspicious-mode* guy to make noise... :(

Really sorry, please accept my apologies for any incovenience.

Yours truly,
Alexandre

---

