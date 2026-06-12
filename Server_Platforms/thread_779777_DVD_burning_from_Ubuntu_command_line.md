---
title: "DVD burning from Ubuntu command line"
date: 2008-05-03
forum: Server Platforms
---

### Post by RHAnthony on 2008-05-03
What tools do you server admins use to burn DVD backups from a command line?  

What DVD burner drives have you used and what did you think of them, and their reliability under Ubuntu?

Again, I'm hoping to only have command line necessary on my server.

---

### Post by andguent on 2008-05-03
99% of the time, I can litterally type "cdrecord mycdimage.iso", twiddle my thumbs for a minute or 5, and be done. I've done this with four or five different burners, 3 different Linux distributions, and ISO files of varying sizes (50MB to 4.7GB).

The only time I can think of a failure that resulted in a coaster was when the media and the burner didn't jive. Someone else found a deal on blank "music" cds and claimed they would work fine for burning knoppix. My optical drive proved him wrong, but they worked fine on his computer.

---

### Post by RHAnthony on 2008-05-04
I'm not looking to burn ISO's really.  I'm more interested in burning serveral directory structures (www/ftp backups) to a DVD-RW that will stay in the drive.

Ideally I'd like something I can turn into a cron job to run once a week or so.

Is this like anything someone has done in the past?

---

### Post by andguent on 2008-05-04
It most definitely has been done. Admittedly I don't do it very often.

I searched around online and found the site below. I think it will get your ideas in motion.
[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

Search within that page for "backup a directory to a cd". The entire page has some really good info & examples.

---

### Post by RHAnthony on 2008-07-12
Thanks for the advice and reading material.  One thing left to make sure of, which I'm fairly confident in, is that a Blu-ray recorder will work pretty much the same as a CD/DVD as far as the commanding/apps go.

Ideally, a BR-RW will sit in the drive and be overwritten once a week for a backup, and changed out once every few weeks to a different one in a rotation.  I figure this should be cheaper and more reliable than alot of older tape systems, and I'm no where near needing a large modern tape/optical solution.

---

