---
title: "Grub2 Neat Trick required"
date: 2010-07-08
forum: Server Platforms
---

### Post by Corrupter on 2010-07-08
Hey guys, i was looking through the grub2 basic guide and doing some searching on interwebs for ways to solve a simple problem that has complex fixes and heres where i am at.

The simple problem (not so much a problem as it is just a preference):

Users who run server and add ubuntu-desktop but dont want it to run at boot up.

The solutions:
So far i've stumbled across a couple of different solutions not all of which were easy to understand, get right or work on all the latest ubuntu distros.  (i wont go into specifics but will summarize)

make a simple script to /etc/init.d/gdm stop  and add it to the start up list * this ISNT a good idea although works.

edit the upstart jobs list to remove gdm from the list (or whatever your desktop is) * better then the first idea but not as easy.

an easier way would be to edit /etc/default/grub and in the line GRUB_CMDLINE_LINUX_DEFAULT="quiet"  simply change to GRUB_CMDLINE_LINUX_DEFAULT="quiet text"  *this only works with grub1.94 or better  however this will change all your linux.kernel* options to load directly to a CLI and some of us might want to be able to boot straight to a GDM login from the grub menu OR CLI if we so choose.

you can also add to /etc/grub.d/40_custom a copy of whats in your /boot/grub/grub.cfg ####10_linux section and change the options on them individually so that each one is a text option, leaving the other options that appear above them to be GUI boot options.  * this works well HOWEVER any time your kernel receives an update this means that whatever kernel version was last input into your 40_custom file will be the one that is loaded to your CLI enviroment which is and isnt good depending on what you are doing.

the neat trick which is required to be the best (but maybe not the easiest) solution would be to somehow make it so any new additions to the /boot/grub/grub.cfg file ###10_linux section automatically update your 40_custom file with the most up to date kernel.

Anyone have any thoughts on how to do this or a guide that will teach me what i need to know to achieve this?  

BTW i did do some searching but i dont know exactly what i am searching for.  The bottom line is that i want to have the grub menu show 1 option for the latest kernel with gui, 1 with CLI and 1 for recovery that auto updates to the latest kernel options.  I've already managed to remove the memtest86+ menu option.

The ideal menu for me is below:
Ubuntu 10.04, with Linux 2.6.32-23-generic-pae (CLI)
Ubuntu 10.04, with Linux 2.6.32-23-generic-pae (GUI)
Ubuntu 10.04, with Linux 2.6.32-23-generic-pae (Recovery)

---

### Post by oldfred on 2010-07-08
Ranchhand posted this:

Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

or

menuentry "Latest Kernel" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5a880a39-36a1-46f5-b106-e979608f295a
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}
Just take your existing entry and remove the specific info from the end of the "vmlinuz" and "initrd" entries. And remove /boot to use link to newest kernel.

---

### Post by Corrupter on 2010-07-08
gonna do some testing with that and see how we go.  Thanks a ton for the speedy reply with an accurate answer.

Thanks for contributing to the community!

---

### Post by arrrghhh on 2010-07-08
Wouldn't it be easier to just install ubuntu-desktop and make sure that gdm doesn't run at startup?  I don't get why people do the server install just to install the entire ubuntu-desktop package on top.  Seems silly to me.

---

### Post by Corrupter on 2010-07-08
because there are SOME things that a server are used for that require ubuntu-desktop for.  I'm also using it as a test box on my lan for certain compatibility and program availability / testing platforms.  

Your statement is like saying:
wouldnt it be easier to just not try?  I never understand why anyone wants to experiment and learn from experience as a pose to simply following what everyone else "thinks" they should do.

---

### Post by Corrupter on 2010-07-08
so what my 40_custom file looks like is

menuentry 'Ubuntu 10.4, with Linux Latest Kernel (CLI)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set 37c5c625-41c3-4a56-b33e-af53e09ba32d
        linux   /vmlinuz root=/dev/sda1 ro   quiet text
        initrd  /initrd.img
}
menuentry 'Ubuntu 10.4, with Linux Latest Kernel (GUI)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set 37c5c625-41c3-4a56-b33e-af53e09ba32d
        linux   /vmlinuz root=/dev/sda1 ro   quiet
        initrd  /initrd.img
}
menuentry 'Ubuntu 10.4, with Linux Latest Kernel (Recovery)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set 37c5c625-41c3-4a56-b33e-af53e09ba32d
        echo    'Loading Linux latest kernel recovery mode'
        linux   /vmlinuz root=/dev/sda1 ro  single
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img
}

which is mimic'd from what my 10_linux section looked like in grub.cfg.

But i get the following problems when attempting to boot.
no init found try passing init= bootarg.

busybox v1.13.3 etc etc etc

(initramfs) prompt

so i read somewhere to give init=3 a go and i added that after quiet text and got

mount: mounting /dev on /root/dev failed: no such file or directory
same for /sys on /root/dev
same for /proc on /root/proc
target filesystem doesn't have 3
no init found try passing init= bootarg.

busybox v1.13.3 etc etc etc

(initramfs) prompt

and occasionaly if i tweak with the options and trim it down based on the 2 options you gave me i get
[    0.557168] Kernel panic - not syncing: VFS: Unable to mount root fs on Unknown-block(0,0)

im doing some research on this and am coming up empty handed on how my menu item is not configured correctly, anyone see a blatant problem my unexperienced eyes dont see?

---

### Post by arrrghhh on 2010-07-08
> **Corrupter said:**
> Your statement is like saying:
wouldnt it be easier to just not try?  I never understand why anyone wants to experiment and learn from experience as a pose to simply following what everyone else "thinks" they should do.

I'm not saying that at all.  If you want ubuntu-desktop, then install it.  ALL of the server-based apps will run.

Just doesn't make sense at all.  If you want a stripped down server and don't need a GUI, install ubuntu-server.  If for whatever reason you need a GUI, install ubuntu-desktop.  Like I said, it'll still run all the same services sessionless.

Why try to fit a square peg into a round hole?  I don't know... I hope you enjoy your exercise in futility :D

---

### Post by spynappels on 2010-07-08
> **arrrghhh said:**
> I'm not saying that at all.  If you want ubuntu-desktop, then install it.  ALL of the server-based apps will run.

Just doesn't make sense at all.  If you want a stripped down server and don't need a GUI, install ubuntu-server.  If for whatever reason you need a GUI, install ubuntu-desktop.  Like I said, it'll still run all the same services sessionless.

Why try to fit a square peg into a round hole?  I don't know... I hope you enjoy your exercise in futility :D

 The server kernel has some differences which I can't remember exactly, but which are optimised for server operation, and if the window manager is installed on the server edition, if it is no longer required at a later date, it can be removed quite easily, leaving a server optimised install. Not everybody knows exactly what they want a testbed server to accomplish, so experimenting with both is not futile IMHO.

---

### Post by oldfred on 2010-07-08
You say set root hd1,1 which is sdb1 but then in vmlinuz say sda1. They have to match unless you have a /boot in sdb1 which then is the set root and the install is in sda1.

---

### Post by arrrghhh on 2010-07-09
> **spynappels said:**
> The server kernel has some differences which I can't remember exactly, but which are optimised for server operation, and if the window manager is installed on the server edition, if it is no longer required at a later date, it can be removed quite easily, leaving a server optimised install. Not everybody knows exactly what they want a testbed server to accomplish, so experimenting with both is not futile IMHO.

Fair enough.  I'd be interested to know the differences.  Also, I thought that only applied to 64-bit (the optimized server kernel vs. the kernel you get with the -desktop version of Ubuntu)

---

### Post by Corrupter on 2010-07-09
Oldfred, 

Again i thank you for contributing to the community and the continued growth of ubuntu users.  Always a pleasure to get someone to help who knows what they are doing.

I did change sda1 to sdb1 and it worked.  When i copied the syntax from your examples and crossed them with my system specific information as found in my grub.cfg 10_linux section for some reason or another i overlooked that entirely.  Works like a charm now.

This is exactly what i was looking for.  A simple menu edited way of loading either the GUI the CLI or recovery mode and it works flawlessly...  I hope this thread helps the countless others interested in doing the same thing.

---

### Post by fro1269 on 2010-08-14
i know this has been said before in this thread but thanks for contributing.  The other guides ive seen on how to edit grub2 dont quite go into as much detail as you do.

---

