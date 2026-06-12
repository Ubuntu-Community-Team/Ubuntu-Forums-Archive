---
title: "Once again, a awfull experience with Linux"
date: 2007-06-10
forum: Testimonials &amp; Experiences
---

### Post by Rorsch on 2007-06-10
Every year I try a couple of distros, just to explain to people why I use Windows. This year I tried Ubuntu 7.04 and the results were worst than previous years. 

Trying to install it in a dual boot with XP on a raid0 was just too much pain, so I tried it on a external hd (via usb). Installation went ok, first load and... grub error 21, that was strange, I had the external hd connected to the pc. Reboot, next step: forcing it to boot from the external hd... "can't load the OS".

Ok, let me try to get back to windows... since grub error 21 doesn't let me load XP I'll try and force the pc from the local hd... I couldn't, it appears that I had no OS on my local hd. 

Windows XP cd, try to fix the mess... no hardrives on my computer? Weird, don't remember taking them off... maybe, just maybe, the raid0 drivers went *kaboom*? 

Installed the drivers for the raid0, fixboot, fixmbr and finally I'm back in Windows XP... how I missed you

Ubuntu didn't took 25min to install, it wasn't Smart or Easy for sure...

[if any of you have solutions for any of these problems please explain them to me, I really wanted to try Ubuntu]

---

### Post by mikeua89 on 2007-06-10
First, I'd have to say that if you're trying out Linux just to prove "why [you] use Windows," then of course you are going to run into problems.

But you should give the Ubuntu distro a chance.  I experimented with a few distros in the past, and found them all to be too difficult, especially because I have been a Windows user for so long and have been used to the "Windows way."  Ubuntu is different from the other distros, but it still requires a learning curve, because it's not Windows.

My suggestion is to install Ubuntu in a simplified environment.  I dual boot between XP and Ubuntu, but I have just a single IDE HD, not a RAID.  Heck, you could pick up a used PC from a garage sale that would most likely run Ubuntu.

If you're sincere about giving Linux a fair shot, then stick with it and continue researching and experimenting.

---

### Post by Rorsch on 2007-06-10
> **mikeua89 said:**
> First, I'd have to say that if you're trying out Linux just to prove "why [you] use Windows," then of course you are going to run into problems.

That was a mean way of saying it, I'm just pissed at Ubuntu for not working

> **mikeua89 said:**
> My suggestion is to install Ubuntu in a simplified environment.  I dual boot between XP and Ubuntu, but I have just a single IDE HD, not a RAID.  Heck, you could pick up a used PC from a garage sale that would most likely run Ubuntu.

Yeah, that's what I think I'll do, install it an old pc just to check it out (but I wanted it in mine :S)

---

### Post by Mazza558 on 2007-06-10
If you have no reason to leave Windows, why try and change?

---

### Post by Rorsch on 2007-06-10
> **Mazza558 said:**
> If you have no reason to leave Windows, why try and change?

just a curious guy

---

### Post by Geekkit on 2007-06-10
> **Rorsch said:**
> Every year I try a couple of distros, just to explain to people why I use Windows. 
...

[if any of you have solutions for any of these problems please explain them to me, I really wanted to try Ubuntu]

Solution is go back to Windows, you're happier there.

---

### Post by Rorsch on 2007-06-10
> **Geekkit said:**
> Solution is go back to Windows, you're happier there.

yeah, guess so... bunch of bitter guys around here, maybe you had to kill a family member to get it to work

---

### Post by fjf on 2007-06-10
Com'on, calm down.  People here are helpful and usually nice, but they dont like to be jerked around with the windoze comparison all the time.  Try a different approach: be polite.  It will work.  It did for me, a looooooooooong time windoze user, and now an ubuntu (almost) convert (but with an XP partition for the kids games).

---

### Post by PhatStreet on 2007-06-10
> **Rorsch said:**
> yeah, guess so... bunch of bitter guys around here, maybe you had to kill a family member to get it to work
Nah, everyone's experiences are different due to hardware. I've personally not had many problems except my laptop, but using the distro Arch Linux taught me a lot and I've gotten everything working.
Some people just prefer the interface and control of a Linux system over a Windows/Mac one, but if you're happy with XP, there's not much reason to try to switch.

I'd honestly recommend you try it in VMWare first, then if you really love it, then you can spend the effort getting it to work.

---

### Post by mortenkjeldgaard on 2007-06-10
If you want a good experience with Linux, you should install it on a separate IDE or SATA disk. You can probably get hold of an old one, 10 Gb is more than enough. Make that disk the MASTER. Ubuntu will locate XP on the other disk and configure GRUB accordingly. The advantage is that you will not touch your XP installation at all.

When Windows XP boots, it expects to be on the C: drive (i.e. the master) but it wont be. However, GRUB will fool it so it thinks it is.

Installing Linux on an external USB disk is something that is very difficult to get to work. It completely depends on how your hardware handles USB. Some motherboards boot up with only USB v.1.1 working, and you can't boot from that. Try installing Windows XP on an external USB drive and you'll see the same thing...

I agree with the other posters, that if you are only trying out Linux to see it fail, then it's not for you. OTOH, if you want to have some fun with your computer, why not give it a go, and be patient?

Good luck,
Morten

---

### Post by Mazza558 on 2007-06-10
> **Rorsch said:**
> yeah, guess so... bunch of bitter guys around here, maybe you had to kill a family member to get it to work

I wasn't being bitter, or trying to deter you from trying Linux, I was just wondering why.

---

### Post by Kobalt on 2007-06-10
You know Rorsch, there is a great thing about Ubuntu : the LiveCD. Just put it in your drive, let it fly, and here you go, you're running Ubuntu on your machine. It's easy and it's safe, it lets you test Ubuntu without touching a single part of your HD... Why not trying that out first ? :)
You know when you come up, as a new forum user, and your first post is : "come one it's not working, I give up", it's not that really constructive... Post your problem in the appropriate sections as new threads and you'll get some good help :)

---

### Post by Rorsch on 2007-06-11
> **Kobalt said:**
> You know Rorsch, there is a great thing about Ubuntu : the LiveCD. Just put it in your drive, let it fly, and here you go, you're running Ubuntu on your machine. It's easy and it's safe, it lets you test Ubuntu without touching a single part of your HD... Why not trying that out first ? :)
You know when you come up, as a new forum user, and your first post is : "come one it's not working, I give up", it's not that really constructive... Post your problem in the appropriate sections as new threads and you'll get some good help :)

I tried the live CD, and was suprised for having sound from the start (I need the driver for XP and Vista), but as any live CD, it's a bit slow.

Tried now with Wubi (not giving up), but a bunch of I/O errors appear when I load Ubuntu.

I'm just sharing my experience with Ubuntu so people won't feel bad when they can't make it work too "at least one guy doesn't find it easy and fast, i'm not alone"

---

### Post by Chuq on 2007-06-14
> **Rorsch said:**
> I tried the live CD, and was suprised for having sound from the start (I need the driver for XP and Vista), but as any live CD, it's a bit slow.

So this sounds like an issue with live CDs, not with Ubuntu.

> I'm just sharing my experience with Ubuntu so people won't feel bad when they can't make it work too "at least one guy doesn't find it easy and fast, i'm not alone"

As others have said - have you tried installing XP on an external USB disk?

You have to compare apples with apples.  You run XP as the only OS on your primary IDE/SATA hard drive, so when comparing it to Ubuntu, it is only fair that you do the same.

---

### Post by yota on 2007-06-14
Trying to keep the focus on problems more than on "what is better than what", I suppose that the main issue comes from the fact that windows is probably installed on a raid 0 fakeraid.

Have a look at [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) to know what fakeraid is:
> 
In the last few years, a number of [WWW] hardware products have come onto the market claiming to be IDE or SATA RAID controllers. These have shown up in a number of [WWW] desktop/workstation motherboards. Virtually none of these are true hardware RAID controllers. Instead, they are simply multi-channel disk controllers combined with special BIOS configuration options and software drivers to assist the OS in performing RAID operations. This gives the appearance of a hardware RAID, because the RAID configuration is done using a BIOS setup screen, and the operating system can be booted from the RAID.

To install Windows onto a RAID device, you must provide a driver (usually on a floppy disk) to the Windows installer in order to access the RAID array. Under Linux, which has built-in softRAID functionality that pre-dates these devices, the hardware is normally seen for what it is -- multiple hard drives and a multi-channel IDE/SATA controller. Hence, fakeRAID.

Unfortunately handling fakeraid is not a newb task an as a bottom line it's unlikely to get satisfied trying to install linux on such a system.
The viable workaround is to add another internal disk and install ubuntu on it.

Hope this helps!

---

### Post by Kobalt on 2007-06-14
> **Rorsch said:**
> 
Tried now with Wubi (not giving up), but a bunch of I/O errors appear when I load Ubuntu.
Wubi is still in developpment, you'd rather use the AlternateCD for example if you have troubles installing.

---

### Post by stuman on 2007-06-16
If you really want to just try out Linux, I recommend you download the free vmware player from vmware and pick any "appliance" which has a cd and about 10 gb virtual hard drive, download the ubuntu install iso, configure the virtual appliance to use it and build yourself a virtual ubuntu computer.  you get to try out the features and ease of use of ubuntu without disrupting the xp install.  i run ubuntu in a virtual machine all of the time...even have a virtual ubuntu server running at home.

---

### Post by vexorian on 2007-06-16
> **Rorsch said:**
> I tried the live CD, and was suprised for having sound from the start (I need the driver for XP and Vista), but as any live CD, it's a bit slow.

Tried now with Wubi (not giving up), but a bunch of I/O errors appear when I load Ubuntu.

I'm just sharing my experience with Ubuntu so people won't feel bad when they can't make it work too "at least one guy doesn't find it easy and fast, i'm not alone"
But you only wanted to test it so you can dismiss it, so the live cd was enough.

I'd like to mention the live cd detects swap partitions, I noticed that when I was installing feisty, thus it is possible to format a part of the hd as swap and live cd will use it so it should be faster, I guess it could even load to virtual memory instead of using CD cause the live cd was very fast for me, perhaps 768MB of RAM also help.

---

