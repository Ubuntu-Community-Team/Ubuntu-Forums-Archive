---
title: "Good News for Jaunty Boot Times"
date: 2009-04-15
forum: The Cafe
---

### Post by jbrown96 on 2009-04-15
I've always been really interested in file system performance, but I have never found anything recent that has some good comparisons. Since Jaunty is getting a new file system (Ext 4) and is supposed to have lots of boot improvements, I figured it would be a good time to test boot performance. 

Perhaps some others would be interested in the results, so I'm posting them here. 

Here's the test information:
IBM Thinkpad T43 upgraded with 2GB of ram. 40GB hard drive. It has a mobile celeron processor, but I'm not sure of the speed. 

Procedure:
Kubuntu 9.04 x86 Beta
Connected to my wireless access point
Automatic login enabled
No other changes

1) Boot the live CD (flash drive using unetbootin)
2) Shred the first 12GB of the hard drive to level the playing field
```
sudo shred -n 0 -zvv /dev/sda
```
3) Install. Create 1 10GB partition at the beginning of the disk. No swap.
4) Boot the computer three times to make sure all "house-keeping" is taken care of. KDE creates a lot of config files on the first boot, so this step is for consistency.
5) Connect to my wifi.
6) No updates. Just vanilla Kubuntu beta.

Timing:
1) The Grub menu is entered on boot
2) Timer is started as soon as the kernel is selected
3) Timer stops on the last tone in the KDE login sound. I did this because it was easy to measure. It also starts playing just when the hard drive light stops. 

File Systems:
I tested three file systems: Ext 3, Ext 4, and ReiserFS. I've always used ReiserFS because I thought it was the fastest of traditional file systems, so while it might not be widely used, I've used it and wanted to know how fast it is. While I use JFS and XFS existensively for my data, they can't hold /boot, so I didn't include them.

Results:
Everyone is probably going to think that I have no life, but I did a lot of runs. The results are attached as a spreadsheet. 

The test is probably not the most precise, but the results do have good consistency, so I'm confident that they are accurate.
If you don't want to check out the raw data, here are the averages

3rd Place: ReiserFS 62.71 seconds
2nd Place: Ext3 58.88
1st Place: Ext4 54.39

I have to say that I'm very impressed with Ext4. 

Here's just a little bit of a comparison. My daily laptop uses Kubuntu 8.10 (KDE 4.2.2) and is a Thinkpad T61p C2D 2GHz, 2GB ram, 160GB hard drive, Nvidia Quadro 570m. This machine is in use daily, so it's a little slower, and I have a lot more software, including Virtualbox (which has a kernel module), Nvidia proprietary graphics (no splash screen), and gnome's nm-applet, so it would make sense that it's a little slower. However, the machine is considerably faster than the T43 that I used for the real test. 
Using the same timing procedure above, the T43 with Ext4 booted about 17 seconds faster on the two trials that I did. Very impressive.

---

### Post by skymera on 2009-04-15
My 9.04 boots in 16 seconds according to Bootchart which is much much faster than 8.10 ever was.

Still, my 7.04 used to boot in 11 seconds on a slow computer. Gone are those days.

---

### Post by 50words on 2009-04-15
How is 9.04 working on your T43? I also have a T43, and 8.10 was so bad compared with 6.10-8.04 that I haven't used Ubuntu on my ThinkPad since last October.

---

### Post by jbrown96 on 2009-04-16
I haven't used it a ton because I gave it to my mom over Easter. It seems to be fully compatible. I didn't have any problems; the new KDE wireless manager is incredible! The only thing was that graphics could get a little slow at times. KDE even suspending Kwin compositing a couple of times, but that's not very important. I didn't try watching any video, so I'm not sure about that.


The T43 is a fantastic computer, and 9.04 ran really great on it. Probably the thing that impressed me the most was being able to boot from USB; I know it's standard on all new stuff, but it's so nice when using old hardware not to have to burn CDs any more.

---

### Post by toupeiro on 2009-04-17
4 second boot time from GRUB to desktop.

Core i7 940 w/ 6GB RAM
OCZ 60GB SSD
noop scheduler
ext4

---

### Post by ghindo on 2009-04-17
> **toupeiro said:**
> 4 second boot time from GRUB to desktop.

Core i7 940 w/ 6GB RAM
OCZ 60GB SSD
noop scheduler
ext4Impressive specs, to say the least.  What's a noop scheduler?  (I read the Wikipedia article but still don't quite understand.)

---

### Post by jbrown96 on 2009-04-17
> **ghindo said:**
> Impressive specs, to say the least.  What's a noop scheduler?  (I read the Wikipedia article but still don't quite understand.)

It relates to how reading from a storage medium (hard disk) is coordinated. Think of it this way. If I have a doctor's appointment, and I need to go to the grocery store, the logical action is to do both jobs on the same trip. It's way more efficient; there's far less travel time. The Noop scheduler would be like having your spouse go to the grocery store, while you just go to the doctor. Since both of you can travel separately, you can do the jobs in whatever order; they don't need to be grouped. So your spouse could get groceries in the morning, while you wait for your 2:00 appointment. The cumultative wait time for both jobs is much better.

This isn't used on hard drives because it would be like only having one car. Both of you need the car, but there's only one available, so you make sure if you're going to use it, you need to complete several jobs at once. 

It takes quite a bit of time (relative to actual read times) to just get the head of the hard drive to the place where data is on the disk, so if you wait for two jobs that are close together on the drive, there is less wear on the drive, and there is less cumulative time if they are both run at the same time.

Hope that makes sense.

---

