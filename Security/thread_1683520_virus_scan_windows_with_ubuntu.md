---
title: "virus scan windows with ubuntu"
date: 2011-02-07
forum: Security
---

### Post by REMIX8604 on 2011-02-07
my main goal here is to virus scan windows with either my linux or a live usb. i have tryed this 2 ways and have failed.

attempt one:

using my ubuntu 10.04 (wubi) on my netbook. i have installed clamtk. i make sure the preferences are set to scan all files and directories within directory. then when trying to locate my main OS for a recursive scan, i can only find my linux file system. (this is part of my problem) since i cant figure how to scan my windows i go to scan my linux file system. i first scan my home folder. that works fine but when i try to scan the whole file system. clamtk just turns grey and i either have to force quit or i wait forever and cancels the scan.

attempt two:

i made a live usb with ubuntu 10.04 (and with 10.10). then loaded up the usb stick. downloaded and installed clamtk. now i can find my main OS windows and see my linux file system. when i run the scan now on the OS, clamtk once again says please wait, then turns grey. i have to force quit.

so if you have stuck with me so far, thank you. i hope to get this resolved because mine and a friends windows both have a virus.

maybe windows is the virus.

---

### Post by Cpierce on 2011-02-07
It may be worth a try to install linux Avast on your USB. May work better than clam.

Also I know there is a eSet live CD that you can download. 

Keep us posted how it goes.

---

### Post by uRock on 2011-02-07
Moved to the Security Discussions sub-forum.

I would recommend using a diferent anti virus. I am not sure if you can install it on the thumb drive if you are using the image with persistence, but downloading and installing BitDefender will give a more up to date free scanner. BitDefender is only free for Linux, but it does have up to date Windows definitions.

ClamAV brings up a lot of false positives and you don't want it to break your Windows.

Does the Ubuntu see the Windows drive at all? If yes, can you mount it and surf through directories with nautilus?

---

### Post by cariboo on 2011-02-07
There are quite a few Live CD virus scanners available, I suggest using one of those. For a listing have a look [here]("http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/")

---

### Post by uRock on 2011-02-07
> **cariboo907 said:**
> There are quite a few Live CD virus scanners available, I suggest using one of those. For a listing have a look [here]("http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/")
Bookmarked!:p

---

### Post by REMIX8604 on 2011-02-08
so far bitdefender worked well on my friends computer and worked scanning my thumb drives. found 1 virus already. i scanned my netbook and came up with nothing. but every file i open or even try to click on. windows tells me i have a virus, it jams up the whole thing then tries to direct me to a site to sell me anti-virus. right now im making a bootable usb with Kaspersky. thanks guys for the help and that link was great.

---

### Post by uRock on 2011-02-08
Have you tried running MS's Malicious Software Removal Tool? [http://www.microsoft.com/security/pc-security/malware-removal.aspx](http://www.microsoft.com/security/pc-security/malware-removal.aspx)

---

### Post by Rhizoid on 2011-02-08
F-Prot's command line scanner for Linux is pretty much my 'go-to' AV for infected Windows machines in the first instance.

[http://www.f-prot.com/download/trial_forms/linux-ws-tgz.html](http://www.f-prot.com/download/trial_forms/linux-ws-tgz.html)

Some quick installation instructions as I can never find them when I want them:

(Assuming tarball has already been downloaded from the link above and is in ~/Downloads)

```
gunzip -c ~/Downloads/fp-Linux-i686-ws.tar.gz | tar -xvf-
sudo mv ~/Downloads/f-prot /usr/lib
cd /usr/lib/f-prot # important as next line _must_ be run from the f-prot folder
sudo ./install-f-prot.pl
```Accept the defaults by pressing return at each question.  An update will be downloaded automatically and a crontab entry made to auto-update the definitiions (a bit redundant on a USB stick really)

Using the scanner is simplicity itself...

Manual definitions update (a bit more use on a USB stick);
```
sudo /usr/lib/fpupdate
```Scan boot sectors only;
```
sudo fpscan -b
```Scan boot sectors and specified directories and their subdirectories, scanning will pause on first infection found and prompt for action;
```
sudo fpscan -b /{insert-dir-name-here}
```Scan specified directories and automatically disinfect on find;
```
sudo fpscan -b -y /{insert-dir-name-here}
```There are more options with --help.

Hope that helps someone ;)

---

### Post by cariboo on 2011-02-08
> **REMIX8604 said:**
> so far bitdefender worked well on my friends computer and worked scanning my thumb drives. found 1 virus already. i scanned my netbook and came up with nothing. but every file i open or even try to click on. windows tells me i have a virus, it jams up the whole thing then tries to direct me to a site to sell me anti-virus. right now im making a bootable usb with Kaspersky. thanks guys for the help and that link was great.

You may want to start your Windows system in safe mode and install and run [ComboFix]("http://www.bleepingcomputer.com/combofix/how-to-use-combofix") on the system. Then once ComboFix has finished, do a complete scan using Microsoft Security Essentials, my recommended av scanner at the moment.

---

### Post by REMIX8604 on 2011-02-10
thanks guys. i finally got that last tricky virus. i used clamtk from a live usb. bootable kaspersky, bootable bitdefender, that MS Malicious Software Removal Tool, avast and a program of my own called ad-aware. in the end i restored the system to a previous month, then switched to my ubuntu. installed bitdefender, updated then scanned and it found it. why every thing i used to scan couldn't find it before, i have no idea. maybe the bitdefender for linux has better definitions. or just when i did a system restore point (on windows) it un-maksed the hidden little thing. 

i love ubuntu but some programs only run on windows. thats the only reason i keep it around. i cant wait for google OS, that way i can run windows apps when needed. 

side note: when i was messin around with this virus thing. my firefox with any site typed in would say "internet explorer cant visit this site because it could be harmful to your computer" (in windows) i found out that my firefox was set to go thru a proxy server. the option "use system proxy settings" was marked instead of the "no proxy" option like always. i changed it and was able to visit sites again.

---

