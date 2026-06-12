---
title: "Vmware Ctrl Alt keys"
date: 2008-03-27
forum: Virtualisation
---

### Post by evilc on 2008-03-27
Have installed Vmware Server and tried Hardy in virtual, works OK. I tried using ctrl alt key combo (for the mouse) but nothing happens? On the bottom of the screen it says vm tools not installed, I can't do that because  I am unable to get the mouse out of screen.
How can I fix this?

tia

---

### Post by fjgaude on 2008-03-27
Can you click on VM/Install VMware Tools menu item?

Let us know how you are doing.

---

### Post by evilc on 2008-03-27
> **fjgaude said:**
> Can you click on VM/Install VMware Tools menu item?

Let us know how you are doing.

Install vmware tools is under VM as previously said,  I can't get out of display screen to click on it and key combo don't work.

---

### Post by fjgaude on 2008-03-27
When you say "display screen" you mean the host?

I've never heard of anything like this before. If you power donw vmware, then come back up without opening up the guest OS, can't you use some option, in Preferences, etc., that are there in vmware?

---

### Post by evilc on 2008-03-27
> **fjgaude said:**
> When you say "display screen" you mean the host?

I've never heard of anything like this before. If you power donw vmware, then come back up without opening up the guest OS, can't you use some option, in Preferences, etc., that are there in vmware?

If I just open vmware (no guest) I can use the pref's etc except the VM drop down, that is all greyed out and that's the one with the install tools is. 
From what I can gather after installing the guest I should be able to ctrl alt to get the mouse out of the guest screen then I should be able to open VM tab and install the tools, I then should be able to use either VM guest or my normal desktop. This is what I an trying to do sorry if I did not explain myself clearly.

---

### Post by fjgaude on 2008-03-27
I think I understand now but I don't have any suggestions for you to try, other than delete the vm and re-install Windows. The console seems to be okay, it's just the vm seems to have not taken the imulator of the mouse.

Maybe someone here has seen this problem and can help. Good luck.

---

### Post by evilc on 2008-03-28
> **fjgaude said:**
> I think I understand now but I don't have any suggestions for you to try, other than delete the vm and re-install Windows. The console seems to be okay, it's just the vm seems to have not taken the imulator of the mouse.

Maybe someone here has seen this problem and can help. Good luck.

Thanks but after working with computers for over 30 years  in my own business and originally started with unix,  I don't use MS Windows Linux is much better.:)

---

### Post by popch on 2008-03-29
> **evilc said:**
> Install vmware tools is under VM as previously said,  I can't get out of display screen to click on it and key combo don't work.

Your mouse appears to be in 'captured' mode, i.e. in use by the virtual machine. To 'uncapture' the mouse you need to press the key assigned to that task.

If I remember rightly, the default key for that task is the ***control*** key on the ***left*** hand side of your keyboard.

---

### Post by fjgaude on 2008-03-29
As I understand his situation, his mouse in out of the VM and can't get in. Thus he cannot install Tools.

The default key to get mouse in and out before installing Tools is Ctrl-Alt for VMware Server.

Maybe he could go into Edit/Preferences/Input/HotHeys and fix it that way.

---

### Post by popch on 2008-03-29
> **fjgaude said:**
> As I understand his situation, his mouse in out of the VM and can't get in. Thus he cannot install Tools.

The default key to get mouse in and out before installing Tools is Ctrl-Alt for VMware Server.

Maybe he could go into Edit/Preferences/Input/HotHeys and fix it that way.

Ah, I must have misread the OP. Sorry for the confusion. Fixing the preferences for the HotKeys sounds like a good idea to me.

---

### Post by upthelum on 2008-03-29
Depends on the OS as with windows you can just click and install but sometimes you may have to run a command to start vmware tools every time you boot a linux image. You should also have an option to run vmware tools at vm startup and yes ctl+alt should release the cursor.

---

### Post by evilc on 2008-03-29
> **popch said:**
> Ah, I must have misread the OP. Sorry for the confusion. Fixing the preferences for the HotKeys sounds like a good idea to me.


Bingo! It was the hotkeys what is happening is, for some reason ctrl alt and any other 2 combo from prefs is not accepted? I set it for just alt key and it released from vm. To go back into vm I use right arrow (haven't set vmtools in yet), at least I can get in and out now, so will make a new virtual and see if I can find what's causing the conflict.

Thanks all,

---

### Post by fjgaude on 2008-03-29
Wonderful, evilc, it's so good when we can find what is holding us up, eh?

Keep us informed as to how you are doing.

---

### Post by evilc on 2008-03-31
UPDATE:

OK, I ran Hardy-Beta (livecd) ISO via create new vm and after loading managed to get mouse in/out of vm screen using Alt only (out) and right arrow key (for back in). When out of vm it tells me vmtools not installed if I try to install them nothing happens although the cdrom icon in vm flashes, would this be because I have only connected using the ISO?
Which would lead me to another question, how to install a livecd. I had a quick look at installing (from the boot screen) and it wanted to install to sda1 my main HD. I want to use my 2nd HD that's where my vmx fliles are kept. I cancelled at that point, don't want to stuff up my OS drive.

---

### Post by fjgaude on 2008-03-31
The Tools are not of the LiveCD that you use to install. If memory serving they come from the Internet and is done while your in the guest VM.

The install of the guest only sees the partition that was declared when you started to make the VM of Hardy Beta.

I tell you you will have issues with that Beta... Gutsy would have been a better choice, but that was up to you and your reasons.

---

### Post by evilc on 2008-03-31
> **fjgaude said:**
> The Tools are not of the LiveCD that you use to install. If memory serving they come from the Internet and is done while your in the guest VM.

The install of the guest only sees the partition that was declared when you started to make the VM of Hardy Beta.

I tell you you will have issues with that Beta... Gutsy would have been a better choice, but that was up to you and your reasons.

Thanks, I only used Hardy for testing the mouse problem (also tried Fedora live, same results). My OS is Gutsy so no point in using that.

---

