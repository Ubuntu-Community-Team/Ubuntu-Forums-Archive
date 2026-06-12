---
title: "Dual boot with two hard drives"
date: 2009-05-14
forum: The Cafe
---

### Post by Ozor Mox on 2009-05-14
There are a couple of PC games I'd really like coming out soon and I might have to finally give in after two years and install Windows somewhere so I can play them. Of course, I'll still use Ubuntu for everything else except that! My new desktop came with two hard drives, so I'd like to put XP on the second, especially as I want to keep the two systems completely separate. Is it as simple as selecting the drive from the BIOS menu to boot in to that OS? I've read in a few places that while installing the second OS you should disconnect the hard drive for the first. Is this just a precaution to prevent picking the wrong drive in the installer, or is it necessary?

I think this is my preferred solution to buying a Mac. This one costs £0, buying a Mac costs a considerable amount more!

Also, sorry about the tidal wave of threads, I had a lot of ideas queued up :D

---

### Post by Bölvaður on 2009-05-14
> **Ozor Mox said:**
>  Is this just a precaution to prevent picking the wrong drive in the installer[..]?

yes it is just so you dont mess things up by an accident.

---

### Post by oomingmak on 2009-05-14
In Ubuntu v9.04 the installer has FINALLY stopped trashing the MBR of other drives which you have not given it permission to write to (and then getting the device numbers wrong so that you are left with an unbootable system).

However, you need to be sure you select the correct device under the "Advanced" button hidden away on the final review page before installation starts.

Of course, the safest method is to just disconnect the other drives so that that can be no mistakes made, but it *can *now be done successfully with all drives connected, if you're using v9.04.

---

### Post by Ozor Mox on 2009-05-20
I was chatting to a friend the other day who dual boots and he reckons that if I tell Windows to install to my blank second hard drive, it will still try to overwrite GRUB on the first drive. This seems really dumb to me, if I tell the OS to install to a hard drive it should not touch the others. I don't put it past Windows to ignore this sense though, since it seems to like to eat other operating systems...

Is there any other way to disable a hard drive or do I really have to physically disconnect it by opening the computer?

---

### Post by PhilMize on 2009-05-20
> **Ozor Mox said:**
> There are a couple of PC games I'd really like coming out soon


I'm gunna go out on a whim here and guess your talking about diablo and starcraft correct?

:mrgreen:

---

### Post by Ozor Mox on 2009-05-20
> **PhilMize said:**
> I'm gunna go out on a whim here and guess your talking about diablo and starcraft correct?

:mrgreen:

Haha actually no I've never played either of those games despite all the good things I hear about them. Maybe I'll give them a try when they're out.

The games I want to try are The Sims 3, Cities XL and Empire: Total War. It's really annoying because I can do everything I want with Ubuntu and occasionally Windows in a VM *except* play games... And the temptation... Agh!

I was really hoping now I have two hard drives it would be as simple as installing one OS to each and selecting which to boot...

---

### Post by Skripka on 2009-05-20
> **Ozor Mox said:**
> I was chatting to a friend the other day who dual boots and he reckons that if I tell Windows to install to my blank second hard drive, it will still try to overwrite GRUB on the first drive. This seems really dumb to me, if I tell the OS to install to a hard drive it should not touch the others. I don't put it past Windows to ignore this sense though, since it seems to like to eat other operating systems...

Is there any other way to disable a hard drive or do I really have to physically disconnect it by opening the computer?

Just turn the machine off, open the box, and pull the power plug off the linux HDD.  That easy.

---

### Post by Ozor Mox on 2009-06-03
> **Skripka said:**
> Just turn the machine off, open the box, and pull the power plug off the linux HDD.  That easy.

I guess that is quite easy really, on a desktop at least!

If I disconnect my primary Ubuntu hard drive, install XP on to the secondary hard drive, and then reconnect the first, GRUB will not see any difference will it? Does anyone know how to set up GRUB so that it will have an option to boot from the secondary (XP) hard drive?

---

### Post by walkerl on 2009-06-03
This may not be much help to you, but I have a dual boot, using 2 HD's I did unplug the linux drive when install windows, just so I wouldn't select the wrong one. You can configure grub so, when you boot up, you can select which OS to use.

---

### Post by Ozor Mox on 2009-06-03
> **walkerl said:**
> This may not be much help to you, but I have a dual boot, using 2 HD's I did unplug the linux drive when install windows, just so I wouldn't select the wrong one. You can configure grub so, when you boot up, you can select which OS to use.

Yeah that's pretty much what I want to do, since I don't want to format my drives and install Windows before Ubuntu just because Windows is too crud to install to a second hard drive without destroying the first!

Do you remember how you configured GRUB to see the OS on the second hard drive and boot it?

---

### Post by hatten on 2009-06-03
Just read up on a GRUB man-page or google!

---

### Post by Slug71 on 2009-06-03
I have a desktop with 2 120GB HDDs.

First HD is XP on a 20GB partition and a second partition with the rest of the space for my media.

Second drive is partitioned in 4 equal sizes for Win 98, Fedora, Xandros and Mandrake.

I has Xandros's bootloader as default which gives me the option to load each Linux OS and Windows.
If i select Windows it then gives me the option to load XP or 98.

I set it up back in 2004 though so cant really remember how i did it.

I know i did Windows XP First.

---

