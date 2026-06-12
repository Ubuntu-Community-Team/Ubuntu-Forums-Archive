---
title: "How can I be 100% sure that the installed distro is not corrupt?"
date: 2014-06-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Rytron on 2014-06-18
Hi.

This is an example scenario.

I download an ISO of an Ubuntu based distro and it matches the checksum.
I use the dd command to put it onto a 16 GB pen drive.
It installs fine onto PC but has the usual new release bugs but they are not critical.

How can I be sure that the pen drive is not corrupt or the ISO was corrupted when installing onto the pen drive? Or is it a case that it would never install from the pen drive if it was corrupted in some way?

---

### Post by Dreamer Fithp Apprentice on 2014-06-19
I wouldn't answer so vaguely if it hadn't been 21 hours since you posted but at this point maybe half an answer is better than none.

I know with cds or dvds you can do an md5sum for the finished disk and it should match that of the iso. There are 2 different procedures depending on whether the disk was burned DAO or TAO. I would imagine there is probably a similar procedure for pen drives. Hopefully that may at least suggest some search strategies for you.

---

### Post by Bucky Ball on 2014-06-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Moved as theoretical and not a support request. Please post in the appropriate support forum when you have real-world issues. Thanks.

> **Rytron said:**
> 

I download an ISO of an Ubuntu based distro and it matches the checksum.


In that case, nothing wrong with the ISO. Can you insert the disk, open a file manager and see the files? If so, that would probably rule out a faulty USB dongle.

PS: There are numerous 'Ubuntu-based' spins, not all of them supported here.

PPS: You will get nothing if you use the dd command. That just copies the files. You need to create a bootable USB, probably using UNetbootin or Universal USB installer in Windows (from memory). Simply copying the files over achieves nothing. You won't be booting from that dongle so the rest of your enquiry becomes redundant. :-k

---

### Post by cariboo on 2014-06-19
dd creates an exact image of the iso, so as far as I'm concerned, if the md5sums match after downloading an image you're good to go. The only way I can see a problem when using dd, is if your system has been compromised, and dd replaced.

---

### Post by Bucky Ball on 2014-06-19
> **cariboo907 said:**
> dd creates an exact image of the iso, so as far as I'm concerned, if the md5sums match after downloading an image you're good to go.

So am I wrong to say that dd will only copy the files in the ISO across and not create bootable media? Confused. :-k

---

### Post by buzzingrobot on 2014-06-19
I use dd all the time to burn install images to USB sticks. The incantation looks like this:```

sudo dd if=image-to-burn.iso of=/dev/sdX  bs=4M  && sync

```
...where "/dev/sdX, of course, is the location of the USB stick, which I typically find by running mount after plugging it in.  Here, I have two drives in the machine, /dev/sda and /dev/sdb, so a USB stick is invariably on /dev/sdc (if it's the only one attached).

"bs=4M" says write 4 megs worth of bytes per pass, and sync runs when dd completes successfully to flush the buffers to the stick. (Sync is essential.)

Frankly, for a GUI tool to use on Ubuntu I think Mint's USB formatter and burner -- MintStick -- can't be beat. Works like a charm.

---

### Post by sudodus on 2014-06-19
> **Bucky Ball said:**
> So am I wrong to say that dd will only copy the files in the ISO across and not create bootable media? Confused. :-k

I agree with cariboo907 and buzzingrobot, and I have made an own tool, [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073"). It is a shell-script that makes it safer to use dd (the infamous 'disk destroyer', that does what you tell it to do without questions, even if you tell it to wipe valuable data, that you have not backed up yet).

For iso files to work when flashed into USB drives, they should be *hybrid* iso files. All current Ubuntu flavour iso files work (except Ubuntu 12.04 LTS mini.iso, but Ubuntu 13.10 and 14.04 LTS mini.iso work).

---

### Post by grahammechanical on 2014-06-19
The installer is not the distro. I have tested many ISO images during the development cycle where the live session would not load or the installer would not run but that says nothing about the code that gets installed on to the hard disk.

What do you mean by "corruption." The Ubuntu Quality Assurance team run all kinds of automated tests before and during the building of ISO images before those images are put on the QA Testing Tracker page for download and manual testing.

[http://www.theorangenotebook.com/2014/03/a-simple-look-at-testing-within-ubuntu.html](http://www.theorangenotebook.com/2014/03/a-simple-look-at-testing-within-ubuntu.html)

[http://ci.ubuntu.com/](http://ci.ubuntu.com/)

[http://ci.ubuntu.com/smokeng/](http://ci.ubuntu.com/smokeng/)

The only way you can be 100% sure that the installed distro is not corrupt is to get involved and become a member of the QA team. In my opinion.

---

### Post by Bucky Ball on 2014-06-19
Thanks all. Learn something everyday. Sorry for straying off topic. As we were. ;)

---

### Post by Dreamer Fithp Apprentice on 2014-06-19
> **grahammechanical said:**
>  . . . What do you mean by "corruption." The Ubuntu Quality Assurance team run all kinds of automated tests before and during the building of ISO images before those images are put on the QA Testing Tracker page for download and manual testing. . . . OP Rytron can correct me if I'm wrong but I believe you've misconstrued the question.> **Rytron said:**
>  . . . example scenario.

I download an ISO of an Ubuntu based distro and it matches the checksum.
. . .
How can I be sure that the pen drive is not corrupt or the ISO was  corrupted when installing onto the pen drive? The wording is  perhaps a little ambigous, but my understanding is that he is wondering how to check for the possibity that the burn process (if you want to call it a burn, by analogy to CDs) didn't go quite right - that the finished thumb drive doesn't quite match the iso perfectly. I've only made a live thumb once and I didn't use DD so I'm not conversant with it's options or if it automatically checks for errors by default but Finagle knows it's a sensible question.

Rytron:
```
man dd
``` might be worth checking out. I just glanced at it. I didn't see anything like a verify option, but I just glanced, I didn't study it. And it does suggest an info coreutils command for further documentation that I didn't investigate. For future burns I'd check out some of the programs that are more specialised specifically for burning live thumbs  from an iso. It wouldn't be surprising if one of them had a verify option. When burning CDs or DVDs for example k3b has such an option and I don't see any reasons programs intended for burning thumbs couldn't also.

But to check a thumb you've already made, those aren't options. Something like the md5sum approach I mentioned earlier,  (assuming there is/are (a) procedure(s) for thumbs like there are for CDs) is a general answer. But it occurs to me now there is probably an even easier one for the specific case. Ubuntu live disks used to contain a self check program for exactly the purpose you are asking about, assuming I correctlly understood your question.  I presume they still do although I don't have a recent one to check because I've used the mini.iso the last few times I installed from scratch. At one point the self-check was actually in the opening menu, but, unfortunately imo, Canonical, in pursuit of the "dumb it down to pop it up" marketing strategy, took it out of the menu but, at least on the last "regular" installer disk I've seen (I'm not sure which one that was, Oneiric maybe), the option was still there in hidden menu options. To expose the additional options you had to press some particular key, Esc or maybe one of the F-n keys, I forget, at a particular point in the boot process (I believe when the menu first appears),  then you'll get an option that is titled something like "check disk integrity". I'm sure there is a tutorial for this somewhere in these forums. You should be able to find it with a few minutes search.

---

### Post by sudodus on 2014-06-19
What you could do to really verify it, is to run the built in md5sum test for all files in the iso file (available at least in some installers).

You can also reverse the dd process (but make sure you write exactly as many bytes from the pendrive as you wrote to it). Then you can create another iso file, which should be identical to the original one (test with diff or with md5sum).

I have used both these methods, and I know that they work. However, flashing a USB pendrive is much more reliable than burning a CD or DVD, and I think it very seldom fails, unless the pendrive has bad sectors. But in that case the flashing stops with an error message or does not even start.

---

### Post by ssam on 2014-06-23
On an installed system you can use the program debsums to check that files match the checksum of the .deb packages that they came from.

---

### Post by Rytron on 2014-06-24
> **sudodus said:**
> ...You can also reverse the dd process (but make sure you write exactly as many bytes from the pendrive as you wrote to it). Then you can create another iso file, which should be identical to the original one (test with diff or with md5sum)...

Hi sudodus.

How could that be done?

---

### Post by Rytron on 2014-06-24
> **ssam said:**
> On an installed system you can use the program debsums to check that files match the checksum of the .deb packages that they came from.

Cheers ssam.

---

### Post by Rytron on 2014-06-24
Thanks to all that posted info in this thread.

---

### Post by Dreamer Fithp Apprentice on 2014-06-24
This is probably of interest:
[http://askubuntu.com/questions/466619/how-to-authenticate-a-startup-disk-image](http://askubuntu.com/questions/466619/how-to-authenticate-a-startup-disk-image)

---

### Post by Rytron on 2014-06-25
> **Dreamer Fithp Apprentice said:**
> This is probably of interest:
[http://askubuntu.com/questions/466619/how-to-authenticate-a-startup-disk-image](http://askubuntu.com/questions/466619/how-to-authenticate-a-startup-disk-image)

Thanks Dreamer Fithp Apprentice.

---

