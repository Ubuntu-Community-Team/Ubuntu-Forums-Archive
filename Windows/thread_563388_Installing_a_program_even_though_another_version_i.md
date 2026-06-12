---
title: "Installing a program even though another version is already installed"
date: 2007-09-29
forum: Windows
---

### Post by Super TWiT on 2007-09-29
I installed a version of mp3 utilities from a bad source.  It came with a Trojan horse virus in the uninstaller.   I need to install a newer version of this software (I know that this came from a reliable source) however, whenever I try to install it install shield says that I should remove the older version of the software.  I can't do this because the uninstaller is corrupted.  I have tried removing from the add/remove program list and deleting all its the program files, however this doesn't work.  Isn't there a key in the registry that I could remove or change to make install shield think that the software isn't installed?

---

### Post by Super TWiT on 2007-09-29
By the way, I can't use system restore to fix it because whenever I try to restore my computer it says that it couldn't restore it to that point.  It does this on all of the restore points.  I am guessing the virus corrupted these.

---

### Post by Midwest-Linux on 2007-09-30
Where was the source that you got the MP3 utilities from? It may help others to avoid that site. That being said...since you cannot do a system restore...the virus also corupted your restore points. Sounds almost what "Spy Sheriff" tried to do with my other computer. 

The biggest mistake  I made was using Internet Explorer to look at a shady tech site linked from another clean site. I had ransomware on my computer, and it came close to infecting my restore points. 

(Ransomware is malware where they infect your computer and suddenly a window comes up with a "cure" for the malware for like $30)

 I did a search on "Spy Sheriff"  and took all the advice I could find from the anti malware sites, I had to rename some infected files to get rid of them and go into the registry. After deleting all that, then I had to do system restore...and then it worked...

 But with your system restore disabled...I cannot say if you can get rid of the trojan like I did....

Try looking up "Spy Sheriff" removal and take it from there...I am NOT saying it is "Spy Sheriff" or "Pest Trap" but thats where I would start looking....

Good Luck....

---

### Post by Super TWiT on 2007-09-30
Unfortunately, I already deleted all of the restore points.  When I had this software installed before all I had to do was use system restore.  I have already removed the virus, at least I think, because my anti virus said that it removed it without any errors.

---

### Post by Super TWiT on 2007-10-03
Anyone?

---

### Post by smoker on 2007-10-03
try this: [http://majorgeeks.com/Brute_Force_Uninstaller_BFU_d4714.html](http://majorgeeks.com/Brute_Force_Uninstaller_BFU_d4714.html)

failing that, you may have to manually delete the folder/s in programme files that contain the app you want to remove, and search the registry and delete any entries you find for that app.

---

### Post by Super TWiT on 2007-10-03
How do you use Brute Force Uninstaller?  It sounds like you need to write a script for it.  I have already deleted the program files and deleted the registry keys.  I have even used this microsoft knowledge base article [http://support.microsoft.com/kb/247501/en-us]("http://support.microsoft.com/kb/247501/en-us")
and even when I followed the instructions here the program still shows up in the add/remove program list.  I am wondering because it had a virus if it didn't infect my system somehow.  I really don't want to reinstall widnows but that looks like what I might have to do.  Oh, Yeah, I got that download from [http://www.mympxplayer.org/amv-convert-tool-368-mp3-player-utilities-368-567-mb-df327.html](http://www.mympxplayer.org/amv-convert-tool-368-mp3-player-utilities-368-567-mb-df327.html)
It says at the end "trojan free version".  I am not certain this is where it came from, but I know it came from that website, and I am fairly certain that that is the version that had the trojan too.

---

### Post by kulturloseramerikaner on 2007-10-04
I don't want to be THAT GUY, but why did they find it necessary to say on a download site "Trojan Free?"  On a legitimate download site, isn't that understood???

---

### Post by smoker on 2007-10-04
> **Super TWiT said:**
> How do you use Brute Force Uninstaller?  It sounds like you need to write a script for it.  I have already deleted the program files and deleted the registry keys.  I have even used this microsoft knowledge base article [http://support.microsoft.com/kb/247501/en-us](http://support.microsoft.com/kb/247501/en-us)
and even when I followed the instructions here the program still shows up in the add/remove program list.  I am wondering because it had a virus if it didn't infect my system somehow.  I really don't want to reinstall widnows but that looks like what I might have to do...

hi, have a look at these links:
[http://www.spywareinfo.com/~merijn/programs.php#bfu](http://www.spywareinfo.com/~merijn/programs.php#bfu)
[http://metallica.geekstogo.com/BFUinstructions.html](http://metallica.geekstogo.com/BFUinstructions.html)
[http://metallica.geekstogo.com/dialers.html](http://metallica.geekstogo.com/dialers.html)

if you do a google search for .bfu scripts, you may find one already written for the particular problem you have.

though, if you have removed all the programme files and reg entries, then a format and reinstall is possibly the only way to guarantee the integrity of your system. it may take you days to track down a problem reg entry that is probably named something innocuous and innocent!

best of luck

---

