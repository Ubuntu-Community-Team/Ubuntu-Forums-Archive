---
title: "HOWTO: Create 12.04 Persistent &amp; Backtrack 5 USB"
date: 2012-04-29
forum: Tutorials
---

### Post by flyingsliverfin on 2012-04-29
Hey all, I just wanted to share the process I went through to somehow put together a working USB that can dual boot BackTrack 5 and Ubuntu 12.04, with ubuntu being persistent as well.

This IS a manual procedure since tools like Unetbootin and the provided usb creator on ubuntu cannot dual boot systems, and they use syslinux. I used GRUB to get mine working.

I don't really know what goes on behind the scenes in GRUB, or ubuntu's boot up process. I pretty much made this by pulling info from different guides and forums on the web, including [A better way to create a customized USB drive with Ubuntu Live on it ]("http://rudd-o.com/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive") (and the comments at the bottom), [this thread]("http://www.backtrack-linux.org/forums/showthread.php?t=42735"), and [this]("http://www.panticz.de/MultiBootUSB") for reference.


This is what I started with:
[LIST]
[*] Ubuntu 12.04 iso
[*] BT5 R2 iso
[*] 16 GB flash drive
[*] GRUB2 for the booting stuff
[/LIST]

Here's what I came up with...

Drawing from the info in the first link (which is slightly outdated but still mostly works except for an old version of GRUB), here's the general layout of my stick:

first partition:
[LIST]
[*] ~4 GB (or any size so that you have ~730 MB left afterward works), 
[*] FAT32 (lba) (code 'c' in fdisk)
[*] this will become the partition with GRUB, BT5,  some files needed by ubuntu to boot, and the casper-rw file that makes Ubuntu persistent
[/LIST]

second partition: 
[LIST]
[*] 730 MB 
[*] ext4
[*] this will become the partition with the ubuntu cd's contents on it
[/LIST]

You can partition/size the partitions from Gparted if you like.

In my specific case I made a third partition for storing my own files (so out of 16 GB I had 4.25 GB for first partition, 730 MB for ext4, and 10 GB for data)

MOST of the command line instructions require superuser privileges, it's easier just to execute them as root, which is what I did.

According to the first link again, I called my first partition UbuntuLive, and mounted it as USBDRIVE (in /media)
```
mkdir /media/USBDRIVE
mount /dev/sdc1 /media/USBDRIVE
```
Note that this is when my USB drive is recognized as /dev/sdc. This is what I assume it to be for the entire tutorial

Here's a very important step: install GRUB onto the first partition (remember I have it mounted as /media/USBDRIVE)

```
grub-install --no-floppy --root-directory=/media/USBDRIVE /dev/sdc
```
Next I mounted the Ubuntu ISO, copied two files (initrd.lz and vmlinuz) into the first partition.
```
mkdir /media/iso
mount -o loop /path/to/ubuntu/image.iso /media/iso
cp /media/iso/casper/{vmlinuz,initrd.lz} /media/USBDRIVE/boot/
umount /media/iso
```
Be sure to replace /path/to/ubuntu/image.iso with the location of the ubuntu iso.

Once again following the first link's instructions, I did a byte by byte copy of the ubuntu ISO to the second, ext4 partition:
```
sudo dd if=/path/to/ubuntu/image.iso of=/dev/sdc2
```
[COLOR="Red"]CAREFUL[/COLOR] with the dd command! You could overwrite your whole hard drive!


I then created a folder in USBDRIVE (first partition) I called BT5, mounted the BackTrack 5 ISO, and copied all the files into the new folder:
```
mkdir /media/USBDRIVE/boot/BT5
mount -o loop /path/to/Backtrack/image.iso /media/iso
cp -R /media/iso/* /media/USBDRIVE/boot/BT5
umount /media/iso
```


Ok: so now we've got our partitions, we've got grub installed, ubuntu and BT5 files are in place. Now we just need to add persistence and edit GRUB's menu.


First Persistence:

Make a file that will be where Ubuntu saves changes etc. I made it the maximum size allowed in the first partition after BT5 and GRUB files (~2.5 GB) were in place.
```
dd if=/dev/zero of=/media/USBDRIVE/casper-rw bs=1M count=1500
```
Making it a 1.5 GB casper-rw persistence file.

Then make it the right type of file. I'm not really sure what this step does, but it seems to me like it turns the file into a sort of ext4 filesystem that is theoretically mountable (?). Just guessing.
```
mkfs.ext4 -F /media/USBDRIVE/casper-rw
```

Finally, we need to edit grub's configuration files to recognize the changes we made. Use whatever editor you want, just create a file /media/USBDRIVE/boot/grub/grub.cfg
Here's what I put in mine:
> 
set default=0
set timeout=5

menuentry "Ubuntu Persistent 12.04" {
search --set -f /boot/vmlinuz
linux /boot/vmlinuz boot=casper file=/preseed/distro.seed quiet splash noprompt -- persistent
initrd /boot/initrd.lz
}

menuentry "BackTrack 5" {
 set gfxpayload=1024x768x16
 linux /boot/BT5/casper/vmlinuz boot=casper live-media-path=/boot/BT5/casper/ text splash
 initrd /boot/BT5/casper/initrd.gz
}




Unmount, reboot, and hopefully everything's working!
Please *check* the commands I wrote up for errors before using them. I was in a bit of a rush and tired when I wrote this.
Let me know how it goes! I'll come back later to see if someone alerted me to a missing step or wrong command ;)

Good Luck!

One last thing:
If you run our of room in the casper-rw file or something else happens, the first link ([here ]("http://rudd-o.com/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive")) has a section called "Care and Feeding of your USB drive" which has some useful bits of information.

---

### Post by appsman on 2012-06-10
I followed all instructions but the laptop will not boot off of the new USB. Must be a problem with GRUB?

I have another USB that I do boot off of, so I know boot order and stuff like that is set OK.

---

### Post by flyingsliverfin on 2012-06-10
Is there an error that shows up when you boot or does it altogether skip the USB and just boot normally?

---

### Post by appsman on 2012-06-10
It skips USB and boots normal.

---

### Post by appsman on 2012-06-10
It skips USB and boots normal.
No error.

---

### Post by flyingsliverfin on 2012-06-10
Sometimes you may need to put the 'boot' flag onto the 1st partition with grub. You can do this both with fdisk (command line) and gparted.

In gparted you can do this by going to the device, then right clicking on the first partition and selecting 'manage flags' (you might need to unmount first). Check the box next to 'boot' and see what happens when you restart.

Also do you have a mac? Mac's need special formatting so this process wouldn't work for them.

---

### Post by appsman on 2012-06-11
Thanks for the reply. After all that work it stunk having just one little thing.

Good news is that I set the boot flag to true using gparted (did not have to unmount). Afterwards, I could boot off of the USB and bring up Back Track 5.

Bad news is that it threw an error when I tried to boot off of Ubuntu Persistent 12.04.
> error: file not found
Press any key to continue ...

Then after a few minutes 13 errors appeared in a different font, beginning with this one:
> kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I found some posts on the web about this error ([like this one]("http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0") which creates an initrd file and runs updage-grub).

What do you think?

---

### Post by flyingsliverfin on 2012-06-11
One time I had a set of errors booting ubuntu when I forgot to run this step

mkfs.ext4 -F /media/USBDRIVE/casper-rw

to install an ext4 filesystem onto the casper-rw file.

Otherwise, does it drop you down to a  ubuntu prompt of some sort?
Can you execute commands when it finished loading or does it just hang after the errors?

Tomorrow afternoon I'll make a new USB with these steps to see if its something with the directions I wrote up. I'll let you know how it goes then

---

### Post by appsman on 2012-06-11
flyingsliverfin, many thanks for your attention.

I do not get any Ubuntu prompt after the 13 errors when I tried to boot off the new USB after selecting Ubuntu. It just hangs and I cannot execute a command.

So I rebooted (into my other USB boot OS) and did the requisite mounting and repeated the command
```
mkfs.ext4 -F /media/USBDRIVE/casper-rw
```
but it seemed to act the same.

Then I tried to boot up on the USB stick again, but this time I hit "e" so I could edit the commands. There were four commands, and after the first three seemed happy, the fourth one barfed.
```
initrd /boot/initrd.lz
```

Then I rebooted into Ubuntu and checked the boot directory:
```
$ ls /media/####-####/boot
BT5  grub  vmlinuz

```

... there is no initrd.lz file. So I reviewed your instructions:
```
mkdir /media/iso
mount -o loop /path/to/ubuntu/image.iso /media/iso
cp /media/iso/casper/{vmlinuz,initrd.gz} /media/USBDRIVE/boot/
umount /media/iso
```

Perhaps the "{vmlinuz,initrd.gz}" is a typo? Should be "{vmlinuz,initrd.**[SIZE="3"]l[/SIZE]**z}"?

---

### Post by flyingsliverfin on 2012-06-18
Sorry for not getting back earlier. Have you tried putting .lz instead of .gz? I think what you pointed out is correct, it should be .lz since the ubuntu ISO does not contain an .gz at all.

Thanks for pointing that out. I will change it to .lz in the guide.
It should work after that :-k

---

### Post by appsman on 2012-07-01
Yeah, FlyingSilverFin that was some good sleuthing, and this USB boot drive rocks! Thanks for the handy guide.

To wrap this up in case anyone is reading this thread, I would say nothing to worry about here, just stick with the original post #1 - *except* the following:
I recommend putting a note about setting the boot flag in the original post.

---
And here are a few side notes.

[LIST=1]
[*] For the record a "read-only" error appears when copying an iso (Backtrack iso in the code below). This error can be ignored.
```
$ sudo mount -o loop /path/to/Backtrack/image.iso /media/iso
mount: warning: /media/iso seems to be mounted read-only.
```
[*] I could not do this >  create a file /media/USBDRIVE/boot/grub/grub.cfg because the partition was full. Root cause is that when I specified "4GB" gparted took it as 4GB maximum, which ended up being about 3.75GB. You reported 4.25GB. I contemplated making the swap file 1300MB instead of this
```
$ dd if=/dev/zero of=/media/USBDRIVE/casper-rw bs=1M count=1500
```
but decided to start all over again because I want the extra swap space, and the ~10GB partition is plenty big anyway.
[*] Finally, there is a "grain of truth" to the .lz versus .gz typo: this file does exist for Backtrack.
```
/media/USBDRIVE/boot/BT5/casper/initrd.gz
```
[/LIST]
):P

---

### Post by sbrown995 on 2012-08-04
Hey flyingsliverfin, This is a great tutorial. I was wondering if there is a way to make backtrack 5 persistent as well. Or does this already do that as well as make ubuntu persistent?

---

### Post by arashiredsun on 2013-01-25
I recommend you watch this video easy and fast ...
[https://www.youtube.com/watch?v=EtPAybac_rY](https://www.youtube.com/watch?v=EtPAybac_rY)

---

### Post by arashiredsun on 2013-01-25
> **appsman said:**
> It skips USB and boots normal.
[https://www.youtube.com/watch?v=EtPAybac_rY](https://www.youtube.com/watch?v=EtPAybac_rY)

---

### Post by complience on 2013-03-05
Can you add these developments to your original post?
I'm not sure on what order all the steps need to be applied now

---

### Post by tom-visser-1985 on 2013-12-23
> **flyingsliverfin said:**
> Then make it the right type of file. I'm not really sure what this step does, but it seems to me like it turns the file into a sort of ext4 filesystem that is theoretically mountable (?). Just guessing.
```
mkfs.ext4 -F /media/USBDRIVE/casper-rw
```


Didn't really read through comments/ replies yet, so i might be restating someone else, but you are indeed correct :-)

ty for the guide, I actually have a script that is very similar that is on another system, and you saved me a lot of work trying to track down what i needed to rewrite it.

---

