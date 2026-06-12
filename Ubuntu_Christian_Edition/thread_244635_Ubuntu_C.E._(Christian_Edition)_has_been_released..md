---
title: "Ubuntu C.E. (Christian Edition) has been released."
date: 2006-08-26
forum: Ubuntu Christian Edition
---

### Post by randell6564 on 2006-08-26
Hello folks!

There really is no difference between Dapper and C.E. except the default wallpaper. Gimp and a couple of other app's have been left out in order to make room for GnomeSword bible software and something called 'Gamba' I think which is some kind of development software, and 'Dansgaurdian', which to me is the best part of it all!

If you have kids and you are sharing a single PC, Dansgaurdian can be used to limit the little 'Crib-monkies' access to certain safe sites, AND limit what type of packages they can download. It's very configurable and simple to use!

Now on the down side of things. After my first installation attempt of the iso, onto my 20GB Ide Primary slave, I rebooted expecting grub to give me a dual-boot option with Dapper Drake.  I got NOTHING! 'Error loading operating system'

So I booted off the cd into Dapper, opened up Qtparted, wiped the drive and tryed again, but this time I used a different iso, burned with a different App and at a slower speed.  Again, the same error.

After doing some googling, I kept reading references to LBA, so I went into my Bios, changed the setting from Auto to LBA mode, rebooted and BAM, Everything is peachy!


I'm guessing that the creaters of C.E. unknowingly have done something that messes with the Bios CHS.  

So, just wanted to post a heads-up to anyone wanting to try C.E. and running into the same problem.

Peace!
OH! BTW, Heres what I thought was REALLY cool!  If your running Dapper and want to upgrade to C.E. The developers have created a script that can be executed from the terminal and install C.E. in a matter of 2 to 3 minutes!
sure beats downloading and installing the iso!
The script can be had here: [http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/convert-to-latest-version-of-ubuntu.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/convert-to-latest-version-of-ubuntu.html)

---

### Post by RAV TUX on 2006-08-27
moving this thread to the Ubuntu Christian Edition,....3rd party forum with a redirect.

---

### Post by Billsey on 2006-10-10
Can GnomeSword, Gamba, and Dansguardian be downloaded separately?

Also, I'd like to make a small suggestion for the developers: Please find a way to make adding additional hard drives after the initail install much easier. Currently, there are quite a few hoops to jump through in doing this, since Ubuntu does not include a root user. Ubuntu is for real people, meaning those who are not computer geeks. There needs to be an easier way, for those who are blessed enough to gain added hard drive space.

Once I knew what I was doing, doing the initial install with multiple hard drives turns out to be failry easy, but this is a huge contrast to adding one later.

---

### Post by mysticrider92 on 2006-10-10
> **Billsey said:**
> Can GnomeSword, Gamba, and Dansguardian be downloaded separately?

Also, I'd like to make a small suggestion for the developers: Please find a way to make adding additional hard drives after the initail install much easier. Currently, there are quite a few hoops to jump through in doing this, since Ubuntu does not include a root user. Ubuntu is for real people, meaning those who are not computer geeks. There needs to be an easier way, for those who are blessed enough to gain added hard drive space.

Once I knew what I was doing, doing the initial install with multiple hard drives turns out to be failry easy, but this is a huge contrast to adding one later.

It is actully pretty easy to add hard drives. Go to Synaptic and install the qtparted package and any dependancies, then open a terminal and type: > sudo qtparted This will open qtparted as a root user, where you can modify, add, and remove partitions on non-active hard drives.

And to answer your first question, yes you can add all of these things to a normal Ubunutu install.

---

### Post by Billsey on 2006-10-13
In order to do that, I first need to get my Ubuntu Box talking to the rest of my home network. It seems all of its ports are solidly locked shut, and I don't know how to open them. So, at the moment, it's like I'm caught in a Catch-22. The stuff I need to make life easier is available on the Internet, but in order to connect to the Internet, my Ubuntu Box needs to play nice with my OSX Mac, which dials up the Internet. But my Ubuntu Box doesn't seem to want to do that. ;)

Now, if only I could find a Debian/Ubuntu package manager for OSX. :D

---

### Post by mysticrider92 on 2006-10-13
I will pm you to see if I can help, if that is ok, because I don't really want to get too off-topic here.

---

### Post by Billsey on 2006-10-13
That would be fine. :)

---

