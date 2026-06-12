---
title: "[SOLVED] VirtualBox 1.5.6 Critical Error Code-0x80070057"
date: 2008-03-24
forum: Virtualisation
---

### Post by Khalis7 on 2008-03-24
Hi erveryone...

I need someone who could assists me in solving my virtualbox 1.5.6 critical code. After some googling on this forum, I couldn't find any solution to my problem.
Here the critical error code goes:


A hard disk with UUID {ca2be21c-df9b-4c13-c986-56e6ba0c1a18} or with the same properties ('/home/khalis7/.VirtualBox/Machines/Windows XP SP2/Snapshots/{ca2be21c-df9b-4c13-c986-56e6ba0c1a18}.vdi') is already registered.


Result Code: 
0x80070057
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

I received this message when I took a snapshot of my Win XP SP2 machine and  because of  didn't know how to solve the error, I removed vitrualbox from my Gutsy machine. Hoping of reinstalling it back may disable the error code message it turn out that I was wrong.

BTW, the Win XP.vdi partition has been removed from my machine when I removed the virtualbox.

I need solution ASAP. Any opinions n suggestions are welcomed. If someone could point me to another thread containing similar problem, that would be helpful as well.

 Thanks in advance.

---

### Post by cuby on 2008-03-24
Hello.
you need to remove the config files in the virtual machines directory. Remove all hdd or images from the VB config and create a new virtual machine using the old xp.vdi that you have. Try to make the new virtual machine as similar as possible with the old one to prevent windows errors.

---

### Post by Khalis7 on 2008-03-24
> **cuby said:**
> Hello.
you need to remove the config files in the virtual machines directory. Remove all hdd or images from the VB config and create a new virtual machine using the old xp.vdi that you have. Try to make the new virtual machine as similar as possible with the old one to prevent windows errors.


Well, If that's the case, could you please tell me how shall I remove the config file. The old xp.vdi partition has been removed as what I mentioned earlier n has been emptied from my trash bin. Any way for me to restore the old partition?

BTW, all snapshots has been removed together with  the xp.vdi partition and actually, the problematic '/home/khalis7/.VirtualBox/Machines/Windows XP SP2/Snapshots/{ca2be21c-df9b-4c13-c986-56e6ba0c1a18}.vdi snapshot doesn't exists in the specified folder when I checked on them before I removed it. I wonder where exactly this troublesome snapshot was registered in my machine.:confused:

---

### Post by Khalis7 on 2008-03-24
Finally, I able to resolved my problem. What I did was removed completely virtualbox using synaptics, deleted .virtualbox file which is hidden in my Home folder and reinstall back tha virtualbox using .deb file I downloaded from virtualbox website. 

Thanks for supporting linux newbie like me although sometimes I find it rather difficult in solving problem in linux but I do enjoy to learn n use linux.Certainly, the learning curve is there for me and hopefully, I will master Linux as what I had did with XP.

All this while, my mind has been colonised by Gates's Microsoft OS until I couldn't see a way lot better, cost effective alternative OS. This certainly will attract more n more people to realise that Microsoft OS is not the ultimate OS for computing.

Thanks very much once again.

---

### Post by mkili on 2010-01-17
I know it's late, but in case someone is looking for answer here: This is a WRONG solution.

The correct one is to run this command:

VBoxManage internalcommands setvdiuuid /path/to/disk.vdi

---

### Post by gynonc on 2011-10-07
Thanks for the lead Mkili, but the syntax is slightly wrong.  Actually the command is:

VBoxManage internalcommands sethduuid /path/to/disk.vdi

I just finished correcting this problem on a windows xp host.  This is how I did it.

1. open a cmd terminal window (Start|Accessories|Command Prompt)
2. Navigate to your VirtualBox folder.  Most likely this is it:
C:\Program Files\Oracle\VirtualBox
3. Run the above command:

VBoxManage internalcommand sethduuid "C:\whateverpathtodiskyoucreated"

4. Open VirtualBox, select the virtual machine and select "Settings"
5. Delete the old hard drive 
6. select the hard drive you just rebuilt

Enjoy...


7. close settings box and start your virtual machine.

---

