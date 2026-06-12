---
title: "HALP! Vista won't recognize my CD &amp; DVD Drive anymore!!!"
date: 2008-06-10
forum: Windows
---

### Post by Redrazor39 on 2008-06-10
There is no drive letter and no preview in My Computer for the CD/DVD drive anymore! It used to work just fine, but even when I pop in a CD it won't work!

This happened right after I put in a movie (Ice Age) into my drive but it wouldn't recognize it. Now, no matter how much I reboot, it won't be recognized!

I'm not sure if Ubuntu recognizes it yet, I might check later.


Please help! I don't want to have to send this computer in because
1) This is a replacement for a computer of the same model that I sent in and never got back until I got a replacement 3 months later

2) I think installing Ubuntu voids the warranty

3) I would just reinstall Windows over all of this but I don't know if I have the installation disc (Geek Squad... >:-o) and then I don't know if I'll be able to install CD-Key software again like Office 2007, Microsoft Student, and Supreme Commander (the game)

---

### Post by LaRoza on 2008-06-12
First, look at the simple solution, is it plugged in?

Open the case and look, there will be a data cable, probably an EIDE (ribbon) cable and another one with four wires coming out of it (molex). They should be attached to the motherboard (EIDE) and to the power supply (molex).

If they are plugged in, see if it is the drive itself. Try booting from a CD to see if that works. (Check the BIOS to see if the drive is detected if you can)

If that works, post back.

---

### Post by Redrazor39 on 2008-06-12
Actually, it's really weird. I put a game in the DVD drive and I can still open and close it and stuff, and it spins, but nothing will show up in My Computer (Computer in Vista). When I go into games explorer and click on the game shortcut, the game loads up just fine. It's just that it won't show up in Windows Explorer.

---

### Post by Redrazor39 on 2008-06-13
Ok. I'm trying to back up my iTunes library to disc but it just says "Disc burner or software not found".

I can't find my CD drive in Windows Explorer either.

This is horrible!

One thing that may be cause of the problem is that I have been disabling some services some speed up vista by some speed up guides in services.msc. I need to know which service controls this so I can reenable it.

---

### Post by fiddledd on 2008-06-14
I notice you mention ITunes, there is (was) a known conflict between Itunes and Vista which caused this. Check this thread:

[http://forums.cnet.com/5208-6142_102-0.html?forumID=133&threadID=267222&messageID=2602033](http://forums.cnet.com/5208-6142_102-0.html?forumID=133&threadID=267222&messageID=2602033)

---

### Post by Redrazor39 on 2008-06-14
yes, except I noticed the CD Drive as well as anything I plug into the USB drive is no longer recognized before I tried iTunes. Thanks for the help though... this is very interesting.

I guess I'm going to have to do a system restore (for the fifth time on this comp) to the oldest one and see if I can get it fixed.

BTW, if I do have to reinstall Windows (I would clean out my whole comp and put on Windows, then install Ubuntu later), I have the Geek Squad CDs that they made at Best Buy, but since this computer came with Windows Vista, that's all I have. Would I be able to reinstall with those?

Also, if I did reinstall Vista, would I be able to reinstall software that is CD-Key licensed like Microsoft Office 2007, Microsoft Student 2007, and a PC Game (Supreme Commander)?

Thank you for all your help but please answer these questions. I don't want to have to repurchase all of this software. That'll be another few hundred down the drain just because Microsoft didn't code Windows very well.

---

### Post by LaRoza on 2008-06-14
> **Redrazor39 said:**
> 
BTW, if I do have to reinstall Windows (I would clean out my whole comp and put on Windows, then install Ubuntu later), I have the Geek Squad CDs that they made at Best Buy, but since this computer came with Windows Vista, that's all I have. Would I be able to reinstall with those?

Also, if I did reinstall Vista, would I be able to reinstall software that is CD-Key licensed like Microsoft Office 2007, Microsoft Student 2007, and a PC Game (Supreme Commander)?


A complete system restore will wipe the entire disk, so you'd have to reinstall Ubuntu.

It will be a pain to do, but you can call them and get a new key for them.

---

### Post by Redrazor39 on 2008-06-14
I just ran the system restore with the restore points and idk if Ubuntu's gone, but idc, I can just reinstall. I don't have anything that important on it.

After running the system restore, I'm still experiencing the same problem. I'm gonna boot into Ubuntu with the game CD in the drive to see if that recognizes it. Then I'll know if this is a software or hardware problem. I'm hoping this is a problem with Windows so I don't have to take it back to those Geek Squad ppl... [shudders]

LaRoza, who can I get a new key from and for what?

Also, my other questions in my earlier post...?

---

### Post by LaRoza on 2008-06-14
> **Redrazor39 said:**
> I just ran the system restore with the restore points and idk if Ubuntu's gone, but idc, I can just reinstall. I don't have anything that important on it.

LaRoza, who can I get a new key from and for what?


Do you mean restoring from restore points or the disks? Restoring from a restore point only affects Windows. Doing a full restore will wipe the entire disk.

You can call whoever made the software (Microsoft for Office for instance) and get a new key if you need to.

---

### Post by Redrazor39 on 2008-06-14
I restored from restore points.

Also, what makes you think MS will be happy to give me a new key if I just call them up and tell them I have office? How in the world does that work? Why would they even have CD Keys if they let that happen?

---

### Post by Redrazor39 on 2008-06-14
ok. I've booted into Ubuntu and it recognizes the CD just fine. It must be a problem with Vista.

I think I know the cause of the problem. I've installed and uninstalled CD rippers, converters, and burners over and over again and I think that corrupted some part of the registry by adding a ton of obsolete filters.

Dang, Windows sucks.

Once I get a definite answer about the CD-key question I'll know if I'm gonna reinstall my comp or not.

---

### Post by wolfen69 on 2008-06-16
do windows key-r, then type sfc /scannow

this will check the integrity of your windows files and automatically repair them.

---

### Post by Redrazor39 on 2008-06-16
well, I did that, and the command prompt just flashed on and went away. Nothing appeared on the command prompt for the split second I saw it.

---

### Post by LaRoza on 2008-06-16
> **Redrazor39 said:**
> well, I did that, and the command prompt just flashed on and went away. Nothing appeared on the command prompt for the split second I saw it.

Run it from the terminal, not from the "Run" dialog.

Open a terminal, (Open the start menu and type in "cmd" and press enter)

---

