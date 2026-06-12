---
title: "Customize your Grub2 screen"
date: 2012-12-15
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2012-12-15
If any one is interested, I customized my Raring Grub2 with the green wiki link in my signature.
Here is what it looks like and it would not be so cluttered if there weren't 8 systems on my box.

[[IMG]http://ompldr.org/tZ3BpcQ[/IMG]]("http://ompldr.org/vZ3BpcQ")

This is with **color_normal=white/black**
and **color_highlight=yellow/black**.

It involves using CLI to modify 2-3 files and copying a picture to /boot/grub/
It gives you a background of your choice, colored highlight and normal fonts as well as a menu that 
never needs changed even when new kernels are installed
The only time you would need to change it is when you delete an OS or add one.

Background pictures can be swapped out easily. The color of that picture may require changing the font colors.

Here is a link to the thread:
[[COLOR=blue]_How to have a custom Grub2 menu that is maintenance free_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2076205")


Here is what my Raring Ringtail 13.04 screen with Gnome Classic looks like:

[[IMG]http://ompldr.org/tZ3BqZw[/IMG]]("http://ompldr.org/vZ3BqZw")

---

### Post by Cavsfan on 2012-12-16
I changed the Grub2 background and font colors.
The color black/black can be used if there is a background image in **/boot/grub/**.
Without an image, black/black will result in transparency, in other words it will be invisible.

These colors are by no means optimum but, prove that black can be used with an image.
Black would be more suitable on a very light picture.

[[IMG]http://ompldr.org/tZ3B6eA[/IMG]]("http://ompldr.org/vZ3B6eA")

---

### Post by Cavsfan on 2012-12-17
OK, last one for a while promise! :) I think I got these colors right to match the background.

[[IMG]http://ompldr.org/tZ3FkdA[/IMG]]("http://ompldr.org/vZ3FkdA")

It uses as font colors **color_normal=cyan/black**
and **color_highlight=light-cyan/black**

---

### Post by ventrical on 2012-12-18
Very nice work Cavsfan.

regards...

---

### Post by Cavsfan on 2012-12-18
> **ventrical said:**
> Very nice work Cavsfan.

regards...

Thank you! Actually **Ranch Hand **and **Drs305** rubbed a lot of their knowledge off on me.

**Ranch Hand** and I were messaging each other and he told me how to do this. It took me quite a while before I worked up the courage to actually do it.

I dual boot windows 7 and Ubuntu and I kept complaining that every time a new kernel got installed, I had to change the default line in **/etc/default/grub**.
I wanted it to default to Windows 7 for my wife in case the system rebooted.

**Ranch Hand** told me how to do this. After quite a while went by and I understood it better I asked him if he minded if I made a How To out of it so others could benefit if they wanted the same thing: a constant default entry.
He thought it was a good idea and the rest is history.

Oh and **Bogan** helped too. He pointed out an error I had made which I corrected. He also helped with the recovery option on Grub 2.00.
We both discovered that without the custom grub, selecting the recovery on Grub 2.00 (Quantal and Raring) and selecting **Run in failsafe Graphics Mode** did not work.
So, **Bogan** figured out a way for my custom method to drop to a root shell prompt.

I am just glad to help as many here in this forum are. :)

---

### Post by mlentink on 2012-12-20
Nice work.

Did you know about [this thread]("http://ubuntuforums.org/showthread.php?t=1823915&highlight=grub+theme")?

---

### Post by grahammechanical on 2012-12-20
Nice work! It is how we learn. Can I put you on to another experiment? I stick with the standard Grub 2 menu with just a background image of my choice. I like the new feature of Grub 2.0 of submenus (called Advance Options ...).

Can I tempt you to experiment in getting submenus into your Grub 40_custom file? :)

Regards.

---

### Post by Cavsfan on 2012-12-20
> **grahammechanical said:**
> Nice work! It is how we learn. Can I put you on to another experiment? I stick with the standard Grub 2 menu with just a background image of my choice. I like the new feature of Grub 2.0 of submenus (called Advance Options ...).

Can I tempt you to experiment in getting submenus into your Grub 40_custom file? :)

Regards.
Thanks! 
I like to keep things as simple as I can. This method will always load the latest installed kernel in whatever Linux OS is on the menu.
[COLOR="Red"]The single most important reason I created this is so I would have a consistant menu with a consistant default OS even when a new kernel was added.
[/COLOR]
I want the default to be Windows 7 (which is always at the bottom) just in case the system reboots and someone else is using it. Windows 7 is currently the 15th menuentry on my machine.

BTW this is a new command **drs305** gave to me: (however it will not span submenus)
```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
``````
     0    menuentry "Lycid Lynx 10.04" {
     1    menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
     2    menuentry "Lycid Lynx Generic 10.04" {
     3    menuentry "Lycid Lynx Generic 10.04 (Recovery Mode)" {
     4    menuentry "Precise Pangolin 12.04" {
     5    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     6    menuentry "Precise Pangolin Generic 12.04" {
     7    menuentry "Precise Pangolin Generic 12.04 (Recovery Mode)" {
     8    menuentry "Quantal Quetzal 12.10" {
     9    menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    10    menuentry "Quantal Quetzal Generic 12.10" {
    11    menuentry "Quantal Quetzal Generic 12.10 (Recovery Mode)" {
    12    menuentry "Raring Ringtail 13.04" {
    13    menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
    14    menuentry "Windows 7" {

```

The Community Wiki states to ***_not_*** save the changes in **40_custom** but, instead put the changes in **04_custom** and save that as **06_custom**. This leaves **40_custom** untouched.

Doing so makes the custom menu appear first even if you have all of the normal entries memtest, etc.

My intent was to have a single normal boot entry, a recovery boot entry along with a windows 7 boot entry.

If you want access to the submenus and older kernels, you could just leave **/etc/grub.d/10_linux** and **/etc/grub.d/30_os-prober** executable.

But, if your default menu entry is the top line making a **06_custom** file is moot.
You said you already have dropped a picture in **/boot/grub/** so you could just change the font and the menu colors and leave everything else as is.
That way you will still have your submenus.
If I have to access another older kernel, which I have yet to do, I would login to that Ubuntu, install grub there and make **/etc/grub.d/10_linux** and **/etc/grub.d/30_os-prober** executable.
But, I cannot come up with a reason why the Wiki should touch the submenus at this time.

---

### Post by grahammechanical on 2012-12-20
> You said you already have dropped a picture in /boot/grub/ so you could just change the font and the menu colors and leave everything else as is.

Yes, I have done that. I do not have a Windows OS. So, I do not have the same need as you. I choose one of my installed Ubuntus as the default install and if a new Ubuntu install over-writes Grub, I simply boot into my default Ubuntu and run

```
sudo grub-install /dev/sda
```

and my default install is back in charge. I have done just a little study of Grub and I appreciate the work that you have done. 

Regards.

---

### Post by Cavsfan on 2012-12-21
> **grahammechanical said:**
> Yes, I have done that. I do not have a Windows OS. So, I do not have the same need as you. I choose one of my installed Ubuntus as the default install and if a new Ubuntu install over-writes Grub, I simply boot into my default Ubuntu and run

```
sudo grub-install /dev/sda
```and my default install is back in charge. I have done just a little study of Grub and I appreciate the work that you have done. 

Regards.

Thank you!
That is exactly what I do too. You must be aware also that a new Ubuntu install pulls in all of the swapfiles into **/etc/fstab** and needs editing.
As well as a re-install as it will not only leave multiple swapfiles but, ext4 entries as well. It will retain where the ext4 was as well as where it is now installed.

So, even though you don't use windows, if you choose a default Ubuntu other than the 1st one you could still benefit from a **/etc/grub.d/06_custom** file.  
How often do you use memtest or an older kernel than the most recent one?
I think it is nice that they came up with sub menus but, I never need an older kernel and if I did I could just change it so I could see them.
Here is mine in Raring (Grub 2.00) with my custom installs in it. I have one Lucid with a custom Grub and a Lucid with a generic Grub, etc.
That is why I labelled them like that. But, what you put between the quotes after the menuentry is totally up to you as you will be the only one to see it.
```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10, Raring Ringtail 13.04 and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Lycid Lynx 10.04" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
menuentry "Lycid Lynx Generic 10.04" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx Generic 10.04 (Recovery Mode)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Precise Pangolin Generic 12.04" {
    set root=(hd0,11)
        linux /vmlinuz root=/dev/sda11 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin Generic 12.04 (Recovery Mode)" {
    set root=(hd0,11)
        linux /vmlinuz root=/dev/sda11 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal Generic 12.10" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal Generic 12.10 (Recovery Mode)" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Raring Ringtail 13.04" {
    set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 ro quiet splash
        initrd /initrd.img
}
menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
    set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
```Since mine is so long, I like the fact I can copy them across partitions to save time. :)

---

### Post by Cavsfan on 2013-01-10
Simplified it a little bit but, I still like the background. I'm going to leave that for a while.
This is the Grub on Raring too.

[[COLOR=blue]_http://ubuntuforums.org/showpost.php?p=12445554&postcount=69_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=12445554&postcount=69")

---

### Post by Cavsfan on 2013-03-13
With today's update of grub-pc in Raring, I accepted the installer's version (which one should always do to get the full benefit of the update) of **/etc/default/grub** and **/etc/grub.d/05_debian_theme** and then modified them again.
In **05_debian_theme** the font colors moved from after line [COLOR=#ff0000]108[/COLOR] to after line [COLOR=#ff0000]114[/COLOR].

If you ever encounter an error while either the system is updating grub or you enter **sudo update-grub** you should make the **06_custom** file unexecutable and then make **10_linux** and **30_os-prober** executable.
[B]sudo chmod -x /etc/grub.d/06_custom
sudo chmod +x /etc/grub.d/10_linux
sudo chmod +x /etc/grub.d/30_os-prober
[/B]
Always remember to enter **sudo update-grub** or the changes will not take effect. You do not want to re-boot with an error coming from grub. If you do you will probably be looking at grub recovery.
Then make the changes to the updated files.
Since Raring is still pre-release I will not update the community wiki until it is released in April.

---

### Post by Cavsfan on 2013-04-09
Today's Grub update to **2.00-13ubuntu3** involved **/etc/grub.d/05_debian_theme** which I selected "Y" to "install the package maintainer's version" to obtain the benefits of the update.

Then I edited the file and inserted my font colors below line 114. You can do a search for 
```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
```
which is on line 114 and re-insert the font colors after that line:
```
        echo " set color_normal=cyan/black"
        echo " set color_highlight=light-cyan/black"
```

---

