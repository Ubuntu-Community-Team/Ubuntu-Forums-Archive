---
title: "Restore a window that I have minimized"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by palimmo on 2012-04-04
Hello!
I'm trying Ubuntu 12.04 beta2 64 bit. It works really good!
But I have some questions and small problems. I'm going to open different threads to discuss about them.

Well.
When I try to restore a window that I have minimized, I obtain a blank view.

I can reproduce this problem if I open more than one window (for example Firefox, Terminal and Nautilus). If I minimize one of them and then I try to reopen it, you can see what happens in the images below.

That seems an ugly bug. Or not?

Thanks!

---

### Post by palimmo on 2012-04-04
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/970140](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/970140)
[http://ubuntuforums.org/showthread.php?t=1949473](http://ubuntuforums.org/showthread.php?t=1949473)

---

### Post by palimmo on 2012-04-04
Wow!
It seems that they have solved it!

Edit: ---NO!---

---

### Post by cariboo on 2012-04-04
From your screenshot, it looks like the windows are open, they just have a white/blank background. Is that what you are seeing?

---

### Post by palimmo on 2012-04-05
> **cariboo907 said:**
> From your screenshot, it looks like the windows are open, they just have a white/blank background. Is that what you are seeing?
Yes. A White unusable background. It happens really often.

---

### Post by cariboo on 2012-04-05
What graphics adapter and driver does your system use?

---

### Post by palimmo on 2012-04-06
> **cariboo907 said:**
> What graphics adapter and driver does your system use?

Nvidia Geforce G105M
and I have problem with both drivers suggested by "additional drivers".

---

### Post by zombifier25 on 2012-04-06
If you have a good memory (or have used Ubuntu for a while without installing the drivers), does the built-in Noveau driver experiences this kind of problem? On my computer the Noveau driver actually works better than the Nvidia-provided ones.

---

### Post by palimmo on 2012-04-06
> **zombifier25 said:**
> If you have a good memory (or have used Ubuntu for a while without installing the drivers), does the built-in Noveau driver experiences this kind of problem? On my computer the Noveau driver actually works better than the Nvidia-provided ones.

I'll do it an opportunity!

---

### Post by mc4man on 2012-04-06
If this is the issue with min'ed windows when going to the 'spread' showing up blank then I'd expect it to fixed fairly soon

While the active bug linked above was a bit old it seems for many this issue was re-introduced with the last compiz upgrade to 0.9.7.4-0ubuntu1 & continues with 0.9.7.4-0ubuntu2

(not uncommon with compiz - fix one thing, break something else

---

### Post by palimmo on 2012-04-07
Someone reported on launchpad having the same problem with intel graphic cards.
So it isn't a strictly nvidia related bug.

---

### Post by palimmo on 2012-04-13
Solved! :guitar:

---

### Post by cariboo on 2012-04-13
> **palimmo said:**
> Solved! :guitar:

How did you solve the problem, inquiring minds want to know. :P

---

### Post by kurja on 2012-04-13
At least for me the problem went away after recent updates.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658)

---

### Post by ubuntu27 on 2012-04-13
> **palimmo said:**
> Someone reported on launchpad having the same problem with intel graphic cards.
So it isn't a strictly nvidia related bug.

Do you mean the bug mentioned in #1 on [this post]("http://ubuntuforums.org/showpost.php?p=11840271&postcount=18")?

It seems to be similar, but not quite since [that bug]("https://bugs.launchpad.net/unity/+bug/976302") only happens when Unity is restarted. But who knows if they might be related.

---

### Post by palimmo on 2012-04-15
> **cariboo907 said:**
> How did you solve the problem, inquiring minds want to know. :P

Simply with the update to unity 5.10.:popcorn:

---

