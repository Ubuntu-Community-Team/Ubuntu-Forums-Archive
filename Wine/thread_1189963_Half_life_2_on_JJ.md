---
title: "Half life 2 on JJ"
date: 2009-06-17
forum: Wine
---

### Post by VoltRabbit on 2009-06-17
Hi all,

I've just built my first dedicated Ubuntu box. I pieced it together with slightly older but still relevant hardware, total cost = $10 Yay! 

AMD 3500+ socket 939, 40gb sata hd, dvdrw/cdrw, 2gb RAM , pci-e Nvidia 8400GS... Ubuntu 9.04 and Wine installed 

I have been having fun with compiz and desktop effects, but now its time to step it up a bit. I have the 5 disc Half Life 2 (includes counterstike source) and want to play it on Ubuntu. First off, I have searched google and the forums, and even youtube.  I see success stories and bits of info here and there, but all of it concerns previous Ubuntu versions and Orange Box.  

I'd like to have a more updated set of instructions to get this going.  Do I need to install DX9 or 10 if I already have Wine installed? What is the proper method to copy the game files from the various discs, and where exactly should they get copied to? I have a Steam account, should this be part of the plan? I have so many questions, and though I have yet to get very familiar with Terminal, I have learned to be a copy and paste ninja.  

I have successfully installed Serious Sam to run in Wine, but that was a cake walk, its just a single CD.

Any help at all is of course much appreciated!  If I get this down, I intend on making a how-to video to share with the interwebs.

---

### Post by Bachstelze on 2009-06-17
Moved to the WINE section.

---

### Post by VoltRabbit on 2009-06-17
Ok, now that the post is in the right spot... help?

---

### Post by u235sentinel on 2009-06-17
> **VoltRabbit said:**
> Hi all,

I've just built my first dedicated Ubuntu box. I pieced it together with slightly older but still relevant hardware, total cost = $10 Yay! 

AMD 3500+ socket 939, 40gb sata hd, dvdrw/cdrw, 2gb RAM , pci-e Nvidia 8400GS... Ubuntu 9.04 and Wine installed 

I have been having fun with compiz and desktop effects, but now its time to step it up a bit. I have the 5 disc Half Life 2 (includes counterstike source) and want to play it on Ubuntu. First off, I have searched google and the forums, and even youtube.  I see success stories and bits of info here and there, but all of it concerns previous Ubuntu versions and Orange Box.  

I'd like to have a more updated set of instructions to get this going.  Do I need to install DX9 or 10 if I already have Wine installed? What is the proper method to copy the game files from the various discs, and where exactly should they get copied to? I have a Steam account, should this be part of the plan? I have so many questions, and though I have yet to get very familiar with Terminal, I have learned to be a copy and paste ninja.  

I have successfully installed Serious Sam to run in Wine, but that was a cake walk, its just a single CD.

Any help at all is of course much appreciated!  If I get this down, I intend on making a how-to video to share with the interwebs.

To get it working I had to (originally) make iso images and mounting them as the software requested.  Since then I just do a steam install across the internet.  It takes more time but you might as well since they have released a bunch of changes since the Orange box came out.

---

### Post by lightstream on 2009-06-17
Make sure you have the latest version of Wine, then try to install from CD. You may well fine it works swimmingly - I have installed other games directly from CD with no issues at all. See the sticky in the Wine forum for how to get the latest version of Wine.

---

### Post by VoltRabbit on 2009-06-17
ok,

Ill try installing, and loading from Wine first.  This install is only a week or two old so it should be the latest version of wine.

I'd like some more info on creating an ISO from 5 disks in case that does not work, I hear the term "mounting" a lot when reading about ubuntu, but what that is exactly I have yet to learn. Right now "mounting" software sounds like alpha male behaviour.

---

### Post by VoltRabbit on 2009-06-17
> **lightstream said:**
> Make sure you have the latest version of Wine, then try to install from CD. You may well fine it works swimmingly - I have installed other games directly from CD with no issues at all. See the sticky in the Wine forum for how to get the latest version of Wine.

The disk drive won't open to let me install the second disc, the application using it wont allow the software to be "unmounted"

I get a small variety of errors when I try to eject it.

---

### Post by NightMKoder on 2009-06-17
You need to use the `wine eject` to eject it. A weird feature of wine installs.

---

### Post by VoltRabbit on 2009-06-17
> **NightMKoder said:**
> You need to use the `wine eject` to eject it. A weird feature of wine installs.

negative ghost rider. this is the error I receive when I try to eject from wine: DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by NightMKoder on 2009-06-17
[http://ubuntuforums.org/showthread.php?p=7298991](http://ubuntuforums.org/showthread.php?p=7298991)

---

### Post by VoltRabbit on 2009-06-18
> **NightMKoder said:**
> [http://ubuntuforums.org/showthread.php?p=7298991](http://ubuntuforums.org/showthread.php?p=7298991)

I thank you, even though I didn't get to try this. 

For anyone else reading I'll round this thread out.

I went ahead and just installed Steam under Wine. I did not have to install any fonts, I didn't really have to do anything at all.

I opened Wine went to the steam site and hit download, after that was done I download/installed HL2 from my steam account. After the download was finished I launched the game and it was realllly slow, but it worked. I rebooted and that helped a bit, and then turned the settings down a bit to improve the frame rates.  The hardware Im running should run the game faster than it is right now, but the point is that it is working. No terminal, no fonts, nothing but pointing and clicking.

Thanks for all your input!!!!!!:popcorn:

---

### Post by Duskao on 2009-06-19
Did you install wine from the Ubuntu repository? If so then you likely have wine 1.0.1 (if I remember correctly). The newest at this point is 1.1.23. Somewhere between the time of 1.0.1 and 1.1.23 the put in so that you can change disc's during installations. 
However, the easiest way to install HL2 is to download the steam client and install it, then download it through steam. Steam works quite well with wine, there are a couple issues with it, but nothing too bad. 
Anyway, it will act the same as with a windows version of steam, just go into your account and you games list then choose half life 2 and install it, or any of the other games in your games list. There are a couple tweaks to getting it to work best, but you can find those at the winehq.org appdb. 
Have fun.

---

