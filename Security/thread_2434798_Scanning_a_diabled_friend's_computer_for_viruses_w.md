---
title: "Scanning a diabled friend's computer for viruses with Ubuntu-based antivrus/malware"
date: 2020-01-11
forum: Security
---

### Post by AbleTassie on 2020-01-11
I have a friend with cerebral palsy like permanent neurological damage from an accident when he was 7 years old. He has a Samsung PC that has Windows 8.1 Pro  operating system, 64 bit operating system. It has a touch screen and  Intel 2.8 GHz CPU. I have been trying to help him with some of the  functionality of the PC, it seems awfully slow and often downright  unresponsive. He does not have any idea if it has an anti-virus program  or is regularly updated. So I think it should be scanned for  viruses. 

  I am thinking that booting the PC off a USB drive that has a Lubuntu operating  system with an anti-virus/malware program like [ClamAV]("https://www.clamav.net/") or [CommodoAntivirus]("https://antivirus.comodo.com/")  on it. This might make the PC  normally responsive at least, even if such a scan does not increase the  speed much.  I am thinking that this procedure of booting off the  thumb or DVD drive (with an antivirus/malware program) will allow the  antivirus/malware programs to more freely scan my friend's hard  drive than downloading and installing an antivirus and/or malware  program on an already infected hard drive with the already installed Windows 8 Operating System. 

  QUESTION(S): Does anybody have any comments about a strategy  of booting off a thumbdrive with an antivirus/malware program on the  thumb drive? 

Is it desirable, necessary or possible? 
(ClamAV and Commodo both make antivirus programs for both Windows and Linux, but I am not sure, for example, that a Linux-based antivirus program will effectively detect and disarm Windows viruses.)

Does anybody have any other suggestions?

  

  Thanks,
  

  A.

---

### Post by guiverc on 2020-01-11
I on occasion do exactly what you are thinking. I don't pre-prepare anything (I'm usually called or asked to do it whilst away).  I boot a [recent] Ubuntu (or flavor) install media (usually repeat the 'Check disc for defects' in case the thumb drive has been through the wash since last used or other), boot it, & install clamav, freshclam & gui clamtk. 

 I naturally run freshclam to add & ensure the database is up-to-date, then have it run over the owners hdd/ssd looking for issues.  I usually manually scan what it finds; often `scp` some of the suspect but possibly user-wanted files to a old netbook (along with results) I usually bring (I don't use the netbook; it still has good battery & is used instead of a thumb-drive (easier to find & I know what it is)). I don't try and clean any files; just remove them (what many malware checks call quarantine anyway; copies of files are usually kept on my netbook should user decide they do need it in the future; though I usually delete the directory in ~six months).

Disarm?   I've primarily used anti-malware that quarantines (ie. removes & hides in a vault) malware, which I don't consider disarming the files. In the end I vary what I do by what is found.   It's usually very successful (or so I'm told).

---

### Post by TheFu on 2020-01-11
I wouldn't expect any Linux-based, free, virus/malware scanner to be completely up to date for Windows needs. There are just so many Windows viruses.  Oh so many.

If it were me, I'd suggest a Windows solution (whatever that is) that includes a separate boot solution as part of the scanning. Definitely need to boot from different media/device than the OS that might be infected with a root kit. This would apply to Linux systems just the same.  Part of the problem is that viruses hide in RAM, so the disk scanners won't ever find them directly, but can find the download tool that pulls a fresh copy of the virus local after each reboot.

My Windows experience has been extremely limited the last decade, so I don't have any specific recommendations for tools. Eset would be on my list, but only because I have a friend who works in their enterprise pre-sales. We never talk about the company, but they do make some interesting bundles that include Android, Windows and Linux. Not all the available bundles are on their website in easy to find locations, unfortunately.

---

### Post by AbleTassie on 2020-01-14
Thank you guiverc and Fu,

Based on all the advice I have received so far, booting off a separate thumb drive is the way to go. But I am uncertain which approach to take: Linux based OS with anti-virus or another approach. Somebody else I polled recommended this [webpage]("https://www.digitalcitizen.life/top-free-bootable-antivirus-rescue-discs-windows-pcs"), which has several free bootable antivirus programs, including one recommended by the Fu, ESET. 

Any other comments will be appreciated.

Thanks,

A.

---

### Post by CelticWarrior on 2020-01-15
Most, if not all, of the the "free bootable antivirus" will have a more comprehensive and updated database than the typical tools like ClamAV that you can find in Linux distros.

---

### Post by AbleTassie on 2020-01-23
Hi,

I have started to use the ESET Rescue system, see [here]("https://www.eset.com/int/support/sysrescue/") . And using it is a lot like an Ubuntu live boot session. The GUI looks a lot like Lubuntu, it is Linux based, see [link]("https://en.wikipedia.org/wiki/ESET#SysRescue_Live") . After the live boot session begins, you connect to the internet and download the latest virus definitions and then scan. I am going slowly, getting experience, so I don't mess up my friend's PC. But it is going well.

His PC is going so slow, I am thinking it might be better to just discard Windows 8 and go with Lubuntu, because he does not do all that much with  his PC except play solitaire and check his email. 

Thanks to everybody for their responses,

A.

---

### Post by AbleTassie on 2020-03-16
Thanks to everybody for their replies. I did use some of the ideas suggested here, but in the end the problem turned out to be hardware: a failing hard drive. So the HDD has been replaced and I will mark this as SOLVED.

A.

---

