---
title: "Frequent Freezing 13.10"
date: 2013-09-20
forum: Ubuntu Development Version
---

### Post by Kevin_Belrey on 2013-09-20
At least once a day, my OS freezes and I have to do a hard shutdown and turn back on.  Any Ideas where to start?

---

### Post by Kevin_Belrey on 2013-09-20
Any advice on where to start, anyone???

---

### Post by QIII on 2013-09-20
[I]Moved to [B]Ubuntu +1.


[/B][/I]13.10 is still pre-release.  This Forum is the appropriate place for this question.

---

### Post by sudodus on 2013-09-20
> **Kevin_Belrey said:**
> Any advice on where to start, anyone???

Which flavour are you running? I know that Lubuntu has a problem with the cooperation between the kernel and zRAM, see this link [Random lockups with Lubuntu 13.10 beta1 64 bit]("http://ubuntuforums.org/showthread.php?t=2175010")

Or do you think it's another problem?

---

### Post by Kevin_Belrey on 2013-09-21
I'm running Regular Gnome Ubuntu 13.10.

---

### Post by sudodus on 2013-09-21
Check with this command if you have zRAM running:

```
swapon -s
```

and post the output in a reply. You can copy and paste from the terminal window to the editing window of the Ubuntu Forums, mark the output text and click the **#** icon at the top of the editing window to put it within CODE tags.

---

### Post by santosh83 on 2013-09-21
Hi, I experienced the same problem (random hard freezing), but then I was pointed to this well known bug in the kernel zram code. It has been fixed but the patches have not yet reached Saucy it seems. And even the previous 3 versions have the same problem apparently. If you observe carefully you'll see that the freezes mostly happen when your memory load is high, which is when the zram swap device is used by the kernel, leading to the lockup. I turned off zram use by the simple command:

```
sudo service zram config stop
```

and for the past several hours have not had any freezes even under high memory usage.

Since this is a kernel level bug it wouldn't matter which flavour one uses, and until the fixes percolate to every system it is best to use the above command to turn off zram. Note that zram is not the same as the usual swap (although it uses a portion of the overall swap) and it is not essential for proper system functioning.

---

### Post by santosh83 on 2013-09-21
Well I spoke too soon it seems. Had a hard lockup even after I'd turned off all zram.

Perhaps it is a hardware issue at my end, as I'd originally thought...? So much for the much vaunted stability of Linux! :-(

I do have an encrypted home directory enabled, due to which the swap parition is also encrypted. Maybe this has something to do with it... No idea at this point. :-(

---

### Post by sudodus on 2013-09-21
> **santosh83 said:**
> Well I spoke too soon it seems. Had a hard lockup even after I'd turned off all zram.

Perhaps it is a hardware issue at my end, as I'd originally thought...? So much for the much vaunted stability of Linux! :-(


... or another instability of this new kernel?

By the way, have you tested your RAM with memtest yet?

---

### Post by grahammechanical on 2013-09-21
This has just happened to me. Ubuntu+Unity 13.10. It used to happen a couple of weeks ago and I thought it was cured. But just now after using Libreoffice for some hours the system froze completely. No movement of mouse or keyboard. No Ctrl+Alt+F2 or anything like that. No choice but a hard shutdown.

I have indicator-multiload running and that freezes as well but nothing has maxed out. Not CPU. Not memory. Not hard disk activity. When this was last happening I used top but there was nothing eating up resources.

Regards.

---

### Post by santosh83 on 2013-09-21
> **sudodus said:**
> ... or another instability of this new kernel?

By the way, have you tested your RAM with memtest yet?

Yes that was one of the first things I did. Actually I didn't wait till Memtest was fully finished but nevertheless it ran for about an hour and there were zero errors with my RAM. That's what initially made me suspect the mainboard chipset (Intel G41-P33, MSI, quite old by today's standards) was somehow locking up under the new kernel, but it seems it's happening to many people, so it's unlikely to be my hardware...

On the other hand, I just ran a session of flightgear (the heaviest, hardest driving app I have installed) without the system locking up, whereas before (with zram) flightgear was almost always guaranteed to lead to a freeze. :-) I have just 1Gb so FG consumes ~95% of memory when running. Turning off zram *has* made a difference but it seems there are other gremlins lurking within the sys still! :-/

---

### Post by sudodus on 2013-09-21
@[grahammechanical]("http://ubuntuforums.org/member.php?u=1087323"), You can test by deactivating zRAM

```
sudo swapoff /dev/zram0
sudo swapoff /dev/zram1
# ... depending on how many processors you have
sudo rmmod zram
```

and see if it freezes again. At this stage I think it is important to find out if the kernel freezes also without zRAM.

---

### Post by sudodus on 2013-09-21
> **santosh83 said:**
> Turning off zram *has* made a difference but it seems there are other gremlins lurking within the sys still! :-/

Yes, I'm afraid there are more gremlins lurking ... 13.10 was very promising earlier, but these bugs that appear late in the release cycle ...

---

### Post by santosh83 on 2013-09-21
> **sudodus said:**
> You can test by deactivating zRAM

```
sudo swapoff /dev/zram0
sudo swapoff /dev/zram1
# ... depending on how many processors you have
sudo rmmod zram
```

and see if it freezes again. At this stage I think it is important to find out if the kernel freezes also without zRAM.

I used

```
sudo service zram-config stop
```

I suppose it is equivalent to your instructions including the rmmod?

As I said previously, I have had one crash after zram was turned off as well. I had both normal Firefox as well as Tor browser open together and ~85% of 1Gb RAM was used. There was no significant swap activity prior to the lockup.

Subsequently I used Flightgear which used up nearly all the RAM and the system *didn't* crash... so mixed signals. :-/

It would be interesting if anyone can reproduce this freezing with VirtualBox/VMWare. I guess that might even allow someone familiar with kernel internals to pinpoint the place in the code when everything stops...

---

### Post by sudodus on 2013-09-21
I don't know enough to say if the two methods are equivalent. I received the 'swapoff and rmmod method' from a zRAM expert in the Lubuntu mail community.

---

### Post by santosh83 on 2013-09-21
> **sudodus said:**
> I don't know enough to say if the two methods are equivalent. I received the 'swapoff and rmmod method' from a zRAM expert in the Lubuntu mail community.

It seems to be equivalent though.

The two swapoff commands gave "swapoff: /dev/zram0: swapoff failed: No such file or directory" and rmmod gave "Error: Module zram is not currently loaded"

Can't figure out a command to disable it though. Giving ```
sudo update-rc.d zram-config disable
``` says

```
update-rc.d: warning: /etc/init.d/zram-config missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/zram-config do not exist.
```

---

### Post by jerrylamos on 2013-09-22
I get frequent freezes with 13.10-x on switching between windows with Alt-Tab.

Leave a little bit of each window visible and switching with cursor select works normally.

No way to do ubuntu-bug when it's frozen since nothing works but the cursor.

---

### Post by cariboo on 2013-09-22
> **santosh83 said:**
> It seems to be equivalent though.

The two swapoff commands gave "swapoff: /dev/zram0: swapoff failed: No such file or directory" and rmmod gave "Error: Module zram is not currently loaded"

Can't figure out a command to disable it though. Giving ```
sudo update-rc.d zram-config disable
``` says

```
update-rc.d: warning: /etc/init.d/zram-config missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/zram-config do not exist.
```

Wouldn't zram be running as a service, and the command to turn it off should be:

```
sudo service zram off
```

---

### Post by santosh83 on 2013-09-22
> **cariboo907 said:**
> Wouldn't zram be running as a service, and the command to turn it off should be:

```
sudo service zram off
```

That's indeed what I used to turn off zram. In fact:

```
sudo service zram-config stop
```

which works, but zram is again enabled on next reboot. I was looking for a way to permanently disable it, hence that update-rc.d attempt which failed.

---

### Post by VMC on 2013-09-22
> **Kevin_Belrey said:**
> I'm running Regular Gnome Ubuntu 13.10.

If this is [Ubuntu Gnome]("http://ubuntugnome.org/"), then yes I use to get freezes at various times. I could **always** get it to freeze by clicking the Gnome3 Activities **Empathy**. Evolution would freeze sometimes, but Empathy anytime. Throughout the day though it would freeze for seemingly unknown reason..until I installed nvidia-173 video driver. Now nothing freezes. nouveau obviously is the reason.

---

