---
title: "Remove Rootkit from SD card"
date: 2011-11-04
forum: Security
---

### Post by yc2 on 2011-11-04
I apologize if my post is maybe not the essence of this forum, but I know many members have good ideas and I hope someone can help.

A friend wanted help with her dig cam. "The pictures are OK in the cam but cannot be copied to disc" - She uses Win XP.

I plugged the dig cam USB chord into a Win7 starter laptop and Avast immediately showed an alarm "Rootkit". Camera got disconnected from Win7.

I got Ubuntu v.11.04 on a USB stick. I run it as it is without antivirus. I am thinking of plugging the camera into that system, but I am not sure I dare.

How should I access the pictures on the SD card and later format the SD card.

Thanks.

---

### Post by Dangertux on 2011-11-04
The safest course of action would be to format the entire thing pictures included. That being said, due to the fact pictures tend to be people's cherished personal memories it may not necessarily be the best course of action in this case.

My recommendation is as follows for removal.

I would virtualize a Windows sytems (preferably 7, XP will do if it's all you have) with a decent AV, Avast! or AVG should work fine. Make sure this AV also detects the "rootkit" to rule out false positives. 

Then scan each of the images individually to make sure they are not the source of the compromise. Once you are sure that the image files themselves are fine, I would rehome them to the Ubuntu host. At this point format the SD Card in the camera (formatting them in Ubuntu can cause issues). Once the card is formatted rescan the card to make sure the "root kit" is no longer found, you may wish to use multiple AV applications for this.

Optionally, if you want the pictures back on the card, you can use the virtualized guest system to place them back on the card. Once again , scan the card to make sure there is no anomalous activity.

Return the card with pictures to your friend, and destroy the Virtual Machine.

If in fact it is a rootkit you may wish to also perform an in depth scan of your friend's Windows machine. 

I realize this probably isn't the most cost effective solution, unfortunately if you actually want to preserve the data you don't have a lot of "safe" options.

Hope this helps.

---

### Post by yc2 on 2011-11-04
Thank you Dangertux. Absolutely 100% logical advice.

I always considered virtualization a "hype". Now I realize I was wrong and need it badly ;)

If no other idea comes up I must virtualize. I must also turn off AV in the virtual machine to make it accept the SD-card.

I only run Ubuntu from a USB-stick on this latptop, since changing partition table means that W7 restore will not work :(

I know too little about virtualization. Sorry for GIYF-questions:
1. Can I virtualize XP or w7 from an Ubuntu USB-stick
2. Which is the simplest virtualization engine? Is there a good and simple guide available? I think I can get at least XP-image free from the internet?

I really hope there is a simpler solution, but I guess there is not?

---

### Post by sanderd17 on 2011-11-04
The easiest virtualisation software is Virtualbox (dowload the one from the oracle site to have USB support).

You can run the entire thing inside a live environment, but Virtualbox is a heavy program, and if it has to load a heavy OS inside it, you really need a good computer.

The best thing for you would probably be to do a Wubi install of Ubuntu first (Wubi installations don't change partitions). Make sure you give enough space to the installation (you will have to install Windows inside that, and Windows will easily take up 20 GB).

---

### Post by yc2 on 2011-11-04
All advice good and logical here. Thank you. I am sure running Win inside Ubuntu inside Win would work!

One more problem is finding a Win image for Virtuabox. I am on a trip and have W7 in a recently bought laptop. My XP/Vista laptops are not available.

Thanks for good advice. If someone comes up with another solution than virtualization, please present it.

Taking the screwdriver and disconnect the HDD of my laptop and run Ubuntu from a stick??????????? (Where did the write protect buttons go? They were available on the HDDs in the 80's ;) ) Or can even BIOS be affected?

If I knew it was a Windows specific rootkit I could connect the camera to Ubuntu, but it does not feel good.

Thanks.

---

### Post by gradinaruvasile on 2011-11-04
I used many infected usb sticks on my Ubuntu and later Debian laptop and nothing happened. All malware was Windows specific. Some didnt even show up in Windows.
I have never seen an infected jpg or any other image format (not referring to PDFs).
Rootkits are very OS specific they wont work on other OSes. If that was really a rootkit (may be false positive you know).

Id say you can safely plug the card in a Linux based system (disable any autorun on it, that really should be common sense), copy the images and format it or just remove the infected files - they 99% of the time are autorun.inf+some folder that contains executable files (exe or other executable extensions such as screensavers).

If you really think that the pictures contain malware (very unlikely) you can load them in an application in Ubuntu and re-save them under another name.
BTW you should have looked up the rootkit's name Avast said it was - some are very well documented on the net and give you a picture of what to look for.

---

### Post by OpSecShellshock on 2011-11-04
I'm taking it that the camera's USB cable is being used to transfer the images rather than just putting the SD card into the laptop, yes? If so, there's an opportunity to possibly isolate the issue to that card: buy another SD card (they're inexpensive now, especially since you only need minimal capacity), format in the camera to be sure it's clean, shoot some photos, then try to transfer those and see what happens.

Another thing to keep in mind: what we seem to know so far is that on your friend's XP machine it just won't copy the files, whereas on your Win7 machine you get rootkit warnings and can't mount the disk. Is this the case? I ask because you may be dealing with 2 separate issues here.

---

### Post by sanderd17 on 2011-11-04
Wubi is not the same as running Ubuntu inside windows. It's just a hack that uses a file as virtual hdd, so when you launch a wubi installation, it won't run any windows code. 

This way, when you connect your infected drive to a running wubi, nothing will happen since the virus is not made for Linux. If you afterwards let it connect to your virtual disposable windows installation, it will probably infect windows, but windows can't access your hdd.  So if you scan your disk until everything is clear, it can't cause problems.

---

### Post by yc2 on 2011-11-04
Thanks, helpful hints.

I read the Avast log more carefully now. The virus is called
[COLOR="Red"]**SafeDrvll.exe**[/COLOR]

I don't know why the cam was not accessible after Avast wrote "virus moved to chest". Maybe I should try to connect the cam again with my Ubuntu-LiveCD-USB stick? (Or even my W7-Avast)

I started to read about disabling autorun for usb. (nautilus autorun, gconfeditor etc) But I think all autorun puts up a prompt before running so you can deny it there?
(I just put the link here for reference: [http://ubuntuforums.org/showthread.php?t=974087](http://ubuntuforums.org/showthread.php?t=974087))

I ran through camera usb. I did not run card-reader.
Good idea to try to separate SD card and camera internal memory as location for virus.
My friend is not here now and is not very computer savvy. "pictures could not be copied" could mean anything, sorry.

Thanks a lot everyone. Will probably try to connect it again to Ubuntu-LiveCD-USB stick. I have no idea if drivers etc will work.

---

### Post by Dangertux on 2011-11-04
This might be helpful

[http://www.securelist.com/en/descriptions/15239246/Trojan-Downloader.Win32.Genome.ayqz?print_mode=1](http://www.securelist.com/en/descriptions/15239246/Trojan-Downloader.Win32.Genome.ayqz?print_mode=1)

---

### Post by yc2 on 2011-11-05
Thanks, I will be back when my friend brings the camera next time.

---

### Post by yc2 on 2011-11-07
Just to tell how it ended.

My friend brought back the camera. We connected it to W7 again. Avast gave no virus-alert (Avast probably removed the virus last time), but we cold not see the pictures. The camera USB only opened with one folder called DATABASE containing two files (rather small) called ACE.DAT ACE.LOG

**We then connected it to Ubuntu which read the pictures perfectly!**

My friend is happy to have the pictures on an external medium now. But I still think there is something fishy with the camera-SD since it didn't open in Win7.

I suggested her to make backup of pics and format SD-card with internal camera menu operations. Just a wild guess.

We are not here to solve Windows problems, but I still wonder why the camera did not open properly via USB to Win.

---

