---
title: "Alert before disk usage hits 100%"
date: 2007-12-28
forum: Ubuntu Brainstorm
---

### Post by Majorix on 2007-12-28
I was using a dual boot up until today, and Ubuntu only had 12 gb's of partition space. So as you can guess it filled up relatively often.

But, there was no warnings until all 100% of the disk space was used. Then it gives a warning, and god knows what would happen to your packages installing in the background.

I have experienced this two or three times and would really like to see it gone with Hardy. I hope it's not hard to code in?

Thanks.

---

### Post by 23meg on 2007-12-28
Related specs:

[https://blueprints.launchpad.net/ubuntu/+spec/handling-full-disks](https://blueprints.launchpad.net/ubuntu/+spec/handling-full-disks)
[https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy](https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy)

---

### Post by lexen on 2007-12-28
I broke my computer twice because I filled up the hard drive, this would have saved me.  I think on top of the system giving you a warning, synaptic should check the amount of free space so you can't install a program that requires more space then you have.  It would also be nice if you had the option to set the amount of free space you always want to retain.

---

### Post by Majorix on 2007-12-28
> **23meg said:**
> Related specs:

[https://blueprints.launchpad.net/ubuntu/+spec/handling-full-disks](https://blueprints.launchpad.net/ubuntu/+spec/handling-full-disks)
[https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy](https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy)
Oh so they are working on it... Good to know :)

---

### Post by unityofsaints on 2007-12-28
+1. Has made one of my boxes unbootable before, had to use live cd and apt-get autoremove, no biggie for me but someone new to linux would panic for sure!

---

### Post by Aualin on 2007-12-29
> **lexen said:**
> I broke my computer twice because I filled up the hard drive, this would have saved me.  I think on top of the system giving you a warning, synaptic should check the amount of free space so you can't install a program that requires more space then you have.  It would also be nice if you had the option to set the amount of free space you always want to retain.
Oh god... how slow will synaptic then get?

---

### Post by rockin_goliath on 2007-12-29
This is a fantastic idea, I'm actually a little surprised that this wasn't implemented in any earlier release. I think it would also be cool if when the user receives such a warning, it will give suggestions as to what the user can do to reduce the disk space and provide links or buttons to those functions. For example, the warning will pop up and say somethings like:

The file system is low on storage space. It is recommended that you delete  unnecessary files or perform a system cleanup.
(buttons for)
"Run the system cleanup utility"           "Ignore"

There have been other threads talking about the construction of this system cleanup utility, which would do things like delete the apt archives, logs, temporary thumbnail files, etc. The average user who is running Ubuntu on a computer with not a lot of storage space should DEFINITELY be helped out in this regard, especially before it gets to a point that it would render the computer unbootable.

---

### Post by 23meg on 2007-12-29
[QUOTE=rockin_goliath]I'm actually a little surprised that this wasn't implemented in any earlier release. [/QUOTE]

It was. It went away with Feisty. I don't know why; if anyone knows, please tell.

---

### Post by madmetal on 2007-12-30
> **23meg said:**
> It was. It went away with Feisty. I don't know why; if anyone knows, please tell.

yeap when i first used ubuntu at my old pc i saw this message i think after 95% 
is went away due to upstream or just ubuntu?

---

### Post by jeffus_il on 2007-12-30
There is an applet in XFCE that does this, will look to see if gnome ahs one and post.

---

### Post by jeffus_il on 2007-12-30
called fsguard

---

### Post by jeffus_il on 2007-12-30
Fished from the net:
The ext3 filesystem reserves an amount of the total space for root. If some user (or daemon) fills the disk then a login couldn't be possible anymore. So even root couldn't login anymore to fix it. Therefore ext3 reserves an amount of 5% (default) of the filesystem for the root user to prevent it (it doesn't work if root fills the disk).

---

### Post by jeffus_il on 2007-12-30
Some more:

xfce4-fsguard-plugin 
The fsguard plugin checks free space on a chosen mount point frequently and displays an alarm if free space is less than given alarm limit.

---

### Post by jeffus_il on 2007-12-30
There are lots of possibilities -
A small script running as a cron would do it.
Many utilities like GKRellm supply the functionality.
I avoid full disks by intelligent partitioning, maybe keeping root, usr, tmp and home in separate partitions,
you can't fill root cause most of your junk goes into home and so on ...

---

### Post by Majorix on 2007-12-30
> **jeffus_il said:**
> Some more:

xfce4-fsguard-plugin 
The fsguard plugin checks free space on a chosen mount point frequently and displays an alarm if free space is less than given alarm limit.

Notice how it says "checks frequently". A real control mechanism would check with each file added to the HDD.

---

