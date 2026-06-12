---
title: "just a quick question about debian....."
date: 2009-04-13
forum: The Cafe
---

### Post by Mokoma on 2009-04-13
when i tried to install 5.0.0 about a week ago it took over 3 hours to erasre the data on my harddrive before installing the etx3 filesystem, should it have taken that long?

---

### Post by supersonicdarky on 2009-04-13
Unless you have an rpm <7200, its not a good sign.

---

### Post by Mokoma on 2009-04-13
> **supersonicdarky said:**
> Unless you have an rpm <7200, its not a good sign.

its 7200. ubuntu has no problem it takes like 1 minute to create a ext3/ext4 filesystem, but debian took f-o-r-e-v-e-r :lolflag:

---

### Post by MaxIBoy on 2009-04-13
Was it because you used a net-install CD?

---

### Post by kerry_s on 2009-04-13
there have been a lot of changes in the installer, i'm sure there are a few hiccups here and there. i used the net installer> [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

didn't really pay much attention when i installed gnome yesterday, it was a little slow installing, but gnome has grown since the last time i tried it, it's around 800+ packages, use to be around 600+.

i'm going to do a xfce4 install later today, i'll try and pay more attention and get back to you.

---

### Post by Mokoma on 2009-04-13
> **MaxIBoy said:**
> Was it because you used a net-install CD?

no it was a full iso image, it was ERASING the harddrive data for over 3hours, it could of actually been longer than that.

---

### Post by Mokoma on 2009-04-13
> **kerry_s said:**
> there have been a lot of changes in the installer, i'm sure there are a few hiccups here and there. i used the net installer> [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

didn't really pay much attention when i installed gnome yesterday, it was a little slow installing, but gnome has grown since the last time i tried it, it's around 800+ packages, use to be around 600+.

i'm going to do a xfce4 install later today, i'll try and pay more attention and get back to you.

noooooooooooooo. im not talking about INSTALLING anything. just when it gets to the section saying ERASING DATA FROM XXXX HDD it took over 3/4 hours

---

### Post by MaxIBoy on 2009-04-13
Okay, sounds like your hard drive is screwed up or something.

Go into the BIOS and enable S.M.A.R.T. (which is a hard drive failure warning built into anything manufactured in the last decade.) 

If it doesn't go off, that doesn't mean your hard drive is OK, but if it does go off, it definitively means your hard drive is *not *OK.

---

### Post by kerry_s on 2009-04-13
> **Mokoma said:**
> noooooooooooooo. im not talking about INSTALLING anything. just when it gets to the section saying ERASING DATA FROM XXXX HDD it took over 3/4 hours

i just started installing, the format the drive part took a split second, it was so quick it just flashed and went straight to retrieving packages. i used reiserfs for my install.

---

### Post by swoll1980 on 2009-04-13
There's a bug that will hang it at 33% for a very long time is that where it happened? Might be 34% it's close to 33% I know.

---

### Post by Mokoma on 2009-04-13
> **MaxIBoy said:**
> Okay, sounds like your hard drive is screwed up or something.

Go into the BIOS and enable S.M.A.R.T. (which is a hard drive failure warning built into anything manufactured in the last decade.) 

If it doesn't go off, that doesn't mean your hard drive is OK, but if it does go off, it definitively means your hard drive is *not *OK.

my harddrive is smart enabled, and theres nothing wrong with it as ive only faced this isssue with debian. everything else is fine

> **kerry_s said:**
> i just started installing, the format the drive part took a split second, it was so quick it just flashed and went straight to retrieving packages.

fair enough must have been a glitch!

i shouldnt have bothered anyway. debian is extremely noob unfriendly xD

---

### Post by kerry_s on 2009-04-13
it could be something wrong with ext3, i haven't used ext3 in a long time, it's just to slow for my tastes.

---

### Post by Mokoma on 2009-04-13
> **kerry_s said:**
> it could be something wrong with ext3, i haven't used ext3 in a long time, it's just to slow for my tastes.

huh? ext4 has only been enabled by the linux kernel for about two months hasnt it?? and debian auto installs ext3 as far as i know O.o

---

### Post by Kareeser on 2009-04-13
Why is nobody questioning the obvious?

It's clear that the Debian CD is writing zeros to the hard drive in preparation for the installation.

Ubuntu overwrites the Master Boot Record, which is essentially a table of contents, which is why it only takes a fraction of a second.

It is similar to the partition manager on the Windows install CD asking if you want to format NTFS "quick" or not.

In any case, this is expected behaviour (unless you didn't select a full format).

---

### Post by Mokoma on 2009-04-13
> **Kareeser said:**
> Why is nobody questioning the obvious?

It's clear that the Debian CD is writing zeros to the hard drive in preparation for the installation.

Ubuntu overwrites the Master Boot Record, which is essentially a table of contents, which is why it only takes a fraction of a second.

It is similar to the partition manager on the Windows install CD asking if you want to format NTFS "quick" or not.

In any case, this is expected behaviour (unless you didn't select a full format).

so debian does a dod on your harddrive???????????

---

### Post by swoll1980 on 2009-04-13
> **Mokoma said:**
> so debian does a dod on your harddrive???????????

I don't know what this guy is talking about I've done a hundred installs all with full formats, and it never took more than 30 minutes to do the whole install from start to finish. like I siad before there is a bug in the Debian installer that will cause it to hang at 33% is this what happened?

---

### Post by Mokoma on 2009-04-13
> **swoll1980 said:**
> I don't know what this guy is talking about I've done a hundred installs all with full formats, and it never took more than 30 minutes to do the whole install from start to finish. like I siad before there is a bug in the Debian installer that will cause it to hang at 33% is this what happened?

no it was consistent in speed. or therefore lack of xD

---

### Post by kerry_s on 2009-04-13
> **Mokoma said:**
> huh? ext4 has only been enabled by the linux kernel for about two months hasnt it?? and debian auto installs ext3 as far as i know O.o

what? i use reiserfs, not ext3 or ext4. yes, debian defaults to ext3 if you use the auto option, i go manual when i do my partions, i only use a swap and a /(root), 2 partions.

---

### Post by Kareeser on 2009-04-13
> **Mokoma said:**
> so debian does a dod on your harddrive???????????

It's the same as if you had done a normal format. It is simply writing zeros to the drive IN ADDITION to writing over the master file table (sorry, I meant MFT instead of MBR, it's late.)

You must have checked some option that asked the installer to format your hard drive completely.

---

### Post by Mokoma on 2009-04-13
> **Kareeser said:**
> It's the same as if you had done a normal format. It is simply writing zeros to the drive IN ADDITION to writing over the master file table (sorry, I meant MFT instead of MBR, it's late.)

You must have checked some option that asked the installer to format your hard drive completely.

ummm no i just followed the on screen prompts......

---

