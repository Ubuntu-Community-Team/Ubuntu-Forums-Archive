---
title: "HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM"
date: 2014-06-02
forum: Tutorials
---

### Post by vargax on 2014-06-02
Hi,

These are the steeps I followed to do a clean dual boot between Windows 8 and Ubuntu 14.04 in a Vaio Pro 13 without disable SecureBoot... It may work with Windows 8.1 and other Vaio models...

[LIST=1]
[*]Check that UEFI and SecureBoot are enabled:
[LIST=1]
[*]Shutdown your Vaio
[*]Turn Vaio on using the ASSIST button
[*]Enter to BIOS advanced settings
[LIST=1]
[*]Boot --> Boot Mode --> UEFI
[*]Security --> Secure Boot --> Enabled
[/LIST]
[/LIST]

[*]Prepare Windows:
[LIST=1]
[*]Desfragment your hard drive
[*]Shrink your Windows partition
[LIST=1]
[*]Open Windows Explorer
[*]Right click on Computer --> Manage
[*]Storage --> Disk Management
[*]Right click on (C:) --> Shrink volume
[*]Resize the Windows partition according to your needs
[/LIST]
[/LIST]

[*]Install Ubuntu:
[LIST=1]
[*]Shutdown Windows
[*]Insert the Ubuntu bootable USB
[*]Turn Vaio on using the ASSIST button
[*]Select Boot from external drive
[*]Select "Try Ubuntu without installing"
[*]Run the Ubuntu installer in the desktop:
[LIST=1]
[*]When you hit the the partitioning section select "Something Else": (Check the NOTE at the end if you want to setup full disk encryption)
[LIST=1]
[*]Create three partitions in the available space:
[LIST=1]
[*]250MB ext2 partition: mount point /boot
[*]4092MB for Linux swap
[*]Remaining for ext4: mount point /
[/LIST]

[*]Select to install the bootloader in the /boot partition (if you had a standard setup it should be /deb/sda7)
[/LIST]

[*]Reboot --> The system should boot directly to Windows, without showing the Grub Menu
[/LIST]

[*]Tell Windows / EFI to show Grub Secure Boot:
[LIST=1]
[*]Log into Windows and start an administrative command prompt:
[LIST=1]
[*]Press Windows key
[*]Search for cmd
[*]Right click --> Run as Administrator
[/LIST]

[*]Type this command:
```
bcdedit /set "{bootmgr}" path \EFI\ubuntu\shimx64.efi
```
[/LIST]

[*]Reboot
[/LIST]

[*]Test Grub: You should see now the Grub menu and select Ubuntu or Windows
[/LIST]

NOTE: If you want to use full disk encryption for the Ubuntu you should create the same three partitions. For the swap partition select "Do not use this partition" and for the root partition select "physical volume for encryption", setup the password and then select ext4 and mount point / in the crypto partition. The installer would complain that you don't have swap... just select "continue without swap" and finish the installation. Setting up cryptoswap is a little tricky: 
[LIST=1]
[*]Using gparted identify the partition you are going to use as swap (in my case it was /dev/sda8)
[*]Get the id of this partition:
[LIST=1]
[*]```
 ls -l /dev/disk/by-id/ 
```
[*]Look for the id that maps to your swap partition, it should be something like: ```
 wwn-0x5002538500056730-part8 -> ../../sda8
``` You need the id, you can not use the UUID!
[/LIST]

[*]Add the partition to /etc/crypttab and set it aas swap: ```
swap /dev/disk/by-id/wwn-0x5002538500056730-part8 /dev/urandom swap
```
[*]Add the swap partition to /etc/fstab: ```
/dev/mapper/swap none swap defaults 0 0
```
[*]Reboot and check that swap is working (using system monitor for example)
[/LIST]


If you have trouble with WiFi change /etc/modprobe.d/iwlwifi.conf for:
```
# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
#remove iwlwifi \
#(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
#&& /sbin/modprobe -r mac80211
#options iwlwifi 11n_disable=1
options iwlwifi bt_coex_active=0 power_save=1
```

If you want you can install the official Intel Graphics Driver for Linux: [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux)

References:
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

[https://wiki.archlinux.org/index.php/Dm-crypt/Swap_encryption](https://wiki.archlinux.org/index.php/Dm-crypt/Swap_encryption)
[http://www.microhowto.info/howto/create_an_encrypted_swap_area.html](http://www.microhowto.info/howto/create_an_encrypted_swap_area.html)
[http://www.cioby.ro/linux/creating-and-using-swap-partitions-on-linux.html](http://www.cioby.ro/linux/creating-and-using-swap-partitions-on-linux.html)
[http://iwtf.net/2010/01/05/encrypting-your-ubuntu-swap-partition/](http://iwtf.net/2010/01/05/encrypting-your-ubuntu-swap-partition/)

---

### Post by al-x2 on 2014-06-10
Hello,

I followed your steps closely with no success. Do you think the fact that my vaio pro runs win 8.1. makes a difference?

---

### Post by vargax on 2014-06-22
In what step are you stuck? Tell me what is the issue and maybe I can help you... I just update my laptop to Win 8.1 and everything is working...

---

### Post by grainbarcelona on 2014-06-23
Hi vargax,
I followed your steps but no success. I get the grub menu, but if I choose Ubuntu, I get a black screen that tells me "gave up waiting for the root device" I also tells me: "ALERT! /dev/disk/by-uuid/..... does not exist (the ... is a 20 character or so number/letter code)

Any idea what could be wrong? Any suggestions?

Thanks!

---

### Post by vargax on 2014-06-23
So you can not enter Ubuntu but you can enter Windows, right?

You should tried to re-install Ubuntu... check that you set up the /boot partition correctly and you select that partition for the bootloader...

It would be great if you can take a screenshot or a picture of the partitioning step of the setup, so we can check your partitions and the way you are setting up them...

---

### Post by grainbarcelona on 2014-06-24
Thanks! I got it to work with one extra step at the end: change the grub line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libata.force=noncq" as explained here: 
[http://askubuntu.com/questions/360285/13-10-on-vaio-pro-with-uefi](http://askubuntu.com/questions/360285/13-10-on-vaio-pro-with-uefi)

That did the trick.

Thanks so much for your simple and elegant manual. It's the best I've found, after hunting for solutions for over a month.

---

### Post by grainbarcelona on 2014-06-24
Oh, and here's the screenshot of the partitions, in case it helps
[ATTACH=CONFIG]254198[/ATTACH]

---

### Post by jerryling315 on 2014-06-24
bcdedit /set "{bootmgr}" path \EFI\ubuntu\shimx64.efi




helped a lot, thx

---

### Post by maffbiff on 2014-07-08
Hi, 
just got myself a vayo pro 13 (svp132a1cm) preinstalled with windows...

i m sorry, i have  problems with step 3.6 : repartitionning the free space isn t an given option... am I missing something.

i m no expert, as youi can guess...

Thanks for your post!

---

### Post by raymond15 on 2014-07-23
Hi, I followed your guide to try to install elementary os on my SVP but instead of a grub menu it just boots straight to windows 8.
I've tried to install this twice. Can anyone give me any suggestions on how to get dual boot working?

---

### Post by vargax on 2014-08-18
Hi,

After some update the [COLOR=#000000][FONT=Ubuntu Mono]bcdedit[/FONT][/COLOR] fix stop working... no matter the settings used in bcdedit

[LIST]
[*]Insert the Ubuntu bootable USB 
[*]Turn Vaio on using the ASSIST button 
[*]Select Boot from external drive 
[*]Select "Try Ubuntu without installing" 
[*]Ctrl + Alt + T to open a new terminal 
[*]sudo su to become root 
[*]mount /dev/sda3 /mnt to mount the efi partition 
[*]cd /mnt/EFI 
[*]cp ubuntu/* Microsoft/Boot/. to copy the contents of ubuntu efi boot to the Windows path 
[*]cd Microsoft/Boot/ to enter the Windows EFI path 
[*]mv bootmgfw.efi bootmgfw_win.efi to preserve the Windows boot manager 
[*]mv shimx64.efi bootmgfw.efi so the make the system believe it is loading Windows, but it is going to load grub 
[*]reboot, you should now see the grub boot menu and you can boot Ubuntu 
[*]Boot ubuntu 
[*]Open a new terminal sudo su to become root 
[*]Now we are going to create a new grub entry for Windows, using the new bootmgfw.efi name: gedit /boot/grub/grub.cfg 
[*]Look for the entry under the os-prober section and copy it, it must be something like this: 
[/LIST]

```

menuentry 'Windows Boot Manager (en /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-efi-C6B9-3FEA' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  C6B9-3FEA
    else
      search --no-floppy --fs-uuid --set=root C6B9-3FEA
    fi
**    chainloader /EFI/Microsoft/Boot/bootmgfw.efi**
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi

```


[LIST]
[*]We are now to create a new grub custom entry with this data: gedit /etc/grub.d/40_custom and paste what you just copy, then replace the chainloader parameter for bootmgfw_win.efi You should end up with something like this: 
[/LIST]

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Windows Boot Manager (en /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-efi-C6B9-3FEA' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  C6B9-3FEA
    else
      search --no-floppy --fs-uuid --set=root C6B9-3FEA
    fi
**    chainloader /EFI/Microsoft/Boot/bootmgfw_win.efi**
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi

```


[LIST]
[*]Now we are going to disable the os-prober script: chmod -x /etc/grub.d/30_os-prober 
[*]Finally we are going to update grub, run: update-grub 
[*]Reboot: You should see the grub menu and start Ubuntu or Windows. 
[*]Optionally, you can set the Windows bootmgr paramether back to the original bootmgfw.efi 
[*]In windows start a command prompt (cmd.exe) as administrator 
[*]Enter this command: [COLOR=#000000][FONT=Ubuntu Mono]bcdedit /set "{bootmgr}" path \EFI\Microsoft\Boot\bootmgfw.efi[/FONT][/COLOR] 
[*]Reboot, everything should work now... 
[/LIST]
 
CVC

---

### Post by shwethashree on 2014-08-26
Hi, I just followed the steps to dual boot in sony VAIO with windows 8 preinstalled. And while this I am stuck in step 3.4, I did not get the option of external boot(but i got icons of -start troubleshooting, start from media, contact and support, start bios setup, start from network). In this case what should I select... can you please help me. I really want to learn coding by installing Ubuntu...

---

### Post by vargax on 2014-08-26
Hi shwethashree,
First you have to make sure the USB you are using is bootable, check this [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
Shut down the PC
Connect the USB while the PC is off
Press the Assist button
Select the bottom left option in the menu, it says something like "boot from and external device".

---

### Post by vargax on 2014-08-26
Hi shwethashree,
First you have to make sure the USB you are using is bootable, check this [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
Shut down the PC
Connect the USB while the PC is off
Press the Assist button
Select the bottom left option in the menu, it says something like "boot from and external device".

---

### Post by AgeT on 2014-09-28
Hello all of you!

I tried to follow the guide to install Dualboot ubuntu next to my Windows 8.
i did complete the install but when I reboot my PC it simply goes staight to Windows. i followed the tutorial completing all steps, and i dont know what i can do to get to ubuntu ?

Help me pls!

Tom

---

### Post by vargax on 2014-09-30
Hi Tom,

Follow the instructions in post [#11]("http://ubuntuforums.org/showthread.php?t=2227580&p=13101917#post13101917") until step 7 (mount /dev/sda3 /mnt to mount the efi partition), then:

```

cd /mnt/EFI/Microsoft/Boot
ls -la

```

and post the output of that command... 

Usually after each update Windows changes the bootmgfw.efi file back to its original file. You can check if this is your case looking for the size of the file... if bootmgfw.efi and bootmgfw_win.efi have the same size it is because Windows had changed the file again. To solve this just copy the shimx64.efi file back:

```

cp /mnt/EFI/ubuntu/shimx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi 

```

CVC

---

### Post by jade2 on 2014-10-16
finally found a solution suggestion for my problem(after installing linux- i see it nowhere) but it doesn't work with me .. what i did was to go in the live version to do the 7 steps of post #11 .. at command "mount dev/sda3 /mnt i get this error "mount:special device dev/sda3 does not exist".
also i tried this command with sda, sda1 and so on (when this matters), always same error ...  what can i do now?

---

### Post by vargax on 2014-10-17
Hi jade2,

Looks like you omit the / preceding the dev line. Try again with mount [COLOR="#FF0000"]/[/COLOR]dev/sda3 /mnt

---

### Post by jade2 on 2014-10-17
same error: "mount: can't find /dev/sda3/mnt in /etc/fstab or etc/mtab "

---

### Post by vargax on 2014-10-17
You have to put a space between sda3 and /mnt ... please check the command in the post.

---

### Post by jade2 on 2014-10-17
oh right but now there is another problem.. in between i followed another forum post which tells to do: 
```

sudo mount -t vfat /dev/sda3 /mnt
sudo cp /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.bkp
sudo cp /mnt/EFI/Microsoft/Boot/bootmgfw.efi /mnt/EFI/Microsoftsudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/MicrosoftBoot/bootmgfw.efi
```
but the last line caused another error, so i wanted to forget about that way  .. now when i want to try again "mount /dev/sda3 /mnt, i receive the error:

[B][I]mount: /dev/sda3 already mounted or /mnt busy
mount: according to mtab, /dev/sda3 is already mounted on /mnt[/I][/B]
how can i undo the comands of before to fix that :O


update:
after a restart (with nothing doing something new in between) there was a boot menu (yay) but some apps in win8 doesn't appear right - is that now a bad sign that windows got affected deeper any whereelse too?
Also when trying to boot linux, it needs a lot of time, which ends in giving up, see here:
 [IMG]https://www.dropbox.com/s/xe2cutyykzdkvh5/358bf9d8bb8ef4fd041e2803bd60c1fa951dcda1634accfb70c5c6d36275c9eb.jpg?dl=0[/IMG]
[https://www.dropbox.com/s/xe2cutyykzdkvh5/358bf9d8bb8ef4fd041e2803bd60c1fa951dcda1634accfb70c5c6d36275c9eb.jpg?dl=0](https://www.dropbox.com/s/xe2cutyykzdkvh5/358bf9d8bb8ef4fd041e2803bd60c1fa951dcda1634accfb70c5c6d36275c9eb.jpg?dl=0)

---

### Post by grainbarcelona on 2015-05-28
Vargax is my hero!

 a year ago this post showed me how to get Ubuntu going on my Vaio Pro with the bcdedit fix (#1). A week ago it suddenly stopped working and my computer started booting directly into Wiindows again. I go back to his original post and see that  the follow up answer is already waiting for me (#11). It worked like a dream & I'm back onto Ubuntu. Thanks Vargax!

By the way, for those of you who find themselves suddenly without a grub screen: "Supergrub2 Disk" worked very well for me. Burn it to a USB stick, boot from it & it'll find and boot any operating system on your computer.

---

### Post by snowman3 on 2015-06-15
I followed all the given steps. I have a Vaio Duo 11 and everything is fine: There is the GRUB2 and the entries for ubuntu and Windows Boot Manager (on /dev/sda2). But when I choose booting windows it sais:  
```

Failure: File >>/EFI/Microsoft/Boot/bootmgfw_win.efi was not found.

```
Then I checked the files in the Boot-Partition and the result is this:
```

root@myconvertible:/mnt/EFI/Microsoft/Boot# ls -la
insgesamt 8313
drwxr-xr-x 40 root root 4096 Jun 15 15:50 .
drwxr-xr-x 3 root root 1024 Jun 15 13:13 ..
-rwxr-xr-x 1 root root 32768 Jun 15 15:45 BCD
-rwxr-xr-x 1 root root 28672 Jun 15 13:13 BCD.LOG
-rwxr-xr-x 1 root root 0 Jun 15 13:17 BCD.LOG1
-rwxr-xr-x 1 root root 0 Jun 15 13:17 BCD.LOG2
drwxr-xr-x 2 root root 1024 Jun 15 13:17 bg-BG
-rwxr-xr-x 1 root root 1355736 Jun 15 15:49 bootmgfw.efi
-rwxr-xr-x 1 root root 1615712 Aug 22 2013 **bootmgfw_win.efi**
-rwxr-xr-x 1 root root 1612128 Aug 22 2013 bootmgr.efi
-rwxr-xr-x 1 root root 65536 Jun 15 13:17 BOOTSTAT.DAT
-rwxr-xr-x 1 root root 4247 Jun 18 2013 boot.stl
-rwxr-xr-x 1 root root 119296 Jun 15 14:23 bootx64.efi
drwxr-xr-x 2 root root 1024 Jun 15 13:17 cs-CZ
drwxr-xr-x 2 root root 1024 Jun 15 13:17 da-DK
drwxr-xr-x 2 root root 1024 Jun 15 13:17 de-DE
drwxr-xr-x 2 root root 1024 Jun 15 13:17 el-GR
drwxr-xr-x 2 root root 1024 Jun 15 13:17 en-GB
drwxr-xr-x 2 root root 1024 Jun 15 13:17 en-US
drwxr-xr-x 2 root root 1024 Jun 15 13:17 es-ES
drwxr-xr-x 2 root root 1024 Jun 15 13:17 et-EE
drwxr-xr-x 2 root root 1024 Jun 15 13:17 fi-FI
drwxr-xr-x 2 root root 2048 Jun 15 13:17 Fonts
drwxr-xr-x 2 root root 1024 Jun 15 13:17 fr-FR
-rwxr-xr-x 1 root root 121 Jun 15 15:49 grub.cfg
-rwxr-xr-x 1 root root 956792 Jun 15 15:49 grubx64.efi
drwxr-xr-x 2 root root 1024 Jun 15 13:17 hr-HR
drwxr-xr-x 2 root root 1024 Jun 15 13:17 hu-HU
drwxr-xr-x 2 root root 1024 Jun 15 13:17 it-IT
drwxr-xr-x 2 root root 1024 Jun 15 13:17 ja-JP
drwxr-xr-x 2 root root 1024 Jun 15 13:17 ko-KR
drwxr-xr-x 2 root root 1024 Jun 15 13:17 lt-LT
drwxr-xr-x 2 root root 1024 Jun 15 13:17 lv-LV
-rwxr-xr-x 1 root root 1493344 Aug 22 2013 memtest.efi
-rwxr-xr-x 1 root root 1178240 Jun 15 15:49 MokManager.efi
drwxr-xr-x 2 root root 1024 Jun 15 13:17 nb-NO
drwxr-xr-x 2 root root 1024 Jun 15 13:17 nl-NL
drwxr-xr-x 2 root root 1024 Jun 15 13:17 pl-PL
drwxr-xr-x 2 root root 1024 Jun 15 13:17 pt-BR
drwxr-xr-x 2 root root 1024 Jun 15 13:17 pt-PT
drwxr-xr-x 2 root root 1024 Jun 15 13:17 qps-ploc
drwxr-xr-x 3 root root 1024 Jun 15 13:17 Resources
drwxr-xr-x 2 root root 1024 Jun 15 13:17 ro-RO
drwxr-xr-x 2 root root 1024 Jun 15 13:17 ru-RU
drwxr-xr-x 2 root root 1024 Jun 15 13:17 sk-SK
drwxr-xr-x 2 root root 1024 Jun 15 13:17 sl-SI
drwxr-xr-x 2 root root 1024 Jun 15 13:17 sr-Latn-CS
drwxr-xr-x 2 root root 1024 Jun 15 13:17 sr-Latn-RS
drwxr-xr-x 2 root root 1024 Jun 15 13:17 sv-SE
drwxr-xr-x 2 root root 1024 Jun 15 13:17 tr-TR
drwxr-xr-x 2 root root 1024 Jun 15 13:17 uk-UA
drwxr-xr-x 2 root root 1024 Jun 15 13:17 zh-CN
drwxr-xr-x 2 root root 1024 Jun 15 13:17 zh-HK
drwxr-xr-x 2 root root 1024 Jun 15 13:17 zh-TW
root@myconvertible:/mnt/EFI/Microsoft/Boot#

```

Obviously, the bootmgfw_win.efi exists. Why it is not found? This is my 40_custom file:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Windows Boot Manager (auf /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-28A1-E5B1' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  28A1-E5B1
    else
      search --no-floppy --fs-uuid --set=root 28A1-E5B1
    fi
    chainloader /EFI/Microsoft/Boot/**bootmgfw_win.efi**
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi

```

---

### Post by phaberest on 2015-08-15
Oh well...I've followed all vargax directives and finally ubuntu works...but it's the only one, actually :D

After renaming the windows efi file grub is showing up on boot, but the update-grub has deleted the windows entry. How do I get it back?

***EDIT***
Ok, well... I ran update-grub again and it now works. Maybe it just didn't load the custom file

---

