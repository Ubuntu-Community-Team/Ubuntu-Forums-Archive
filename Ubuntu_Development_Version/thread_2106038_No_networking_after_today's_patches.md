---
title: "No networking after today's patches"
date: 2013-01-17
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2013-01-17
I just patched my main test machine with today's updates and.... networking no longer starts up.  So, beware.

I'm off to see if I can figure out what broke now.

---

### Post by 3vi1 on 2013-01-17
There seems to be a bug in the latest network-manager package.  I backleveled the package and can connect fine again.

---

### Post by Harry33 on 2013-01-18
> **3vi1 said:**
> There seems to be a bug in the latest network-manager package.  I backleveled the package and can connect fine again.

Well that was not the issue in your original post.
Network-manager has not been updated for some time in RR repos.

Sometimes during shut down and booting or rebooting the network card fails to reset.
If this happens, it always helps to shut down the pc and in addition to that, cut the power completely.

---

### Post by 3vi1 on 2013-01-18
I had completely powered-down and rebooted at least 3 times before back-leveling network-manager, and have /never/ had a problem like what you describe with the network card on reboot (and I've been running Linux on this system for years).  So, I don't think that was the issue.

But, you're right that the network-manager package itself hasn't been updated recently (since the 9th, or so).  So, the problem must be in the way the current network-manager interacts with some other package that was updated on the 17th. When I back-leveled it, I just installed the quantal version.

I'll trouble-shoot it some more when I have time this weekend, I just didn't have the time to last night since this is my main desktop.

---

### Post by kevpan815 on 2013-01-19
No problems here, with a Full Nightly Build Download, and then Clean Install, have not even been using zsync due to a problem with a dark screen during install (as I mentioned earlier in a different post) am waiting to see if it gets fixed, so I am sorry to tell you that your trying to Update through the program itself rather than using zsync is what caused your problem.

---

### Post by cariboo on 2013-01-19
I did 3 new installs yesterday, 

[LIST=1]
[*]Gnome Remix 12.10
[*]Gnome Remix Raring
[*]Ubuntu
[/LIST]

The Gnome Remix 12.10 was just that, with all the current updates, the Gnome Remix Raring, was an upgrade from 12.10 900+ packages updated, and Ubuntu was yesterday's daily i386 live. In all 3 cases wireless networking now connects flawlessly, and instantly even when coming out of suspend. This is on a 2009 vintage Compaq netbook with an Atom N270 cpu and 1 GiB ram.

I wanted to get into the fun of having multiple installs, so I plan to install Xubuntu and Debian later on today.

---

### Post by dmiranda on 2013-01-20
Same here. After the kernel update the network doesn't work

---

### Post by jdthood on 2013-01-20
> **dmiranda said:**
> Same here. After the kernel update the network doesn't work

What network hardware and drivers do you have?

---

### Post by ft_ on 2013-01-22
Do you still suffer from this bug ?

With 3800 kernel, no problem, but with 3801 I can only use wifi (ethernet does not work at all).

---

