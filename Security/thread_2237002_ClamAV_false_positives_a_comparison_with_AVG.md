---
title: "ClamAV false positives: a comparison with AVG"
date: 2014-07-30
forum: Security
---

### Post by thanuntu on 2014-07-30
After running Ubuntu for almost 4 years on my machine, I decided to install an antivirus (I know, I know...). My first choice was clamav (with clamtk GUI). I installed the stock version from the 12.04 repos.

**[SIZE=3]First test (clamav)[/SIZE]**
A scan of my home folder literally left me shocked: 740 detected threats!

As I looked at the results, I realised that almost all of them were PUA (Potentially Unwanted Application, as I later found out).
[LIST]
[*]The vast majority were windows files from wineprefixes in my .wine and .PlayOnLinux directories and they were mostly flagged as **PUA.Win32.Packer.Winzip**, **PUA.Win32.Packer.Armadillo-59**, **PUA.Win32.Packer.SetupExeSection**, **PUA.Win32.Packer.PrivateExeProte-7** etc. These were mostly .exe and .dll files, many of which I immediately recognized as being legitimate.
[*]Many of my "infected" files were pdf's (**PUA.Script.PDF.EmbeddedJS-1**, **PUA.Script.PDF.EmbeddedJavaScript**, **PUA.PDF.LaunchActionObject**), even for pdf's I created myself or which I downloaded from trusted sources.
[*]ClamAV flagged ~/.wine/system.reg with **PUA.CVE_2011_3397**      
[*]It also flagged several of my own tar.gz files with **PUA.Script.Packed-2**
[/LIST]
The only non-PUA "threats" was the **Heuristics.Encrypted.PDF**, which, however concerned some pdf files I got from a trusted source (European Space Agency), or which I created myself (with LibreOffice).
The only legitimate threat suspect was flagged "Trojan.Win32.Crack", which I am looking into.

**[SIZE=3]Verification (AVG)[/SIZE]**
A bit incredulous about these results, I decided to cross-reference them with AVG, which is available as a deb install. After installing, I ran a scan of my home folder (from the command line).
The bulk of the messages I received were errors:
[LIST]
[*]I often had warning of "corrupted executable files" (dosx.exe, dsound.vxd, ddhelp.exe) in my C: wineprefix drive (drive_c/windows/system32) in various wine or PlayOnLinux prefixes.
[*]Also, "Object scan failed; No medium found" for the D: drives of those prefixes, as well as for locations "My Pictures", "My Music" and "My Videos".
[*]Most of those errors concerned .dll's and .exe's for TeamViewer 8 and 9 installations (these are installed as wine applications).
[/LIST]
However, I did get a couple of probable threat suspects: Trojan horse Downloader.Generic10.AZDW and potentially harmful program Crack.CO IN an .exe file in one of my POL prefixes. I am looking into those as well

**[SIZE=3]CONCLUSION[/SIZE]**
It seems that clamav overuses signatures of packed files (something which is discussed and referenced [here]("http://askubuntu.com/questions/488649/clamav-finding-threat-in-steam-file") and [here]("http://www.clamav.net/lang/en/2007/09/03/detection-of-potentially-unwanted-applications/")).
The CLI clamscan tool has options to detect or exclude PUA's, but the clamtk GUI version from the repos (4.38), offers no such option (from what I managed to understand). Without some easy access to those options I cannot see how meaningful is its use.
AVG, even without a GUI seems better adapted, but still one has to sift through lots of errors to find probable threats worth looking into (2 possible threats among 280 errors and warnings in this case). The only reporting system I detected is the screen printout, without possibility of categorizing for easy access.
In any case however, with 2-3 probable threats after 4 years of active use (all of which concern files working through wine) I think that even those limited options are more than enough.

---

### Post by nuts2 on 2014-08-01
If you use Wine it is a good idea to run AV because malware runs in Wine just as good as Windows.

---

### Post by SuperFreak on 2014-08-01
> **nuts2 said:**
> If you use Wine it is a good idea to run AV because malware runs in Wine just as good as Windows.


Would that not be only if you are connecting to the internet with WINE programs? Perhaps best to stay away from such programs as Teamviewer, IE, etc

---

### Post by monkeybrain20122 on 2014-08-01
It is well known that ClamAv gives false positives,--and false negatives too,-- you can even check out Wikipedia, it is not very good as far as AV goes.

---

