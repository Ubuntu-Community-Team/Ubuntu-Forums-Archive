---
title: "Problem with virtual box."
date: 2011-03-06
forum: Virtualisation
---

### Post by abnordude on 2011-03-06
I used my virtualbox to install windows Xp for downloading a large file through the use of IDM.
It is an iso image that I need to burn it to a disk. But when I insert a blank disc, windows doesn't read it [linux does].
So, is there any way to move the downloaded iso into linux. Please help me.

---

### Post by howefield on 2011-03-06
I don't think you have write access to optical drives in VirtualBox, as you have found out.

You can copy the iso to Ubuntu via a pen drive or setup a shared folder(s).

Go to your VM settings > Shared folders and select the folder you wish to share and check mark automount. You can then see your share in XP > Windows Explorer > Network folders

---

### Post by abnordude on 2011-03-06
> **howefield said:**
> I don't think you have write access to optical drives in VirtualBox, as you have found out.

You can copy the iso to Ubuntu via a pen drive or setup a shared folder(s).

Go to your VM settings > Shared folders and select the folder you wish to share and check mark automount. You can then see your share in XP > Windows Explorer > Network folders


I did like the way you said [except for the check marking the automount, becoz I didnt find it there].
Then I logged into windows & went to network folder. I didnt find it there. [I shared my home folder itself].

---

### Post by howefield on 2011-03-06
> **abnordude said:**
> I did like the way you said [except for the check marking the automount, becoz I didnt find it there].
Then I logged into windows & went to network folder. I didnt find it there. [I shared my home folder itself].

Then you'll need to mount the shared folder manually. I can't remember the command for that having become used to doing it by using the automount option.

Let me get you a screenshot in case you are just missing it.

---

### Post by abnordude on 2011-03-06
I think I found a hint but I dunno how to use it.
Tis' written o're there
For linux use "mount -t vboxsf...."
Do you know anything about that?

---

### Post by howefield on 2011-03-06
Which version of virtualbox are you using ?

Here's the screenshot of the automount option, this is from the current version 4.04 with the extension pack installed..

---

### Post by abnordude on 2011-03-06
Also, I tried the usb part that you told me.
It is also not read.

---

### Post by abnordude on 2011-03-06
> **howefield said:**
> Which version of virtualbox are you using ?

Here's the screenshot of the automount option, this is from the current version 4.04 with the extension pack installed..

I'm using VirtualBox OSE.

---

### Post by howefield on 2011-03-06
> **abnordude said:**
> I'm using VirtualBox OSE.

OK, in that case you won't have access to USB or shared folders. Only the PUEL version can do that.

For info, recent versions are no longer called OSE or PUEL, there is one version to which you can add the extension pack which includes closed source code giving the ability to use USB devices, shared folders and other such goodies.

How about setting your network adapter to bridged. This will allow the host and guest to communicate as if they were separate machines on the same LAN.

---

### Post by abnordude on 2011-03-06
> **howefield said:**
> 
How about setting your network adapter to bridged. This will allow the host and guest to communicate as if they were separate machines on the same LAN.

i did that to bridge.
Now how can I access it in windows.
Also, could you try checking the
"mount -t vboxsf.." part.

---

### Post by abnordude on 2011-03-06
I installed oracle VM Virtualbox 
I also did the folder sharing option and did auto mount
But in xp's network places. I couldnt find anything

---

### Post by howefield on 2011-03-06
Try rebooting your VM and when you click on Network in Windows Explorer, press F5 to refresh.

---

### Post by abnordude on 2011-03-06
Hey, thnx, it worked.

---

