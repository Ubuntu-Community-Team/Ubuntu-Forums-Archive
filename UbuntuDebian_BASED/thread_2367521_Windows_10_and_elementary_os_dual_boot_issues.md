---
title: "Windows 10 and elementary os dual boot issues"
date: 2017-07-31
forum: Ubuntu/Debian BASED
---

### Post by maxwellgisborne on 2017-07-31
Hi, I know that this is a form for Ubuntu but Elemental is based of Ubuntu so I hop you can help. 

I downloaded the Iso from [hear]("https://elementary.io/") and followed the instructions. I shrank the windows partition and used rufus to creat a bootable usb. 
I followed the install wizard until It told me to restart. But when it turned back on the thing booted straight back to windows.
I googled around and found a thread on [stack overflow]("https://askubuntu.com/questions/748631/installed-ubuntu-15-10-alongside-windows-10-but-it-wont-boot"). I did what the commenter there advised and booted from the usb and selected "try with out installing", opend a terminal and typed:
sudo add-apt-repository -y ppa:yannubuntu/boot-repair;

But the terminal repleted by saying that it didn't understand add-apt-repository, and I did a copy and past so Im sure its wast spell wrong. 

Dose any one know whats going on with this and dose anyone have any advise?

Thanks :)
PS: i wrought elemental in the title instead of elementary, sory

---

### Post by oldfred on 2017-07-31
Moved to Other OS & edited title.

What brand/model system? What video card/chip?

UEFI or BIOS install? Is Windows UEFI boot?

If both systems are installed in UEFI, you should be able to press the UEFI boot menu key, often f10 or f12 check your manual. If fast boot on in UEFI, you may not have time to press any keys and need to do a full cold boot (total power off, remove battery if laptop). Or may be able to get into UEFI from Windows.
And make sure fast start up is off in Windows.
If UEFI see also link in my signature below for more info & links.

---

### Post by yancek on 2017-08-01
The link you posted from Stack Overflow was posted by a user an not by the developers of Boot Repair.  The link to the Boot Repair page is below and I would suggest you read through it and use the commands they have and try again.  If that works for you, I would suggest that you select the option in boot repair to Create BootInfo Summary and post a link to the results here so that members more familiar can try to help.  Trying to repair and not understanding might make it worse.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by maxwellgisborne on 2017-08-01
Okay, Good advice thanks for the link, I'm new to this and keen to learn.

---

### Post by maxwellgisborne on 2017-08-01
I have done what you suested and hear is the link to the log:
[http://paste.ubuntu.com/25220295/](http://paste.ubuntu.com/25220295/)
The commands from the link you posted are the same as from the thread i originally posted, so I created a bootable USB insted.
I did not click the repair option only the create bootinfo summary instead

Also something I didn't say erlyer is that after It didn't boot I tried installing again so theirs two elementary partitions on my hard drive.

---

### Post by oldfred on 2017-08-01
Boot-Repair says this:
 SecureBoot enabled. 

Turn off UEFI Secure boot. And make sure Windows fast start up is off.
Then in Boot-Repair, advanced options choose the install you want to keep and install/reinstall of grub to sda drive. It should offer both installs.

Then see if in UEFI boot menu, you can boot.

You may be able to just run the autofix.[B][SIZE=1]
[/SIZE][/B]
**[SIZE=1]       [/SIZE]**> [h=1][FONT=arial]**[SIZE=1]Suggested repair[/SIZE]**[/FONT][/h]   The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda7, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot 

  
 [h=1][FONT=arial][SIZE=1]Advice in case of suggested repair[/SIZE][/FONT][/h]   Please disable SecureBoot in the BIOS. Then try again.Do you want to continue? 



Whenever reinstalling always use the Something Else install option. Choose(change button) the existing install that you want to replace as new / (root) partition. If you have a separate /home partition, you need to choose that but must NOT check the format box, or else data will be erased. But always have good backups before any system change, both of Windows & Linux configuration & your data.

---

### Post by maxwellgisborne on 2017-08-01
it seems that i cant disable secure boot. In the UEFI settings the secure boot row is greyed out. I can see that it is enabled but I cant select it.
Is this something from the manufacturer?
EDIT: I put a pasword on the UEFI which alowed me to change it

---

### Post by maxwellgisborne on 2017-08-01
Iv done what you sugested, hear is the new log
[http://paste.ubuntu.com/25220997/](http://paste.ubuntu.com/25220997/)

I still have the same problem thoght. It just boots into windows and if i hit F12 there is only windows boot manager listed

---

### Post by oldfred on 2017-08-01
In your UEFI menu, do you not see & are able to boot the Ubuntu entry?
Line 1575 of report:
```
 BootOrder: 0000,0001,0002,2001,2002,2003
Boot0000* ubuntu	HD(2,GPT,9bb33374-5115-4f04-8a85-835bfe709df8,0xe1800,0x32000)/File(EFIubuntushimx64.efi) 




```

Some brands have unique requirements like Acer, and others need work arounds like HP, Sony and several others.

---

### Post by maxwellgisborne on 2017-08-01
I do not see it in the UEFI menu

---

### Post by oldfred on 2017-08-01
What brand, model system?

---

### Post by maxwellgisborne on 2017-08-03
I dont know how to progress

---

### Post by maxwellgisborne on 2017-08-03
acer n1501 is the modle number

---

### Post by oldfred on 2017-08-03
All Acer's have a unique requirement of setting "trust" on the .efi boot files. Then the entries you trust will be in menu.

You have to have Secure Boot on, add password in UEFI and from UEFI set trust.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

