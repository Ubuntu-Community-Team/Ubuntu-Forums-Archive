---
title: "Chrome OS ISO"
date: 2009-11-21
forum: The Cafe
---

### Post by PhoHammer on 2009-11-21
Can someone make a Chromium OS iso image? That would be very cool. I know there are many 
compiling gurus here that might be able to do this (it's beyond my current skills). What are
your thoughts on the idea?

---

### Post by zagz on 2009-11-21
I dont have a gmail account so cannot install it anyway. :neutral:

---

### Post by myusername on 2009-11-21
there is a virtual machine image in circulation. just try that. IMO chrome os is too slow and buggy right now. its just a waste of time. all it really is right now is the chrome browser

---

### Post by PhoHammer on 2009-11-21
:confused: Gmail accounts are free...

> **myusername said:**
> there is a virtual machine image in circulation. just try that. IMO chrome os is too slow and buggy right now. its just a waste of time. all it really is right now is the chrome browser

Yeah I have installed it in VirtualBox, I just want to see what it's like actually running on my machine.
It's a bit more than a browser and the concept is really cool. It might be buggy, but that's as 
expected this early in the game...

Anyways, I didn't want to get into another "Chrome OS isn't cool" argument. Just wondering
if someone could build an iso...

---

### Post by Psumi on 2009-11-21
> **PhoHammer said:**
> :confused: Gmail accounts are free...

Yeah but, what if you don't plan to check your gmail account ever because you already have an email account with some other company like Microsoft, AOL, etc?

---

### Post by PhoHammer on 2009-11-21
> **Psumi said:**
> Yeah but, what if you don't plan to check your gmail account ever because you already have an email account with some other company like Microsoft, AOL, etc?

Then don't ever check it again...? They flush unused accounts every 9 months or so, it will be okay.

These are some odd excuses not to try something...

---

### Post by Psumi on 2009-11-21
> **PhoHammer said:**
> Then don't ever check it again...? They flush unused accounts every 9 months or so, it will be okay.

These are some odd excuses not to try something...

And if you do not like Chrome, the browser, because of the spyware "feature"?

---

### Post by provoko on 2009-11-21
> **PhoHammer said:**
> Can someone make a Chromium OS iso image? That would be very cool. I know there are many 
compiling gurus here that might be able to do this (it's beyond my current skills). What are
your thoughts on the idea?

[jmml made a USB image]("http://ubuntuforums.org/showthread.php?t=1331975&highlight=chrome+os").  You could put it on a USB stick and boot your computer with it and test it out.  I read that you could boot from a USB image and then install the OS to your PC, at least thats what I think it says [here]("http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions"):

```
WARNING: this nukes your hard drive

Boot from the USB image you just burned. (If this is the first time you've booted from USB, you may need to go into the BIOS settings and change the boot order so that it'll boot from the USB drive)

After logging in, use Ctrl+Alt+T to open a terminal window and type:

/usr/sbin/chromeos-install

Note: this will ask you for the password you set in the recommended step earlier. Unplug the USB drive, reboot and you're there.
```

Thats a script, so check it out to see what it says AND MAKE SURE YOU DON'T OVERWRITE YOUR HARDDRIVE.


> **Psumi said:**
> Yeah but, what if you don't plan to check your gmail account ever because you already have an email account with some other company like Microsoft, AOL, etc?

So check your mail on MS AOL YAHOO... it's a browser.

> **Psumi said:**
> And if you do not like Chrome, the browser, because of the spyware "feature"?

If you don't like Chrome the browser, which is Chrome OS because it's better with it's spyware feature?????...  THEN YOU SHOULDN'T BE HERE!  Please stop thread jacking.

---

### Post by zagz on 2009-11-21
My bad, honestly I thought Gmail was by invite only.

---

### Post by AllRadioisDead on 2009-11-21
> **zagz said:**
> My bad, honestly I thought Gmail was by invite only.
uhm, alright lol.

---

### Post by Psumi on 2009-11-21
> **zagz said:**
> My bad, honestly I thought Gmail was by invite only.

It was at one time.

---

### Post by PhoHammer on 2009-11-22
> **provoko said:**
> [jmml made a USB image]("http://ubuntuforums.org/showthread.php?t=1331975&highlight=chrome+os").  You could put it on a USB stick and boot your computer with it and test it out.  I read that you could boot from a USB image and then install the OS to your PC, at least thats what I think it says [here]("http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions"):

```
WARNING: this nukes your hard drive

Boot from the USB image you just burned. (If this is the first time you've booted from USB, you may need to go into the BIOS settings and change the boot order so that it'll boot from the USB drive)

After logging in, use Ctrl+Alt+T to open a terminal window and type:

/usr/sbin/chromeos-install

Note: this will ask you for the password you set in the recommended step earlier. Unplug the USB drive, reboot and you're there.
```

Thats a script, so check it out to see what it says AND MAKE SURE YOU DON'T OVERWRITE YOUR HARDDRIVE.




So check your mail on MS AOL YAHOO... it's a browser.



If you don't like Chrome the browser, which is Chrome OS because it's better with it's spyware feature?????...  THEN YOU SHOULDN'T BE HERE!  Please stop thread jacking.

Thanks! I'm gonna give it run, see what happens.

---

### Post by Eagles18 on 2009-11-22
Here you go [http://www.megaupload.com/?d=ZTBN6RE0](http://www.megaupload.com/?d=ZTBN6RE0)

---

### Post by PhoHammer on 2009-11-22
> **Eagles18 said:**
> Here you go [http://www.megaupload.com/?d=ZTBN6RE0](http://www.megaupload.com/?d=ZTBN6RE0)

Umm.. why is that called gos-live-2.0.0-by.gumaro.thegeni..iso?

Probably wouldn't download that, as "gos" and 2.0.0 have nothing to do with Chromium OS or Chrome OS...

Anyways, I have been trying to build the USB image, but I am stuck at the step where you
enter this command:
> ./make_local_repo.sh
I get:
> Couldn't find these debs: apt base-files base-passwdetc.

The instructions say to "sudo rm -rf ~/chromiumos/repo before recalling this script" if anything fails. Well I did that and I get:
> chroot: cannot run command `reprepro': No such file or directory

So I give up for now :popcorn:

---

### Post by zagz on 2009-11-22
> **Eagles18 said:**
> Here you go [http://www.megaupload.com/?d=ZTBN6RE0](http://www.megaupload.com/?d=ZTBN6RE0)


!!!!

---

### Post by Paqman on 2009-11-22
> **Psumi said:**
> And if you do not like Chrome, the browser, because of the spyware "feature"?

You think Chromium has spyware? Since it's open source that should be well documented.

---

### Post by SawyerLX on 2009-11-22
good call, im missed that-then noticed 536megs and you mention Gos-heyt that's linux distro test run GOS from distrowatch.com.
keep working on it, there is another thread here - search chrome os.

---

### Post by PhoHammer on 2009-11-23
I have found a USB image and written a much simpler guide to install it to a USB drive here:
[Install Chrome OS to a USB drive]("http://bit.ly/5qDV0C")

---

### Post by provoko on 2009-11-23
> **PhoHammer said:**
> I have found a USB image and written a much simpler guide to install it to a USB drive here:
[Install Chrome OS to a USB drive]("http://bit.ly/5qDV0C")

Cool thanks, I'll reply as soon as I try it.

---

