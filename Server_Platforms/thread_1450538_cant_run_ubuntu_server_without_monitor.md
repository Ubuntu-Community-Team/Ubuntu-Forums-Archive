---
title: "cant run ubuntu server without monitor?"
date: 2010-04-09
forum: Server Platforms
---

### Post by JUSTINBEAIRD on 2010-04-09
i have a web server, nas server sitting in the corner of my room and just upgraded to lucid via ssh and it is quite strange that 
ubuntu server wont start unless a monitor is plugged in and i really don't want a monitor sitting in the corner

---

### Post by wojox on 2010-04-09
You must have a GUI on that thing huh?

---

### Post by JUSTINBEAIRD on 2010-04-09
> **wojox said:**
> You must have a GUI on that thing huh?

nope just ubuntu server
openssh, lamp, samba, squid, bind9

---

### Post by wojox on 2010-04-09
That is weird. They say you shouldn't upgrade via ssh, but I've done it as well. No problems. That was 8.10 to 9.04 though. 

Are you login in through another Linux box or Windows and PuTTy?

---

### Post by JUSTINBEAIRD on 2010-04-09
> **wojox said:**
> That is weird. They say you shouldn't upgrade via ssh, but I've done it as well. No problems. That was 8.10 to 9.04 though. 

Are you login in through another Linux box or Windows and PuTTy?

ssh'd from linux
I was running 9.10 upgraded then rebooted and nothing happened held in the power button to do a hard shutdown and still nothing plugged in a monitor and it started right up tryed it a few more times with the monitor and it started every time unplugged the monitor and it will not start

and when i turn it on without a monitor then plug one in it is blank

---

### Post by wojox on 2010-04-09
I had a problem with the 10.04 desktop edition where I had to edit the grub file. May want to try it, may work may not.

```
sudo nano /etc/default/grub
```

Scroll down to the line: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash" and add &#8220;nomodeset&#8221; at the end.

So it looks like this: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash nomodeset"

Then run: sudo update-grub

---

### Post by R.Bucky on 2010-04-09
I have a server that will not boot up unless it has a keyboard attached... What's next?...

---

### Post by moetunes on 2010-04-09
> I have a server that will not boot up unless it has a keyboard attached... What's next?...
normally that is a bios option - is it newer or older h/ware you're using?

---

### Post by volkswagner on 2010-04-09
> **R.Bucky said:**
> I have a server that will not boot up unless it has a keyboard attached... What's next?...

If you BIOS is so old or just sucks, you may want to try a utility called [NOF1.com]("ftp://ftp.compaq.com/pub/softpaq/sp0501-1000/SP0667.ZIP").

It is made for Compaq MOBO's and I'm not sure if it works with other vendors...Use at your own RISK!...LOL

It is the only thing I have found other than hanging a keyboard on the PC.

---

### Post by JUSTINBEAIRD on 2010-04-09
well its still not booting without a moniter

---

### Post by Iowan on 2010-04-09
Some machines (HP's?) have a "server mode" in the BIOS that (aside from requiring password to be set) lets them boot without keyboard - dunno if it helps with monitor.

---

### Post by JUSTINBEAIRD on 2010-04-09
> **Iowan said:**
> Some machines (HP's?) have a "server mode" in the BIOS that (aside from requiring password to be set) lets them boot without keyboard - dunno if it helps with monitor.

well it worked just fine with 9.10 so dout it has anything to do with bios

---

### Post by NullHead on 2010-04-09
So, you know this computer isn't working because you cannot ssh into the machine, or the machine doesn't respond if you plug in a monitor after it's already been booted? 

I'm thinking either the IP changed, the network device isn't coming up, sshd isn't working properly, or there's something halting the boot.

---

### Post by papibe on 2010-04-10
> **R.Bucky said:**
> I have a server that will not boot up unless it has a keyboard attached... What's next?...

In order to make my old Pentium 4 IBM work as a headless server, I had to set two BIOS parameters: (1) enable an option called something like "Keyboardless Operation", and (2) disable all network booting protocols.

In my case, my machine used two boot most of the time. However, sometimes the keyboard error (2 loud beeps) triggered PXE (a network booting protocol). 

Now it boots considerable faster, no beeps, and so far so good.

Regards.

---

### Post by JUSTINBEAIRD on 2010-04-10
> **NullHead said:**
> So, you know this computer isn't working because you cannot ssh into the machine, or the machine doesn't respond if you plug in a monitor after it's already been booted? 

I'm thinking either the IP changed, the network device isn't coming up, sshd isn't working properly, or there's something halting the boot.

it is assigned a static ip i already checked the router and it is not connecting and if you plug in a monitor the screen is completely blank and wont do anything at all no matter how many times you do a hard shutdown 

but if you plug in a monitor and start it everything works every time 

so i think it is probing for a monitor when it shouldnt be and not finding one and not continuing boot

this is an old dell dimension 2400 worked fine with 9.10

---

### Post by Dayofswords on 2010-04-10
no idea, but i went and found the manual

[http://support.dell.com/support/edocs/SYSTEMS/dim2400/en/F75560LRs.pdf](http://support.dell.com/support/edocs/SYSTEMS/dim2400/en/F75560LRs.pdf) (PDF)

and driver page from dell
[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&os=WW1&osl=en&catid=&impid=&SystemID=DIM_PNT_P4_CEL_2400](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&os=WW1&osl=en&catid=&impid=&SystemID=DIM_PNT_P4_CEL_2400)

---

### Post by NullHead on 2010-04-10
> **JUSTINBEAIRD said:**
> it is assigned a static ip i already checked the router and it is not connecting and if you plug in a monitor the screen is completely blank and wont do anything at all no matter how many times you do a hard shutdown 

but if you plug in a monitor and start it everything works every time 

so i think it is probing for a monitor when it shouldnt be and not finding one and not continuing boot

this is an old dell dimension 2400 worked fine with 9.10

I wonder if Xorg got installed on accident. I guess if Xorg crashes when it's booting, then that might be the cause. Then again, on a desktop system, you can restart/crash xorg all you want and still have access to your ttys on F1, F2 etc. 

Try downloading the ISO of 10.04beta2 (that's what you tried to upgrade too, right?) and boot it as a live environment.

---

### Post by SakJur on 2010-04-10
> **NullHead said:**
> I wonder if Xorg got installed on accident. I guess if Xorg crashes when it's booting, then that might be the cause. Then again, on a desktop system, you can restart/crash xorg all you want and still have access to your ttys on F1, F2 etc. 

Try downloading the ISO of 10.04beta2 (that's what you tried to upgrade too, right?) and boot it as a live environment.

NullHead: There is no live enviorment for Ubuntu Server.

---

### Post by volkswagner on 2010-04-15
Have you solved this yet?

I would investigate the files located at /etc/X11

I don't have 10.04 running so I wont post my contents.  Perhaps someone else can compare if you post yours.

Have you tried the following?

```
dpkg-reconfigure x11-common
```

---

