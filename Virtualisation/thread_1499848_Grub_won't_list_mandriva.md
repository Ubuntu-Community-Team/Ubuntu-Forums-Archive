---
title: "Grub won't list mandriva"
date: 2010-06-02
forum: Virtualisation
---

### Post by BALD PATCHES on 2010-06-02
I have a multiple boot setup and have just installed Lucid behind Mandriva on an external HD
 
I can boot into all of the other 7 OS's no problem but Mandriva won't list properly
 
I have used the Grub Disc but - NO LUCK
 
I know it's just a simple case of editing a Grub file somewhere but which one and where.
 
Anyway the last Grub bootloader was installed by Lucid so has anyone any ideas[-o<

---

### Post by oldfred on 2010-06-02
If it is a clean install of Lucid its osprober is usually pretty good at finding other systems. Have you run 

sudo update-grub

To see your entire configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Some of the other systems it seems to leave off the init line. We will see what is where with the script.

And welcome to the forums.

---

### Post by BALD PATCHES on 2010-06-07
Thanks - I'll give it a try and see what I get!

---

### Post by BALD PATCHES on 2010-06-10
Here are the results from 'infoscript':
 
I thought it might be easier as a PDF attachment![ATTACH]159951[/ATTACH]
 
 
#-o

---

### Post by oldfred on 2010-06-10
that will teach me to ask for a bootinfoscript. I only have 4 Ubuntus's and XP and I get confused with my system.

Mandrive posts this way:
kernel (hd1,1)/boot/vmlinuz BOOT_IMAGE=linux root=LABEL=MANDRIVA
ae88-4519-8774-345c41958c76 splash=silent vga=788
initrd (hd1,1)/boot/initrd.img

And that is using old grub, but the osprober in Ubuntu copies those command lines but in grub2 the partition number has changed so those entries will not work in grub2. ( should be hd1,2) Also it may not be drive hd1 as grub's drive numbering seems to vary depending on which drive boots. When I set sdc to boot first I have to chainload to sda but call it hd1 ( I assume grub thinks the boot drive is hd0).

You can copy your mandriva entries into 40_custom and remove the (hd1,1) at the beginning of the kernel & intrd lines. You have to reformat to be like grub2. change root to set root = and add the {} like all the other entries.

I had to simplify my grub.cfg. I had a grub only partition for booting older installs that still used old grub where I could install grub to the partition without grub2's complaints. 

I am not sure why you do not have sdb but have sdc. You may want to check. /boot/grub/device.map That may change drives from hd0, hd1, hd2 so if you do change device.map you may have to reinstall grub.
sudo grub-install /dev/sda
sudo grub-install --recheck /dev/sda
sudo update-grub

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows and other systems entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php...54&postcount=1](http://ubuntuforums.org/showpost.php...54&postcount=1)

I added this :
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

after all changes:
sudo update-grub


I also would install Ubuntu's grub to sdb and set it first in BIOS to boot. Then you can have a different boot loader in sda and chainload and/or use BIOS or Fkey to boot it.

A lot to digest. I sure you will have more questions. As I am not 100% sure of everything.

---

### Post by BALD PATCHES on 2010-06-14
[LEFT][SIZE=2]**For OLD FRED**[/SIZE]...
 

I got the correct address from GParted as OS-Prober produced something totally confusing - there is no device.map file and my second drive changed to sdb after the first edit??? - I took out the “hd’s” - and just as I was getting ready to give up and shut down for the night Mandriva booted.
 
 

[SIZE=2]**After numerous re-edits this is what finally worked so many thanks Old Fred:**[/SIZE]

 [/LEFT]
[FONT=Liberation Serif][COLOR=#dd1d1d][LEFT]menuentry "Mandriva 2010 (on /dev/sdb2)" {
insmod ext4
set root=
search --no-floppy --fs-uuid --set 9b8a9870-e1e0-4408-b694-465a3464744a
linux /boot/vmlinuz BOOT_IMAGE=linux root=LABEL=MANDRIVA root=UUID=9b8a9870-e1e0-4408-b694-465a3464744a splash=silent vga=788
initrd /boot/initrd.img
}
 

[SIZE=2][COLOR=black]**Where as what os-prober produces is:**[/COLOR][/SIZE]
[COLOR=#000000][/COLOR] 
[/LEFT]
[/COLOR][/FONT][FONT=Liberation Serif][COLOR=#4e34e3][LEFT]menuentry "linux (on /dev/sdb2)" {
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 9b8a9870-e1e0-4408-b694-465a3464744a
linux /boot/vmlinuz BOOT_IMAGE=linux root=LABEL=MANDRIVA resume=UUID=81917bd1-ae88-4519-8774-345c41958c76 splash=silent vga=788
initrd (hd1,1)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb2)" {
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 9b8a9870-e1e0-4408-b694-465a3464744a
linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=MANDRIVA resume=UUID=81917bd1-ae88-4519-8774-345c41958c76
initrd (hd1,1)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb2)" {
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 9b8a9870-e1e0-4408-b694-465a3464744a
linux /boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=MANDRIVA failsafe
initrd (hd1,1)/boot/initrd.img[/LEFT]
[/COLOR][/FONT][FONT=Liberation Serif][LEFT]}

 
[SIZE=2]***I shall follow the rest of your advice and tidy up my boot menu and disable os-prober!!!\\:D/***[/SIZE][/LEFT]
[/FONT]

---

### Post by oldfred on 2010-06-14
Glad you got it working.

It should also work with the 
[FONT=Liberation Serif][COLOR=#4e34e3]set root='(hd1,2)'
[/COLOR][/FONT]As I understand it, grub uses the set root and then uses the search. I think the set root is supposed to speed things up. The problem was the difference between the set root of grub2 partition numbering and the mandrive grub legacy partition numbering.
[FONT=Liberation Serif][COLOR=#4e34e3]
[/COLOR][/FONT]

---

