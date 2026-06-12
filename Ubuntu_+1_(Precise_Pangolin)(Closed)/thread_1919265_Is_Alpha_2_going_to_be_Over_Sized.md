---
title: "Is Alpha 2 going to be Over Sized?"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-02-02
Is Alpha 2 going to be Over Sized? Or is it going to be Delayed?

---

### Post by kaldor on 2012-02-02
The alphas, betas, etc are just milestone markers. You can grab [today's daily build]("http://cdimage.ubuntu.com/daily-live/current/") and it'll be identical to Alpha 2.

The last build was yesterday, but just running an update once installed will bring it up to date for today (only a few mb I think).

---

### Post by kevpan815 on 2012-02-02
Yeah, well I usually like to start fresh whenever a New Mile Stone Build comes out.

---

### Post by kevpan815 on 2012-02-02
Re: Alpha 2 is Oversized so be sure to use a DVD and not a CD! Just fyi.

---

### Post by BC59 on 2012-02-02
An annoying bug....

---

### Post by sgage on 2012-02-03
> **BC59 said:**
> An annoying bug....

I believe I read that the final release version is going to be oversized (from a CD standpoint) by design. No more CD's - it's USB sticks or DVD's from now on.

---

### Post by Bucky Ball on 2012-02-03
> **sgage said:**
> I believe I read that the final release version is going to be oversized (from a CD standpoint) by design. No more CD's - it's USB sticks or DVD's from now on.

It's a bug which will hopefully be ironed out by the final release late April 2012. Not by design.

---

### Post by pajn on 2012-02-03
It is by design. The new limit is 750MB

---

### Post by jerrylamos on 2012-02-03
> **pajn said:**
> It is by design. The new limit is 750MB

No problem for me.  On test systems I always have a couple installations, even Lucid LTS or Ocelot or whatever, so on the first partition on the hard drive I put the latest oversized fat .iso and then boot from the .iso using the following entry in 
/etc/grub.d/40_custom:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Pangolin sdb1" {
set isofile="/precise-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
exit 0

```
Oh, yes, sudo chmod 777 /etc/grub.d/40_custom, sudo update-grub and always on a development release back up anything you want to save....if you really want to live dangerously you can even install by booting the oversized .iso, then do a df to see where the isofile is, then do sudo umount -r -l /dev/sdb1 in this case, and install away...

Jerry

---

### Post by jerrylamos on 2012-02-03
My opinion, the reason for the size increase is lots and lots of eye candy and menus and fancy finger sized hieroglypic icons and overlays and ....

Nothing to do with the user's application function...

You have choices.  You're interested in function, there's xubutu and lubuntu.  They'll do everything and at this writing fit on a CD.

You want lots and lots of eye candy and revolving overlaying 3d images and pseudo tablet (with all of tablet's limitations) ... I can hardly imagine it all, there'll be ubuntu.

Jerry

---

### Post by xyzzyman on 2012-02-03
An even more fun way to install is create a RAW VMDK file pointing to the target partition, and install inside VirtualBox... When it's done, just update grub in your main partition, and reboot into your freshly installed Ubuntu. :) 

I don't do seperate home directories for my test installs, otherwise it would be a little more involved.

---

### Post by sgage on 2012-02-03
> **Bucky Ball said:**
> It's a bug which will hopefully be ironed out by the final release late April 2012. Not by design.

Alas, I think you are incorrect. I'm quite sure that they've abandoned the CD-size limit.

---

### Post by cariboo on 2012-02-03
Please quit spreading FUD about disk image size, until we get closer to the release date. It was stated at UDS that the image size can be up to 750MiB **if needed**. We won't see the real size of the iso until the beta is released. The alpha's have always been over sized.

---

### Post by MacUntu on 2012-02-03
> **cariboo907 said:**
> The alpha's have always been over sized.
Please quit spreading FUD about disk image size. :P:P:P

---

### Post by xyzzyman on 2012-02-03
Mine is bigger than yours. [-X

---

### Post by sgage on 2012-02-03
> **cariboo907 said:**
> Please quit spreading FUD about disk image size, until we get closer to the release date. It was stated at UDS that the image size can be up to 750MiB **if needed**. We won't see the real size of the iso until the beta is released. The alpha's have always been over sized.

I said that I had read a statement from an Ubuntu spokesperson that the final release was going to be "oversized", which is true. I wasn't aware they were modifying that statement a bit at UDS. Kindly do not refer to my good-faith reporting of what I read from official Ubuntu sources as "spreading FUD". OK?

---

### Post by Bucky Ball on 2012-02-03
Please check this:

> Warning: This image is oversized **(which is a bug)** and will not fit onto a standard 700MiB CD.... from the daily build page:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

The quote I have given is in red under every ISO image.

---

### Post by kevpan815 on 2012-02-03
> **pajn said:**
> It is by design. The new limit is 750MB

Thank You. I was unaware that the new limit is 750 MB's. It's not a problem for me, although Ubuntu currently does not burn DVD's well on my 2 systems running it, my Mac running OS X Lion Server Edition burns them just fine.

---

### Post by cariboo on 2012-02-03
Everybody says the 750MB limit is a hard limit except for [OMGUbuntu]("http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/"), who updated the article.

---

### Post by jerrylamos on 2012-02-03
Just did Alpha2 installs on a tower and a notebook of oversized .iso (well, larger than a CD) as on my post #9 in this thread.  Went fine.  Some Alpha 2 bugs for launchpad of course.  No DVD or USB required, and fast direct from the hard drive.

Jerry

---

### Post by cgraham on 2012-02-05
[IMG]http://cdimage.ubuntu.com/cdicons/iso.png[/IMG] [precise-desktop-amd64.iso]("http://cdimage.ubuntu.com/xubuntu/releases/precise/alpha-2/precise-desktop-amd64.iso")           01-Feb-2012 19:14  704M  Desktop CD for 64-bit PC (AMD64) computers (standard download)

This the download link for Xubuntu Precise A2 and no where on the page does it say anything about a "Bug".
I downloaded this .iso and it is reported to be 738.5 MB. The link above says 704 MB.

---

