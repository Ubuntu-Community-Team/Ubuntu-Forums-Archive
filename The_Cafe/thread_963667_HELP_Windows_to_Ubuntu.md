---
title: "HELP Windows to Ubuntu"
date: 2008-10-30
forum: The Cafe
---

### Post by AaronsDarts on 2008-10-30
Hello im new to ubuntu. i origianly used windows vista and i really hated it. ill give you a little info on whats going on. 

Ok my windows vista kept crashing like 12 times in say 15-20 min. just about every time i logged on. then it just stoped fully booting i was able to create a backup disc and then reformated like 3-4 times and that didn't work so i contacted HP since its a HP and there taking my comp and repairing it currently i would like to know if im able to open the back up disc it uses a .exe which will not open and a .fbw file which will not open.

Long story short i have alot of important info on that disc and would like to be able to open it and start using ubuntu as the main OS because i hear alot about it. So could some one please help me with this.  PS vista is the worst os ever made.

---

### Post by vikramaditya on 2008-10-30
Don't have any solutions to your dilemma, but you'll get mo' better answers in the Absolute Beginners forum.

---

### Post by Bölvaður on 2008-10-30
What you need to do is:

1. save all your data onto a backup disk.. like a portable hdd or usbkey. SAVE ALL DATA, your data is most important of all.
2. download and burn ubuntu 8.10
3. insert the cd in the cd drive and boot up, make sure all hardware will work (wireless and some graphical cards are not supported on first boot)
4. Partition your hard disk drive * (see below for options), when you know what you want and when you know ubuntu will work
5. boot up the live cd again (the one you burned) and install (according to the partitions you made before)


* When you partition make sure what you know what you are doing. If you want to have both windows and ubuntu then you should dual boot. You can do that by making 1 NTFS partition for windows and then have 1 ext3 and 1 swap partition.
_Look up on google and these forums for help, these forums are your best friend._
It is recommended to use partition in windows when you deal with NTFS and please defrag if you can.
If you do not need windows, then this will be very easy.. just install and dont worry about parititons.

---

### Post by HittingSmoke on 2008-10-30
> **AaronsDarts said:**
> Hello im new to ubuntu. i origianly used windows vista and i really hated it. ill give you a little info on whats going on. 

Ok my windows vista kept crashing like 12 times in say 15-20 min. just about every time i logged on. then it just stoped fully booting i was able to create a backup disc and then reformated like 3-4 times and that didn't work so i contacted HP since its a HP and there taking my comp and repairing it currently i would like to know if im able to open the back up disc it uses a .exe which will not open and a .fbw file which will not open.

Long story short i have alot of important info on that disc and would like to be able to open it and start using ubuntu as the main OS because i hear alot about it. So could some one please help me with this.  PS vista is the worst os ever made.

Sounds like your backup is some sort of self extracting archive. You may be able to open it in WINE, maybe not. There may be some way to convert it to a ZIP archive that you can open in Ubuntu also.

---

### Post by Bölvaður on 2008-10-30
> **HittingSmoke said:**
> Sounds like your backup is some sort of self extracting archive. You may be able to open it in WINE, maybe not. There may be some way to convert it to a ZIP archive that you can open in Ubuntu also.

If I understand correctly he hasnt installed ubuntu yet.
I'd say try it on a different computer that runs windows and save the data onto a portable disk, but not as .exe or other junk.. only plain normal files.

Then when you have installed ubuntu you can connect the portable disk to your computer and move all your personal data onto it :)

---

### Post by AaronsDarts on 2008-10-30
Ok let me shed some more light onto this..

My desktop i was duel booting Windows and ubuntu. i rarley used ubuntu since i already had all my stuff on the vista side. my little brother dealeted his OS and tushiba wanted him to pay like $100 for a new recovery disc so i put ubuntu on his laptop and now im trying to get my backup disc and the info off of it to load on the ubuntu system since my desktop is in the shop and since its coming back as a fresh system and no info on it i was gana delete vista off of it and load ubuntu on the hole thing.

so im trying to load it off and wine isn't loading either file and i can't find anything on the internet about a fbw file and opening it in ubuntu.

---

### Post by Bölvaður on 2008-10-30
when you said he deleted his OS, are you saying there is nothing left on the computer (then you need a data recovery disk that you can boot off from which undeletes info).

Or do you still have the windows partition will all the data still on?
Then you only need to boot up ubuntu and drag and drop the info to ubuntu partition, like /home


please explain further and perhaps make it as a list or a drawing to make it very clear how the status is.

---

### Post by AaronsDarts on 2008-10-30
no the laptop has a OS on it now when i got it it didn't have anything on it. so i ordered the ubuntu Os because my friend told me about it. now im am fully new to ubuntu and so far im really liking it i just need to know how to open a fbw file in ubuntu since wine isn't opening it.

---

### Post by Bölvaður on 2008-10-30
ok this is only a rescue plan to save data then :KS

From a quick google search ("fbw file") I found this:


> The HP System Recovery utility creates backup files of the form backup.####.fbw where #### is a series of numbers starting at 001 and increasing. In some versions there appears to be a bug in the naming process and #### goes from 009 to 010. It should go to 0010. Each number should have two zeros in front of it. If you encounter this bug, rename backup.010.fbw to backup.0010.fbw and add a leading to zero to all subsequent numbered files. Run the EXE file in the directory with the backup and it should then restore properly


> I found the solution! If you read the small print on the recovery disk instructions, you are supposed to back up your data on a CD or DVD. I didn't read this and backed mine up on an external hard drive. Bad move. I wasn't able to restore my files.

Now I have the fix. First, copy EACH of the files onto its own DVD. (don't try to fit 2 onto a DL dvd--it won't work--I tried that). Copying these huge backup files (~3.5GB each)is very time-consuming, but it's the only way to get your files restored. So now you have one disk for each of the files in your backup folder (I had nine disks-my files ranged from backup.001.fbw to .009)

Next, reboot your computer in Safe Mode (continually click on the f8 key until the menu appears so you can make that selection as your computer is rebooting). Once Windows has started in Safe Mode, put in the DVD containing the first file--the one called backup.001.exe. Open "my computer" and double click on the file to start it. The recovery manager panel appears, and your DVD is ejected. You're then asked to put in your last disk. (mine was backup.009.fbw. Yours may be different.) The "NEXT" button on the recovery manager panel will activate. Click it, and you're on your way! You'll be prompted for each of your disks in descending order.

I spent about 6 hours total with HP support, and no one was able to help me. I figured this out on my own, I hope it works for you!

This is some sort of file made in Vista, that is kind of unreadable. This seems like a very popular bug in vista.

So you need to have access to Vista I think. Perhaps through a virtual machine and then run the exe files. I think you need to do some digging of your own while you are solving this puzzle.

---

### Post by AaronsDarts on 2008-10-30
am i able to get a vista vertual machine on a laptop lol and if so do you know where i should go.

---

