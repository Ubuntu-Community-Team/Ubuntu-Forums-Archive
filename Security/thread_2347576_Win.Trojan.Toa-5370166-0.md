---
title: "Win.Trojan.Toa-5370166-0"
date: 2016-12-26
forum: Security
---

### Post by Mike_Andrews on 2016-12-26
System 76 laptop, c. 2014 running Ubuntu 16.04.1. NO WINDOWS

. . . Just had a bout with a Windows Trojan - Win.Trojan.Toa-5370166-0. Don't know where it came from or when.
After running a very desultory clam scan earlier today, mostly for want of anything else to do. . . ha! Clam turned up a bad penny in Win.Trojan.Toa-5370166-0, which had made a few deposits in Firefox (the home folder) and in my file system.
I was able to delete the virus' entries in home, but a scan of file system turned out differently. My machine was NOT infected, of course; I merely wanted to avoid spreading a bad thing to others. So -
Coupled with a lack of expertise in handling Clam's methodology and understanding little pertaining to Root-enabled Ubuntu file management, I then tried to delete 6 virus entries that turned up in file system after the 2nd scan completed, but Clam refused to cooperate. . . leaving "no action" as result.
I rebooted and re-scanned file system to see if the 6 entries were still there. They were, and that time the delete action worked. 
. . . Unfortunately.
Because, a third reboot brought up one of my worst nightmares. . . a barren desktop, sans the compiz gui and with no way to function as happy camper. I guess I deleted something poignant?
It's like the old cliché about ghosts: 'They can't hurt you but they can make you hurt yourself.'
After an hour of grappling with the nightmare I was eventually able to locate (using another computer) a few commands for Terminal that resolved my dilemma: sudo rm ~/.cache/compizconfig-1 (and) sudo rm -fr ~/.compiz  (The foregoing was listed as 'fix number 1' of five, BTW.)
I was both amazed, being an abject pessimist and elated when the next reboot brought my desktop up, restored to full gui!
I might add, while all reading this hard luck story are no doubt snickering, that I managed to run a deja-dup --restore on the file system via Terminal. . . twice, actually, using a slightly different parameter each time, and both runs failed to R-W/restore the Ecrypts folders, popping up an error message telling me that I lacked permission, etc. Palm. Forehead.
So, if one of you more experienced types can throw me a bone by offering a code entry that will allow me to run a restore as Root User, or even ute rooser, I will remain grateful for several hours.
Short of that I want to wish everyone happy holidays!
. . . And keep on running those Clam scans!
M.

---

### Post by &amp;KyT$0P# on 2016-12-26
> **Mike_Andrews said:**
> System 76 laptop, c. 2014 running Ubuntu 16.04.1. NO WINDOWS

. . . Just had a bout with a Windows Trojan - Win.Trojan.Toa-5370166-0. Don't know where it came from or when.
After running a very desultory clam scan earlier today, mostly for want of anything else to do. . . ha! Clam turned up a bad penny in Win.Trojan.Toa-5370166-0, 
I got similar results when using clamd to scan some of my files for Windows malware, and it's definitely a false positive on my end.  i.e. those files are as infected as rubbing alcohol.  I know this because the "infected" files are identical in every way to a known-clean backup.

Do you have any specific reason to suspect those files might actually contain Windows malware?  If not, just ignore the warnings, restore known-clean backups of what you deleted, and enjoy the rest of the holiday season. :)

---

### Post by Mike_Andrews on 2016-12-26
Thanks for your interest, halogen2. 
In answer to your question, yes, I do have reason to believe this was the real thing.
When setting Clamtk to scan PUAs it will come up with bunches of false positives. But leaving the PUA line in Settings unticked eliminates all the headaches.
That's why I was so surprised when Clam came up with this doosie, because I keep PUAs unticked. If I had continued browsing others may have been infected, so it's good that something told me to run that scan!
I'm confident that the infection attempt. . . and it had to be deliberate by someone who saw that I was using Firefox and assumed I was also running Windows, would have created other victims had it not been caught so soon.
. . . I run frequent  scans and keep my antivirus defs updated.
Call me paranoid, but just please never call me late for dinner.
Thanks again, halogen2.

---

### Post by &amp;KyT$0P# on 2016-12-26
> **Mike_Andrews said:**
> ... something told me to run that scan!
What told you?

> I'm confident that the infection attempt. . . and it had to be deliberate by someone who saw that I was using Firefox and assumed I was also running Windows,
What makes you that confident it's deliberate and targeted like that?


Without all the specifics, there's no telling whether it'd be safe to restore your backups.

---

### Post by Mike_Andrews on 2016-12-27
Re: What told you?

Gee, halogen2, I dunno. . . I suppose the same source informs me in such instances as that which tells me water is wet and the sky is blue on a clear day. 
Of course there are those who will argue endlessly with such logic, including the Flat-Earthers; but the garden variety 'gut hunch' has always been good enough for me. It's pulled the rabbit out of the hat on quite a few occasions. 
But if you're concerned that the backup I *attempted* to run (twice) may be infected, please let me allay your fears by writing that the latter is stored on 16GB SD card media, most recently updated yesterday using Backup. The System76 laptop I use features a special slot for SD chips that simplifies making frequent updates to stored Backup data.

Re: What makes you that confident it's deliberate and targeted like that?

I've been doing this for a long, long time, halogen2. It's true that Ubuntu Linux is still a bit new to me, but I have used other computers and operating systems since the mid 1990's. . . and before that I was involved in the now antiquated data base technology at a major airline.
You don't believe in seat-of-the-pants computing? Tsk tsk. 
Sometimes SOTP is the only way to go.
But in attempting to provide you with a cogent answer, let me just say that not all the websites I frequent are what you would call "approved" by the Mainstream - especially given the present climate involving the mounting controversy over false news. 
I DO make politically oriented posts now and then, and yes. . . sometimes maybe the things I write are not well received. It's a big world out there, my friend and in it are all types.
I've gotten infected with viruses for NO REASON when all I wanted was to surf the Net and mind my own business. There are people in this world who derive perverse enjoyment from causing others to suffer. And, given the fact that this is the first time a Windows oriented Trojan has come down the pike for me in Ubuntu, together with the fact that I've recently entered a post certain people may find, er, offensive. . . well, it doesn't take a JPL shift manager to deduce what follows. 
For many years it was my pleasure to monitor router packet logs, noting the dropped inbounds and if persistent enough, sending off an email to the affiliated domain replete with a copy-paste of all the hits and asking the honchos there to contact the DHCP users of those IP addresses and notify them of a possible infection. Botism.
. . . The foregoing is an effective means of fighting against treachery and malicious behavior without having to pay attorney's fees.
Besides, knowing the difference between a mother hen guarding her clutch and a billing attorney has been extremely beneficial to me in proffering the way.
What's that. . . you don't know the difference between a hen guarding her clutch and a high-priced attorney billing his clients?
. . . Well, the hen clucks defiance.
So, anyway what told me to run that scan?
. . . You know what I think, halogen2? I think it was Houdini's ghost.
At least, that's as good a possibility as any other and maybe you'll guess my age now, after so-saying.
You're not by any chance born in November, are you? I don't do November.
...

---

### Post by &amp;KyT$0P# on 2016-12-27
Thanks for the detailed answer.  I agree, you really could have Windows malware in your Firefox stuff.

Since you don't have any reason to believe the compromise attempt got through, and you're using a command-line program, you can use [FONT=Courier New]sudo[/FONT] to run the restore command as root.  For example, where you entered [FONT=Courier New]deja-dup --restore[/FONT] before, you would enter [FONT=Courier New]sudo deja-dup --restore[/FONT]

I don't think I have anything else to offer here, sorry.

---

### Post by Mike_Andrews on 2016-12-27
Thank you for coming back, halogen2.
But but but. . . I DID use sudo when running Backup with deja-dup!
That's why the frustration, since I had no place left to go.
Maybe the Ecrypts folders were uninfected (which is more than just likely given the fact that even I lack permission to RW there) - meaning, ergo that replacement was not vital to removing the virus' implants because they were never there to begin with. N'est pas? There's a difference between getting non-toxic code rammed into your bailiwick and running the vacuum to remove it, and receiving a toxic deposit from someone who had mapped out a vulnerability in your OS; and of course Linux is affected by few-to-no viruses so should the latter take place it would pretty much rock the Ubuntu Linux Community.
But it is my policy to ALWAYS resort to SUDO when there is any question of permissions. I run Clamtk scans from terminal for that reason.
No, deja-dup seems to suffer from a small, bleeding wart where it comes to fully restoring encrypted files.
 
Thanks again, halogen2 and come back anytime!
Happy New Year to all Gregorians!

---

### Post by coffeecat on 2016-12-27
> **Mike_Andrews said:**
>  
I DO make politically oriented posts now and then,

Don't. It's against the forum rules: [https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

> **Politics**: This topic has caused serious problems in the past, and as such is subject to tight control. Discussion of the politics of open source is permissible within the Ubuntu, Linux and OS Chat forum. No other political posting is permitted in any form in any other area of the forum.

Do you still have a specific question to put to the forum membership? Please be reminded that this is a support forum; this is not the place for grandstanding. The Security sub-forum tagline reads:

> Questions about security in Ubuntu and the official flavours.

.

---

### Post by sgian on 2016-12-28
If you ever find a file that ClamAV (or the ClamTK that is a gui for ClamAV) claims is malware, I would recommend running it at [https://www.virustotal.com/](https://www.virustotal.com/) which scans that file with about 50 malware scanners the last time I used it.  If ClamAV is the only one finding a positive, then chances are it is a false positive.  Many of us have had these problems with ClamAV, that is probably why you ran into some skepticism.  It wasn't skepticism of you, it was skepticism of ClamAV.  ClamAV just has so many false positives compared to other scanners that I don't even use it except as a last resort.  Since I started using virustotal to verify ClamAV positives, I have never found a true positive out of the many false positives.

Unfortunately I can't recommend a better linux malware scanner.  There just isn't a market for it due to the difficulty of making malware for linux and the small number of linux users.  There is sophos-av, which I have on a computer I use for finances, but it wants to run all the time and really slows down boot time.  There is Comodo, but they appear to have stopped developing it since they list Ubuntu 12.04 and Linux Mint 13 as suppported OS's.  

So it is best to just be careful.  Since Windows is the target of most malware, I would recommend against using WINE on a computer that you do finances or other private stuff on, and I would recommend using separate browsers for finances and general browsing.  That is a step further than most people take, but I think it is better to be safe than sorry.    For Windows software, I would use Windows in a Virtual Machine rather than WINE since you can control access between the guest and host OS in a virtual machine.

---

### Post by Habitual on 2016-12-28
> **sgian said:**
> If you ever find a file that ClamAV (or the ClamTK that is a gui for ClamAV) claims is malware, I would recommend running it at [https://www.virustotal.com/](https://www.virustotal.com/) which scans that file with about 50 malware scanners the last time I used it.  If ClamAV is the only one finding a positive, then chances are it is a false positive.  Many of us have had these problems with ClamAV, that is probably why you ran into some skepticism.  It wasn't skepticism of you, it was skepticism of ClamAV.  ClamAV just has so many false positives compared to other scanners that I don't even use it except as a last resort.  Since I started using virustotal to verify ClamAV positives, I have never found a true positive out of the many false positives.
Good tip. ;)
I have 2 tips for desktop users of ClamAV
Leave PUA **disabled** (it is post install disabled) and 
Don't scan /

ClamAV doesn't clean either, but it does do a Great Job of telling me of infections.
"Clean" in Linux AV seems to be "restore from backup".
Some argue, AV presents another attack vector or weakness.
I just don't want folks to think there's an instant "fix" for infections.

---

