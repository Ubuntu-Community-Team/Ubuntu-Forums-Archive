---
title: "Trojans found in .wine folder."
date: 2016-06-15
forum: Security
---

### Post by joe225 on 2016-06-15
I scanned my computer with clamscan and found 5 infected files. How do I get rid of these and what are they? Can they harm my computer?
Output from terminal:
```
/home/joe/.wine/drive_c/users/joe/Local Settings/Temporary Internet Files/Content.IE5/M9WNCGTM/AIQZPMRJ: Win.Trojan.Agent-1381919 FOUND
/home/joe/.wine/drive_c/users/joe/Temp/csPOOy1oS2/b6CpR4pP.exe: Win.Trojan.Agent-1381919 FOUND
/home/joe/.wine/drive_c/users/joe/Temp/csw8XbuBZF/t8X7kgu3.exe: Win.Trojan.Agent-1381919 FOUND
/home/joe/.wine/drive_c/users/joe/Temp/csnBG2ss00/BMlNcEFa.exe: Win.Trojan.Agent-1381919 FOUND
/home/joe/.wine/drive_c/users/joe/Temp/cszur9XPrk/3i80Z4tG.exe: Win.Trojan.Agent-1381919 FOUND
```

---

### Post by KenUBF on 2016-06-15
Hi joe225,

When I run ClamAV it often finds Trojans and other things in Firefox's cache folders, which looks very similar to this situation. Long story short, I believe these may be false positives. Have you scanned with a second anti-virus to double check? There are few anti-virus solutions for Linux but I use Comodo as it seems to work well. They have a Linux installer (.deb) you can download from their website. I usually just let ClamAV delete those files since they are junk files anyway, assuming /Temp is just for cache and other unnecessary files. I do not have much experience with Wine. As a matter of fact, as I'm writing this ClamAV just found six alleged viruses and trojans, all in the cache folders of Firefox and Chromium (attached pic). After using Bleachbit to clear out the cache I rescanned and nothing was there.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=269598&stc=1[/IMG]

---

### Post by joe225 on 2016-06-15
I cleaned my cache using bleachbit before scanning.

---

### Post by KenUBF on 2016-06-15
Hi Joe,

OK. Have you scanned with any other AV program to confirm ClamAV's findings? I can't find any information at all on the .exe  that are in the files. I would just delete them by hand if necessary and then rescan. You could also download from the Software Center CHKRootkit and RKHunter which you can also use to scan your system to see if Trojans are actually there. If none of these programs flags anything I would say these are false positives and that your computer is OK. Let me know what the scan results are.

I should have put this in the last message but I didn't. Here is a link to the Comodo AV download: [https://www.comodo.com/home/download/download.php?prod=antivirus-for-linux](https://www.comodo.com/home/download/download.php?prod=antivirus-for-linux)

To use CHKRootkit open the Terminal and type: ```
 sudo chkrootkit 
```

Enter your password and the scan should start. Copy/paste your results here.

To use RK Hunter open the Terminal and first update the program by typing: ```
 sudo rkhunter --update 
```

Then run a scan by typing: ```
 sudo rkhunter --check 
```

Copy/paste the results here.

---

### Post by joe225 on 2016-06-15
[https://www.virustotal.com/en/file/fdc7743f594e7e2802fdd33dcdc8f4c34032d6182995baf776ceda77463560f8/analysis/1466043796/](https://www.virustotal.com/en/file/fdc7743f594e7e2802fdd33dcdc8f4c34032d6182995baf776ceda77463560f8/analysis/1466043796/)
Above is a virus total link of one of the files. Seems like it is a lot of different things but not harmful. The product name is [COLOR=#333333][FONT=&amp] Extreme Injector v3.6 which I downloaded and opened with wine and it didn't work. Anyways know any good terminal commands software to get rid of these files?[/FONT][/COLOR]

---

### Post by KenUBF on 2016-06-15
Do you know how to navigate the file system in the terminal? If so, get to the directories where the files are located and use the [COLOR=blue] rm [/COLOR] command, but be sure to also add [COLOR=blue] -i [/COLOR] after to tell it to execute in interactive mode so it will prompt you before deleting files, so you can double check you're not deleting anything you need. So, for example, in the Terminal you need to navigate your way through the folders until you end up with something like this, then use that [COLOR=blue] rm -i [/COLOR] command. That should work. (Or you can go through to the Wine folder and delete it that way. It would likely be faster.) ```
 yourusername@computername: ~ [COLOR=#000000][FONT=Ubuntu Mono]/Temp/[/FONT][/COLOR][COLOR=#0000FF]$ [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]csPOOy1oS2/b6CpR4pP.exe[/FONT][/COLOR][COLOR=blue] [COLOR=#000000][FONT=Ubuntu Mono]rm -i [/FONT][/COLOR][/COLOR]
``` Do that with each of the other files, but make sure you have navigated to the right place and are trying to remove the correct file. The [COLOR=blue] rm [/COLOR] command can be dangerous if you're not careful because once a file you delete with this method it's gone for good. If you don't feel comfortable using the command line method just go to the Wine folders and delete them that way in your file manager. I hope this helps.

---

### Post by joe225 on 2016-06-16
Okay, Thanks for your help!:D

---

### Post by KenUBF on 2016-06-16
You're welcome! Did it work? FYI: I edited the example to be more accurate to what you would actually see when you've reached one of the desired folders to delete the files. The longer string I had before was meant to show the path that you would need to navigate in the Terminal, but it did not look anything like what you would actually see. I'm assuming you don't have much experience with the command line so I made it look more like what you would actually see once you've gotten to the correct folder. I thought the other way might be too confusing. Good luck!

---

### Post by joe225 on 2016-06-16
Well i just moved them to the trash and emptied it cause i rescanned the folder and came up with nothing.

---

### Post by KenUBF on 2016-06-16
Awesome! I'm glad you were able to get rid of those. :)

---

### Post by Habitual on 2016-06-16
Don't scan with PUA enabled?
Don't use wine?

---

### Post by SeijiSensei on 2016-06-16
I'd delete the entire ~/.wine folder to begin with.  Then run wine again, and it will rebuild the folder.  Make a copy of the folder so you can revert back to it if you have a problem again.

The same strategy works with virtual machines like running Windows in VirtualBox.  Install Windows, configure to your liking, then take a snapshot.  If something goes awry, you can replace the running version with the snapshot.

---

