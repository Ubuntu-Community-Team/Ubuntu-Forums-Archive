---
title: "Safely delete hard disk"
date: 2008-09-30
forum: Security
---

### Post by Lucrezia on 2008-09-30
Hello!

i have to send my notebook to repair, but since i don't want the customer care to put the nose in my HD i have to safely delete it. Following to this guide:

[http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)


I burned an ubuntu 8.04 live cd and from the live console i typed:

ubuntu@ubuntu:~$ shred -vfz -n 100 /media/disk
shred: /media/disk: failed to open for writing: Is a directory


/dev/sda1 and /dev/sda2 start, but obviously they aren't my hd... what to do?


thanks!

---

### Post by Louis de Broglie on 2008-09-30
Never tried to do that .:)

But what appears here is that /media/disk is not your hard drive. It is the live cd i guess. And you cannot write to that disk. That's the error message says.

I think your harddrive should be somewhere in /dev. Open a terminal and type ls -l /dev. This will give you the contents of dev. From there you should see device named like sdx ( x replaced by relevant characters ). That will be the hard drive i think.

**Shreding the hdd 100 times may take very long time.**

---

### Post by Lucrezia on 2008-09-30
found... it was sda... thank you!


i started with 3 shred... i'll see how many i'll be able to do before tomorrow... how many do you think are sure enough?

---

### Post by hyper_ch on 2008-09-30
I'd

(1) first find out what the drive name is
```

sudo fdisk -l

```
and

(2) run
```

sudo dd if=/dev/urandom of=/dev/sdX

```

---

### Post by Biochem on 2008-09-30
> **Lucrezia said:**
> found... it was sda... thank you!


i started with 3 shred... i'll see how many i'll be able to do before tomorrow... how many do you think are sure enough?

One is more then enought unless you are a spook and the repair shop an NSA branch. Repaire shop employees don't have the time to play with AFM (couple of 100 k$) on client's HD

One pass of dd if=/dev/urandom of=/dev/sda would be good also.

---

### Post by eitreach on 2008-09-30
Before I re-sold my Asus EEE, I used Darik's Boot And Nuke. 

[http://www.dban.org/](http://www.dban.org/)

---

### Post by HermanAB on 2008-10-01
I would just keep the hard disk.

Any computer shop will have spare disks lying around to test your machine with, so remove it and add a note saying that you removed it for security reasons.

Cheers,

Herman

---

### Post by Thelasko on 2008-10-03
> **eitreach said:**
> Before I re-sold my Asus EEE, I used Darik's Boot And Nuke. 

[http://www.dban.org/](http://www.dban.org/)

+1 for DBAN.  It's very quick and easy.

---

### Post by lukjad on 2008-10-03
What does it do? Is it a drive shredder?

---

### Post by Thelasko on 2008-10-03
> **lukjad007 said:**
> What does it do? Is it a drive shredder?

DBAN writes over the drive a few times with [random data]("http://en.wikipedia.org/wiki/Anti-computer_forensics#Artifact_wiping").  The CIA could probably retrieve your data in a few months, but your average *Joe Identity Thief* won't be able to.

The only thing better than DBAN is degaussing the drive, which involves taking a really big magnet to it.  The only thing better than degaussing it is a [drill.]("http://www.popularmechanics.com/home_journal/how_to/4284709.html?page=10") (see #80)  Obviously, once you do this the drive won't be useful anymore.

---

### Post by surfed on 2008-10-03
You could always try this for some overkill:
[http://www.edrsolutions.com/](http://www.edrsolutions.com/)

[http://gizmodo.com/386216/hard-drive-crusher-how-much-would-you-spend-to-secure-your-data](http://gizmodo.com/386216/hard-drive-crusher-how-much-would-you-spend-to-secure-your-data)

---

### Post by solitaire on 2008-10-03
I'd go with the dd method....

First I'd format the disk then use:
 dd if=/dev/urandom of=/dev/sda
then
 dd if=/dev/zero of=/dev/sda

It takes a while; "urandom" is much slower than "zero", but better for a first pass of the drive.

If you have nothing Seriously Illegal (i.e. "Garry Glitter" style, UK people will know of this perv! ) on your drive that should be enough to stop any general nosing around.

---

