---
title: "Simple Ubuntu 14.04 lock screen bypass discovered"
date: 2014-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by WogBoy on 2014-04-30
> [h=2]Just hold enter.[/h]                                                                                                               
                                                                     	A user has discovered an embarrassingly simple security security  vulnerability affecting the latest version of Ubuntu, which allows  snoops to bypass the lock screen.
  	Throwing sophisticated hacks and brute forcing to the wind, one  enterprising user found that password protection on machines running [Ubuntu 14.04]("http://www.ubuntu.com/download") could be bypassed by simply holding the enter key for about 30 seconds which crashed the system.
[LEFT][COLOR=#000000]
Read more: [http://www.itnews.com.au/News/384036,ubuntu-lock-screen-bypass-hold-enter.aspx#ixzz30PfUgY4H](http://www.itnews.com.au/News/384036,ubuntu-lock-screen-bypass-hold-enter.aspx#ixzz30PfUgY4H)
[/COLOR][/LEFT]


Me thinks somebody messed up.

---

### Post by ian-weisser on 2014-04-30
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1308572](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1308572)
Reported April 16
Fix Released April 17

Me thinks somebody fixed a newly-discovered vulnerability. Happens regularly.

Oh, and here's a better quote from Oliver Grawert (ogra)                    :
> Just  a sidenote: Unlike what the sensationalist article at heise.de from  today suggests (which links here), this bug was fixed in a heroic effort  over night *before* final release, the fix is on the 14.04 image that  was released to end users.

---

### Post by deadflowr on 2014-04-30
Fixed for me, at least.

---

### Post by 3rdalbum on 2014-05-01
I knew something like this would happen. Like many software developers, Canonical has fallen into the trap of assuming that a lock screen is easy to write, and that "if it works it is good".

This bug has been fixed. What about the rest of the embarrassing bugs that are yet to be uncovered?

---

