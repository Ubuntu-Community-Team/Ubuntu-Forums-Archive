---
title: "Antivirus on Ubuntu"
date: 2023-01-08
forum: Security
---

### Post by voxpopili on 2023-01-08
Nice fantasy about not needing Antivirus with Ubuntu.

I clicked on a link on an Australian Police Facebook page yesterday and it installed a Trojan / malware on my system. 

I am getting pop up windows every 10 minutes stating "Warning - virus has infected your system -click here to delete"  Of course i am not clicking on them , The warning signs have cloned icons for mcAfee , Nortons and various others.

I tried setting up Kaspersky , Bitdefender and ClamAV  , none of those antivirus are finding the Trojan / Virus and / or i am not getting complete installations of the software to enable finding and removing the Malware.

An example is the ClamAV , in terminal i get the message stating the library definitions is not updating , If i run a scan it says i have a library of 27,400 items in the definitions library yet it finds nothing ;

 freshclam
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
ERROR: initialize: libfreshclam init failed.
ERROR: Initialization error!

I am using Mozilla Version 108.0  and i assume the infection is through Mozilla , more so than being embedded in Ubuntu.

Any suggestions ?

---

### Post by ActionParsnip on 2023-01-08
> **voxpopili said:**
> Nice fantasy about not needing Antivirus with Ubuntu.

I clicked on a link on an Australian Police Facebook page yesterday and it installed a Trojan / malware on my system. 

I am getting pop up windows every 10 minutes stating "Warning - virus has infected your system -click here to delete"  Of course i am not clicking on them , The warning signs have cloned icons for mcAfee , Nortons and various others.

I tried setting up Kaspersky , Bitdefender and ClamAV  , none of those antivirus are finding the Trojan / Virus and / or i am not getting complete installations of the software to enable finding and removing the Malware.

An example is the ClamAV , in terminal i get the message stating the library definitions is not updating , If i run a scan it says i have a library of 27,400 items in the definitions library yet it finds nothing ;

 freshclam
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
ERROR: initialize: libfreshclam init failed.
ERROR: Initialization error!

I am using Mozilla Version 108.0  and i assume the infection is through Mozilla , more so than being embedded in Ubuntu.

Any suggestions ?

You can't "use mozilla". Mozilla is a company. They make a browser named Firefox which you can use.

Did you run freshclam prefixed with sudo? Users don't have write access outside of their home folders by default and explains the error you are seeing

---

### Post by voxpopili on 2023-01-08
> **ActionParsnip said:**
> You can't "use mozilla". Mozilla is a company. They make a browser named Firefox which you can use.

Did you run freshclam prefixed with sudo? Users don't have write access outside of their home folders by default and explains the error you are seeing

Thankyou

Yes i used sudo prefix but it wouldnt run update however I browsed through some Y.T. videos and copied a different c-line  to get the definitions successfully updated.
 
sudo apt-get install clamav clamav-daemon -y   ... this worked !

clamav-freshclam.service - ClamAV virus database updater
     Loaded: loaded (/lib/systemd/system/clamav-freshclam.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Sun 2023-01-08 23:09:04 AEDT; 14min ago
       Docs: man:freshclam(1)
             man:freshclam.conf(5)
             [https://docs.clamav.net/](https://docs.clamav.net/)
    Process: 3557 ExecStart=/usr/bin/freshclam -d --foreground=true (code=exited, status=0/SUCCESS)
   Main PID: 3557 (code=exited, status=0/SUCCESS)

Jan 08 22:16:21 vbvb freshclam[3557]: Sun Jan  8 22:16:21 2023 -> ^Your ClamAV installation is OUTDATED!
Jan 08 22:16:21 vbvb freshclam[3557]: Sun Jan  8 22:16:21 2023 -> ^Local version: 0.103.6 Recommended version: 0.103.7
Jan  08 22:16:21 vbvb freshclam[3557]: Sun Jan  8 22:16:21 2023 -> DON'T  PANIC! Read [https://docs.clamav.net/manual/Installing.html](https://docs.clamav.net/manual/Installing.html)
Jan 08  22:16:21 vbvbfreshclam[3557]: Sun Jan  8 22:16:21 2023 -> daily.cld  database is up-to-date (version: 26775, sigs: 2015380, f-level: 90,  builder: raynman)
Jan 08 22:16:21 vbvb freshclam[3557]: Sun Jan  8  22:16:21 2023 -> main.cld database is up-to-date (version: 62, sigs:  6647427, f-level: 90, builder: sigmgr)
Jan 08 22:16:21 vbvb  freshclam[3557]: Sun Jan  8 22:16:21 2023 -> bytecode.cld database is  up-to-date (version: 333, sigs: 92, f-level: 63, builder: awillia2)
Jan 08 23:09:04 vbvb systemd[1]: Stopping ClamAV virus database updater...
Jan 08 23:09:04 vbvb freshclam[3557]: Sun Jan  8 23:09:04 2023 -> Update process terminated
Jan 08 23:09:04 vbvb systemd[1]: clamav-freshclam.service: Succeeded.
Jan 08 23:09:04 vbvb systemd[1]: Stopped ClamAV virus database updater.


 Now though i have another error , when i run a scan now it gives me error message on every line of file scanning and says "denied access"


scan result

/home/nuc/.local/share/recently-used.xbel: Access denied. ERROR
/home/nuc/.local/share/tracker/data/tracker-store.ontology.journal: Access denied. ERROR
/home/nuc/.local/share/tracker/data/tracker-store.journal: Access denied. ERROR
/home/nuc/.local/share/xorg: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/keyrings: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/gnome-shell: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/evolution: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/applications: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/sounds: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/gvfs-metadata: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/nautilus/scripts: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/webkitgtk: File path check failure: Permission denied. ERROR
/home/nuc/.local/share/RecentDocuments/E Suites .png.desktop: Access denied. ERROR

/home/nuc/.cache/.fr-DxS25m: File path check failure: Permission denied. ERROR
/home/nuc/.cache/.fr-GchsXl: File path check failure: Permission denied. ERROR
/home/nuc/.cache/.fr-R2YZYl: File path check failure: Permission denied. ERROR
/home/nuc/.cache/rhythmbox: File path check failure: Permission denied. ERROR
/home/nuc/.cache/.fr-6R6PNA: File path check failure: Permission denied. ERROR
/home/nuc/.cache/.fr-9secsA: File path check failure: Permission denied. ERROR
/home/nuc/.cache/.fr-Xn87eC: File path check failure: Permission denied. ERROR
/home/nuc/.cache/totem: File path check failure: Permission denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-new-signatures.20220819T085856Z.to.20220907T161355Z.sigtar.gz: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-full-signatures.20220705T134709Z.sigtar.gz: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-inc.20220819T085856Z.to.20220907T161355Z.manifest: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-inc.20220706T161348Z.to.20220819T085856Z.manifest: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-new-signatures.20220706T161348Z.to.20220819T085856Z.sigtar.gz: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-new-signatures.20220705T134709Z.to.20220706T041830Z.sigtar.gz: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-inc.20220705T134709Z.to.20220706T041830Z.manifest: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-new-signatures.20220706T041830Z.to.20220706T161348Z.sigtar.gz: Access denied. ERROR
/home/nuc/.cache/deja-dup/9b2403c15a774cbf7d31d00d23d4c9a0/duplicity-inc.20220706T041830Z.to.20220706T161348Z.manifest: Access denied. ERROR
/home/nuc/.cache/deja-dup/056e994ace4c34a50958dd78410f758e/duplicity-full-signatures.20221002T112312Z.sigtar.gz: Access denied. ERROR
/home/nuc/.cache/deja-dup/056e994ace4c34a50958dd78410f758e/duplicity-full.20221002T112312Z.manifest: Access denied. ERROR
/home/nuc/.cache/.fr-F1XxJt: File path check failure: Permission denied. ERROR
/home/nuc/.gnupg: File path check failure: Permission denied. ERROR

/home/nuc/Downloads/All mail Including Spam and Trash-002.mbox.part: Access denied. ERROR
/home/nuc/Downloads/All mail Including Spam and Trash-002(1).mbox.part: Access denied. ERROR

------------------
new scan of downloads directory 

sudo clamscan --infected --detect-pua=yes --recursive /home/nuc/downloads/
/home/nuc/downloads/: No such file or directory
WARNING: /home/nuc/downloads/: Can't access file
----------- SCAN SUMMARY -----------
Known viruses: 8662735
Engine version: 0.103.6
Scanned directories: 0
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Data read: 0.00 MB (ratio 0.00:1)
Time: 18.225 sec (0 m 18 s)
Start Date: 2023:01:08 23:48:54
End Date:   2023:01:08 23:49:12

---

### Post by ActionParsnip on 2023-01-08
Are those files owned by your user? You can check with
```

ls -l filename

```
Replace "filename" with the full path of one of the files in your output.

---

### Post by voxpopili on 2023-01-08
I tried that , does the --rw-------1 response indicate it is user owned or malicious ?

from the file names i can see 90 % of them are mine but 10 % remaining i have no idea if they are system files  , they are all showing as "access denied"

thankyou

ls -l /home/nuc/.local/share/recently-used.xbel
-rw------- 1 nuc nuc 638272 Jan  8 21:11 /home/nuc/.local/share/recently-used.xbel

---

### Post by voxpopili on 2023-01-08
i must be doing something wrong here or possibly the virus is blocking a search ?

"no such file or directory"  and no files scanned.


sudo clamscan --infected --detect-pua=yes --recursive /home/mozilla/
[sudo] password for nuc: 
/home/mozilla/: No such file or directory
WARNING: /home/mozilla/: Can't access file

----------- SCAN SUMMARY -----------
Known viruses: 8662735
Engine version: 0.103.6
Scanned directories: 0
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Data read: 0.00 MB (ratio 0.00:1)
Time: 16.260 sec (0 m 16 s)
Start Date: 2023:01:09 00:14:15
End Date:   2023:01:09 00:14:31

---

### Post by tea for one on 2023-01-08
> **voxpopili said:**
> 
sudo clamscan --infected --detect-pua=yes --recursive /home/mozilla/
[sudo] password for nuc: 
/home/mozilla/: No such file or directory
WARNING: /home/mozilla/: Can't access file

The mozilla folder in your user directory is a hidden folder.
i.e. preceded with a full stop or period.

```
/home/username/.mozilla/
/home/voxpopili/.mozilla/
```

---

### Post by ActionParsnip on 2023-01-08
The leftmost 'nuc' is the user owner. The rw bit and where it is shows it is readable and writable by the owner. Should be OK.

---

### Post by QIII on 2023-01-08
@voxpopili:  Please start your own thread instead of hijacking nefartete's thread.

But just so you know:  The most likely cause of your "warnings" issue is a scripted pop-up/cookie aimed at Windows users attempting to get you to click the "Let us help you remove the nasty malware we found" button -- which will install malware on a Windows user's machiune.  

It's called "social engineering" and is one of the most common ways to get you to react foolishly.  See TheFu's comments about using one's brain being the best antivirus.  Clear your cache/cookies and see what happens.

You may or may not have had something "installed" by your user action.  There is malware for Linux ... but what you have described is not likely it.

And, by the way, the directory is hidden.  It's ".mozilla" not "mozilla".

---

### Post by QIII on 2023-01-08
Conversation moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2479248](https://ubuntuforums.org/showthread.php?t=2479248)

---

### Post by VMC on 2023-01-08
> **QIII said:**
> @voxpopili:  ...
But just so you know:  The most likely cause of your "warnings" issue is a scripted pop-up/cookie aimed at Windows users attempting to get you to click the "Let us help you remove the nasty malware we found" button -- which will install malware on a Windows user's machiune.  

It's called "social engineering" and is one of the most common ways to get you to react foolishly.  See TheFu's comments about using one's brain being the best antivirus.  Clear your cache/cookies and see what happens.

You may or may not have had something "installed" by your user action.  There is malware for Linux ... but what you have described is not likely it.

And, by the way, the directory is hidden.  It's ".mozilla" not "mozilla".I was wondering if he ran into a click-bait scenario. It appears so.

---

### Post by voxpopili on 2023-01-08
> **QIII said:**
> @voxpopili:  Please start your own thread instead of hijacking nefartete's thread.

But just so you know:  The most likely cause of your "warnings" issue is a scripted pop-up/cookie aimed at Windows users attempting to get you to click the "Let us help you remove the nasty malware we found" button -- which will install malware on a Windows user's machiune.  

It's called "social engineering" and is one of the most common ways to get you to react foolishly.  See TheFu's comments about using one's brain being the best antivirus.  Clear your cache/cookies and see what happens.

You may or may not have had something "installed" by your user action.  There is malware for Linux ... but what you have described is not likely it.

And, by the way, the directory is hidden.  It's ".mozilla" not "mozilla".

Yes i agree , its something aimed at Windows users but its still got its fingers inside Firefox , i cleared all cache as my first port of call but its still there.

ClamAV apparently cant see this thing , If i have to delete Firefox and reinstall at least thats better than doing a full system restore.

$ sudo clamscan --infected --detect-pua=yes --recursive /home/nuc/.mozilla/
[sudo] password for nuc: 

----------- SCAN SUMMARY -----------
Known viruses: 8662735
Engine version: 0.103.6
Scanned directories: 4661
Scanned files: 8015
Infected files: 0
Data scanned: 238.73 MB
Data read: 340.12 MB (ratio 0.70:1)
Time: 47.828 sec (0 m 47 s)
Start Date: 2023:01:09 07:54:41
End Date:   2023:01:09 07:55:29

---

### Post by voxpopili on 2023-01-09
> **VMC said:**
> I was wondering if he ran into a click-bait scenario. It appears so.

The Ooops moment , Yes i clicked on a link inside of the Facebook page operated by my local Police .



I never had a problem with Viruses on Ubuntu in 2 - 3 years of use , and i still love Linux over windows any day.

---

