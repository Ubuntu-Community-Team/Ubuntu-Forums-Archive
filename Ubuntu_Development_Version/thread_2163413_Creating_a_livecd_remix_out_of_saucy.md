---
title: "Creating a livecd remix out of saucy"
date: 2013-07-18
forum: Ubuntu Development Version
---

### Post by sudo san on 2013-07-18
Hello everyone, I have decided to join you with the development of Saucy Salamander! ):P

I did not know where to put this thread as there was no obvious place from looking at the home page so feel free to yell at me that it shouldn't be here.

Recently, I have been trying to create my own little remix of ubuntu from scratch using saucy and raring using this guide (with some variations): [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

After trying many times and failing, then getting one to work, I boot it up using unetbootin and BAM. I encounter error messages saying I cannot mount so and so because the UID is 1000.

Here is what I did:

1) I created my work environment.
2) I did not use debootstrap, I extraced the saucy-core-i386.tar.gz file from [http://cdimage.ubuntu.com/ubuntu-core/daily/current/](http://cdimage.ubuntu.com/ubuntu-core/daily/current/) into the chroot environment.
3) I bound the /dev filesystem to the one in the chroot.
4) I then copied the /etc/hosts, /etc/resolv.conf, and /etc/apt/sources.list to the chroot environment and changed the sources.list file to accommodate saucy.
5) In the next set of steps in the guide, I found that the mount commands do not work after chrooting so I mounted them first and then chrooted. I then executed all the commands afterwards except for adding the public key.
6) I then linked /bin/true with /sbin/initctl.
7) I checked and there were no packages to upgrade.
8) I then installed the packages: ubuntu-standard casper lupin-casper
9) I then installed the packages: discover laptop-detect os-prober
10) I then installed the linux-image package.
11) I did not want to install ubiquity so I skipped that step.
12) I then proceeded to clean up the environment, the commands executed:
```

[COLOR=#333333][FONT=UbuntuMono]rm /var/lib/dbus/machine-id
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]rm /sbin/initctl
[/FONT][/COLOR]dpkg-divert --rename --remove /sbin/initctl
apt-get clean
rm -rf /tmp/*
rm /etc/resolv.conf

```
Again, I tried to un-mount the other filesystems but did not work so I had to exit the chroot environment to unmount them, I also unmounted /dev. Although I then had to reboot as I removed them!
13) After rebooting I created the work environment for the image.
14) I then copied the kernel, initrd image, memtest and isolinux binaries to the correct files in the image directory.
15) I created the isolinux.txt file in the correct directory and added the example text bellow the splash.rle file into it.
16) I skipped a couple of commands that add the splash image.
17) I created the isolinux.cfg file in the correct directory and added the just about the same text into the file. I removed comments from the bottom and renamed some of the menu entries.
18) I created the manifest for the  chroot but I changed the REMOVE variable as I did not install ubiquity.
19) I then created a squash file-system along with the filesystem.size file.
20) I cannot find in my bash history the command to remove the /boot folder but I cannot find any of the files that should be in the /boot folder in the manifest.
21) I created the README_.diskdefines file in the correct folder and added the example into file.
22) I then created all the files and added in all the appropriate information into them to get it recognised as an ubuntu image.
23) I created the md5sums.
24) I then created the iso with the same commands as given.
25) I tried to use usb-creator-gtk to create a usb but failed after copying with the error message:
```

An uncaught exception was raised: unorderable types: NoneType() <= str()

```
26) I then tried with unetbootin and after automaticly booting, it gives me the error message while trying to mount file systems.

I feel that it has something to do with the fact that I mounted the file systems before the chroot.

Any suggestions and replies would be greatly appreciated.
Feel free to shout at me for not putting it in the right section! (I know it probably isn't but saucy was my bast guess).

Many Thanks in advance.

---

### Post by Gavin77 on 2013-07-18
That seems like a lot of effort when you can just use Remastersys with one click.

---

### Post by sudo san on 2013-07-18
> **Gavin77 said:**
> That seems like a lot of effort when you can just use Remastersys with one click.
I know, I'm adventurous!
You can no longer get Remastersys as the project has been closed down, as I saw it on the page that re-directed me to to one I quoted :[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
Remastersys: [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

The creator has re-enabled the repositories, but they are for precise and quantal, I however am using raring.

Thanks for the suggestion of Remastersys.

---

### Post by cpatrick08 on 2013-07-18
> **sudo san said:**
> I know, I'm adventurous!
You can no longer get Remastersys as the project has been closed down, as I saw it on the page that re-directed me to to one I quoted :[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
Remastersys: [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

The creator has re-enabled the repositories, but they are for precise and quantal, I however am using raring.

Thanks for the suggestion of Remastersys.
Remastersys will be forked as [http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/). You can find downloads for it at [http://sourceforge.net/projects/os4systemimage/files/](http://sourceforge.net/projects/os4systemimage/files/), for now just an upadte to remastersys.

---

### Post by sudo san on 2013-07-19
> **cpatrick08 said:**
> Remastersys will be forked as [http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/). You can find downloads for it at [http://sourceforge.net/projects/os4systemimage/files/](http://sourceforge.net/projects/os4systemimage/files/), for now just an upadte to remastersys.

Thanks, I will try the method above once again and also test this. It looks very promising!

Thanks.

---

### Post by sudo san on 2013-07-19
Ok, I'm ditching the create-it-myself idea. How do I use this remastersys?

Say I have a custom, testing saucy installation and I want to share it with friends on an installable live cd, can I do this with remastersys? If so then how? The menu screen does not describe a lot.

---

### Post by wojox on 2013-07-19
Have you seen [Ubuntu Builder]("https://code.google.com/p/ubuntu-builder/") - Ubuntu Builder is a simple tool to build your own distribution. It allows to download, extract, customize in many ways and rebuild your ubuntu images. You can customize i386 and amd64 images

---

### Post by sudo san on 2013-07-20
> **wojox said:**
> Have you seen [Ubuntu Builder]("https://code.google.com/p/ubuntu-builder/") - Ubuntu Builder is a simple tool to build your own distribution. It allows to download, extract, customize in many ways and rebuild your ubuntu images. You can customize i386 and amd64 images

Yes, I have Ubuntu builder, I was going to use it to configure the desktop after creating the iso from scratch. I'll have a go with it and see how it turns out and post back with results. Thanks for reminding me about how you can build them using it.

---

### Post by gazhead on 2013-07-20
first post :)

+1 for ubuntu-builder -> the only tool iknow of that works proper with UEFI. And you can add/remove .deb packages and repos/add user etc -very noobfriendly.
btw -> "yourdistro .iso" will be created in /home/ubuntu-builder

salut

---

### Post by sudo san on 2013-07-31
> **gazhead said:**
> first post :)

+1 for ubuntu-builder -> the only tool iknow of that works proper with UEFI. And you can add/remove .deb packages and repos/add user etc -very noobfriendly.
btw -> "yourdistro .iso" will be created in /home/ubuntu-builder

salut

Thanks for telling me where the iso is put, I'm gonna try this now. Providing my notebook is powerfull enough! :biggrin:

---

