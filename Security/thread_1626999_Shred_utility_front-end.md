---
title: "Shred utility front-end"
date: 2010-11-20
forum: Security
---

### Post by thotheolh on 2010-11-20
Hi. I thought of starting a project for a shred utility front-end for Gnome that uses the  'shred' command in linux and have created a rough image design of the front-end but  I am not familiar with programming for Linux or Ubuntu so if anyone's  interested in this project, could you just PM me.

I have attached a mockup PNG image. There are two buttons in the image, besides the 'Select File / Folder' textbox. The button on the left is for selecting files or folders. The button on the right is to select the trash bin to be cleanly shredded and emptied.

---

### Post by Andrew.Z on 2010-11-21
How is it better than existing applications such as BleachBit (which can shred arbitrary files through the File menu)?  Also, I suggest taking off the option for [multiple passes because they don't help](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk).

---

### Post by thotheolh on 2010-11-21
I think shred is integrated into most cores of linux by default. Having an esoteric command line without a front-end makes shred a waste. I think giving it a GUI would make it useful.

I have once tried Bleachbit as you said, but somehow my Bleachbit, after I let it start.... it's progress just got stuck at the same place for half an hour or so while trying to clear some temp cache before it could proceed to do anything like wiping out specified folders. It's an interesting tool but I never got it I guess. I couldn't understand why it took so long just to wipe a couple of files in temp folder that aren't really so big, so I had to abort it and manually use 'shred' command which prove to be faster somehow (but tedious without an automation of GUI). I tried it a few times and I just simply uninstalled it since it's behaviours are hard to predict and the options at the side can be intimidating. You have no idea what it meant for certain files to be selected for wiping (there is no hint) and the user (who are not computer experts) would hesitate to select applications like '.DS_Store' for wiping.

I was wondering that it would be nice if some kind of integrated front-end can be made in combination of the 'shred' command. I would like to see my proposed shredder as a more simple and less complicated and integrated (with 'shred' command) front-end while Bleachbit is the heavy use utility.

The amount of passes depends on the users. If they want as many, they would have their own choices. If they want 1 pass, they can specify 1 pass, if they want 10 passes, they can have 10. If's simply there for them to manipulate what they want to do and allow them flexibility. 

I noticed it would be useful if Bleachbit would have a progress status for each process it is doing besides an overall progress bar, and to display current status in a more friendly way (that is the reason I decided to uninstall Bleachbit... because I have no idea what was holding the wipe at a particular process for more than half an hour) to use and to understand.

If there are people who show interest with this project, it could continue.

---

### Post by cariboo on 2010-11-21
Have a look at [Quickly]("https://wiki.ubuntu.com/Quickly"), it should get you started.

---

### Post by thotheolh on 2010-11-21
Thanks. Would look into Quickly.

---

