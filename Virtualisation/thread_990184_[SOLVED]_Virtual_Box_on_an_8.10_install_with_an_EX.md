---
title: "[SOLVED] Virtual Box on an 8.10 install with an EXISTING version of XP"
date: 2008-11-22
forum: Virtualisation
---

### Post by wet_colored_arch on 2008-11-22
Trying to install Virtual Box on an 8.10 install with an EXISTING version of XP.  I have tried to methods with no luck 

Method 1:

I tried following Sand Lee's tutorial at 
[http://ubuntuforums.org/showthread.php?t=769883&highlight=virtualization](http://ubuntuforums.org/showthread.php?t=769883&highlight=virtualization)

but get an error opening the raw disk /media/sda , where VERR_FILE_NOT_FOUND the raw VMDK was not created when executing third line of code: VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register  (but I substituted /media/sda and -partitions 1 because this is where my windows ended up when I first installed Ubuntu)

Method 2:  

from Virtual Box gui I tried to follow instructions but don'e see how to configure for existing install.  It asks for a CD/DVD or floppy and there is no VDMK file with my windows as indicated from method 2

I am unsure but assume the creation of the vdmk file would allow me to use virtual box to get into media/sda1 where my windows is but I could be wrong and not clear why I can't create the vdmk file in the first place.

---

### Post by Sand Lee on 2008-11-22
> **wet_colored_arch said:**
> Trying to install Virtual Box on an 8.10 install with an EXISTING version of XP.  I have tried to methods with no luck 

Method 1:

I tried following Sand Lee's tutorial at 
[http://ubuntuforums.org/showthread.php?t=769883&highlight=virtualization](http://ubuntuforums.org/showthread.php?t=769883&highlight=virtualization)

but get an error opening the raw disk /media/sda , where VERR_FILE_NOT_FOUND the raw VMDK was not created when executing third line of code: VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register  (but I substituted /media/sda and -partitions 1 because this is where my windows ended up when I first installed Ubuntu)

Good news **wet_colored_arch**, I've posted an updated tutorial that should fix any problems users experience (limited to hardware). :guitar:

---

### Post by wet_colored_arch on 2008-11-24
thanks, I'll give it a try

is there anything I need to "undo" before restating the tutorial?

another thing,  from the links section I realized I had to change ownership of the folder to create the VDMK file and then have it found using virtual box -  I used CHOWN 666 sda* but this resets on boot;  would you expect this problem?  (I'll poke around and see if I can understand how to change this permanent - I am still a noob and not sure .)

do you want me to move future comments to your other thread?

---

### Post by Sand Lee on 2008-11-24
I'm not sure about using chown on a disk - it just doesn't look safe. But then again, I haven't seen anything on it so I may be wrong. My tutorial will add you to the disk group, so you shouldn't have to run that command.. This isn't a problem I would "expect" so I'm not sure if the tutorial will still work as - I don't believe - a 'chown'ed HD is very common situation.

As to where you should post, I think this thread is good since you could (hopefully) mark it as solved afterwards. :)

---

### Post by wet_colored_arch on 2008-11-24
in tutorial I am not clear on how to configure the menu.lst file

I see it says the following (but I am too noob to follow) - fp I leave alone or somehow identify windows as default?  

ALSO, is this the ISO disk I should put in drive when using Virtural Box?


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your syst

---

### Post by wet_colored_arch on 2008-11-24
1

---

### Post by Sand Lee on 2008-11-24
> **wet_colored_arch said:**
> in tutorial I am not clear on how to configure the menu.lst file

I see it says the following (but I am too noob to follow) - fp I leave alone or somehow identify windows as default?  

ALSO, is this the ISO disk I should put in drive when using Virtural Box?

There is a hyperlink on the word, "Configure" that leads to instructions on how to do so. I do not understand your last question, however it looks like the answer to it might be in Step 5.

---

### Post by wet_colored_arch on 2008-11-24
I'm getting the below.  I think I saw this mentioned in another link having to do with the permissions issue I cited above in this thread.




VM cannot start because the hard disk '/home/michael/.VirtualBox/WinXP.vmdk' is not accessible (VD: error opening image file '/home/michael/.VirtualBox/WinXP.vmdk' (VERR_ACCESS_DENIED)).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


following some of your posted links arrived at:  
[http://forums.virtualbox.org/viewtopic.php?t=333&highlight=createrawvmdk](http://forums.virtualbox.org/viewtopic.php?t=333&highlight=createrawvmdk)

Jun 07 note from kilou suggests (which I changed for my case):  
1) sudo su
2) umount /dev/sda1
3) chmod 666 /dev/sda1
5) chown michael:users /home/michael/.VirtualBox/WinXP.vmdk 

_this allows virtual box to proceed but then I get a _...........
GRUB loading stage 1.5

GRUB loading, please wait ...
Error 17

===========
I don't know why the chown is needed to progress and now need to look up Error 17 for ideas >> 

NEW INFORMATION:  got past the error 17 message (I had burned the ISO disk wrong and not mounted the drive.) but now when I select the XP boot option or let it time out and pick itself I get an:

"Error 15: File not found" (and when I hit key to continue it reverts to the os selection screen

so at current time have two problems:
1) Error 15
2) don't understand why I need chown 666

---

### Post by Sand Lee on 2008-11-24
From my experience, Error 15 comes from a badly configured menu.lst. Here are couple questions so I can help you and make the tutorial better...

[LIST=1]
[*]Are you sure you have your menu.lst (in the cd) configured correctly?
[LIST=1]
[*]If no, did you click on the Configure link?
[/LIST]
 
[*]Is there a "savedefault" option in your Windows entry of menu.lst?
[/LIST]

---

### Post by wet_colored_arch on 2008-11-25
Ran through whole process again.  I **still have error 15** but it did clear up the permissions issue requiring CHOWN but not sure why.

1)  Yes, I did click configure and believe I did it right.  (I used the # approach to set "default".)  However, there is an independent commented line in the list "### END DEBIAN AUTOMAGIC KERNELS LIST" ...  I wasn't sure if I should "count" or not when identifying the default.  

Also, not sure why it matters because when my grub.iso file it still gives me all my normal OS/Kernal choices.

2)  Yes, windows option has "savedefault" was listed under windows.  This is a bit confusing to me because the configure link says that the Ubuntu versions will have this (they did not or at least aren't visible) but not sure what XP should have by default.
 
see from configure link:  "Each entry that should be remembered must have the 'savedefault' keyword, this is the case for the normal Ubuntu entries, but not the recovery alternatives"


attached is edited menu.lst file . couln't seem to attach

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		8

..............edited center section
..............
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=cd3a853a-ef19-4dab-9b0a-807d9435ee33 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=cd3a853a-ef19-4dab-9b0a-807d9435ee33 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=cd3a853a-ef19-4dab-9b0a-807d9435ee33 ro quiet splash 
initrd		/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=cd3a853a-ef19-4dab-9b0a-807d9435ee33 ro  single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=cd3a853a-ef19-4dab-9b0a-807d9435ee33 ro quiet splash 
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=cd3a853a-ef19-4dab-9b0a-807d9435ee33 ro  single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by canabal on 2008-11-25
When you are half way through step 1 (of sand lee's tutorial) go to the copied grub.lst and delete the savedefault line, then continue with the rest.  That did it for me.

---

### Post by wet_colored_arch on 2008-11-25
deleting "savedefault" line in menu.lst seems to of worked -- I didn't put it there in the first place that I know of and thanks.  It turns out I do have poor performance, I assume I need to resize my memory and perhaps aggravated by this old machine I am using

thanks to all

---

### Post by Sand Lee on 2008-11-25
Glad to hear it works. It looks like I'll have to mention the removal of "savedefault" in the tutorial. Don't forget to mark this thread as solved btw! :)

---

