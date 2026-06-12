---
title: "Pop_OS installed. Windows 10 dual. both systems work, but boot loader -no"
date: 2023-03-22
forum: Ubuntu/Debian BASED
---

### Post by jackstarz on 2023-03-22
I am starting this Thread bc all the discussions I read usually talk about Grub or have some other issues. From my research it's saying not to use Grub anymore for current Pop install which is whatever the stable version  is today. I have a working Win 10 and Pop os. Win has the fast boot off and secure boot off in bios. if I startup fresh -  Pop os automatically boots perfectly. if I need win I can switch bios boot order or use a recovery grub USB and it loads perfectly. This PC is a Tower, super powerful, has some nvidia 3060 ti.. all working. Bios has UEFI .. But when I did this install.. I installed grub and did all that.. It seems to be in legacy mode. Anyway I had Grub go bad before I used a recovery USB to fix boot. Thats where I am. Everything works except boot menu. does anyone know about this issue with 'boot loader' as separate from/instead of Grub?  Thanks

---

### Post by oldfred on 2023-03-22
Do not know Pop.
Question is whether you are booting with grub or with SystemD boot?

This may show details, do not run any fixes as it may want to install grub as that is its normal fix:

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jackstarz on 2023-03-22
hey man, thanks for lookin --  and ya, I've been in Linux long enough to never run a boot repair without checkin things out first.. cuz I used to like learn everything the hard way  :) haha

[http://*******.us/GzQWyW](http://*******.us/GzQWyW)

---

### Post by guiverc on 2023-03-22
The system I'm using now was purchased in February 2023, as my prior system had *failed* (*dead PSU, along with some other issues*).  When purchased; it wasn't new, but a refurbished system & came with *clean *Windows 11.

I have no use of windows, but decided I'd not overwrite it, but use the box to QA-test (ie. *Quality Assurance test installs*) install the two OSes I did want.

I installed Lubuntu* lunar* (ie. *what will be 23.04 on release next month*), which is what I'm using now, shrinking the windows partition to make space, then confirmed windows still booted & worked as well as Lubuntu *lunar* & recorded the results (*given I used my box for a QA test install*).

My next install was Lubuntu *jammy* (22.04.2 *at the time*) again *alongside* the other OSes, confirmed the prior installs worked (ie. Lubuntu *lunar* & windows 11) & the new 22.04 install works. Recorded that result (*another QA test install*).

I like my systems dual booting; this is my primary PC where I want the current *development* release, but my backup OS is usually the LTS release (*currently 22.04*). I select which I'll use at startup, thus when I turn on this system I briefly see a DELL logo, then GRUB menu which lets me select
- Ubuntu *lunar*, 
- Ubuntu 22.04 LTS
- windows 11
- some other options (uEFI setup etc).
 This system has secure (uEFI) boot enabled.  I like GRUB & use it.

I also purchased a few other boxes too, and did some other *like* installs on them, some had windows 10 - thus my options are *lunar*/22.04/windows[10] on those.  When I need extra disk space, I'll delete the windows partition(s), but for now all came with large enough disks I was happy to let windows keep ~40GB & just ignore it.  My installs all just worked; which was on 1x dell system, 3x hp systems, 1x lenovo.

I don't want to have to go into BIOS to change a setting there; some systems are a *pain* in doing this (*I have one that requires me to hold a key whilst off to have it turn on & ask me, another requires me to hold down a key then turn it on... of ~20+ systems I use somewhat regularly that is 7+ different procedures!*). Using `grub` makes it the same for all systems & its easy (a menu); even allowing me to enter uEFI settings easily on the boxes that require me to press & hold keys whilst off....

I'm not sure what you're asking, if you're after support, or just wanting a *discussion* on grub & boot loaders.

The only problem I've had is on one [uEFI] system which is dual boot (Ubuntu, OpenSuSE *tumbleweed*, & Fedora), when OpenSuSE upgrades it takes 'ownership' of the grub bootloader & my order setup in Ubuntu is thus not used. As all boot options are detected when all OSes upgrade packages (ie. all offer other other installed OSes as options for boot) I just ignore that & manually change it back to Ubuntu ownership when I next have Ubuntu booted (*if I remember; the only difference is which grub I'll see; green-gecko (opensuse) vs blue-bird (lubuntu) & order of the items* *thus of no importance*)

Do note:  Its my understanding that grub will require both OSes to be installed in the same mode for it to work; ie. is your windows installed with the same settings as your Pop OS  (ie. you didn't change any BIOS settings to boot the PopOS installation media did you?).   This new system had Secure-uEFI enabled; thus I just installed Lubuntu *lunar* & 22.04 using that mode so all are identical (here I'm talking about uEFI vs. Secure-uEFI vs. CSM|legacy|BIOS as the  CSM|legacy|BIOS boot is very different to either uEFI mode).  I installed Ubuntu with the same mode all the machines I purchased were already in (*Ubuntu will install in all modes*)

*FYI:   I refer to Ubuntu & Lubuntu is a number of places, I consider this system I'm using a Ubuntu system regardless of the desktop I'm actually using (ie. Lubuntu to me is a Ubuntu system).*

---

### Post by jackstarz on 2023-03-22
thanks for the notes. I'm jus trying to get a dual boot menu that works so I dont need to go into bios. My bios is pretty easy.. but I'd like to fix boot. I don't know if I'll every use WIN as I despise it, but I figured I would keep 1 machine with the option since I am running a Mint laptop and some super low resource Ubuntu on an old laptop. I'll fix this issue if its uncomplicated but if it involves some horror show I'll just leave it as a Bios thing.  I didn't change anything in Bios except boot order that I can remember

---

### Post by yancek on 2023-03-23
>   I installed grub and did all that.. It seems to be in legacy mode

Your link to boot repair above does is broken but, if you did install Pop OS in Legacy mode and windows is in UEFI mode Pop using Grub will not boot windows. Grub will only boot windows if the Linux OS is installed in the same mode (Legacy or UEFI).  Have you changed bootloaders?  What are you using?

---

### Post by jackstarz on 2023-03-23
hey! I didnt at anytime specifically choose anything about legacy or UEFI for anything. I just ran my installs. I installed grub 2.. it wouldn't load either OS. I did a boot repair and now it loads into POP--- so I the only boot I know is happening is whatever POP has in whatever the active boot sector is

---

### Post by jackstarz on 2023-03-23
[http://*******.us/21XKC7](http://*******.us/21XKC7)       here another link.  I just made this one

---

### Post by westie457 on 2023-03-23
You have posted another broken link. Please post one with no obfuscated characters in it.

---

### Post by jackstarz on 2023-03-23
ya I cant access it either.. I dont want to hide the char it just keeps doing it when I post..

---

### Post by jackstarz on 2023-03-23
ok

---

### Post by jackstarz on 2023-03-23
[https://pastebin.ubuntu.com/p/KShH5RvYK7/](https://pastebin.ubuntu.com/p/KShH5RvYK7/)

---

### Post by coffeecat on 2023-03-23
> **jackstarz said:**
> it deleted my post!   

Why are you uploading to a 3rd party site, when the boot repair utility uploads it for you to [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/) **and** gives you a link to include in your post? Why make things more difficult for yourself and for others? The site you are linking to was thoroughly abused a while ago, and we were forced to include the domain in our censor list. Maybe it's time to remove it from the censor list - maybe not. In either event, simply use [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/). It's all done for you. That's what 99% of people asking for help here do.

---

### Post by oldfred on 2023-03-23
Please post to pastebin site so others can see report.
Not sure what is correct for SystemD boot.

But most systems do not allow two ESP on one drive. You can have one per drive.
Change to one ESP & reinstall boot loader(s) that were in other ESP.

---

### Post by jackstarz on 2023-03-23
I didnt choose the site. I have never posted this report until last night. I only ran the software. It asked if I would like to upload to pastebin. I agreed and that is the link it gave me. I looked through all settings and found no option to choose a diffferent upload site. I would have to edit the software ..  anyway I copied it manually and the updatte is above

I do have an issue where I have multiple drive partitions. 1 of them I can't get rid of. the boot doesn't make sense.. I would assume WIN 10 was installed in Efi no? but when I ran the command to check legacy or no it said I am in legacy.  so I am not sure. I am happy to fix it.. I hope not to reinstall the whole thing.  now after a update it seems my nvidia went off. I have no sound and only 1 monitor works.. notes I found said it nvid update doesnt write to boot.. (update I fixed nvidia)

---

### Post by jackstarz on 2023-03-23
> **oldfred said:**
> Please post to pastebin site so others can see report.
Not sure what is correct for SystemD boot.

But most systems do not allow two ESP on one drive. You can have one per drive.
Change to one ESP & reinstall boot loader(s) that were in other ESP.

pop forced me to make the 1GB EFI  #6 to get through install --  I made 4 & 7   are you saying to remove some of the drives? I assume Win won't want me to mess with its drives.. but pop required that big 1GB...  
 1,2,3,5 were existing win10 partions

---

### Post by jackstarz on 2023-03-23
I checked for EFI with these commands and verified GPT present.  It was telling me legacy before but now UEFI after Boot repair.  

So then at startup, the Bios checks boot order and loads whichev is #1.. which is why I have 2 working ESP i figure. I don't see how to join them together since the windows one is 100MB and Pop is 1GB... I guess I was thinking that a boot loader would ameliorate that and could direct things anywhere it wanted so I wouldn't need to move the Win files to the Pop ESP... (which is what your notes on UEFI seem suggesting)  



[PHP]jackstarz@pop-os:~$ test -d /sys/firmware/efi && echo efi || echo bios
efi
jackstarz@pop-os:~$ [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"
Installed in UEFI mode
ackstarz@pop-os:~$  ls /sys/firmware/efi
config_table  esrt              fw_vendor  runtime-map
efivars       fw_platform_size  runtime    systab


[/PHP]

Thanks!

---

### Post by oldfred on 2023-03-23
UEFI looks for the ESP to know what files to boot.
But it actually is the GUID/partUUID that is used once an entry is added to UEFI.
I think esp,boot flags are used to find the partition to be used to create or update a boot entry and where to store boot files.
SystemD boot does have a lot more files in the ESP, but I thought they could also use a boot partition that is not the same as a Linux boot partition, but do not know details as never have used it. 

You can see UEFI entries.
sudo efibootmgr -v
And the partUUID
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

### Post by jackstarz on 2023-03-23
[PHP]BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0004,0001,0000
Boot0000* Windows Boot Manager    HD(1,GPT,e2a01b86-381e-453b-9d98-668966cfe187,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* pop    HD(6,GPT,64e7d9dd-ce6f-4664-90c5-210c8b17af99,0x1d699800,0x225fff)/File(\EFI\POP\GRUBX64.EFI)
Boot0003* Pop!_OS 22.04 LTS    HD(6,GPT,64e7d9dd-ce6f-4664-90c5-210c8b17af99,0x1d699800,0x225fff)/File(\EFI\SYSTEMD\SYSTEMD-BOOTX64.EFI)
Boot0004* UEFI OS    HD(6,GPT,64e7d9dd-ce6f-4664-90c5-210c8b17af99,0x1d699800,0x225fff)/File(\EFI\BOOT\BOOTX64.EFI)..BO
$ lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME FSTYPE   SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID                                 PARTUUID
zram0
             15.5G                        [SWAP]                                          
nvme0n1
&#9474;           465.8G                                                                        
&#9500;&#9472;nvme0n1p1
&#9474;    vfat     100M              EFI system partition
&#9474;                                                    3205-D34E                            e2a01b86-381e-453b-9d98-668966cfe187
&#9500;&#9472;nvme0n1p2
&#9474;              16M              Microsoft reserved partition
&#9474;                                                                                         13c78014-9fae-4fc4-8b30-cb2c985bec3b
&#9500;&#9472;nvme0n1p3
&#9474;    ntfs   232.6G              Basic data partition
&#9474;                                                    D09E06B89E0696DE                     3f28f52e-0a14-402e-b6b5-be8a24f25c8f
&#9500;&#9472;nvme0n1p4
&#9474;    swap     2.1G        swap                       d281788c-feda-4a5f-a97b-c48594dbcc09 3511b258-8aca-4472-9162-361eac2f0583
&#9474; &#9492;&#9472;cryptswap
&#9474;    swap     2.1G        cryptswap
&#9474;                                         [SWAP]     dbb4a53e-7379-4013-b688-8a770dbbfff3 
&#9500;&#9472;nvme0n1p5
&#9474;    ntfs     541M                                   483867A6386791AC                     4c6909f4-c36c-4484-acae-b2695139f889
&#9500;&#9472;nvme0n1p6
&#9474;    vfat     1.1G 283.9M                 /boot/efi  E7A7-7D9E                            64e7d9dd-ce6f-4664-90c5-210c8b17af99
&#9492;&#9472;nvme0n1p7
     ext4   228.9G  14.2G                 /          54cce43d-1171-43e0-bc8a-9c29896ef5a4 5d1e5e14-aedf-49ad-8e9f-ae8b5e22968b


[/PHP]

---

### Post by oldfred on 2023-03-23
lsblk cannot have a space in list of columns.

You are showing two different GUIDs for boot entries.
0001 looks like a typical grub boot entry.
0003 may be a Pop entry, but do not have an entry to compare to.

---

### Post by jackstarz on 2023-03-23
If it is talking about boot from Bios.. it may be retaining an ID from a Live disc or other boot USB?  

I updates Lsbsk above

---

### Post by oldfred on 2023-03-24
Have you tried all 3 UEFI boot entries?
One is grub, one is SystemD and one is fallback or drive entry.

---

### Post by jackstarz on 2023-03-24
hmm.. I think ya. The boot in bios only had windows when I started. so I think all the other boot options are POP,  and recovery.. then I did a boot repair which may have created an entry

---

