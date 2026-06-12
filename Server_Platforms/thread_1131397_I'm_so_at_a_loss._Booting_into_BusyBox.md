---
title: "I'm so at a loss. Booting into BusyBox"
date: 2009-04-20
forum: Server Platforms
---

### Post by Hopworks on 2009-04-20
I'm really rusty and new to Linux, Ubuntu, etc.

I'm not sure why, but lately I've had some really bad things happen with my Linux Ubuntu Lamp Server. I would love to give the version but don't even know how to get that info. I know I'm into the 8's. If it's 8.1 or 8.04 I don't know.

It was singing along nicely until about a month ago. I started to see files and folders having issues, can't be moved or deleted, etc. Today on boot, the drive was locked. I could see it from my windows machine but couldn't write to it as it was set for read only.

So I rebooted, got into a screen that said it (the partition) was isolated, have to run FSCK, etc etc. So I did. A TON of errors came up, multiply- something or other. I cloned them the last time this happened. This time I said no. Went through a bunch of them... rebooted, now at BusyBox whatever that is. 

I googled it the last three days. Many said MEMORY issues, DRIVE issues, so I ran a memtest86 all night. No failures. I ran diagnostics on the drives in my windows machine, all past with no errors at all. The hardware seems to be sound. I put in a stored hard drive that boots Windows XP and the machine came up just fine, ran for a few days. Never had a prob. 

All I can think of is I had a couple power surges I think about 3 months ago, the system rebooted after a weird noise. I have it hooked into a power backup with protection. $200 on this APC. I have removed all the extra cards, video tuning cards, serial cards, etc. It's stock now. I can't for the LIFE of me figure out what caused the multiply-claimed blocks in inode. Whenever I shut down, I do it either by command line or otherwise, but never just turn it off.

And now I have absolutely NO IDEA how to regain control of my Ubuntu LAMP server. 

I'm sorry if this plea for help is too vague. I don't know enough to help myself with this. I hope someone can attempt to direct me back to at LEAST getting the LAMP back online.

I backed up 2 days ago so the data is safe, but not the system, just the stores.

Thank you SO MUCH for your time reading this.

Hop

---

### Post by Hopworks on 2009-04-24
Well I've tried Super Grub, the LiveCD, about a dozen walk through posts and I'm still booting into busybox. I ordered a couple of 640gb Western Digital Caviar Black drives so I would have clean gear to reinstall on. I'm hoping I can gain access to that busted boot drive and pull my data off. 

I am missing files that ubuntu needs I'm sure, but I'm not sure how to proceed with repairs and was hoping for some advice here for how to at least see what I need to do initially. The new drives will not arrive from NewEgg until Monday so I have the weekend to work on it.

If anything, I'd like to know what happened, how I can prevent it, and learn how to fix it. I'm not ready to give up yet.

Hop

---

