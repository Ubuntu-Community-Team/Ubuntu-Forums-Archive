---
title: "installed a program under wine, clamav reports Win.Trojan.Ramnit"
date: 2016-01-07
forum: Security
---

### Post by a-you on 2016-01-07
I made a mistake: I installed a windoze program in wine that's basically a GUI to bootstrap; the program was called Mobirise. Then when I ran a check I do anytime I install anything clamav detected 2 trojans:

/home/myusername/.wine/drive_c/Program Files (x86)/Mobirise/Qt5Core.dll: Win.Trojan.Ramnit-6068 FOUND
/home/myusername/.wine/drive_c/Program Files (x86)/Mobirise/Qt5WebKit.dll: Win.Trojan.Ramnit-6196 FOUND

Does anybody know about Win.Trojan.Ramnit?? and could that conceivably be dangerous to ubuntu 14.4 when installed with wine?? I immediately uninstalled it, deleted the ~/.wine folder, then uninstalled and reinstalled wine with synaptic. But since I had briefly tested Mobirise I freaked!

Is there any chance of malware having been installed on my system through that? The install of Mobirise in wine never involved the use of sudo, but I wonder if there's any chance of my normal user having been compromised with a keylogger or some other crap.

And if anybody has specific info on Win.Trojan.Ramnit is and what it's designed to do please tell me! I have done quite a lot of searching on it but haven't managed to get any specific info about it.

Thanks in advance!!

Ubuntu Studio 14.4 Trusty 64 bit

---

### Post by SeijiSensei on 2016-01-07
If you removed ~/.wine I don't think you have much to worry about.  Writers of malware for Windows don't expect their software to be running in an environment like wine.

---

### Post by a-you on 2016-01-08
Thanks [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"). I probably worried too much about it.

Do you happen to know anything about Win.Trojan.Ramnit by any chance, what it is designed to do?? A lot of people here seem to know quite a bit about other systems too. Maybe you have had occasion to deal with windows trojans? I've almost no experience with windows, having made the switch from a strictly mac history.

---

### Post by maglin2 on 2016-01-08
Lots of info on ramnit about. Here is one link  [https://nakedsecurity.sophos.com/2015/02/27/europol-takedown-of-ramnit-botnet-frees-3-2-million-pcs-from-cybercriminals-grasp/](https://nakedsecurity.sophos.com/2015/02/27/europol-takedown-of-ramnit-botnet-frees-3-2-million-pcs-from-cybercriminals-grasp/)    Note also though that clamav does report false positives sometimes. You could try submitting the detected files to virustotal to see if any other AV thinks they are infected.  [https://www.virustotal.com/](https://www.virustotal.com/)

---

### Post by a-you on 2016-01-09
Ah, because I was searching for the whole name "Win.Trojan.Ramnit" but true, lots of info about ramnit. Thanks for that.

I'm still freaking about this because everything on ramnit says it tries to steal bank info! Does anybody know if ramnit can do anything on a linux system??

In case anybody else has this bizarre experience it appears that those were likely false positives. One has definitely been reported as a false positive (Qt5WebKit.dll) and the other seems related enough that it perhaps should be considered to be false too.

Some info:
[https://www.dropboxforum.com/hc/en-us/community/posts/205824835-VIPRE-Antivirus-flags-Qt5Webkit-dll](https://www.dropboxforum.com/hc/en-us/community/posts/205824835-VIPRE-Antivirus-flags-Qt5Webkit-dll)
[https://community.spiceworks.com/topic/1177285-vipre-detecting-dropbox-dll-as-rootkit](https://community.spiceworks.com/topic/1177285-vipre-detecting-dropbox-dll-as-rootkit)

---

### Post by QDR06VV9 on 2016-01-11
Hi i had something similar a few months back and I contacted Wine myself to be sure.
> [B]Risks


[B]11.1. Wine is malware-compatible

Just because Wine runs on a non-Windows OS doesn't mean you're protected from viruses, trojans, and other forms of malware. 
There are several things you can do to protect yourself: 


[LIST]
[*]Never run executables from sites you don't trust. [Infections have already happened.]("http://www.winehq.org/pipermail/wine-devel/2007-January/053719.html")
[*]In web browsers and mail clients, be suspicious of links to URLs you don't understand and trust.
[*]Never run any application (including Wine applications) as root (see [above]("http://wiki.winehq.org/FAQ#run_as_root")).
[*]Use a virus scanner, e.g. [ClamAV]("http://www.clamav.org/") is a free virus scanner you might consider using if you are worried about an infection; see also [Ubuntu's notes on how to use ClamAV]("https://help.ubuntu.com/community/ClamAV"). No virus scanner is 100% effective, though.
[*]Removing the default Wine Z: drive, which maps to the unix root directory, is a weak defense. It will not prevent Windows applications from reading your entire filesystem, and **will prevent you from running Windows applications that aren't reachable from a Wine drive (like C: or D:smile:.** A workaround is to copy/move/symlink downloaded installers to ~/.wine/drive_c before you can run them.
[*]If you're running applications that you suspect to be infected, run them as their own Linux user or in a virtual machine (the [ZeroWine]("http://wiki.winehq.org/ZeroWine") malware analyzer works this way).
[/LIST]


[B]11.2. How good is Wine at sandboxing Windows apps?

[B]Wine does not sandbox in any way at all. When run under Wine, a Windows app can do anything your user can. Wine does not (and cannot) stop a Windows app directly making native syscalls, messing with your files, altering your startup scripts, or doing other nasty things. 
You need to use AppArmor, SELinux or some type of virtual machine if you want to properly sandbox Windows apps. 
Note that the [winetricks]("http://wiki.winehq.org/winetricks") sandbox verb merely removes the desktop integration and Z: drive symlinks and is not a true sandbox. It protects against errors rather than malice. It's useful for, e.g., keeping games from saving their settings in random subdirectories of your home directory. [/B][/B][/B][/B]
[COLOR=#000000]Form Here [/COLOR][http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
[COLOR=#000000]Maybe Helpful to others.
[/COLOR]Here is my old thread   [http://ubuntuforums.org/showthread.php?t=2280054](http://ubuntuforums.org/showthread.php?t=2280054)
They all turned out to be false positives
[COLOR=#000000]Regards[/COLOR]

---

### Post by Shane_Mundee on 2016-01-15
I have had this experience and you're right, they were false positives.

---

### Post by bashiergui on 2016-01-16
> **a-you said:**
> I'm still freaking about this because everything on ramnit says it tries to steal bank info! Does anybody know if ramnit can do anything on a linux system??
In wine yes. In linux no. 
If you're still worried, then change your bank password. If they managed to get your password then if you change it there won't be any more issues.

---

### Post by a-you on 2016-02-16
I'll mark this solved because it really seems likely that they were false positives.

---

