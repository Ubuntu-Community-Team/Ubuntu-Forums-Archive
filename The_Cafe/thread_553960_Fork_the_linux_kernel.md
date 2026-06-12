---
title: "Fork the linux kernel?"
date: 2007-09-18
forum: The Cafe
---

### Post by Acglaphotis on 2007-09-18
I just saw this on /.

[http://linux.slashdot.org/article.pl?sid=07/09/18/131240&from=rss](http://linux.slashdot.org/article.pl?sid=07/09/18/131240&from=rss)

Personally, i think we should fork, starting where Colin Kolivas left.

---

### Post by hardyn on 2007-09-18
can you qualify that a little?  Not tying to be a jerk, but i would like to know why we should consider it, lets turn this in to a proper deabate.
I personally don't know enough about schedulers etc. to really be of any contribution to such a debate, but im sure there are in the UF community.

---

### Post by tehkain on 2007-09-18
Forking it would be stupid. Having a desktop branch might be a good idea but no to forks and spoons. To much FUD.

---

### Post by insane_alien on 2007-09-18
forking would just slow things down. just because someones patch didn't get accepted for the mainline kernel doesn't mean the whole thing is corrupt and evil.

---

### Post by SunnyRabbiera on 2007-09-18
still if someone feels that a fork is needed hey its all GPL in the end

---

### Post by mips on 2007-09-18
Nice inteview with Con here, [http://apcmag.com/6735/interview_con_kolivas](http://apcmag.com/6735/interview_con_kolivas)

---

### Post by Acglaphotis on 2007-09-18
A desktop branch could eliminate the need of a fork though. But having things separete will kinda help organize things.

---

### Post by tehkain on 2007-09-18
> **Acglaphotis said:**
> A desktop branch could eliminate the need of a fork though. But having things separete will kinda help organize things.
Well its would lead to duplication of effort.
My biggest thing is, like echoed on slashdot, what defines a desktop and a server. 
> Slow, scalable algorithms are used rather than lean but limited ones.

If this is true it is actually a good idea. Today's personal computers have a lot in common with high end machines from 10 years ago.
Multiple processors? Check.
Gigabytes of RAM? Check.
Harddisks with hundreds of Gigabytes? Check.

And I guess the trend will continue, so what belongs in the big iron of today will be fine for tomorrow's personal computers.
--

---

### Post by BDNiner on 2007-09-18
coming from a windows environment i like the idea of having separate desktop and server versions of the kernel. But i also agree with the articles in that the current development model that open source software uses does not lend itself well to the maintenance of 2 different kernels. but isn't the point of open source the fact that you can freely obtain to code and make whatever changes you see fit to it, to satisfy your personal needs. That is what large corporations like Novell, IBM  and Red Hat do. and they are the ones who supply a lot of the money for the development of linux. also forking the kernel would hopefully lead to more home use software written for linux.

---

### Post by Beau D. on 2007-09-18
Forking a monlithic kernel isn't alot of fun, nor usually productive. If people are that concerned...then simply compile your own.  Remove the modules you want, add the ones you need etc. Forking the kernel may not even be legal, not sure. Linux may be GPL, but the kernel is owned by one Linus Torvalds. You'd put the desktop fork back years by forking. All new agreements for drivers(Intel anyone?), propagation of said drivers under what a new GPL, BSD type? GPL 3? To many headaches. 

 If anyone is so concerned with what is in their generic kernel..feel free to recompile and gain that 2% performance gain you might get. If you don't kill off something you need, or break your system. 

Beau D.

---

### Post by justin whitaker on 2007-09-18
The really big issue here is how the scheduler works, which you can patch without forking the kernel. So there really is no need to have a completely separate desktop kernel: just pick up where CK left off.

---

### Post by Lord Illidan on 2007-09-18
Has anyone used these -ck patches here? Are they that good?

And, I am mostly against forking. There are already too many applications which have been forked to hell, a fork of the kernel would be crazy..

---

### Post by JNowka on 2007-09-18
Before you vote fork or not, may I suggest reading this real quick.  

[http://www.linux.com/feature/119256](http://www.linux.com/feature/119256)

My vote is to not fork, nor branch the Linux kernel.

---

### Post by BDNiner on 2007-09-18
I actually switched to the low latency kernel and overall i feel my computer runs better. It took 3 complete reinstalls before it worked correctly and i don't think that my hardware is unsupported, everything was detected on the live CD and after the install. 

maybe instead of a fork of the kernel there should be more quality home desktop software written, as opposed to the enterprise applications that dominate linux now

---

### Post by K.Mandla on 2007-09-18
I've used the -ck patches in Arch, but got no improvement on my hardware. I respect that some people find them more responsive, but a fork to me would be an unnecessary effort.

---

### Post by Beau D. on 2007-09-18
> **BDNiner said:**
> I actually switched to the low latency kernel and overall i feel my computer runs better. It took 3 complete reinstalls before it worked correctly and i don't think that my hardware is unsupported, everything was detected on the live CD and after the install. 

maybe instead of a fork of the kernel there should be more quality home desktop software written, as opposed to the enterprise applications that dominate linux now

 Now that I couldn't agree more with.

Beau D.

---

### Post by angryfirelord on 2007-09-18
I'd spork it! ;)

I think the kernel is fine the way it is. Even if a fork came around, it probably wouldn't get much support and would be playing catchup with the other kernel.

---

### Post by Lord Illidan on 2007-09-18
I also think many apps should be streamlined somewhat. Firefox, Open Office, the entire Gnome and KDE desktops, Eclipse, Beagle, are just a few of what I have in mind. If the apps are not written properly, then the OS isn't at fault.

---

### Post by angryfirelord on 2007-09-18
> **Lord Illidan said:**
> I also think many apps should be streamlined somewhat. Firefox, Open Office, the entire Gnome and KDE desktops, Eclipse, Beagle, are just a few of what I have in mind. If the apps are not written properly, then the OS isn't at fault.
Sure. That's why there's Opera, Abiword/Gnumeric, XFCE, Geany, & find. ;)

Or better yet: lynx/links/elinks, groff, frame buffer console, and vi/emacs.

---

### Post by Daishiman on 2007-09-19
This is a storm in a teacup. If anything, the current performance issues are due to the size of the software that runs on top of the kernel (GNOME, KDE, etc.). I really don't see where people are claiming that the desktop is unresponsive; I've had amarok and gcc taking over the entire CPU time and time again and neither movies nor audio stuttered. If that happens to you you can blame the most likely unoptimizes graphics or audio drivers; worst case de disk I/O scheduler might be to blame.

But c'mon, even with the O(1) scheduler it handles loads much better than any other OS I've seen. At least I can have amarok and konqueror go wild without having to reboot, unlike Windows, where you can get your entire system locked up because Explorer.exe's decided time out on failed I/O next year.

GTK, QT, X.Org and pals are much more likely to blame for performance. Besides, like it's been said, the difference between a server load and a desktop load is quite minimal nowadays, and frankly a masive kernel quagmire for 2% performance increase is simply not worth it. If it is to you, run Gentoo.

---

### Post by K.Mandla on 2007-09-19
> **Daishiman said:**
> This is a storm in a teacup. If anything, the current performance issues are due to the size of the software that runs on top of the kernel (GNOME, KDE, etc.). I really don't see where people are claiming that the desktop is unresponsive; I've had amarok and gcc taking over the entire CPU time and time again and neither movies nor audio stuttered. If that happens to you you can blame the most likely unoptimizes graphics or audio drivers; worst case de disk I/O scheduler might be to blame.

But c'mon, even with the O(1) scheduler it handles loads much better than any other OS I've seen. At least I can have amarok and konqueror go wild without having to reboot, unlike Windows, where you can get your entire system locked up because Explorer.exe's decided time out on failed I/O next year.

GTK, QT, X.Org and pals are much more likely to blame for performance. Besides, like it's been said, the difference between a server load and a desktop load is quite minimal nowadays, and frankly a masive kernel quagmire for 2% performance increase is simply not worth it. If it is to you, run Gentoo.
Wow. I wish I had written that. Big +1.

---

### Post by Polygon on 2007-09-19
> **Daishiman said:**
> This is a storm in a teacup. If anything, the current performance issues are due to the size of the software that runs on top of the kernel (GNOME, KDE, etc.). I really don't see where people are claiming that the desktop is unresponsive; I've had amarok and gcc taking over the entire CPU time and time again and neither movies nor audio stuttered. If that happens to you you can blame the most likely unoptimizes graphics or audio drivers; worst case de disk I/O scheduler might be to blame.

But c'mon, even with the O(1) scheduler it handles loads much better than any other OS I've seen. At least I can have amarok and konqueror go wild without having to reboot, unlike Windows, where you can get your entire system locked up because Explorer.exe's decided time out on failed I/O next year.

GTK, QT, X.Org and pals are much more likely to blame for performance. Besides, like it's been said, the difference between a server load and a desktop load is quite minimal nowadays, and frankly a masive kernel quagmire for 2% performance increase is simply not worth it. If it is to you, run Gentoo.


i agree with this statement as well. I mean... what is the REAL difference between a server and a desktop/laptop computer? They are both still considered ' computers'... but one usually has a GUI..... but then if your saying that desktop computers arnt responsive. like daishiman said, your starting to get into the real of X/QT/GTK and all that stuff that could be the culprit

---

