---
title: "Adding the mounted ISO"
date: 2005-01-01
forum: Repositories &amp; Backports
---

### Post by hazza96 on 2005-01-01
First of let me say that I am inherently lazy and look for ways to make my life easier :)

When I select a package that needs the CD I have to dig around my messy desk to find it. I have the warty ISO image on my box and I have loop mounted it in the file system.

I now want to change the respository so that it points to the loop mounted ISO image instead of requesting the CD.

Does anyone know what I should add in or change so that it gets the standard packages it needs from the /mnt/ubuntu mount point instead of cdrom:[.....

---

### Post by hazza96 on 2005-01-03
Ok, since no-one responded I worked out how to do it myself.

First I installed Proftpd and enabled anonymous logins. You do that by editing the file /etc/proftpd.conf and uncomment most of the lines at the bottom. I do not recommend uncommenting the "Incoming" section.

I enabled loop devices by running 'sudo modprobe loop'. To make loop devices available automatically after you reboot add the line "loop" to the file /etc/modules.

To loop mount the ISO run the command 'sudo mount /home/ftp' after adding a line to /etc/fstab:
/path/to/ISO/image/warty.iso /home/ftp iso9660 ro,loop,auto 0 0

This makes all the files that are on the CD available to the anonymous ftp user.

Start Synaptic, disable the CD entry and add a new repository with the following details:
Type: Binary
URI: [ftp://localhost](ftp://localhost)
Distro: unstable
Sections: main restricted

Now you have the CD debs available to you and you can give your next door neighbour that Ubuntu CD you have on your desk :)

---

### Post by hazza96 on 2005-01-05
Ok I eventually found and even easier way to do it. You still have to insert the loop device and add a line to the fstab like this:
```
/path/to/ISO/image/warty.iso /mnt/ubuntu iso9660 ro,loop,auto 0 0
```
Start Synaptic, disable the CD entry and add a new repository with the following details:
Type: Binary
URI: file::///mnt/ubuntu
Distro: unstable
Sections: main restricted

---

### Post by faheyd on 2007-05-12
> **hazza96 said:**
> Ok I eventually found and even easier way to do it. You still have to insert the loop device and add a line to the fstab like this:
```
/path/to/ISO/image/warty.iso /mnt/ubuntu iso9660 ro,loop,auto 0 0
```
Start Synaptic, disable the CD entry and add a new repository with the following details:
Type: Binary
URI: file::///mnt/ubuntu
Distro: unstable
Sections: main restricted


Thanks OP!

Believe it or not, the above helped me mount my feisty 7.04 dvd.iso file and then add it to my repos.  For readers, don't forget, it's three forward slashes, not two.  Can be an image of the CD or DVD.  When using synaptic pkg mngr (gui), do this in the 'Settings/Repositories/Third Party Tab', click on ADD:


Type: Binary
URI: file:///mnt/where/it/is
Distribution: feisty
Components: main restricted

or manually add it to your /etc/apt/sources.list:
deb file:///mnt/where/it/is main restricted

Of course, reload your repo's to get them to show up.

---

### Post by mezhaka on 2007-11-29
thank you guys this is really helpful!!!

---

### Post by WSmart on 2008-09-20
[http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/](http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/)

Even better; Josh Fuller's comment from above:

" sudo apt-cdrom add -d /media/ubuntu-7.04-alternate/

&#8230; adds and authenticates gpg keys and alleviates the need to&#8230;

sudo vi /etc/apt/sources.list "

This worked great for me in Gutsy.  Only my Hardy CD's, and the Gutsy, showed up in the Synaptic-not the Ibex I have.

Thanks everyone.  This is cool chit mon.  I was just sitting here trying to decide where to aquire some optical media to shuffle around with all this-what a pain.  Yeeea.

---

