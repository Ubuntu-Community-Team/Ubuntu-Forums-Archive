---
title: "Live-anything doesn't work"
date: 2012-04-29
forum: System76 Support
---

### Post by Newbunto on 2012-04-29
I am trying to make a Live-something so that I can boot from it in the  event that my Ubuntu laptop becomes unbootable for some reason (and so  that I can do a clean backup and so that I can do a reinstall and ...).

I followed the instructions linked to but the results so far are not promising.

What I have tried so far:

Download ubuntu-11.10-desktop-amd64.iso
Verified good download by MD5 value

Burned to CD at lowest possible burn speed.

Boot  from CD starts to work. Get some cryptic icon and can choose Language  and get Help etc. Can choose "Try Ubuntu without installing". That goes  for a little while and then I get a lot of white text on a black screen.  It isn't obvious from any of the text that there is an error message  but it's all fairly cryptic.

At that point it will echo what I  type but nothing that I have typed has resulted in any kind of response.  (I don't know whether it really is expecting me to type something or is  just pausing to show me the text or input is asynchronous with respect  to the boot process.)

Has the boot failed? What state is it in?

The  only thing that appears to elicit any meaningful response is  Ctrl-Alt-Del, which results in a bit more output and then restarts.

From  reading other posts, someone is bound to say that the burn was no good.  So I followed the procedure to make a bootable USB flash drive. The  result was basically the same as with the CD.

When booting, the last line of output says

[9.895005] sd 6:0:0:0: [sdc] Attached SCSI removable disk

(The exact numbers at the beginning of the line in square brackets vary.)

I don't think I can *easily* get the full text but I can post more (i.e. previous lines of output) if someone thinks it will help.

How  long should a boot from CD take? How long should a boot from USB flash  drive take? (With the USB flash drive I waited about 10 minutes.)

Giving  up on that, I thought that maybe there is a bug that is fixed in 12.04  so I downloaded ubuntu-12.04-desktop-amd64.iso and created a bootable  USB from that.

No luck.

At one point I got "No DEFAULT or  UI configuration directive found!" and a prompt "boot:". That message  doesn't help me. I see from the internet that other people have had that  problem but I wasn't able to get anywhere.

I wondered whether  maybe there's a 64 bit problem so I wanted to try the 32 bit version  (even though it won't actually solve my problem). Aaaarrrgggh! Between  the time of downloading the 11.10 64 bit iso and all this failure, the  11.10 32 bit iso has gone away (can't see where to download it). Is it  still available for download somewhere?

That's as far as I have got.

I  may try to buy a new flash drive. Does anyone know definitively how a  flash drive should be partitioned and how it should be formatted (file  system type, file system parameters) in order to use it to boot from?

Does  it make any difference whether I use F2 to get into BIOS setup and  alter the boot order or use F7 to choose boot options? Both seemed to  have the correct effect (boot from other than the normal boot device)  but neither seemed to work once the boot started.

---

### Post by Newbunto on 2012-04-30
ubuntu-12.04-desktop-i386.iso doesn't work either. Tried that burnt to CD. CD drive shows activity for about 5 minutes then goes quiet and nothing ever happens after that. Up to that point I have got the menu offering "Try Ubuntu without installing", which I choose.

MD5 says that the copy on the CD is identical to the downloaded copy is identical to the original on the net (to a high degree of probability).

---

### Post by sibir on 2012-04-30
I am experiencing the same issue. I just updated from 11.10 to 12.04, and failed the purity test, choosing which partition to put grub on. I went with sda1 instead of sda, so now I need to repair from the live cd, but the live cd is DOA.

Any ideas?

---

### Post by isantop on 2012-04-30
What URL are you guys downloading from? Is it the official [www.ubuntu.com](www.ubuntu.com) page or something like cdimage.ubuntu.com? Downloading from the latter may mean you got the Apple CD for Mac computers, which won't work in our systems.

Also, make sure you have the Desktop CD, not a DVD, and not the Alternate CD. Both of these are untested, and we don't check their reliability with our systems.

---

### Post by sibir on 2012-04-30
I downloaded from ubuntu.com. 

I just got off the phone with system76 support and they cleared it right up for me. It turns out that in order to run the live cd, you must first hit f6 on the live cd's first menu. There you select "nomodeset" and then try to run the live cd.

---

### Post by Newbunto on 2012-04-30
> **isantop said:**
> What URL are you guys downloading from?

I am starting at [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop), choosing 32 bit or 64 bit (I've tried both), and clicking on "Start download". Beyond that it is difficult to tell what the final resulting URL is.

I will try the "nomodeset" thing later today.

---

### Post by Newbunto on 2012-05-01
> **sibir said:**
> There you select "nomodeset"

Thank you! I have finally managed to boot a live CD (11.10 64bit).

---

### Post by Newbunto on 2012-05-06
I should add that I also managed to boot a live USB flash drive.

---

### Post by Newbunto on 2012-05-06
Since it is bound to come up ... while that trick works for doing "nomodeset" on a Live-something, I assume that it won't work on reinstalling Ubuntu. That is, after installing Ubuntu, you may need to add "nomodeset" (temporarily or permanently?). The internet says that in order to add "nomodeset" temporarily during a boot of an installed Ubuntu, hold down the Shift key during the boot. That will pause in GRUB and you can make a temporary change to the boot options.

NB: I haven't tried the reinstall yet so don't know at all what will be needed.

---

### Post by isantop on 2012-05-07
> **Newbunto said:**
> Since it is bound to come up ... while that trick works for doing "nomodeset" on a Live-something, I assume that it won't work on reinstalling Ubuntu. That is, after installing Ubuntu, you may need to add "nomodeset" (temporarily or permanently?). The internet says that in order to add "nomodeset" temporarily during a boot of an installed Ubuntu, hold down the Shift key during the boot. That will pause in GRUB and you can make a temporary change to the boot options.

NB: I haven't tried the reinstall yet so don't know at all what will be needed.

Once you've installed, all you need to do is run the System76 Driver and install the Nvidia driver to get everything set up.

---

### Post by Newbunto on 2012-07-13
> **isantop said:**
> Once you've installed

I still haven't got around to reinstalling but I did do a full install onto a USB flash drive (just for emergency booting).

> **isantop said:**
> , all you need to do is run the System76 Driver and install the Nvidia driver to get everything set up.

Not necessarily disagreeing with what you wrote but the nomodeset thing is needed twice.

You need it once on the Live USB (or CD).

Then you do "Install". When it installs it won't automatically add the nomodeset.

So on the *first* reboot from the newly installed disk, you need to stop in GRUB and edit in the nomodeset.

Then I installed the nVidia driver and this (apparently) removes the need for nomodeset on any subsequent reboots.

This is all in accordance with the instructions on the System 76 web site.

---

### Post by isantop on 2012-07-13
> **Newbunto said:**
> I still haven't got around to reinstalling but I did do a full install onto a USB flash drive (just for emergency booting).



Not necessarily disagreeing with what you wrote but the nomodeset thing is needed twice.

You need it once on the Live USB (or CD).

Then you do "Install". When it installs it won't automatically add the nomodeset.

So on the *first* reboot from the newly installed disk, you need to stop in GRUB and edit in the nomodeset.

Then I installed the nVidia driver and this (apparently) removes the need for nomodeset on any subsequent reboots.

This is all in accordance with the instructions on the System 76 web site.

That's an excellent point. In the future, perhaps it would be a good idea to check what parameters Linux was booted with before installing, then echo those into the Grub configuration for the installed system.

---

### Post by Newbunto on 2012-07-18
Yes, I thought about that but then once you have installed the nVidia driver it seems that the nomodeset is not needed - and there probably isn't an easy way to make it go away once it is not needed, particularly for novice users like me.

There may be a down side to using nomodeset if it's not needed. I don't know.

One thing that I noticed is that the install created multiple items in GRUB. In addition to the default boot, it created a recovery boot and the recovery boot has the nomodeset present. I don't know whether it always puts nomodeset on the recovery boot or put it there because it rightly saw that at the time the install was done nomodeset had been used.

The good aspect of this is that even if someone got stuck after the install (didn't know how to work GRUB), the recovery boot should still work.

Possibly the right answer is that if the install detected that the user used nomodeset to boot the Live-whatever then the install should warn the user before the restart after the install that most likely ... nomodeset will continue to be needed on each boot until appropriate video drivers are installed, *tell the user how to edit it in on booting*, and suggest that those drivers get installed ASAP. A variation would be to give the user the option of getting the install to make nomodeset permanent i.e. if the user doesn't intend to install the drivers.

---

### Post by isantop on 2012-07-18
> **Newbunto said:**
> Yes, I thought about that but then once you have installed the nVidia driver it seems that the nomodeset is not needed - and there probably isn't an easy way to make it go away once it is not needed, particularly for novice users like me.

There may be a down side to using nomodeset if it's not needed. I don't know.

One thing that I noticed is that the install created multiple items in GRUB. In addition to the default boot, it created a recovery boot and the recovery boot has the nomodeset present. I don't know whether it always puts nomodeset on the recovery boot or put it there because it rightly saw that at the time the install was done nomodeset had been used.

The good aspect of this is that even if someone got stuck after the install (didn't know how to work GRUB), the recovery boot should still work.

Possibly the right answer is that if the install detected that the user used nomodeset to boot the Live-whatever then the install should warn the user before the restart after the install that most likely ... nomodeset will continue to be needed on each boot until appropriate video drivers are installed, *tell the user how to edit it in on booting*, and suggest that those drivers get installed ASAP. A variation would be to give the user the option of getting the install to make nomodeset permanent i.e. if the user doesn't intend to install the drivers.

The true solution is for Nvidia to not be lazy any more and develop KMS support in the open source drivers (support in the proprietary drivers would be nice to). Or better yet, release some specs on the GPUs so that the best drivers can be the open source drivers anyway.

Anyway, nomodeset does cause problems on non-Nvidia Systems, but the Nvidia drivers don't care about that parameter anyway, so it doesn't really have an effect.

---

