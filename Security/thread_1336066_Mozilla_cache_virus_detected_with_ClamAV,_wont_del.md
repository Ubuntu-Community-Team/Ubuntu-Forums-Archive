---
title: "Mozilla cache virus detected with ClamAV, wont delete..."
date: 2009-11-24
forum: Security
---

### Post by Cytochromec on 2009-11-24
Ok, I have a peculiar problem here. ClamAV always detects one virus, as follows:

Location: /home/cosmos/.mozilla/firefox/ar0d2qfx.default/Cache/01FD104Bd01 
Status: PUA.Script.Packed-2

When I try to delete or quarantine this file using the ClamAV UI, nothing works. I also clear my cache under Mozilla via Preferences - Advanced - Network - Clear Now and confirm that there are zero files in my cache withabout:cache - list all files; at which point there are no files listed because I cleared the cache. I run ClamAV again and sure as day, the same result as above shows up. 

I am a Linux newb, is there a way to manually locate the above directory? Also, any other ideas about getting rid of this "virus"? Even if its a false positive or harmless, I cant say that I like getting 1 virus found all the time as a result. Thanks mates.

---

### Post by Logan1985 on 2009-11-24
You can manually check if the file is there by going to Places > Home Folder 

Press Ctrl + H to show hidden files and directories (you will notice everything starting with a . is hidden)

You can then go into /.mozilla and work your way through to the directory in question. 

I have no idea what it refers to mind, so proceed with caution.

---

### Post by R2-Duck2 on 2009-11-24
PUA.Script.Packed-2
 
PUA is ClamAV's identification of a ***P**otentially **U**nwanted **A**pplication* 
 
*Script.Packed* is identifying that several of the javascripts are compressed 
 
 
If you want to disable the PUA function... 
 
First, log into the console. 
Then, type in this command: 
 
*nano /etc/clamav/clamd.conf.tmpl* 
 
Use the down arrow key to the line that says: 
*DetectPUA yes* 
 
Change it to:  
***#**DetectPUA yes* 
 
Press Control X
Type Y where it asks to save at the bottom of the screen. 
Press Enter where it asks for the name. 
 
Reboot. 
 
The **#** symbol turns off the *DetectPUA* line...

---

### Post by Cytochromec on 2009-11-24
R2-Duck2, I had a feeling it was not something to worry about and your post confirms it. However, I rather not disable any functions of ClamAV, even if they are yielding false positives.

Logan, Ctrl + H ftw! I located the directory and just moved it to trash manually, ran ClamAV, and it was gone. Nice. 

Thanks for help guys.

---

### Post by R2-Duck2 on 2009-11-24
Glad you got things sorted out, Cytochromec!!

---

