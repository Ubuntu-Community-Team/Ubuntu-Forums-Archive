---
title: "Unable to boot into Ubuntu after update"
date: 2010-06-17
forum: Server Platforms
---

### Post by gencha on 2010-06-17
I logged into one of our development servers (9.10 x64) today to be reminded that the server still requires a reboot. I assumed due to a pending kernel update.
So I rebooted the server and now Ubuntu won't start anymore.
I don't even get the message from grub2 that normally appears during boot time. All I see is the white, blinking caret on an otherwise completely black screen.
So I assumed the update broke grub2 and booted from a desktop live cd. I then went on to re-install grub2 as explained in this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Sadly, it had no effect. 

Then I went home cause it got very late. And now I hope you can give me some ideas for what to try in the morning.

---

### Post by CharlesA on 2010-06-17
If you hold down shift does it show the grub menu?

If you can get that far, you could try booting into a previous kernel and see if it will boot.

---

### Post by gencha on 2010-06-17
Holding down shift has no effect.
If I'm not mistaken grub usually displayed a message like "Press ESC to select different boot options" or something along those lines.
I don't even see that message anymore. And I never touched the grub configuration on that system.

---

### Post by CharlesA on 2010-06-17
Grub was replaced with Grub2 in 9.10, so it doesn't display the menu by default any more. 

It sounds like the machine isn't even getting to the point of loading grub.

---

### Post by gencha on 2010-06-18
Yeah, correct me if I'm wrong. I wasn't expecting to see a menu, but as far as I remember, grub2 displays a message that it will start Ubuntu in 3 seconds if you don't press ESC (or something similar to that).
That's what I expected to see.

---

### Post by gencha on 2010-06-18
After checking the /etc/default/grub again, I noticed that GRUB_HIDDEN_TIMEOUT is set to 0 and GRUB_HIDDEN_TIMEOUT_QUIET is set to true. So, I guess, the line i was expecting wouldn't show up anyway.
Sadly my attempts to regenerate the grub.cfg from the live cd failed. Additionally, holding down shift has no effect either.
So I'm not quite sure if grub2 is running correctly (or at all) or if something else is at fault.

Just to be sure, I also ran memtest86, which brought up no errors.
One of the things I also tried yesterday was simply selecting "Boot from first hard drive" in the Ubuntu CD menu. This gives me the same results.

---

### Post by wilee-nilee on 2010-06-18
The tutorial is excellent but like many of them is chocked full of information that can make it confusing. The simplest way to reload grub2 is this.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You can also boot a live cd and run this command to confirm the grub type.
```
sudo grub-install -v
```
I assume this can be done though I know it works from a running OS

---

### Post by gencha on 2010-06-18
I actually rebuild my grub.cfg following the guide on [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Yet, this still didn't help.

I actually resolved the issue a few minutes ago. Seeing that none of what I tried with grub2 seemed to have any effect, I started to blame the hardware itself. After several changes in the boot order and whatnot (which didn't help at all), I just removed the second hard drive from the system.
And what do you know? The system loads grub2 again and let's me boot.
So I put the second drive back in and reboot. And grub2 still comes up.

So basically, I have changed nothing, but it works again.

Thanks anyway, guys :)

---

### Post by CharlesA on 2010-06-18
Hardware hiccups are awesome. Were you able to run any tests on that second hard drive to make sure it was ok?

---

### Post by gencha on 2010-06-18
Yeah, the system is up and running as if nothing happened.

What confused me the most is, during boot time, the hdd controller displays a list of drives. One drive (the wrong one) shows "Boot" next to it (this should have been an early clue).
But I found no place in the config utilities to change that flag.
What is even more confusing is the fact that right now the wrong disk still shows that flag. So maybe that flag doesn't even have any meaning in the current context.

I really don't understand why it is working now, but I also don't understand why the issue appeared in the first place. Quite unsatisfying.

---

