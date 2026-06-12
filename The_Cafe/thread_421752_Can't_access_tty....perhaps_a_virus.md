---
title: "Can't access tty....perhaps a virus?"
date: 2007-04-24
forum: The Cafe
---

### Post by lakersforce on 2007-04-24
Ok, so I am having the same problem as so many others when I try to install Feisty Fawn.

I remember when this bug popped up in beta and I reported it, then went back to 6.10 for the time being.

I have tried all the fixes suggested, all to no avail. Even the Alternate cd does not work. A upgrade from 6.10 to 7.04 over the internet works for me, though.

But I really wanted to put Ubuntu back on my machine after having tried out some other linux distros. So I thought the easiest way would be to install my beta cd of Feisty and then do a cd-rom upgrade from there.

So I popped the good old reliable Beta disk in my drive and started to boot. I was astonished!! Even the Beta disk, which I know worked just fine before because I have used it, gave me the excact same error!!!

Maybe we are dealing with some really nasty virus here.

---

### Post by Brunellus on 2007-04-24
absent facts--the nature of the error, the precise error message, and the type of error--we could be dealing with anything.

---

### Post by tbroderick on 2007-04-24
It's not a virus. Just a bug that Ubuntu hasn't dealt with yet. It's the 2.6.20 kernel that is screwing things up. Some systems have to use piix. When installing Feisty from the CD, I believe  if you boot with the added break-top command, you will boot to a busybox prompt. Once there you can modprobe piix and then exit the shell. It should work.

---

### Post by lakersforce on 2007-04-24
> **tbroderick said:**
> It's not a virus. Just a bug that Ubuntu hasn't dealt with yet. It's the 2.6.20 kernel that is screwing things up. Some systems have to use piix. When installing Feisty from the CD, I believe  if you boot with the added break-top command, you will boot to a busybox prompt. Once there you can modprobe piix and then exit the shell. It should work.

But it does not work! Of course I have already tried it out.

And I have not changed any hardware recently.

My point is that my beta disc of Feisty worked fine the first time I installed it. I installed the beta version a couple of weeks before the error first showed up and were reported. Now my beta disc gives me the error! And it is the excact physical same disc!! Think about it a moment.

I dont want to scare the community . I just would like a discussion about it. It might be a virus, it might not.

---

### Post by markoloka on 2007-04-25
Same here... but difference is that... my pc hasn't been online since i installed from beta. So no virus can go my hdd. I noticed one thing: there seems to data on all partitions ubuntu intsallation (failed in middle of installing software) so format all partitions and try  again. Gparted live cd is nice tool for that.
My pc there's data on: /boot, / and swap.

---

### Post by Crashmaxx on 2007-04-25
I get a similar error here. Its "/bin/sh: can't access tty; job control turned off" but its on a Clonezilla live cd, and only on one specific machine.

Has to be a kernel bug.

---

