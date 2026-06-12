---
title: "Updating Help"
date: 2009-12-04
forum: Ubuntu Christian Edition
---

### Post by Pursuer on 2009-12-04
Need baby-stepping help. I came here a year or so ago and received so much great help, I thought I would come back for more.
I currently have Ubuntu CE version 7.04, and want the newer version. I tried to install it, but it would not let me. I tried following the directions on the Ubuntu CE website.
I went through the terminal and all that.
Any help would be great.

---

### Post by david_kt on 2009-12-04
> **Pursuer said:**
> Need baby-stepping help. I came here a year or so ago and received so much great help, I thought I would come back for more.
I currently have Ubuntu CE version 7.04, and want the newer version. I tried to install it, but it would not let me. I tried following the directions on the Ubuntu CE website.
I went through the terminal and all that.
Any help would be great.

Ubuntu 7.04 is way to old, and I am not sure whether or not it could be upgraded without problem. It is recommended to do fresh install instead of upgrade. But if you want to upgrade, here is the path:

7.04 ---> 7.10 --> 8.04 --> 8.10 --> 9.04 --> 9.10

As you can see, you will need to upgrade 5 times. It would waste a lot of time, and there is still no guarantee that it would work flawlessly.

So again, I recommend fresh install. Backup all your documents first before doing fresh install.

DK

---

### Post by Pursuer on 2009-12-04
DK, thanks for your help.
I am not kidding when I say I need baby steps! How do I do a backup?
And then after that, how do I do a fresh install?
(One of these days after receiving help from others, I would love to help others in return.)
You are awesome for helping. Thank you.

---

### Post by david_kt on 2009-12-04
> **Pursuer said:**
> DK, thanks for your help.
I am not kidding when I say I need baby steps! How do I do a backup?
And then after that, how do I do a fresh install?
(One of these days after receiving help from others, I would love to help others in return.)
You are awesome for helping. Thank you.


To backup means to copy your files in your home folders to other harddisk/partition.

Do you have external harddisk? If yes, copy all your files and folder from
/home/ to external harddisk.

Or, just select which files you want to keep, and copy them to external harddisk


After that, download the iso, follow the instruction below:
[http://ubuntuce.com/download.htm](http://ubuntuce.com/download.htm)

Use bittorent client to download.

After it has been downloaded, burn it to DVD  and boot from that DVD.

DK

---

### Post by Pursuer on 2009-12-08
A friend of mine gave me a Maxtor external hard drive to borrow for this task. I went to move my files over and it said I do not have permission to write files onto the external hard drive. I went into the properties section of the hard drive and am unable to give myself any permissions of any kind.
What is an easy way to get all of my stuff onto the hard drive?
(And thank you in advance!)

---

### Post by david_kt on 2009-12-08
> **Pursuer said:**
> A friend of mine gave me a Maxtor external hard drive to borrow for this task. I went to move my files over and it said I do not have permission to write files onto the external hard drive. I went into the properties section of the hard drive and am unable to give myself any permissions of any kind.
What is an easy way to get all of my stuff onto the hard drive?
(And thank you in advance!)

I guess you do not have ntfs-3g on your system:
```
sudo apt-get install ntfs-3g ntfs-config
```

After that launch Application >> system tools >> NTFS configuration tools, specify support for external drives write support.

For more details instruction, see below:
[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

DK

---

### Post by Pursuer on 2009-12-11
I am finally all set to go with this. Where do I download this to on my computer? You mentioned burning a copy to DVD. All I have are 2 700 MB CD-R's. I doubt those would work.
Is it possible to just do everything without downloading onto a CD/DVD?

---

### Post by david_kt on 2009-12-11
> **Pursuer said:**
> I am finally all set to go with this. Where do I download this to on my computer? You mentioned burning a copy to DVD. All I have are 2 700 MB CD-R's. I doubt those would work.
Is it possible to just do everything without downloading onto a CD/DVD?

First download the iso file but, CD will not work for desktop version. Only the server version is live CD. 

You could use usb (1 GB usb or higher) and unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

May be borrow your friends windows to transfer the iso file to usb using unetbootin, or find ubuntu box hardy or later:

[https://launchpad.net/~gezakovacs/+archive/ppa](https://launchpad.net/~gezakovacs/+archive/ppa)

That is provided you computer could boot from usb.
Otherwise, just download normal ubuntu, burn it to CD and install it, and convert to CE after that.
 
DK

---

### Post by JoeIsuzu on 2009-12-14
While Ubuntu CE may require a DVD, standard Ubuntu 9.10 does not.  A CD works fine.  You could install it, then convert it to CE.

And what about saving the .iso to his external drive and installing from it?  Isn't that an option?

Jack

---

