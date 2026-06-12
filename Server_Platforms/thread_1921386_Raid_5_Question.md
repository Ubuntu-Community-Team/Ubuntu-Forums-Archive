---
title: "Raid 5 Question"
date: 2012-02-06
forum: Server Platforms
---

### Post by N3PT00n on 2012-02-06
Hello Guys and Gals,

I have a quick question. I am going to build a home server, and decided on Ubuntu, not only because of the community but because the Windows Servers cost money..lol.

I have been reading up on RAID, and it seems like it is pretty straightforward. All the configuration and so on. If I had a software RAID, DriveA - had the configuration and the OS on it, and it died. How would I go about recovering the RAID array?

Thanks for the help

---

### Post by rubylaser on 2012-02-06
You'd want to boot from a RAID1 or RAID10, not RAID5 with mdadm.  Also, the [Ubuntu docs]("https://help.ubuntu.com/community/Installation/SoftwareRAID") cover this for you :)  Welcome to the Forums!

---

### Post by N3PT00n on 2012-02-07
thanks rubylaser for the quick response. Maybe I should be a little clearer on what I am trying to do.

Ubuntu OS is installed on DriveA. My raid 5 is composed of 3 separate physical hard drives, we can call them Drive1, Drive2 and Drive3.

My question is this, if the software raid 5 configuration is created on the OS drive (DriveA). And it dies. How do I recover/access the files on Drive1-3?

Is it as simple as getting a new hard drive, reinstalling Ubuntu on in and saying, search for Raid configuration?

---

### Post by Krupski on 2012-02-07
> **N3PT00n said:**
> Hello Guys and Gals,

I have a quick question. I am going to build a home server, and decided on Ubuntu, not only because of the community but because the Windows Servers cost money..lol.

I have been reading up on RAID, and it seems like it is pretty straightforward. All the configuration and so on. If I had a software RAID, DriveA - had the configuration and the OS on it, and it died. How would I go about recovering the RAID array?

Thanks for the help

I have an Ubuntu based RAID file server at home. What I do is use the hard drives **solely for data storage** and use a small separate solid state drive to boot and run Linux from.

I use this card (click pic for link to seller):

[[img]http://ecx.images-amazon.com/images/I/41et5k-hijL._SL500_AA300_.jpg[/img]]("http://www.amazon.com/Apricorn-Velocity-Desktop-Upgrade-VEL-SOLO/dp/B005C983O4")

...and an Intel 40GB 2.5 inch notebook solid state drive for Linux.

With this setup, the system will always boot, no matter what happens with the RAID array.

Here's a link to my review of the card with the SSD: [http://www.amazon.com/review/R3U07EV4ZIVM19/ref=cm_cr_pr_viewpnt#R3U07EV4ZIVM19](http://www.amazon.com/review/R3U07EV4ZIVM19/ref=cm_cr_pr_viewpnt#R3U07EV4ZIVM19)

For what it's worth....

---

### Post by trundlenut on 2012-02-07
> **Krupski said:**
> I have an Ubuntu based RAID file server at home. What I do is use the hard drives **solely for data storage** and use a small separate solid state drive to boot and run Linux from.

I use this card (click pic for link to seller):

[[img]http://ecx.images-amazon.com/images/I/41et5k-hijL._SL500_AA300_.jpg[/img]]("http://www.amazon.com/Apricorn-Velocity-Desktop-Upgrade-VEL-SOLO/dp/B005C983O4")

...and an Intel 40GB 2.5 inch notebook solid state drive for Linux.

With this setup, the system will always boot, no matter what happens with the RAID array.

Here's a link to my review of the card with the SSD: [http://www.amazon.com/review/R3U07EV4ZIVM19/ref=cm_cr_pr_viewpnt#R3U07EV4ZIVM19](http://www.amazon.com/review/R3U07EV4ZIVM19/ref=cm_cr_pr_viewpnt#R3U07EV4ZIVM19)

For what it's worth....

However if you are using MDADM and something happens to the SSD you are going to have issues with getting the data from the RAID 5 array.  Data recovery would be simpler with RAID 1 though.

---

### Post by rubylaser on 2012-02-07
> **trundlenut said:**
> However if you are using MDADM and something happens to the SSD you are going to have issues with getting the data from the RAID 5 array.  Data recovery would be simpler with RAID 1 though.

No, mdadm is very portable and easy to restore on any Linux distro.  You'd just reinstall your OS (assuming you didn't have a backup image of the hard drive). Then do this to get it recognized:
```
apt-get install mdadm
```
Answer **all** the the arrays to mount question, and then add an /etc/fstab entry, and you'd be back up and working in a matter of minutes.  Can't be much easier than that :)

---

### Post by Krupski on 2012-02-07
> **trundlenut said:**
> However if you are using MDADM and something happens to the SSD you are going to have issues with getting the data from the RAID 5 array.  Data recovery would be simpler with RAID 1 though.

There isn't much that will go wrong with the SSD. It won't crash like a hard drive can. I also make regular backups of the SSD by simply using **dd** and creating an image of the disk.

If I screw up something REALLY badly, I can always pull out the SSD, plug it into my PC and use **dd** to re-image the drive from a backup.

In fact, I HAVE made some big boo-boo's in the past and re-imaged the boot drive to save my bee-hind.

40GB copies back and forth "in a flash" (pun intended) :)

---

### Post by N3PT00n on 2012-02-07
> **rubylaser said:**
> No, mdadm is very portable and easy to restore on any Linux distro.  You'd just reinstall your OS (assuming you didn't have a backup image of the hard drive). Then do this to get it recognized:
```
apt-get install mdadm
```
Answer **all** the the arrays to mount question, and then add an /etc/fstab entry, and you'd be back up and working in a matter of minutes.  Can't be much easier than that :)

thank you. this was the answer I was looking for. Building my ubuntu server this weekend. thanks for all the help.

---

### Post by rubylaser on 2012-02-07
If you're building an array for the first time, you may like to follow [my tutorial]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") that includes setting up the array, SMART monitoring, UPS setup, and email alerts.

---

### Post by CharlesA on 2012-02-07
> **rubylaser said:**
> If you're building an array for the first time, you may like to follow [my tutorial]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") that includes setting up the array, SMART monitoring, UPS setup, and email alerts.
Nice job on the tutorial. :)

That makes mdadm look easy to set up.

---

### Post by rubylaser on 2012-02-07
> **CharlesA said:**
> Nice job on the tutorial. :)

That makes mdadm look easy to set up.

Thanks :) I hope it will help people get off to a good start with all of the proper pieces in place have a safe mdadm experience.

---

### Post by CharlesA on 2012-02-07
> **rubylaser said:**
> Thanks:) I hope it will help people get off to a good start with all of the proper pieces in place have a safe mdadm experience.
Well it sure helped make it not look like the huge scary monster I thought it was. :)

---

### Post by rubylaser on 2012-02-07
> **CharlesA said:**
> Well it sure helped make it not look like the huge scary monster I thought it was. :)

Thanks, I laughed at this one :)  On the surface, mdadm looks very complicated and tricky, but it really only has a few base commands that you use 99% of the time. As long as you understand how it works, and why it isn't working when something went wrong, it's very simple to manage.

---

