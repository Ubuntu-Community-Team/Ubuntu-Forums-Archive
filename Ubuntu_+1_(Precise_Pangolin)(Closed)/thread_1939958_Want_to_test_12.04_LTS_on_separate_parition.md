---
title: "Want to test 12.04 LTS on separate parition"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by UnknownFearNG on 2012-03-12
I want to, if possible, make a small partition for testing purposes for the 12.04 LTS Beta. I know I'll use GParted, but how would I go about marking the new partitions so I know which to delete after 12.04 gets released? Or should I just wait till it gets released next month?

---

### Post by howefield on 2012-03-12
When you create the partition, mark it with a label.

Then don't mark it for formatting during the install else you'll lose the label :)

---

### Post by UnknownFearNG on 2012-03-12
Thanks for the help :)

---

### Post by grahammechanical on 2012-03-12
I was not smart enough to mark my partitions with a label. So, I have to keep a note of the description that Gparted gives. It will be something like

/devsda3

I have two primary partitions.

1) /devsda1 is where 11.10 is installed
2) /devsda2 is an extended partition in which I have all the other partitions.
3) /dev/sda3 is the /home partition attached to 11.10 and it is in the sda2 extended partition. As are all the others.

4) /dev/sda5 is one of my two 12.04 installs

So you can see how things are marked by Gparted. I also make a note of the partition size as a means of recognising the partition.

So, yes, I would agree that giving the partitions a label is a very good idea.

Regards

---

### Post by dcstar on 2012-03-13
> **grahammechanical said:**
> 
.........
So, yes, I would agree that **giving the partitions a label** is a very good idea.


Which can be done at any time on an unmounted partition, **so why don't you do it?**

---

### Post by grahammechanical on 2012-03-13
> Which can be done at any time on an unmounted partition, so why don't you do it?

Because when I tried to do this a few years back I got a warning message about loosing data. It may be pre-cautionary but it is scary when you have never done anything like it before.

Regards.

---

### Post by dcstar on 2012-03-14
> **grahammechanical said:**
> Because when I tried to do this a few years back I got a warning message about loosing data. It may be pre-cautionary but it is scary when you have never done anything like it before.

"A few years back" is not now, things do change.

---

### Post by scheuri on 2012-03-14
> **dcstar said:**
> "A few years back" is not now, things do change.
The only thing that does not change is:
Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup...whatever you do.

Cheers
scheuri

---

### Post by dcstar on 2012-03-14
> **scheuri said:**
> The only thing that does not change is:
Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup, Backup...whatever you do.


Not when you are basically experimenting with development software.

You are (supposed to be) testing things that may well break so you can then put in bug reports so they get fixed and then the whole user community benefits.

If you need to "backup" this sort of software, then you are basically using it inappropriately.

---

### Post by keithpeter on 2012-03-14
+1 for keeping a note of the partition number.

I personally would arrange things so that 11.10 grub recognised Precise rather than Precise grub recognising 11.10 if that makes sense so that if there was a bug that affected the boot up process you are not left looking at a grub prompt...

@dcstar: I use a separate home partition and reinstall the testing OS on a regular basis. I sometimes delete the 'dotfiles' in the home partition to see what the default Precise profile is like. I then basically do everyday work. Dropbox helps keep my importantish work files duplicated on a netbook running 11.10. I have backups!

---

