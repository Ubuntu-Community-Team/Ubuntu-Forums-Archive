---
title: "Clam antivirus found threats? What's this?"
date: 2013-08-03
forum: Security
---

### Post by Askel on 2013-08-03
In my home-folder Clam found .wine-browser/drive_c/windows/Installer/ac8.msp and .wine-browser/drive_c/Program Files/Microsoft Silverlight/sllauncher.exe and rated them as threats.
sllauncher.exe is, from all I know, the Sliverlight plugin and I guess it was installed with the netflix-desktop using this: [B] ppa:ehoover/compholio

[/B]Is it infected or is it just that clam doesn't recognise it? And what is ac8.msp?

//Askel

---

### Post by unspawn on 2013-08-03
> **Askel said:**
> Is it infected or is it just that clam doesn't recognise it? 
Since you don't tell us *what exactly it's supposed to be infected with* there's nothing much anyone can say, really...


> **Askel said:**
> And what is ac8.msp?
Your favorite search engine will tell you the extension is in use by Microsoft Installer denoting a patch file.

---

### Post by Askel on 2013-08-03
I tired googling it but i didn't find anything about it. I don't know how to get any details from Clam so I don't know what it would be infected with. Could it be false positives?

---

### Post by unspawn on 2013-08-03
> **Askel said:**
> I don't know how to get any details from Clam so I don't know what it would be infected with. 
If there's no log file try ```
clamscan -v .wine-browser/drive_c/windows/Installer/ac8.msp
```


> **Askel said:**
> Could it be false positives?
 Sure.

---

### Post by Askel on 2013-08-04
I got this for ac8.msp
```
clamscan -v .wine-browser/drive_c/windows/Installer/ac8.msp
```
```

Scanning .wine-browser/drive_c/windows/Installer/ac8.msp
.wine-browser/drive_c/windows/Installer/ac8.msp: OK

----------- SCAN SUMMARY -----------
Known viruses: 2547052
Engine version: 0.97.8
Scanned directories: 0
Scanned files: 1
Infected files: 0
Data scanned: 57.84 MB
Data read: 19.40 MB (ratio 2.98:1)
Time: 8.649 sec (0 m 8 s)
```

And
```
clamscan -v .wine-browser/drive_c/Program\ Files/Microsoft\ Silverlight/sllauncher.exe
``` gives ```
Scanning .wine-browser/drive_c/Program Files/Microsoft Silverlight/sllauncher.exe
.wine-browser/drive_c/Program Files/Microsoft Silverlight/sllauncher.exe: OK

----------- SCAN SUMMARY -----------
Known viruses: 2547937
Engine version: 0.97.8
Scanned directories: 0
Scanned files: 1
Infected files: 0
Data scanned: 0.47 MB
Data read: 0.46 MB (ratio 1.01:1)
Time: 4.243 sec (0 m 4 s)

```

If I'm not totally lost Clam doesn't see them as infected anymore. But why did it alert earlier then?

---

### Post by unspawn on 2013-08-04
> **Askel said:**
> (..) Clam doesn't see them as infected anymore. But why did it alert earlier then?
No supporting nfo (log files, screen shots, etc, etc) means no "evidence" which means no clue why.

---

### Post by Askel on 2013-08-04
I did a full scan of the system, and now it sam sllauncher.exe and  ac8.msp as threats again. Also  /usr/share/wine-browser-installer/SilverlighSetup.exe and  /usr/share/wine-browser-installer/FirefoxSetup.exe
When I scan them  separatly in the terminal I get the same result, that they are not  infected, but when scanning the folder they're in they're listed as  threats.

I removed netflix-desktop for now. I'm just hoping their new native Linuxsupport will be up soon.

---

### Post by unspawn on 2013-08-04
> **Askel said:**
> When I scan them  separatly in the terminal I get the same result (..) but when scanning the folder they're in they're listed as  threats.
Depending on what automation or front-end (if any) you use to scan directories check if you can configure it to be verbose when scanning and write alerts / output to a log file. Other than that a manual scan confirmed the files were not infected (with a virus ClamAV knows about) so apart from 0) verifying the files against a download from a known safe location and maybe 1) getting a second opinion by submitting the files to on-line AV scanners I see no reason why you should remove the application.

---

