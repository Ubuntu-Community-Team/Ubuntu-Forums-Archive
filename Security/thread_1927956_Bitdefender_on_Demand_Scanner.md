---
title: "Bitdefender on Demand Scanner"
date: 2012-02-19
forum: Security
---

### Post by RangerRay on 2012-02-19
Hello everyone, right now i am completing a scan from bitdefender. The scan is Bitdefender on Demand, I am actually scanning on my incomplete installation of Xubuntu,. The only way I got network access was through Bitdefenders update dialog box. Any way did a scan, but it will not allow me to fix the problems. There are no viruses, but  a threat is potentially present. I'm going to give you the directory, how many files scanned and how  many I/O Errors were detected. [COLOR=DarkOrange]SYS [/COLOR]- 6,714 files scanned, 758 I/O Errors. File was to large to display, so here is the logs address home/bitdefender/.localshare/Bitdefender-Scanner//logs/bduilog1329639343. System log has today date as modified. Next is[COLOR=DarkOrange] rofs[/COLOR]-  27,956 files scanned,  31 I/O Errors detected. Last modified date was 7-28-2011.[COLOR=DarkOrange] Proc[/COLOR] - 13, 113 files scanned, 2, 676 I/O Errors, today is last date modified On Proc file was to large so here's the file number 1329641191. [COLOR=DarkOrange] Media[/COLOR] - 2 files scanned, 1 I/O Error.[COLOR=DarkOrange] etc[/COLOR] - 573 files scanned, 19 I/O Errors. I'm goig to display afew for you %sys/devices/virtual/block/loops/trace/enable there were over 100 of this loops stating permission denied. Under rofs - rofs/etc/chatscripts, rofs/etc/ppp/peers, rofs/etc/ssl/private stating permission denied. / Roots permission denied, this is where bit defender stated potential threat may be present. I know my system, I now know just the scans that I have someone watching me, I knew it wasn't a virus. My question is this a new install, yesterday I had done a new install, but i turned around and erased it, because it was installing previous packages. It was downloading it scripts so it can prevent me from accessing the internet. I want to know how to get a clean install, without any network whatsoever. Until I can injstall an antivirus, network detection system firewall, etc. without worrying about being compromised before I can even install a clean upload. Also, you need to let the devlopers know whats going. they have scripts in the loop system. Excuse the misprint, etc, the printing is so small i have to use a magnifying glasses to read the print.

---

### Post by unspawn on 2012-02-19
> **RangerRay said:**
> right now i am completing a scan from bitdefender The scan is Bitdefender on Demand, I am actually scanning on my incomplete installation of Xubuntu,. 
What purpose does this serve? Why would you think you need it?


> **RangerRay said:**
> Any way did a scan, but it will not allow me to fix the problems.
Because there probably are *none*.


> **RangerRay said:**
> There are no viruses, but  a threat is potentially present. 
Antivirus tools mainly targeting *The Other OS* may mark an item as "a potential threat" if they don't know or can't determine if it actually *is* a threat.

The purpose of /sys (not "SYS"), /proc and /dev is such that scanning in general does not make much sense. Also for you /etc apparently resides in a read-only file system (rofs/) so scanning it doesn't make much sense either. Finally /root can only be accessed with the right privileges so if you run a scan from an  unprivileged account you will be denied access. That again is OK.


> **RangerRay said:**
> (..) I have someone watching me, (..) yesterday I had done a new install, but i turned around and erased it, because it was installing previous packages. It was downloading it scripts so it can prevent me from accessing the internet. (..) Until I can injstall an antivirus, network detection system firewall, etc. without worrying about being compromised before I can even install a clean upload. Also, you need to let the devlopers know whats going. they have scripts in the loop system.
I think you best start by reading basic Ubuntu documentation for new Linux users. The conclusions you have drawn from *what you think you see* is in value closer to *bird divination* (and I don't mean Megan Fox) than anything else. Should you however remain adamant you are "being watched" and the system is compromised without showing evidence of that then, with all due respect, I think you are trying to solve a problem no technology can ever hope to cure...

---

### Post by RangerRay on 2012-02-19
> **unspawn said:**
> What purpose does this serve? Why would you think you need it?



Because there probably are *none*.



Antivirus tools mainly targeting *The Other OS* may mark an item as "a potential threat" if they don't know or can't determine if it actually *is* a threat.

The purpose of /sys (not "SYS"), /proc and /dev is such that scanning in general does not make much sense. Also for you /etc apparently resides in a read-only file system (rofs/) so scanning it doesn't make much sense either. Finally /root can only be accessed with the right privileges so if you run a scan from an  unprivileged account you will be denied access. That again is OK.



I think you best start by reading basic Ubuntu documentation for new Linux users. The conclusions you have drawn from *what you think you see* is in value closer to *bird divination* (and I don't mean Megan Fox) than anything else. Should you however remain adamant you are "being watched" and the system is compromised without showing evidence of that then, with all due respect, I think you are trying to solve a problem no technology can ever hope to cure...


The problem is, that this is daily, I can not get a clean complete installation. Hell, if I didn't something wrong, whoever is doing this, should let me know what i did. I know who's behind it, as a whole. I want the individual. But if I have to report this to the NSA as a whole, then it will be done. I just got through scanning another hard drive with Ubuntu this time. Pros was scanned, identified 2,651 files, scanned 12,870 files . Sys was scanned, scanning 6,673 files, 756 I/O Errors found. When I started the scan, I started down up in file system, as i started getting closer to the top, their were no files, so i went back and checked the bottom files again, and they all disappeared also. As far showing evidence of that, this hacker doesn't want to compromise himself, by coming on bitdefender. The only way I can use the internet, is use bitdfefender as my medium. This hacker has denied me permission to basilly every I/O Errors iv'e stated, the majority of them are permission denied. Here's one off right now, before they started disappearing - Failed to scan /sys/kernel/debug/ieee802.11/phyO/detdev/wlano/flags/ - permission denied.Here's one more failed to scan /sys/firmware/acpi/tables/DSDT, also FACS, FACP, replace these with DSDE at the end.

If there probably are none, then i want someone to tell me how to gt a clean, complete installation. This problem for me has been going on for over four months, different operating systems, computers motherboards, harddrives, memory. I guess there was nothingh there, also. I am asking for solutions, not theories.

---

### Post by spynappels on 2012-02-20
Dude,

I really don't want to sound harsh here, but in several threads now you have been given lots of advice and suggestions as to what could be going on with the various issues you've described, other than you being the target of some shadowy figure hellbent on "getting" you.

You're not really helping yourself by running scans which are notorious for throwing up false positives on a system which has not even fully completed installation. The temp files alone would give any scanner a fit.

If you are convinced that you are in fact being cyber stalked, however much I and others tell you this is so unlikely as to be in the realms of fantasy based on what you've told us, then do as you said in a previous post:

> But if I have to report this to the NSA as a whole, then it will be done.

You are wearing yourself out running scan after scan and not listening when people explain the results to you.

I'm sorry man, but I really think you need more help than the forums are qualified to give.

---

