---
title: "NetbootCD"
date: 2009-12-07
forum: The Cafe
---

### Post by maybeway36 on 2009-12-07
NetbootCD is my live CD that can install many Linux distros. It boots into a slightly modified Tiny Core in text-mode and pops up a few dialogs asking you which distro and version to install. Then, it downloads the kernel and initrd and uses kexec to load them, replacing itself in memory with the new distro's installer. The installer then proceeds to install the rest of the distribution as normal.

It can also load the latest versions of Tiny Core Linux and GRUB4DOS. (This is mostly to show off.)

You can get it at: [http://netbootcd.tuxfamily.org/](http://netbootcd.tuxfamily.org/)

The newest version is 4.0, based on Tiny Core's microcore 3.6.

This will be my new thread for support requests. If something doesn't work right, feel free to post.

---

### Post by earthpigg on 2009-12-07
outstanding idea!

does it give detailed/expansive options, such as giving you the option to (using ubuntu as the example) get a command line only install, kubuntu, or ubuntu?

how is wireless support? 

does it play well with unetbootin?

---

### Post by maybeway36 on 2009-12-09
In response to your questions:

1. When installing Ubuntu, NetbootCD will ask if you want a desktop or command-line install. Then, while the installer is running, it asks if you want Ubuntu, Kubuntu, etc. (this is built into the installer itself.) It even does this if you said command-line only, and I'm not quite sure why - maybe I can fix this.

2. There actually isn't any wireless support, so you'll have to connect the computer to an Ethernet cord to install Linux on it. This is because of various distribution issues (b43) as well as keeping the size small.

3. As for UNetbootin, I can't see any way they would conflict. They do a lot of the same things, but NetbootCD does it from a live CD with kexec while UNetbootin does it from an installed system and a new GRUB entry.

---

### Post by maybeway36 on 2009-12-09
Okay, I've released version 3.2.1. It fixes the "download" menu option being left out, and tasksel no longer shows up when you select an Ubuntu command-line install. I also fixed the download link. #-o

---

### Post by dragos240 on 2009-12-09
Hmm... is the kernel compiled with wireless support, and does it come with wireless firmwares and wireless tools including wpa_supplicant?

---

### Post by earthpigg on 2009-12-09
> 3. As for UNetbootin, I can't see any way they would conflict. They do a lot of the same things, but NetbootCD does it from a live CD with kexec while UNetbootin does it from an installed system and a new GRUB entry.

i was asking if i could feed unetbootin ***your*** .iso and have the end result work (ie: bootable and functional thumb drive containing your NetbootCD release) :D

none of my systems (netbook and desktop) have an optical drive... i have an external USB one buried in the closet somewhere.

---

### Post by maybeway36 on 2009-12-10
> **dragos240 said:**
> Hmm... is the kernel compiled with wireless support, and does it come with wireless firmwares and wireless tools including wpa_supplicant?

Wireless firmware and tools are not included, but I might make a seperate version where they are. The kernel, I believe, does have wireless support, since I don't think I disabled anything when compiling it.

> **earthpigg said:**
> i was asking if i could feed unetbootin ***your*** .iso and have the end result work (ie: bootable and functional thumb drive containing your NetbootCD release) :D

none of my systems (netbook and desktop) have an optical drive... i have an external USB one buried in the closet somewhere.

I'm thinking that might work. I haven't tried it myself, but UNetbootin is generally good about getting CDs to work when they just have one kernel and one initrd.

---

### Post by maybeway36 on 2011-05-16
I just updated NetbootCD to version 4.0. The newest script is built in. Also, the CD version (not the floppy one, though) comes with pxe-kexec, which lets you use PXELINUX.CFG config files, in case that's your thing.
Oh, and the CD version works on a USB drive (thanks to isohybrid.) Just grab a small, unneeded USB stick and put this on it with dd!

---

### Post by compact1 on 2011-06-15
Though I'm not a programmer I stumbled upon KEXEC as a 'kind of booting' of devices like pcmcia and usb where the mainboard bios itself can't boot from.

'Kexec loader': [http://www.solemnwarning.net/kexec-loader/](http://www.solemnwarning.net/kexec-loader/) 
Is a nice (and only ?) tool for making things easier. But this loader lacks some hardware detection where MicroCore does detect the hardware very fine. 
So I'm happy with your NetBootCD. Kexec doesn't seem to be in the standard TinyCore tcz-packagelist. Thank you.

Isn't it an idea to expand NetbootCD with an adapted or kind of "kexec loader" for local boot ? It would make NetBootCD even stronger with KEXEC's 'special' boot
possibilities and it will not change the mb's that much I think.
I'm sorry if I ask too much. In that case NetBootCd is just nice the way it is.

Friendly Greetings, Compact1

---

### Post by maybeway36 on 2011-06-21
> **compact1 said:**
> Though I'm not a programmer I stumbled upon KEXEC as a 'kind of booting' of devices like pcmcia and usb where the mainboard bios itself can't boot from.

'Kexec loader': [http://www.solemnwarning.net/kexec-loader/](http://www.solemnwarning.net/kexec-loader/) 
Is a nice (and only ?) tool for making things easier. But this loader lacks some hardware detection where MicroCore does detect the hardware very fine. 
So I'm happy with your NetBootCD. Kexec doesn't seem to be in the standard TinyCore tcz-packagelist. Thank you.

Isn't it an idea to expand NetbootCD with an adapted or kind of "kexec loader" for local boot ? It would make NetBootCD even stronger with KEXEC's 'special' boot
possibilities and it will not change the mb's that much I think.
I'm sorry if I ask too much. In that case NetBootCd is just nice the way it is.

Friendly Greetings, Compact1

The thing kexec-loader has going for it is that it fits on one 1400 KB floppy ;)
Anyways, with NetbootCD, you can exit to the command line, then run kexec. (Actually, sudo kexec, because you need to be root.) The manpage will help you out: [http://man.cx/kexec](http://man.cx/kexec)

---

### Post by compact1 on 2011-07-15
> **maybeway36 said:**
> 
Anyways, with NetbootCD, you can exit to the command line, then run kexec. 

Yes. I did that already.
Typing that whole lot in again and again is not that comfortable.
That was the reason why I asked you.
But I managed to take the kexec binary out of nbinit.gz and use it together with TinyCore from the tc+nb.iso.
It's a pitty kexec is not in tinycore.gz for it is in nbinit.gz.
It may be an idea to implement kexec in tinycore.gz aswell for local kexec booting ?

Another fine thing is that you can boot, fully load & run your TinyCore with Plop from a USB drive where the mainboard-bios itself can't boot from. There are not many distro's (but Vector 6 does) who can fully load and run this way because too often booting is alright but loading stops with errors because they can't recognise where they are booting from. Not so with your version of TinyCore ! Runs perfectly right out of the box !

So thanks again for NetbootCD and your reply.
Sorry for my late answer.

Friendly Greetings, Compact1

---

### Post by maybeway36 on 2011-07-16
> **compact1 said:**
> Yes. I did that already.
Typing that whole lot in again and again is not that comfortable.
That was the reason why I asked you.
But I managed to take the kexec binary out of nbinit.gz and use it together with TinyCore from the tc+nb.iso.
It's a pitty kexec is not in tinycore.gz for it is in nbinit.gz.
It may be an idea to implement kexec in tinycore.gz aswell for local kexec booting ?

Another fine thing is that you can boot, fully load & run your TinyCore with Plop from a USB drive where the mainboard-bios itself can't boot from. There are not many distro's (but Vector 6 does) who can fully load and run this way because too often booting is alright but loading stops with errors because they can't recognise where they are booting from. Not so with your version of TinyCore ! Runs perfectly right out of the box !

So thanks again for NetbootCD and your reply.
Sorry for my late answer.

Friendly Greetings, Compact1

How would you like me to implement pxe-kexec into the menu? I'm not quite sure how it works, exactly.
By the way, the regular Tiny Core kernel doesn't support kexec. The tc+nb.iso loads Tiny Core with NetbootCD's kernel. I really should put the kexec binary in tinycore.gz.

---

### Post by compact1 on 2011-07-19
Me too has no exact idea how to implement this. But an extra menu item with which you can start your own kexec-boot-scripts (which can be easily self made from a isolinux.cfg or menu.lst) would be very welcome. 
Perhaps via a special map or so where you can place them ?
I just managed to boot DSL from pcmcia compact flash where the bios itself cannot boot from. Thanks to NetBootcd !

On the other side. Tinycore and MicroCore with the kexec binary and kernel from netBootcd work very fine. So this also could be enough. With it I hope it is also possible to make a syslinux menu with autostart scripts for microcore to ease the choice of "special" booting tasks. Is it also possible to release a "kexec.tcz" file so that kexec can be installed in TinyCore aswell as in MicroCore ?

Friendly Greetings, Compact1

---

### Post by maybeway36 on 2011-07-23
I suppose I could make a tcz file for kexec, but it wouldn't help that much because the regular Tiny Core kernel doesn't support kexec. I'll probably just add kexec to the tinycore.gz on tc+nb.iso, and have it use the NetbootCD kernel like it is now.

---

### Post by compact1 on 2011-07-25
> **maybeway36 said:**
>  I'll probably just add kexec to the tinycore.gz on tc+nb.iso

Yes this would be an excellent idea. This way it's easier to use kexec for other booting purposes.

I personally did the following :
- placed 'text' in the append line and nodhcp; noswap etc. 
- made an empty extra tce dir. So TC doesn't load all the extra stuff it would normally load and refer to that one in the append line too
- edit /opt/bootlocal.sh to start up the kexec script automatically
- and saved it with filetool.sh -b

Works very nice and you can boot now from devices you normally can't boot from.
Even with 1 key press in a syslinux menu !
I hope this is usefull information for others too.
I'm glad with NetBootCD. Thanks again.

Friendly Greetings, Compact1

---

### Post by maybeway36 on 2011-07-27
I'm glad you were able to get it to work!
Just curious - what does your kexec script look like? Is it different depending on what you're booting?

---

### Post by compact1 on 2011-07-30
> **maybeway36 said:**
> what does your kexec script look like? Is it different depending on what you're booting?

This is the dsl.cfg for syslinux (I personally load it with config.c32 in syslinux.cfg):

default tinycore
label tinycore
 kernel /boot/tcl/kexec.bzI
 append initrd=/boot/tcl/tinycore.gz text tce=hda2/boot/tcl/kexec/dsl vga=791 noswap nodhcp noutc nozswap quiet

The kexec-scripts 2nd-line differ nearly as much as a menu.lst or syslinux.cfg would for their normal grub or syslinux boot.

This is the dsl.sh kexec-script:

sudo mount -o loop -t vfat /dev/hde1 /mnt/hde1
sudo /mnt/hda2/boot/tcl/kexec/kexec -l /mnt/hde1/KNOPPIX/linux24 --initrd=/mnt/hde1/KNOPPIX/minirt24.gz --append="xmodule=fbdev quiet frompcmcia ramdisk_size=100000 init=/etc/init lang=us apm=power-off mydsl=hde2 vga=791 nomce noapic BOOT_IMAGE=KNOPPIX"
sudo umount /dev/hde1
sudo /mnt/hda2/boot/tcl/kexec/kexec -e

It would shorten the dsl.sh script a little if the kexec-binary would be in tc in the tc+nb.iso.
I don't understand the need of a TinyCore version with a kexec compiled kernel if the kexec-binary itself is missing. Can you explain that to me ?

For a more detailed description about this Damn Small Linux booting with NetbootCD from a "not bootable by bios pcmcia" you could read Compact at: 
[http://forum.plop.at/index.php/topic,313.0.html](http://forum.plop.at/index.php/topic,313.0.html)
Or do you want me to post an abstract of it here too ?

Friendly Greetings, Compact1

---

### Post by maybeway36 on 2011-07-30
You need both kexec support in the kernel AND a kexec binary. It's silly :)
I think with the next NetbootCD version, I'll add an option to the NetbootCD menu that lets you run a custom script. The only problem with automating something like this is that NetbootCD would have to find out where its own boot device is. But I suppose that could be done by searching for some sort of marker file (I believe this is what Slax/Porteus does.)

---

### Post by compact1 on 2011-07-31
> **maybeway36 said:**
> NetbootCD would have to find out where its own boot device is. But I suppose that could be done by searching for some sort of marker file

I'm afraid I can't help you with this one ...... perhaps someone else ???

To be able to run kexec-scripts more directly would fill in a gap though.
Some example scripts for the starting up of NetBootCD itself and specialy Grub4dos could perhaps also be nice ?

But Kexec in TinyCore also add very nice extra "special boot options" in a "1 key press" Syslinux menu as I described. It can be done with the same (eventually full blown) TinyCore and it costs little extra fuzz and space. Works great ! 

Keep up your good work !

friendly Greetings, Compact1

---

### Post by bumble-b on 2011-08-23
I'm trying to use NetbootCD for multiboot-flash-drive purpose. 
Feature is - no special partition creation / iso modifications. New images are added by simply copying them to a flash drive. How to try it: [http://gitorious.org/multi-boot-disk-test/pages/Home](http://gitorious.org/multi-boot-disk-test/pages/Home)

---

### Post by maybeway36 on 2011-08-25
I've released NetbootCD 3.5. See the "Notes" section of [the website](http://netbootcd.tuxfamily.org/) for information. Version 4.0 isn't technically obselete - it still works just fine.

---

### Post by compact1 on 2011-09-04
Thank you for NetBootCD 4.5
And for updating TinyCore from 3.6 to 3.7.1 with the implementation of the kexec binary.
Works very fine.

Unfortuneatly I couldn't test the read-cfg.sh script more profound.
For the gui doesn't appear without an internet connection.
and the use of Network.gz takes ~110Mb extra of my 142Mb total memory ?!
Probably that's why nbcd couldn't start up with wifi ?
But I could load and run the script isolinux.cfg of nbcd in VMware 
Player and it did work very well ! 
Wonderful idea and scripting ! I didn't even knew this can be possible !
You sure can do nice things with and for kexec ! Thank you ! 

Friendly Greetings, Compact

---

### Post by maybeway36 on 2011-09-04
Thanks! You might want to know that I did not consider RAM at all when writing that new .cfg loader script. :P So anythng with multiple initrds needs a lot more RAM to load from within NetbootCD.

---

### Post by AlexTALL on 2011-09-19
I'm not sure if these are connected, so I'll separate them into different issues and we'll find out.

1) When installing CentOS from the default mirror, I get a message that the file type of /tmp/nb-linux cannot be determined, and I am given a command line.

2) When trying to install CentOS, it appears the script ignores the HTTP server typed in and instead simply uses the default mirrors.kernel.org. I have tried using both a different source all together and simply using a different architecture (x86_64).

Thanks!

P.S. I am using 4.5 and have tried redownloading the script in case there was a problem there.

---

### Post by maybeway36 on 2011-09-19
For #1, I assume the default server doesn't work for some reason. For #2, I'm not sure, but maybe the command-line syntax has changed. I should look into both of these.

In other news, there's a nice tutorial on NetbootCD here: [http://www.makeuseof.com/tag/netbootcd-install-ubuntu-fedora-debian-cd-linux/](http://www.makeuseof.com/tag/netbootcd-install-ubuntu-fedora-debian-cd-linux/)

---

### Post by sungjinhong on 2011-09-21
CentOS does not work. Apart from mirror.kernel.org currently not working, specifying other mirrors still makes Netboot download CentOS from mirror.kernel.org.

When changing the mirror URL directly in the nbscript, kext does not work with error that --args-linux does not exist.

Here's the patch (If you have a github account, I can send a push request to you):

```
--- nbscript.sh.old	2011-09-21 12:15:30.000000000 +0900
+++ nbscript.sh	2011-09-21 12:15:35.000000000 +0900
@@ -214,10 +214,11 @@
 	5.5 "CentOS 5.5" \
 	Manual "Manually enter a version to install" 2>/tmp/nb-version
 	getversion
-	KERNELURL="http://mirrors.kernel.org/centos/$VERSION/os/i386/isolinux/vmlinuz"
-	INITRDURL="http://mirrors.kernel.org/centos/$VERSION/os/i386/isolinux/initrd.img"
 	#Ask the user which server to use (the installer doesn't have a built-in list like Ubuntu and Debian do.)
 	dialog --inputbox "Where do you want to install CentOS from?" 8 70 "http://mirrors.kernel.org/centos/$VERSION/os/i386" 2>/tmp/nb-server
+	SERVER=$(cat /tmp/nb-server)
+	KERNELURL="$SERVER/isolinux/vmlinuz"
+	INITRDURL="$SERVER/isolinux/initrd.img"
 	echo -n "method="$(cat /tmp/nb-server) >>/tmp/nb-options
 	rm /tmp/nb-server
 fi
@@ -334,9 +335,6 @@
 else
 	ARGS="-l /tmp/nb-linux --initrd=/tmp/nb-initrd --append=\"$OPTIONS\""
 fi
-if [ $DISTRO = "centos" ];then
-	ARGS=$ARGS" --args-linux"
-fi
 #This checks to make sure you are indeed on a TCB system.
 if [ -d /home/tc ];then
 	echo kexec $ARGS
```

---

### Post by ascent1729 on 2011-09-22
I tried to use this by downloading [NetbootCD-4.5+TinyCore.iso]("http://downloads.tuxfamily.org/netbootcd/4.5/NetbootCD-4.5+TinyCore.iso") from the NetbootCD site and putting it on a USB drive using Unetbootin, but every download fails with "/tmp/nbscript.sh: line 346: kexec: not found". The kexec.gz file exists (in the boot/ directory), but there is no kexec file on the accessible system when I boot the USB drive, and you can't mount any drives, so there's no way to put kexec there.

---

### Post by maybeway36 on 2011-09-23
I fixed CentOS and added support for Scientific Linux. Use the "download" option on the main menu.

@ascent1729: NetbootCD 4.5 needs multiple initrds. I never thought it would mess up unetbootin. :( Download version 4.01 instead from [here,](http://downloads.tuxfamily.org/netbootcd/4.01/) then press "download" first whenever you boot it.

---

### Post by maybeway36 on 2011-09-27
NetbootCD 4.6 is out. The floppy version is fixed, Scientific Linux 6 and CentOS 6 are now supported, and it should work with UNetbootin now (I put kexec in nbinit4.gz.)

Also, I'm now posting update notices for this and multicd on Twitter (@multicd) and Tumblr ([http://multicd.tumblr.com](http://multicd.tumblr.com)). I'm really just using Tumblr as a frontend for Twitter, but you can follow it either way, or just use [RSS.](http://multicd.tumblr.com/rss)

---

### Post by AlexTALL on 2011-09-28
Thanks for the prompt response! I'm setting up CentOS now.

Is there a way to install a 64bit OS? I've tried changing the download URL to x64 or x86_64 depending on the distro, but it seems to ignore the change and still download the i386 build. I'm seeing this specifically with Fedora.

---

### Post by maybeway36 on 2011-10-04
I updated the nbscript.sh to add an option for 64-bit CentOS/ScientificLinux. Press "download" and then see if it works.

---

### Post by rikels on 2011-10-13
for me the CentOS installations still don't work... 
V5 and 6 don't work. tried them both.

---

### Post by compact1 on 2012-04-23
It has been some time I've been here.
In the mean time it seems NetBootCD had it's effect for TinyCore has kexec compiled in the kernel now. And a new comparabel kexec loader appeared on the horizon called: Plopkexec. But (Tiny)Core still misses the kexec package and Plopkexec gives a kernel panic on my old Dell Inspiron 3000. The 'script' option of NetBootCD is very nice for local booting from pcmcia and usb  with a bios that has impossibilities to do so. But NBCD needs a working internet connection before it starts up and a internet connection is not directly needed and wanted for local booting ..........

So now I tried to combine the new Core with the essential parts of NBCD for local booting. It took me some time to autostart read-cfg.sh but this is how I finally did it with Lubuntu 11.10.

- copy the 'boot' dir of the core-4.4.iso to hd
- rename isolinux in syslinux (fat) or extlinux (ext) and make the partition bootable
- create a dir nbcd in the root of the partition and in it the dir /nbcd/optional
- the following .tcz files (incl. *.dep and *.md5.txt) have to be copied in this optional dir. kexec.tcz is taken from the NetbootCD-4.9+CorePlus-4.3.1.iso:

  bash.tcz
  ncurses-common.tcz
  ncurses.tcz
  dialog.tcz
read-cfg.tcz
  kexec.tcz

- the above mentioned list has to be copied and pasted, extacly as it is, in a textfile called: onboot.lst. onboot.lst has to be saved in /nbcd so like: /nbcd/onboot.lst
- The read-cfg.tcz is made on the following way:
  - first we copy /usr/bin/read-cfg.sh from a working NBCD (or out of nbinit4.gz, nbinit4 is a cpio archive) to a working dir called x like this: /path-to/x/usr/bin/read-cfg.sh 
    $ sudo mksquashfs /path-to/x read-cfg.tcz
- Because read-cfg.sh has its dependencies we also make a read-cfg.tcz.dep text-file wich must contain:
  
  bash.tcz
  dialog.tcz

- You also have to make a md5 checksum file and call it: read-cfg.tcz.md5.txt
- isolinux.cfg has to be renamed to syslinux.cfg (fat) or extlinux.conf (ext)
  and has to contain the following lines:

KERNEL /boot/vmlinuz
APPEND initrd=/boot/core.gz tce=sda?/nbcd showapps noswap nodhcp noutc quiet

? is your partition. With only 1 partition this is usualy sda1


Core should boot and start-up now and if you type in: 
$ sudo read-cfg.sh
The "Load Script" dialog should appear.
We "Cancel" and go to the autostart part now while in Core.

$sudo vi /etc/passwd
In the 2 lines that start with "root" and "tc" "/bin/sh" has to be replaced by: "/usr/local/bin/bash"
We save that change.

$echo "sudo /usr/bin/read-cfg.sh" > /home/tc/.bash_profile

$sudo vi /opt/.filetool.lst
We add the following line:
/etc/passwd
And save the change

$filetool.sh -b
saves the above changes in /nbcd/mydata.tgz.

The 'Load Script' dialog (read-cfg.sh) should autostart now if you reboot.

Keep in mind that you still have to copy or rename extlinux.conf to extlinux.cfg otherwise read-cfg.sh is not able to find it. But you got a fine and special kexec local bootloader now that is not dependent on a internet connection. It seems to be working fine here.

If I forgot something; did something wrong or things can be done better please tell me.

Thanks again for NBCD.

Friendly greetings, Compact1

---

### Post by maybeway36 on 2012-04-23
Thanks for the information! I'm sure someone will find it handy.
I haven't tested your instructions but you might be able to get the same effect by starting with the CorePlus+NetbootCD boot option on the combined ISO. It loads the NetbootCD kernel/initrd but also the tcz extensions that CorePlus comes with.
Then you can bypass the network check by running "sudo /usr/bin/read-cfg.sh" directly. Make sure that when you run it you're in text mode, not in X11.

---

### Post by compact1 on 2012-04-23
> **maybeway36 said:**
> Make sure that when you run it you're in text mode, not in X11.

It doesn't seem that CorePlus provides any kexec.tzc nor in the repos of TinyCore ? I only found kexec.tcz in CorePlus+NetbootCD. And "of course" I also did put kexec.tcz and read-cfg.tcz in the "normal" TinyCore to see wether it would work. And it even seems to work under X11. At least the "Load Script" dialog popped up and it could find some cfg's. All in a terminal. But I still have to test the real kexec-booting and running (only a few distro's will fully load and run because of pcmcia and usb recognition). Do you mean that kexec-booting and running will not work under X11 with these 'special' distro's ?

---

