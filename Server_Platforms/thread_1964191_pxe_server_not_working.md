---
title: "pxe server not working"
date: 2012-04-23
forum: Server Platforms
---

### Post by baronobeefdip on 2012-04-23
i am trying to make a working pxe server that can boot and install onto it's clients by serving the contents of a live iso cd (extracted somewhere of course) i have the boot kernels like vmlinuz and initrd.lz files loading the installation process but for some reason the cdrom media is not being mounted so the installation process can't continue and won't work. i have done everything that i have seen online such as the nfsroot declaration, the root, and netboot configurations and nothing seems to be working, i have exhausted all resources on google searching and i jjust simply want to know how do i get the pxe client to mount the cdrom based on what i am sharing via nfs, in other words how do i get the contents of the nfs share to mount onto the pxe client as the /cdrom directory so only then will it have access to the file through the network and start retrieving them like i want it to do. it will think it't retrieving from the cd but in actuality it's retrieving from the pxe server while it hosts itself as the pseudo device that the client take as being the cd rom

all help is appreciated i have been trying to get this to work for weeks already and all the guides on the internet aren't very easy to follow and all answers haven't been very clear i just simply want to know how to get thr nfs share to mount itself on the client as the cdrom drive media

---

### Post by gordintoronto on 2012-04-23
Did you follow this guide: [http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10](http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10)

I think all the important stuff has stayed the same.

---

### Post by Jonathan L on 2012-04-24
All deleted as it was rather off-topic.  Reposted as a How To [http://ubuntuforums.org/showthread.php?t=1969041](http://ubuntuforums.org/showthread.php?t=1969041)

Jonathan

---

### Post by newbie-user on 2012-04-24
Look here for instructions on how to do this without a CD or iso file: [http://techblog.glendaleacademy.org/?p=36](http://techblog.glendaleacademy.org/?p=36)

---

### Post by baronobeefdip on 2012-04-24
i already got it working for ubuntu lucid, i am trying to get it working for debian squeeze, whenever it looks for a disk it looks in the physical drive for the cd contents, i don't want it to do that i want it to look at the nfs share for the files on the cdrom, if that works then all would be fine

---

### Post by newbie-user on 2012-04-24
This tutorial covers PXE for different distributions:

[http://www.howtoforge.com/setting-up-a-pxe-install-server-for-multiple-linux-distributions-on-debian-lenny](http://www.howtoforge.com/setting-up-a-pxe-install-server-for-multiple-linux-distributions-on-debian-lenny)

Same deal with Squeeze, you don't need the CD.

---

### Post by Jonathan L on 2012-04-24
>  i am trying to get it working for debian squeeze, whenever it looks for a disk it looks in the physical drive for the cd contents, i don't want it to do that i want it to look at the nfs share for the files on the cdrom, if that works then all would be fine

I believe the magic parts are the APPEND parts of the flags in the pxeboot configuratiion, which I understand are kernel flags, so should work regardless of the distribution:[COLOR=Red][FONT=monospace]
[/FONT][/COLOR]```
netboot=nfs nfsroot=192.168.1.32:/exports/ubuntu-10.04.3-desktop-i386
```

Kind regards,
Jonathan.

---

### Post by baronobeefdip on 2012-04-24
the thing i want to know here is what declaration tells the client to mount the nfs share as /cdrom, i also saw no mention of using the contents of the iso image or cdrom

by the way what does nfsdir do because in some of the documentation on pxelinux i have seen it in the form of this
```

nfsdir=192.168.1.22:/cdrom

```
or somethimes the directory of the file containing the live cd itself
```

nfsdir=192.168.1.22:/srv/tftp/debian

```
i have tried some of these and they don't work when it comes to mounting the nfs share as a cdrom

---

### Post by baronobeefdip on 2012-04-24
> **Jonathan L said:**
> I believe the magic parts are the APPEND parts of the flags in the pxeboot configuratiion, which I understand are kernel flags, so should work regardless of the distribution:[COLOR=Red][FONT=monospace]
[/FONT][/COLOR]```
netboot=nfs nfsroot=192.168.1.32:/exports/ubuntu-10.04.3-desktop-i386
```

Kind regards,
Jonathan.

i tried that already and it's still attempting to look in the /cdrom directory where it will find nothing, i am expecting to remain seeing it say it's looking in the cdrom drive i just want the os to look at the nfs share containing the contents of the cdrom drive while it thinks it looking inside a cdrom drive

i am trying to get the pxe server to install debian squeeze by using the files that were in the cd image or in some cases on the cd itself

nfsroot i don't think determines the directory of what it should mount as a cdrom i think it does something completely different depending on the os you plan on installing because it worked fine in the ubuntu install but it's getting me a different outcome in the debian install

---

### Post by Jonathan L on 2012-04-24
> nfsroot i don't think determines the directory of what it should mount as a cdrom i think it does something completely different depending on the os you plan on installing because it worked fine in the ubuntu install but it's getting me a different outcome in the debian installI think you're probably right about that.

The initrd.gz of the pxeboot should have an /etc/fstab in it: have you looked in there?

Then you might be able to mount it "conventionally":
```
192.168.1.32:/export/something /cdrom ...

```Kind regards,
Jonathan.

---

### Post by baronobeefdip on 2012-04-24
so what your saying is that inside of the initrd.gz archive there is an fstab file in there that i can edit and get it to automatically mount the nfs share as the cdrom, seems convincing. but i just explored the initrd.gz file and there are tons of files to go through, i want my search to be narrowed down and save myself some time, i would like to know what the name of the file is called that you said functions like the fstab file. also where is this fstab file located in the archive? (if on inside of the disk)

thanks for all your help everything is starting to make a little more sense now

---

### Post by Jonathan L on 2012-04-25
Hi again Baronobeefdip

> everything is starting to make a little more sense now

I'd love to be able to give you a proper "put this line into this file" answer; I'm afraid I don't know the details.  But I do know the boot process which maybe will help you find the right exact answer.

I believe all PXEBOOT linux will do the following:

1.  PXE: DHCP for IP address, mask, router, and critically 'filename' and 'next-server'.
2.  PXE: tftp fetch the 'filename' from 'next-server', in our case pxeboot.0
3.  pxeboot.0 runs a menu, decides on kernel, flags, and initrd.gz
4.  pxeboot.0 fetches kernel and runs it with flags
5.  something, I believe the kernel, tftp fetches initrd.gz
6.  unpacks initrd.gz and executes 'init', the top level script, with appropriate flags

Depending on the contents of this script, anything could happen.  (You unpack the init.gz file to look at the script.)

In Ubuntu installer CD, at least up to 10.04.X Desktop, the boot flags in the pxeboot config specifiy 'boot=casper', which means we'll use the casper scripts instead of others.  It then continues:

7. Init sources scripts/casper, which defines a shell function mountroot() (and subsidiary functions  do_netmount() and do_nfsmount())
8. init runs mountroot, which mounts the root nfs system on /cdrom and then mounts /cdrom/casper/filesystem.squashfs on /root (in a union) -- this squashed filesystem is the real root
9. init execs run-init which moves /root to the real / and then runs its /sbin/init
10.  There is a an /etc/fstab in this filesystem, but it's pointless to specify the CD image here as we've already used it in step 8

I'll guess your system diverges somewhat at step 6.  But if you look at that script you should be able to work it out.

I hope that helps.

Kind regards,
Jonathan.

---

### Post by Jonathan L on 2012-04-25
> by the way what does nfsdir do 

... the variables set in the pxeboot configuration are interpreted by the init script inside initrd.gz, and so are specific to the invidiual release and distribution.  (see my previous post)

Kind regards,
Jonathan.

---

### Post by baronobeefdip on 2012-04-25
so i guess your little initrd.gz extracting and text editing the fstab file would work, i have gotten then initrd.gz fstab file located but it turns out it's inside of another archive and it's read only.it looks like i need to extract them twice, change the file and re-archive everything which for me is the challenge. how can i archive some files in the form of an initrd image. i can't just delete the fstab and replace it with the one that i have because it's read only and won't allow me to do so

also your sure there aren't any flags that need to go after your fstab line
sormally i see this line after the mountpoint and device declarations
```

*(ro,async,no_root_squash,no_subtree_check)

```
this is really starting to make a little bit more sense. and i don't know how i can make it more deinitive since the only issue i was having that the installation dvd image that had been tranferred to the client was looking in the physical cdrom drive and settings in the default file seemed futile, and i was seeking a solutions to get the installer look at the nfs share instead thinking that it was the cdrom it was looking for

now all i need to know is how to edit these file or in the least know how to archive them again in the formats in which they were originally made

---

### Post by Jonathan L on 2012-04-25
> now all i need to know is how to edit these file or in the least know how to archive them again in the formats in which they were originally made

... why not post a link to the CDROM image or at least the initrd.gz and we can have a look at something concrete.

Thanks,
Jonathan.

---

### Post by baronobeefdip on 2012-04-25
Its just a simple Debian DVD for I386 architecture. just a fresh unmodified dvd installer that can be freely downloaded from the debian.org website so when you install it just like that then you'll pretty much have the same setup as i do

---

### Post by baronobeefdip on 2012-04-26
its the tenth link on the page

[http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/](http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/)

---

### Post by baronobeefdip on 2012-04-27
i would like to know at lease a way to configure the initrd.lz (maybe a different extension dependiing on your distro) the easy way, if there is a gui tool out there i would really like to give it a shot because all of the command line extracting and re-archiving seems very complicated when you go by command linxe. it can also be a series of options in the cli in other words it be like a menu in the command line that you can navigate through as you make changes to the initrd file

---

### Post by Jonathan L on 2012-04-27
Hi baronobeefdip

I downloaded the image you describe: [http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/debian-6.0.4-i386-CD-1.iso](http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/debian-6.0.4-i386-CD-1.iso)

And set it up on my server here (copying install.i386/vmlinuz and initrd.gz), with the following in pxeboot's menu:
```
LABEL debian-6.0.4-i386
  MENU LABEL debian-6.0.4-i386
  KERNEL debian-6.0.4-i386/vmlinuz
  APPEND initrd=debian-6.0.4-i386/initrd.gz root=/dev/nfs nfsroot=192.168.0.32:/exports/debian-6.0.4-i386
```The first part boots perfectly, but -- as you've said -- there's no "CD-ROM" for it to use.

It appears that there's no way to mount an NFS export from the contents on this initrd.gz file, as it doesn't have nfsmount, nor ifconfig or as far as I can tell, any way to run the network.

There is, definitely, nothing wrong with PXE boot server in this case.  It's the installer in the image which doesn't know how to do NFS.

I'm afraid I've no experience with Debian, and recommend a specific forum for that OS for the details of how to PXE boot that CD image.

Kind regards,
Jonathan.

---

### Post by baronobeefdip on 2012-04-27
did you modify the initrd file like you told me in a previous post, get the fstab file to mount the nfs share, i think that it pretty much tricks the installer into thinking the nfs share is an actual cd, but if you did modify it and say that it doesn't work then i don't know what i will do next.

---

### Post by Jonathan L on 2012-04-28
Hi again baronobeefdip

Respectfully, you're in a Ubuntu forum, not a Debian one.  Installation details vary enormously from one to the other.

To do what you want (PXE boot, install Debian) I followed the instructions here [http://wiki.debian.org/PXEBootInstall?action=show&redirect=DebianInstaller%2FNetbootPXE]("http://wiki.debian.org/PXEBootInstall?action=show&redirect=DebianInstaller%2FNetbootPXE")

In essence, don't use the CD-ROM image you referenced, as it simply isn't designed for what you want to do.  (Also, don't use the one called debian-6.0.4-i386-netinst.iso, that is for CD-ROM boot, packages on network.)

What you want is PXEBOOT, packages on network, no CD-ROM at all.

Use the following 8Mbyte tar file as your whole /var/lib/tftpboot
[http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/netboot/netboot.tar.gz](http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/netboot/netboot.tar.gz)
MD5 is 258f9cd742870213f373048954ccb9ac

That is to say, do this
```
cd /tmp
wget http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/netboot/netboot.tar.gz

sudo mv /var/lib/tftpboot /var/lib/tftpboot-old
sudo mkdir /var/lib/tftpboot
cd /var/lib/tftpboot
tar xvfpz /tmp/netboot.tar.gz
```This boots you into a network based installer which configures your ethernet card, asks you to choose a server where the images are (from a list) and installs.  You won't need NFS.

I'm sure this is exactly what you need.

Kind regards,
Jonathan.

---

### Post by newbie-user on 2012-04-29
[http://www.howtoforge.com/setting-up-a-pxe-install-server-for-multiple-linux-distributions-on-debian-lenny](http://www.howtoforge.com/setting-up-a-pxe-install-server-for-multiple-linux-distributions-on-debian-lenny)

That link will show you how to boot all sorts of distributions off of a single debian server. No CD needed for this! You just download the boot files from your local mirror. No need for NFS mounts or anything like extracting initrd.gz

---

### Post by Jack Alexander on 2012-05-07
Ubuntu 12.04
I have a local network with a PXEboot server. I'm trying to add Ubuntu 12.04 to the menus so I can image servers in the local network.
The initrd and vmlinuz load just fine. I know I have the network installer configured with my tftpboot server, because instead of looking for a CDROM, it lets me configure and eth device. Using DHCP from my server it gets the connection.
Now the problems start, first it tries to use a mirror site, which I don't want. and then it always using wget to try to get the files from my server. I don't want it to use http, I want it to use NFS.
I've tried many APPEND options to specify the NFS info, but nothing works. It always tried wget instead.

Does NFS work for installation from a PXE environment?

---

