---
title: "Walking the bleeding edge..."
date: 2007-01-25
forum: The Cafe
---

### Post by wylie348 on 2007-01-25
Well, I found it quite amusing that I cannot even stand to use windows for one week, and that I simply need to stay with Ubuntu (addicted - new forum?).  Regardless, I was hoping to get some assistance with my walking the bleeding edge problem.
I simply have to use Feisty as it is so good at my hardware and some other issues with Edgy, but, there must be some careful ways to walk that edge.  In other words, does anyone have some advice for someone who is using an unstable platform, but wishes it to be as stable as possible until official release?
Thanks!
:)

---

### Post by DSn0wMan on 2007-01-25
Just make lots of backups. Of course this wont help the stability, but it might save you alot of headache one day.

---

### Post by wylie348 on 2007-01-25
What is the best backup program around or is it Mondo Rescue?
Thanks!

---

### Post by ButteBlues on 2007-01-25
Check the forum often.

If dist-upgrade wants to remove one or more crucial packages, wait until it no longer wants to before upgrading.


Don't dist-upgrade while drunk. Ever.

---

### Post by hscottyh on 2007-01-25
Great advice! I did that once :( I had to get drunk again to fix it :D

---

### Post by DSn0wMan on 2007-01-26
> **wylie348 said:**
> What is the best backup program around or is it Mondo Rescue?
Thanks!

I usually just tar up my home folder. Here is a link for a full system backup using tar. 
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

---

### Post by jvc26 on 2007-01-26
> **ButteBlues said:**
> 
Don't dist-upgrade while drunk. Ever.
Oh so true - and it can seem such a good idea! keep those backups = I just burn my stuff to a separate HDD, and also have a second /home partition which is always a useful thing if the main OS gets messed up.
Il

---

### Post by Brunellus on 2007-01-26
and if you have a second hard drive, you could just rsync for periodic backups of key dirs.

---

### Post by doobit on 2007-01-26
> **Brunellus said:**
> and if you have a second hard drive, you could just rsync for periodic backups of key dirs.

For me, that's the best way. I also back up all my settings and emails (invisible files in /home) and documents to a USB pen drive.

---

### Post by salsafyren on 2007-01-27
I am using Feisty right now.

I use 'aptitude upgrade' regularly and this has worked fine without breaking my system.

---

### Post by The Noble on 2007-01-27
Copying your entire /home directory is a good idea if you have a massive hard drive, but if you have a laptop, that may be a problem. I have a 60 Gig laptop, and I have an extra partition on my hard drive allocated as /stuff through the fstab. This makes it really easy if anything happens. You don't end up losing lots of space, but everything important is stored in /stuff (which is /dev/hdc3). Use the gparted live CD, as it is really easy to shift partitions when needed.

---

