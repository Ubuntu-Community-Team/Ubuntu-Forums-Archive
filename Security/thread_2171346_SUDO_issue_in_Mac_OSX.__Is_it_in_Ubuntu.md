---
title: "SUDO issue in Mac OSX.  Is it in Ubuntu?"
date: 2013-08-30
forum: Security
---

### Post by fyfe54 on 2013-08-30
I was alarmed to read this today.  [http://www.zdnet.com/apple-mac-flaw-gives-hackers-super-status-root-access-7000020061/]("http://www.zdnet.com/apple-mac-flaw-gives-hackers-super-status-root-access-7000020061/")

Is this in Ubuntu?  is it something to be worried about?

---

### Post by Hungry Man on 2013-08-30
It definitely *used* to allow unprivileged users to change the time. I would hope they finally fixed it, but part of me doubts they ever bothered to.

---

### Post by 3rdalbum on 2013-08-31
> **fyfe54 said:**
> I was alarmed to read this today.  [http://www.zdnet.com/apple-mac-flaw-gives-hackers-super-status-root-access-7000020061/]("http://www.zdnet.com/apple-mac-flaw-gives-hackers-super-status-root-access-7000020061/")

Is this in Ubuntu?  is it something to be worried about?

a. The attacker has to be able to run code on your computer first.

b. There are easier ways to get root on an Ubuntu machine if you can already run code on it as user.

c. It's probably only a problem on Apple's special version of 'sudo'. Apple's engineers have a history of not being very security-conscious. As long as the code runs, it'll pass Apple's QA.

---

### Post by Hungry Man on 2013-08-31
> [COLOR=#000000]a. The attacker has to be able to run code on your computer first.[/COLOR]

Yes, any RCE or SE attack will allow this.

> [COLOR=#000000]b. There are easier ways to get root on an Ubuntu machine if you can already run code on it as user.[/COLOR]

How? You can either attack a root service or the kernel, or attempt to trick the user into allowing for root. Or... you can just change the time. Seems pretty easy.

> [COLOR=#000000][INDENT]c. It's probably only a problem on Apple's special version of 'sudo'. Apple's engineers have a history of not being very security-conscious. As long as the code runs, it'll pass Apple's QA.[/INDENT]
[/COLOR]
Definitely not Apple specific. It has to do with sudo checking the time "Oh, did they just have root? I'll allow root commands if they did without password prompt." So if you can change the time you can always have root. Ubuntu didn't require root for a long time, not sure if they still don't/ if they ever fixed it. And Apple is about as security conscious (maybe moreso?) than Canonical lol

Avoiding the terminal won't help as long as, at some point, you've used it to gain root. I doubt it'll help at all actually even if you never used it.

---

