---
title: "Grub Legacy vs Grub2"
date: 2011-10-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-14
Where do you stand? I don't use many distros, but as far as I know only Ubuntu and derivatives use Grub2?

Grub2 focus seems to be on non-essential features. If you look at their development, you see plans for embedded video player (!?), OpenGL animations, animated images, sound, etc.

Grub Legacy seems to be talking about enhancing code speed, portability, develop support for wireless keyboards, better pata/sata drivers, etc.

---

### Post by ronacc on 2011-10-14
I much prefer gurb I don't give a flip about fancy graphics etc during boot and it was much easier ( and lasting ) to "adjust" menu.list as opposed to grub.cfg , I run a multi boot multi distro multi version test box and grub.cfg is a pain in the sit upon .

---

### Post by Blasphemist on 2011-10-14
I use Fedora, openSUSE, Bodhi and LMDE in addition to buntu flavors, all multiboot. Fedora has switched to Grub2 and for me that leaves maybe openSUSE (haven't checked it lately) not on Grub2. Everyone else that I use is grub2 and that is what I'll focus on. Neither one is really designed for multi boot vs dual boot. The buntu distros at least run grub-update when upgrading the kernel and take care of the symlinks.

---

### Post by arpanaut on 2011-10-14
> Grub Legacy seems to be talking about enhancing code speed, portability,  develop support for wireless keyboards, better pata/sata drivers, etc.

The problem I see in trying to use GRUB Legacy long term is:

**GRUB Legacy is not actively developed any longer. Only bugfixes will be made so that GRUB Legacy can stil be used for older systems.**

From: [http://www.gnu.org/software/grub/grub-legacy.en.html](http://www.gnu.org/software/grub/grub-legacy.en.html)

While still a viable option for now, not a permanent or long term solution.
There will not be any new features or enhancements.

---

### Post by ranch hand on 2011-10-14
Debian uses grub-pc (grub2).

As a long time lover of grub I prefer grub-pc.

The script based system is more flexible and capable of dealing with the fast changes in file systems and bootable media.

It does take some getting used to and would work better for folks if they would use the built in abilities to customize grub-pc to their box once it is installed.  Most of the scripts used to create your first grub.cfg are totally un-needed after that.

They are needed at first to make sure that all computers will be served functional and all OS' will be detected.  Very few, if any computers need all of that.  You can easily speed up your menu loading and the time it takes update-grub to run by simply disabling the scripts that are not needed.

The use of custom menus will speed things up greatly but few folks use them.  This is why there is a 40_custom script in there in the first place.  Yes I know, there he goes again.  I do use, and have used since the introduction of this grub-pc in 9.10 testing.

Grub-pc gives me a menu that I never have to mess with at all.  If I change a Debian based install to some other Debian based install, keeping the grub I normally use on the MBR, I don't even need to change the menu for the new install.  I would have to if I changed to a RH branch OS on a previously Debian branch OS partition.

---

### Post by Quackers on 2011-10-14
I had a very limited use of grub legacy and whilst I appreciate that menu.lst could just be edited I definitely agree with ranch hand.
What can be easier than running update-grub? It does everything for you, as I see it. It finds all known OSes, it seems, you can boot isofiles direct from the grub menu by making use of the /etc/grub.d/40_custom file (together with any custom menu entries you prefer).
I think grub2 is great :-)

---

### Post by sgage on 2011-10-14
> **effenberg0x0 said:**
> Where do you stand? I don't use many distros, but as far as I know only Ubuntu and derivatives use Grub2?

Grub2 focus seems to be on non-essential features. If you look at their development, you see plans for embedded video player (!?), OpenGL animations, animated images, sound, etc.

Grub Legacy seems to be talking about enhancing code speed, portability, develop support for wireless keyboards, better pata/sata drivers, etc.

It seems like the just-released Fedora 16 Beta is the first rpm-based distro to move to grub2.

---

### Post by effenberg0x0 on 2011-10-14
> **sgage said:**
> It seems like the just-released Fedora 16 Beta is the first rpm-based distro to move to grub2.

I didnt know that, I was under a wrong impression that (n)Ubuntu and Ubuntu-based were grub2 while mostly all others (relevant ones) were all still grub. From the info you guys gave me above, specially the fact that, as it seems, grub-legacy development is stopped, grub2 is the only viable option now.

I'm not gonna ask you about lilo :)

Thanks guys

Effenberg

---

### Post by ranch hand on 2011-10-14
Yup, stuff keeps changing.  Grub-pc has been in development by the grub folks for some time because grub was just getting to be made of patches.

I have never used lilo but know people that do.  Have read up on it.  Sounds like it is still the answer to some very rare but serious problems.  Not mentioning its ability to boot MS which I have no desire to do.  Versatile boot loader.

---

### Post by effenberg0x0 on 2011-10-14
There was a very popular local distro here, which was bought by Mandrake Linux and later disappeared. This is like 1999, 2000. It had lilo. People used to freak out with it. It was far from easy and reliable (at least back then).

---

### Post by malspa on 2011-10-15
Still using Mepis here to boot all my other distros, and Mepis still has grub-legacy. I figure I'll have to learn to multi-boot with grub2 eventually, but for now I'm sticking with the "tried and true."

---

### Post by ranch hand on 2011-10-15
> **effenberg0x0 said:**
> There was a very popular local distro here, which was bought by Mandrake Linux and later disappeared. This is like 1999, 2000. It had lilo. People used to freak out with it. It was far from easy and reliable (at least back then).
Really, I thought Conectiva bought Mandrake when they were broke due to the copyright fight with the cartoon, created Mandriva that way.

Not that I was paying a lot of attention to it at the time.  Just got that stuck in my head.

---

### Post by effenberg0x0 on 2011-10-17
I thought no one ever heard of Conectiva outside Brazil lol... Well, the story here is that Mandrake bought them in 98 along with many regional distros in other countries and broke all of them with the whole mandriva thing a while later. Conectiva was hell. Lots of people and companies used it here back in 98-2000. Looking online I found screenshots of the WindowMaker desktop. Don't miss it at all.

---

### Post by cariboo on 2011-10-17
I used LILO and wmaker when I first started using Debian back in 2002-2003, I never really liked LILO, and was very happy the first time I installed Ubuntu, and didn't have to deal with it. Windowmaker was great at the time, it's just unfortunate it was never developed any further.

---

### Post by effenberg0x0 on 2011-10-17
Cariboo => Look here : [http://repo.or.cz/w/wmaker-crm.git](http://repo.or.cz/w/wmaker-crm.git) 
Some guys are still pushing a fork of it.

---

### Post by cariboo on 2011-10-17
> **effenberg0x0 said:**
> Cariboo => Look here : [http://repo.or.cz/w/wmaker-crm.git](http://repo.or.cz/w/wmaker-crm.git) 
Some guys are still pushing a fork of it.

Thanks for that, I'll have to wait and see what comes out of this new development. :)

---

### Post by manzdagratiano on 2011-10-18
I love grub2... os-prober is so much more awesome compared to editing menu.lst!

If only I could get rid of my grub2 bug of having multiple entries for the same distro (with a single kernel installed!):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/758887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/758887)

---

### Post by Quackers on 2011-10-18
manzdagratiano, what does your /etc/grub.d folder contain?

---

### Post by seenthelite on 2011-10-18
Sabayon uses grub-pc (grub2)and Gentoo also.

---

### Post by jerrylamos on 2011-10-18
Grub 2 busted big time on fresh install of Oneiric Ocelot release image.  For whatever reason Install Ubiquity got an error configuring Apt.  By that time install was well under way, I found out later the image would boot though incomplete.

This was on a multi-boot.  After the "Apt error" it would only boot to 
Grub rescue>
at which point only a few of the Grub rescue connands would work, example the command "linux" would not leaving me stranded.

Eventually located Ubuntu Wiki Community Support on Grub 2 and followed the commands to use a bootable CD - I used Lucid Lynx 10.04.3.  Successfully able to install grub 2 with the directions there.

Install should certainly put in a usable Grub2 with full rescue commands just as soon as it formats the target partition.

Yes there is a launchpad bug #.

No I don't expect any developer action.

Jerry

---

### Post by ronacc on 2011-10-18
jerry do what I do , if you have multi-boot and more than one drive have a different install write its grub to the other drive and that way you can switch boot order in bios to get to a working install.

edit: also super grub disk can come in handy incase of a grub failure .

---

### Post by thatguruguy on 2011-10-18
> **jerrylamos said:**
> Grub 2 busted big time on fresh install of Oneiric Ocelot release image.  For whatever reason Install Ubiquity got an error configuring Apt.  By that time install was well under way, I found out later the image would boot though incomplete.

This was on a multi-boot.  After the "Apt error" it would only boot to 
Grub rescue>
at which point only a few of the Grub rescue connands would work, example the command "linux" would not leaving me stranded.

Eventually located Ubuntu Wiki Community Support on Grub 2 and followed the commands to use a bootable CD - I used Lucid Lynx 10.04.3.  Successfully able to install grub 2 with the directions there.

Install should certainly put in a usable Grub2 with full rescue commands just as soon as it formats the target partition.

Yes there is a launchpad bug #.

No I don't expect any developer action.

Jerry

I'm not sure that your experience was universal.

---

### Post by sanderd17 on 2011-10-18
Arch normally uses all the most recent, but stable packages. But yet, the default bootloader in Arch is still Grub legacy.

Also note that the version number of Grub2 is still 1.99

[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
[https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

---

### Post by BwackNinja on 2011-10-18
> **sanderd17 said:**
> Arch normally uses all the most recent, but stable packages. But yet, the default bootloader in Arch is still Grub legacy.

Also note that the version number of Grub2 is still 1.99

[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
[https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

And the version number for Grub Legacy is 0.97 (last updated upstream in January 2010), with 7 patches vs 1 for Grub2 in their respective PKGBUILDs.

---

### Post by manzdagratiano on 2011-10-23
> **Quackers said:**
> manzdagratiano, what does your /etc/grub.d folder contain?

Erm... apologies for the  late reply... Here's what's in my /etc/grub.d:

```

manjul@chaar:~$ ls /etc/grub.d/
00_header        10_linux      20_memtest86+  40_custom  README
05_debian_theme  20_linux_xen  30_os-prober   41_custom

```and the custom files are unmodified:
```

manjul@chaar:~$ cat /etc/grub.d/41_custom 
#!/bin/sh
cat <<EOF
if [ -f  \$prefix/custom.cfg ]; then
  source \$prefix/custom.cfg;
fi
EOF

manjul@chaar:~$ cat /etc/grub.d/40_custom 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```Also, as the attachments of that Bug-report

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/758887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/758887)

indicate, the respective multiple entries are not artifacts of leftover kernels... in fact, I am very very religious about removing old kernels after every upgrade. For example, here's my grub.cfg:

```

manjul@chaar:~$ cat /boot/grub/grub.cfg 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 9904cf51-bb50-4343-a112-dbc2056bac3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 089f196f-2f3c-4615-aff4-8babd1e6a29f
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 9904cf51-bb50-4343-a112-dbc2056bac3c
insmod tga
background_image -m stretch /usr/share/images/grub/Windbuchencom.tga
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 9904cf51-bb50-4343-a112-dbc2056bac3c
insmod tga
if background_image /usr/share/images/grub/Windbuchencom.tga; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 089f196f-2f3c-4615-aff4-8babd1e6a29f
    linux    /vmlinuz-3.0.0-12-generic root=UUID=9904cf51-bb50-4343-a112-dbc2056bac3c ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 089f196f-2f3c-4615-aff4-8babd1e6a29f
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=9904cf51-bb50-4343-a112-dbc2056bac3c ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 089f196f-2f3c-4615-aff4-8babd1e6a29f
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 089f196f-2f3c-4615-aff4-8babd1e6a29f
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch Linux (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 9dc8bfcc-97ed-440f-876f-4fbca4d8079c
    linux /boot/vmlinuz26 root=/dev/sda4
    initrd /boot/kernel26.img
}
menuentry "Arch Linux (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 9dc8bfcc-97ed-440f-876f-4fbca4d8079c
    linux /boot/vmlinuz-linux root=/dev/sda4
    initrd /boot/initramfs-linux.img
}
menuentry "Debian GNU/Linux (wheezy/sid) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 04608121-4401-49e7-9e31-40b22377ba00
    linux /vmlinuz root=/dev/sda7
    initrd /initrd.img
}
menuentry "Debian GNU/Linux (wheezy/sid) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 04608121-4401-49e7-9e31-40b22377ba00
    linux /vmlinuz root=/dev/sda7
    initrd /initrd.img
}
menuentry "Debian GNU/Linux (wheezy/sid) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 04608121-4401-49e7-9e31-40b22377ba00
    linux /boot/vmlinuz-3.0.0-2-amd64 root=/dev/sda7
    initrd /boot/initrd.img-3.0.0-2-amd64
}
menuentry "Debian GNU/Linux (wheezy/sid) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 04608121-4401-49e7-9e31-40b22377ba00
    linux /vmlinuz root=/dev/sda7
    initrd /initrd.img
}
menuentry "Debian GNU/Linux (wheezy/sid) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 04608121-4401-49e7-9e31-40b22377ba00
    linux /vmlinuz root=/dev/sda7
    initrd /initrd.img
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 9badb81d-44aa-452e-b1be-301e459898f9
    linux /boot/vmlinuz root=/dev/sda8
    initrd /boot/initrd.gz
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 9badb81d-44aa-452e-b1be-301e459898f9
    linux /boot/vmlinuz root=/dev/sda8
    initrd /boot/initrd.gz
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 9badb81d-44aa-452e-b1be-301e459898f9
    linux /boot/vmlinuz-generic-2.6.38.7 root=/dev/sda8
}
menuentry "Slackware Linux (Slackware 13.37.0) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 9badb81d-44aa-452e-b1be-301e459898f9
    linux /boot/vmlinuz-huge-2.6.38.7 root=/dev/sda8
}
menuentry "Gentoo Base System release 2.0.3 (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root f78cc2a6-2ff1-4d06-a523-e24039710306
    linux /boot/kernel-2.6.39-gentoo-r3 root=/dev/sda9
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```And to look at Debian in /dev/sda7, here's what's in the /boot folder:

```

manjul@chaar:~$ sudo mount /dev/sda7 /mnt
[sudo] password for manjul: 
manjul@chaar:~$ ls /mnt/boot/
config-3.0.0-2-amd64      System.map-3.0.0-2-amd64
initrd.img-3.0.0-2-amd64  vmlinuz-3.0.0-2-amd64
manjul@chaar:~$ 

```And yet, five entries for Debian in grub!!! I am surprised this hasn't affected anyone else (the bug marks a +1 aside from me, but that seems to be a different issue). Since no one has taken note, I was trying to look into it myself, but I haven't had much time to sit through the code... the output of os-prober by itself is good, but it is linux-boot-prober that is the culprit.

Edit: Oh yeah - and the entries in the root of /dev/sda7 are just symlinks:
```

manjul@chaar:~$ ls -al /mnt/vmlinuz 
lrwxrwxrwx 1 root root 26 2011-10-18 22:22 /mnt/vmlinuz -> boot/vmlinuz-3.0.0-2-amd64
manjul@chaar:~$ ls -al /mnt/initrd.img 
lrwxrwxrwx 1 root root 30 2011-10-18 22:22 /mnt/initrd.img -> /boot/initrd.img-3.0.0-2-amd64

```

However, despite this, I love grub2 - I think os-prober is SO much better than having to edit menu.lst. When I installed Arch on my fianceé's laptop, I had some trouble setting grub up to detect the Winblows (oh how I would love to wipe it off! But she needs it for some proprietary Dental school stuff) - grub2 and problem solved!

---

