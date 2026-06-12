---
title: "HowTo: uNetbootin and Ubuntu persistent install - EASY!"
date: 2014-02-28
forum: Tutorials
---

### Post by motocollage on 2014-02-28
[FONT=Ubuntu]I've been using Ubuntu and Lubuntu for a few years now and have very little formal technical training, but I finally feel like I might be able to contribute to the community. This method worked like a charm for me, and I don't think it's too technical. I'm assuming this works using uNetbootin on Windows, though I did this through Ubuntu and Lubuntu 12.04 to create a working Persistent install. Hope this helps someone![/FONT]


[FONT=Ubuntu]**SETTING UP USBDRIVE**[/FONT]
[FONT=Ubuntu]Format to FAT/FAT32 with Disk Utility, Gparted, or similar. My procedure was to use Disk Utility to format my drive MBR, then format it to FAT.[/FONT]


[FONT=Ubuntu]**STEP 1**[/FONT]
[FONT=Ubuntu]Download 'buntu distro iso[/FONT]
[FONT=Ubuntu]Install uNetbootin [/FONT]
[FONT=Ubuntu]Open uNetbootin with Ubuntu iso. Set 'space across reboots' at minimum of 128 (to be resized later). [/FONT]
[FONT=Ubuntu]Reboot to check that all is well and the USB drive runs a live session[/FONT]


[FONT=Ubuntu]**STEP 2**[/FONT]
[FONT=Ubuntu]Using Gparted, shrink partition. The installed iso should be 800-900mb. I'm using a 16GB usb 3.0 drive (3.0 is faster, so it is a better option for a persistent install), so I resized my partition to 4GB, knowing that I would resize my casper-rw file within that space. From what I understand, once the iso partition is shrunk, you can always replace it with a different iso.[/FONT]


[FONT=Ubuntu]Using Gparted, I created a 1GB Linux Swap partition. The remaining space I formatted to fat32, both as external storage and to still use this usb as a flash drive. I had roughly 10GB left.[/FONT]


[FONT=Ubuntu]**STEP 3**[/FONT]
[FONT=Ubuntu]information based on this link: [http://ubuntuforums.org/showthread.php?t=1885392](http://ubuntuforums.org/showthread.php?t=1885392)[/FONT]


[FONT=Ubuntu]Followed procedure listed by Sudodus to make sure everything was behaving correctly. Make sure the disk is mounted.[/FONT]


```

[FONT=Ubuntu]sudo fdisk -lu[/FONT]
[FONT=Ubuntu]
df[/FONT]
[FONT=Ubuntu]
sudo blkid[/FONT]

```

[FONT=Ubuntu]With USB mounted, navigated in the iso to syslinux.cfg (opened, edited, and saved it with Gedit, but any text editor will do). I changed the label from [COLOR=#0000ff]Default[/COLOR] to [COLOR=#ff0000]Ubuntu 12.04 LTS [/COLOR][COLOR=#ff0000]*persistent* [/COLOR]and saw that that &#8220;quiet *splash&#8212;*[COLOR=#ff0000]*persistent*[/COLOR]*&#8221;* part was already set, thanks to uNetbootin.[/FONT]

```

default menu.c32
prompt 0
menu title UNetbootin
timeout 100


label unetbootindefault
menu label [COLOR=#ff0000]Boot into Ubuntu 12.04 LTS *persistent*[/COLOR]
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --[COLOR=#ff0000] persistent[/COLOR]


label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent


label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- persistent


label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent



```




[FONT=Ubuntu]**STEP 4**[/FONT]
[FONT=Ubuntu]information based on this link: [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)[/FONT]


[FONT=Ubuntu]Followed instructions for **Resize an existing casper-rw loop file**, seen below. I'll go ahead and say that I set my size to ____, which combined with the actual iso was almost a perfect fit in my 4GB partition (the one that I shrank). Remember that I set 'space across reboots' at 128mb. 8Also, be patient because the two commands below may take a few minutes:[/FONT]


[FONT=Ubuntu][COLOR=#333333][FONT=Lucida Grande]The following method will allow you to [/FONT][/COLOR]*[COLOR=#333333][FONT=Lucida Grande][I]resize your existing casper-rw *[/FONT][/COLOR][/I][COLOR=#333333][FONT=Lucida Grande]image(expand casper-rw). You should create a backup just in case before proceeding.[/FONT][/COLOR][/FONT]

[LIST=1]
[*][COLOR=#333333][FONT=Lucida Grande]After    you're up and running in Linux, insert the flash drive that contains    your [/FONT][/COLOR]**[COLOR=#333333][FONT=Lucida Grande]casper-rw [/FONT][/COLOR]**[COLOR=#333333][FONT=Lucida Grande]loop    file[/FONT][/COLOR]
[*]    [COLOR=#333333][FONT=Lucida Grande]Open    a terminal and change directory (CD) to the location of your    casper-rw file[/FONT][/COLOR]
[*]    [COLOR=#333333][FONT=Lucida Grande]Type    the following into the terminal window and press enter[/FONT][/COLOR][INDENT]    **[COLOR=#343434][FONT=Lucida Grande]dd    if=/dev/zero bs=1M count=[/FONT][/COLOR]****[COLOR=#ff0000][FONT=Lucida Grande]1024[/FONT][/COLOR]****[COLOR=#343434][FONT=Lucida Grande] >>    casper-rw[/FONT][/COLOR]**[/INDENT]
    [COLOR=#333333][FONT=Lucida Grande](replacing    [/FONT][/COLOR]**[COLOR=#ff0000][FONT=Lucida Grande]1024    [/FONT][/COLOR]**[COLOR=#333333][FONT=Lucida Grande]with    the size in MB you wish to increase the original size by)[/FONT][/COLOR]
[*]    [COLOR=#333333][FONT=Lucida Grande]Type    the following into the terminal window and press enter[/FONT][/COLOR][INDENT]    **[COLOR=#343434][FONT=Lucida Grande]resize2fs    casper-rw[/FONT][/COLOR]**[/INDENT]
[/LIST]
[COLOR=#333333][FONT=Lucida Grande]If all goes well, you should now have a larger casper-rw loop file to use for saving your persistent changes.[/FONT][/COLOR]


[FONT=Ubuntu]FINAL THOUGHTS[/FONT]
[FONT=Ubuntu]I want to use my new live system on desktops primarily, but I also use it on my Acer D250 netbook, which requires an updated wireless driver anytime I install a new system. This is my second run through of the procedure, just to make sure that I can successfully repeat the results. I did find out that once I got my wireless up and running all was fine.....then I slipped my usb into a school computer and booted up my system, installed some software, **updated and upgraded**. The last step required a restart, and when I did I could not longer access wireless. It may be because I hit Restart during my live session on the school computer and when it shutdown I pulled out my usb, THEN opened it again on my Acer. I still don't completely understand what I did, but it gave me a reason to repeat the process. Also, my research into this mentioned that the casper-rw file will eventually get irreversibly full, so it doesn't truly behave like a standard installation.[/FONT]


[FONT=Ubuntu]If anyone has any questions about anything covered above, or any insight into what I actually did, I'm happy to hear it![/FONT]

---

