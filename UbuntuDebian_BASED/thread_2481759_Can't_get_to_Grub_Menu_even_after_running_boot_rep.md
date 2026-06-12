---
title: "Can't get to Grub Menu even after running boot repair - Windows 10/LXLE dual boot"
date: 2022-12-08
forum: Ubuntu/Debian BASED
---

### Post by pgslmatias on 2022-12-08
This is the output of boot repair: [https://paste.ubuntu.com/p/QxV9NKDBnk/](https://paste.ubuntu.com/p/QxV9NKDBnk/)

At first I had Windows 10. I created an empty partition with 100 GB and I burned a USB with LXLE and installed Ubuntu by selecting install Ubuntu alongside Windows 10.

Everything seemed ok. When selecting boot order in BIOS I have as options Windows Boot Manager, my SSD and lxle. When I put lxle first in the boot order I only get to the GRUB terminal, I can't access the menu to choose between Windows 10 and LXLE. If I type exit at the terminal it boots to Windows, and it does the same if I choose Windows Boot Manager or my SSD as the first option in BIOS. 

I ran boot repair from the live USB, but nothing changed at all. I can access Windows 10 perfectly, but have not been able to get to my lxle installation. 

I have Secure Boot turned off.

What's the next step in debugging the problem?

---

### Post by oldfred on 2022-12-08
Moved to other OS since not Lubuntu.

What model Lenovo?
Do you have Windows fast start up off? Note that Windows updates may turn it back on.

Grub only boots working windows, so fast start up must be off. Also Windows must not need other repairs, like chkdsk.

---

### Post by pgslmatias on 2022-12-08
It is a Lenovo ideapad 3. 

> Grub only boots working windows, so fast start up must be off. Also Windows must not need other repairs, like chkdsk

Right now Grub is not booting anything, I can only boot into Windows, not into Ubuntu. 

As for turning off fast startup, I don't have the option to do so. It doesn't appear and as such, according to [https://answers.microsoft.com/en-us/windows/forum/all/turn-off-fast-startup/5362cd29-86ca-4b39-be60-718446f9d5f8](https://answers.microsoft.com/en-us/windows/forum/all/turn-off-fast-startup/5362cd29-86ca-4b39-be60-718446f9d5f8) I am supposed to edit the registers. I'm not sure I should do that though: Windows is working perfectly. 

I don't understand how a problem with Windows would make Grub not show the menu and show the terminal instead, and not being able to boot into Ubuntu. I could understand a problem with Windows not allowing me to boot into Windows from grub, but that's not what is happening.

---

### Post by MAFoElffen on 2022-12-08
From terminal of a LiveCD media
```

efibootmgr

```

---

### Post by oldfred on 2022-12-08
The output from efibootmgr is in the Boot-Repair summary report.

Can you directly boot this from UEFI boot menu?
Boot0001* lxle	

Are you then able to get grub menu, or maybe press escape right after vendor logo but before grub menu normally appears?
And then boot recovery mode? Or second line in grub menu?

---

### Post by pgslmatias on 2022-12-08
```
efibootmgr
BootCurrent: 0014
Timeout: 0 seconds
BootOrder: 0014,0000,0012,0001,0013,0015,0016,0017
Boot0000* Windows Boot Manager
Boot0001* lxle
Boot0010  Setup
Boot0011  Boot Menu
Boot0012* NVMe: SKHynix_HFM512GDHTNI-87A0B             
Boot0013* ATA HDD:
Boot0014* USB HDD: Kingston DataTraveler 3.0
Boot0015* USB LAN:
Boot0016* USB FDD:
Boot0017* USB CD:


```

---

### Post by pgslmatias on 2022-12-08
> **oldfred said:**
> The output from efibootmgr is in the Boot-Repair summary report.

Can you directly boot this from UEFI boot menu?
Boot0001* lxle    

Are you then able to get grub menu, or maybe press escape right after vendor logo but before grub menu normally appears?
And then boot recovery mode? Or second line in grub menu?

I'm not sure I understand what you are asking for :( If you mean in UEFI try to boot into lxle, by putting it as the first option, yes. As I described in the OP, that's what I do and all I get is the terminal, not grub menu. 

If this is not it then I don't know...

---

### Post by oldfred on 2022-12-08
Are you getting grub's limited terminal like grub> or Ubuntu's full terminal where it has not booted into the gui?

---

### Post by pgslmatias on 2022-12-08
> **oldfred said:**
> Are you getting grub's limited terminal like grub> or Ubuntu's full terminal where it has not booted into the gui?

grub limited terminal

---

### Post by oldfred on 2022-12-08
Can you from grub>run this?
configfile (hd0,5)/boot/grub/grub.cfg 

OR:
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/boot/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/boot/initrd.img
boot


This should show partition, so above commands are at right partition.
ls (hd0,5)/ 
ls (hd0,5)/boot

---

### Post by pgslmatias on 2022-12-08
> **oldfred said:**
> 
configfile (hd0,5)/boot/grub/grub.cfg 


This worked perfectly! I can access Grub menu, and I have tried and successfully entered both LXLE and Windows from it :)

Now I want to be able to just access Grub menu when I turn on the computer, instead of having to type this everytime (which is the behaviour I'm getting).

I re ran boot repair, this time from LXLE installed on my SSD. This is the output 

```
An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com

Please write on a paper the following URL:
https://paste.ubuntu.com/p/bs4N7g5NHf/


In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com 

Locked-NVram detected.

```

I googled it and found [https://askubuntu.com/questions/1325390/locked-nvram-detected](https://askubuntu.com/questions/1325390/locked-nvram-detected) saying it's a hardware error, which is weird, as everything is working correctly and so I will disregard this information. It doesn't appear to be my exact situation.

I also googled the fix you gave me and it seems like it is just making grub load the correct configuration file: that is my understanding from [https://wiki.archlinux.org/title/GRUB#Generated_grub.cfg](https://wiki.archlinux.org/title/GRUB#Generated_grub.cfg)

Do you know how to proceed now?

By the way, at this point I am already very thankful <3

---

### Post by oldfred on 2022-12-08
I thought the Locked NV-RAM was an UEFI setting.
Some systems not only have UEFI Secure Boot but have added UEFI settings to lock ESP and/or lock USB boot for added security.
Was UEFI updated? 
Sometimes you may not know it as Windows updates may include an UEFI update. And now many systems can be updated from Ubuntu/Linux with fwupdate entry in grub or systemd.

But if you have UEFI entry and the configfile works, then it may just be something else.
But I am not seeing problem. GUIDs & UUIDs all look correct.

The chain of boot process is UEFI using GUID/partUUID finds ESP and loads shimx64.efi.
Then in ESP is a 3 line grub.cfg that uses a configfile entry like you now are manually typing.  Lines 267 thru 269. It does search by UUID for your / where grub.cfg for install is. You are just typing in what search should find.

I use browser search & plug in GUID/partuuid in UEFI entry and it finds ESP.
Then from ESP I use UUID of its search to find / (or /boot) 
Those all look consistent which they should from a grub reinstall using Boot-Repair.

---

### Post by pgslmatias on 2022-12-18
> **oldfred said:**
> I thought the Locked NV-RAM was an UEFI setting.
Some systems not only have UEFI Secure Boot but have added UEFI settings to lock ESP and/or lock USB boot for added security.
Was UEFI updated? 
Sometimes you may not know it as Windows updates may include an UEFI update. And now many systems can be updated from Ubuntu/Linux with fwupdate entry in grub or systemd.

But if you have UEFI entry and the configfile works, then it may just be something else.
But I am not seeing problem. GUIDs & UUIDs all look correct.

The chain of boot process is UEFI using GUID/partUUID finds ESP and loads shimx64.efi.
Then in ESP is a 3 line grub.cfg that uses a configfile entry like you now are manually typing.  Lines 267 thru 269. It does search by UUID for your / where grub.cfg for install is. You are just typing in what search should find.

I use browser search & plug in GUID/partuuid in UEFI entry and it finds ESP.
Then from ESP I use UUID of its search to find / (or /boot) 
Those all look consistent which they should from a grub reinstall using Boot-Repair.

I did not manually update UEFI. I have no idea if Windows did it by itself. 

I'm sorry I haven't been able to dig in to figure out what is happening. It seems to just work with the hack you gave me, and I'm ok with typing it everytime I turn on the computer. Should I follow the link in your message about "[COLOR=Navy]UEFI boot install & repair info - Regularly Updated :
[/COLOR] [https://ubuntuforums.org/showthread.php?t=2147295]("http://ubuntuforums.org/showthread.php?t=2147295")" to see if there is anything else I can do, when I try to make GRUB get to the configfile automatically?

I'm now experiencing another bug when booting. Do you think they are related? This is it: [https://ubuntuforums.org/showthread.php?t=2482071](https://ubuntuforums.org/showthread.php?t=2482071)

---

