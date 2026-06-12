---
title: "Weird Arch Linux install error..."
date: 2009-11-09
forum: The Cafe
---

### Post by user1397 on 2009-11-09
So I decided to see what all the fuss was about and just play with arch linux for a bit and see if I am competent enough to handle installing it.

I currently have windows 7 and ubuntu 9.10 (main OS), so I made some unallocated space from a chunk of my ubuntu partition using the 9.10 live cd (gparted). I then proceeded with the arch install.

The installation went surprisingly smooth, I easily told it to install the ext4 FS into that unallocated space and by going through most of the defaults everything went smoothly.

In the last step, the one about installing grub and such, I chose to not install it, since I figured I already have grub2 installed from ubuntu 9.10

I then rebooted and logged into ubuntu and proceeded to update the /boot/grub/grub.cfg file as recommended in the ubuntu wiki using the command ```
sudo update-grub
``` which worked quite well; it immediately recognised my arch install and added an entry for it.

- - - - - - - - - - - -

So so far so good; but as soon as I attempted to boot into my arch install for the first time, I received a kernel panic error saying ```
Kernel panic - not syncing VFS: unable to mount on unknown-block(0,0)
```

There it just locks and I am forced into doing a hard reboot.  Any ideas?

---

### Post by HomoGleek on 2009-11-09
> **ubuntuman001 said:**
> So I decided to see what all the fuss was about and just play with arch linux for a bit and see if I am competent enough to handle installing it.

I currently have windows 7 and ubuntu 9.10 (main OS), so I made some unallocated space from a chunk of my ubuntu partition using the 9.10 live cd (gparted). I then proceeded with the arch install.

The installation went surprisingly smooth, I easily told it to install the ext4 FS into that unallocated space and by going through most of the defaults everything went smoothly.

In the last step, the one about installing grub and such, I chose to not install it, since I figured I already have grub2 installed from ubuntu 9.10

I then rebooted and logged into ubuntu and proceeded to update the /boot/grub/grub.cfg file as recommended in the ubuntu wiki using the command ```
sudo update-grub
``` which worked quite well; it immediately recognised my arch install and added an entry for it.

- - - - - - - - - - - -

So so far so good; but as soon as I attempted to boot into my arch install for the first time, I received a kernel panic error saying ```
Kernel panic - not syncing VFS: unable to mount on unknown-block(0,0)
```

There it just locks and I am forced into doing a hard reboot.  Any ideas?
Don't want too sound like an *****, but [http://bbs.archlinux.org/](http://bbs.archlinux.org/) may be more help?

---

### Post by user1397 on 2009-11-09
> **DarrenTod said:**
> Don't want too sound like an *****, but [http://bbs.archlinux.org/](http://bbs.archlinux.org/) may be more help?hehe, it's cool I kinda expected someone to post that, but in truth I am not dying to know how to solve this problem as it is not really a problem...I am merely tinkering with it.  It is not nor will it be my main OS, at least for the foreseeable future.

So yea I'd rather ask here partly because I don't see why not, and partly because I'm too lazy to become part of another forum :P

---

### Post by gn2 on 2009-11-09
> **ubuntuman001 said:**
> I'm too lazy to become part of another forum 


If you're that lazy, Arch probably isn't the distro for you.

---

### Post by ~sHyLoCk~ on 2009-11-09
> **gn2 said:**
> if you're that lazy, arch probably isn't the distro for you.

+1

---

### Post by Xbehave on 2009-11-09
Looks like you need to update your initramfs, i'd guess VFS means virtual filesystem so the initramfs is either corrupted or failing to setup a virtual filesystem that consists of a raid/lvm partition.

---

### Post by pwnst*r on 2009-11-09
> **gn2 said:**
> If you're that lazy, Arch probably isn't the distro for you.

ding ding.

---

### Post by Dharmachakra on 2009-11-09
Another thing you might wanna do is check to see if the entry Grub made actually makes sense. I've come across similar errors due to menu.lst entries that were wacko. I'd go with Xbehave's suggestion first though.

Also, you can search the Arch forums without joining the board. There isn't even a captcha or anything. I'm sure they have something on this.

---

### Post by user1397 on 2009-11-09
> **Xbehave said:**
> Looks like you need to update your initramfs, i'd guess VFS means virtual filesystem so the initramfs is either corrupted or failing to setup a virtual filesystem that consists of a raid/lvm partition.
hmm, I don't have any raid/lvm partitions.  how would I go about updating my initramfs?

and to all those other replies...c'mon guys, I mean I actually attempted installing arch for fun...that can't mean I'm lazy!? :lolflag:

---

### Post by user1397 on 2009-11-09
> **Dharmachakra said:**
> Another thing you might wanna do is check to see if the entry Grub made actually makes sense. I've come across similar errors due to menu.lst entries that were wacko.

Also, you can search the Arch forums without joining the board. There isn't even a captcha or anything. I'm sure they have something on this.
Yea I was beginning to think this might be the problem.  I noticed how the grub2 menu entry for arch displayed a different location for the arch partition than the one in the arch /boot/grub/menu.lst file itself (one pointd to /dev/sda3 while the other to /dev/sda4), which I was able to read by mounting it in ubuntu.

But, even after changing one to the correct one (as in fact it is in /dev/sda4) I tried again and still no go.

And yup, I'm looking in the arch forums as we speak :)

---

### Post by dragos240 on 2009-11-09
Could you post the output of:

```

cat /boot/grub/menu.lst

```

---

### Post by ~sHyLoCk~ on 2009-11-09
> **dragos240 said:**
> Could you post the output of:

```

cat /boot/grub/menu.lst

```

I think he is using grub2 so it's /boot/grub/grub.cfg

Well I let my Arch grub deal with ubuntu since it's more customizable. I feel at ease with it. Customizing the themes,icons etc are really easy through arch. So see if [this]("http://pdg86.wordpress.com/2009/11/08/triple-booting-archubuntu-and-windows/") helps.

---

### Post by dragos240 on 2009-11-09
> **~sHyLoCk~ said:**
> I think he is using grub2 so it's /boot/grub/grub.cfg

true. Most people use grub 0.97.

---

### Post by user1397 on 2009-11-09
> **dragos240 said:**
> true. Most people use grub 0.97.```
xxx@xxx:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 01d29d3f-aae5-4cab-921d-2e7853cf6efd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 01d29d3f-aae5-4cab-921d-2e7853cf6efd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=01d29d3f-aae5-4cab-921d-2e7853cf6efd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 01d29d3f-aae5-4cab-921d-2e7853cf6efd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=01d29d3f-aae5-4cab-921d-2e7853cf6efd ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0f0e16bb122ffd46
    chainloader +1
}
menuentry "Arch (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set a498c36a-19d6-424b-b185-3174eef4e3e5
    linux /boot/vmlinuz26 root=/dev/sda4
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```And yes most people have grub 0.97 but I just did a clean install of ubuntu 9.10 which installs grub2 by default.

---

### Post by dragos240 on 2009-11-09
> **ubuntuman001 said:**
> ```
xxx@xxx:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 01d29d3f-aae5-4cab-921d-2e7853cf6efd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 01d29d3f-aae5-4cab-921d-2e7853cf6efd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=01d29d3f-aae5-4cab-921d-2e7853cf6efd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 01d29d3f-aae5-4cab-921d-2e7853cf6efd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=01d29d3f-aae5-4cab-921d-2e7853cf6efd ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0f0e16bb122ffd46
    chainloader +1
}
menuentry "Arch (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set a498c36a-19d6-424b-b185-3174eef4e3e5
    linux /boot/vmlinuz26 root=/dev/sda4
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```And yes most people have grub 0.97 but I just did a clean install of ubuntu 9.10 which installs grub2 by default.


There's no initrd, that'll do it.

---

### Post by dragos240 on 2009-11-09
Add this after that last line in the arch section.

    initrd    /boot/kernel26.img

---

### Post by chris200x9 on 2009-11-09
> **gn2 said:**
> If you're that lazy, Arch probably isn't the distro for you.

maybe he can't become a member? For the life of me I can't...that board is screwed up in my expierence.

---

### Post by Skripka on 2009-11-09
> **dragos240 said:**
> There's no initrd, that'll do it.

In the words of teh Great Philosopher:

[QUOTE=]
THERE'S yer problem!!
[/QUOTE]

---

### Post by user1397 on 2009-11-09
> **dragos240 said:**
> Add this after that last line in the arch section.

    initrd    /boot/kernel26.img
Thanks, that did it.  It finally works now.

---

