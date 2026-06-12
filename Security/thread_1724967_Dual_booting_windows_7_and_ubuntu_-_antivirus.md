---
title: "Dual booting windows 7 and ubuntu - antivirus"
date: 2011-04-09
forum: Security
---

### Post by SilentShadow on 2011-04-09
I'm dual booting with windows 7 and Ubuntu and i was wondering where i should download AVG (i have a paid version) and what other security precautions should I take between both operation systems?
 
i have:
1 windows partition (~23gbs)
1 Ubuntu partition (~23gbs)
1 linux swap partiton (~10 gbs)
1 NTSF partition for storage (~170gbs)

---

### Post by Duncan Williams on 2011-04-09
there are free windows and linux anti-virus, security and privacy programs available at:
[http://my.opera.com/internetsecurity/archive/](http://my.opera.com/internetsecurity/archive/)

You don't need much on the linux side.

---

### Post by listerdl on 2011-04-09
> **SilentShadow said:**
> I'm dual booting with windows 7 and Ubuntu and i was wondering where i should download AVG (i have a paid version) and what other security precautions should I take between both operation systems?
 
i have:
1 windows partition (~23gbs)
1 Ubuntu partition (~23gbs)
1 linux swap partiton (~10 gbs)
1 NTSF partition for storage (~170gbs)

If you are worried about accidentally downloading or installing malware that creeps into linux partition - i doubt that it would work. Generally my understanding is that windows viruses are designed for windows, mac for mac etc...

---

### Post by supershin on 2011-04-09
I believe he is concerned about a windows virus opened in linux somehow making its way to his other partitions, his windows via the storage one for example.

F-prot seems to be the one best maintained. ClamAV seems outdated and for gateways only. Avg and the others seem to just want to say 'hey we're on linux too.' but don't really have good support. AVG even states there is no support.

Generally, you don't need an anti-virus for linux but it helps to keep your windows partition clean. Lookup some of bodhi.zazen threads on security.

This thread will help you. Scroll down to the antivirus section.
[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")
> Reasons AGAINST antivirus on Ubuntu:
They scan primarily for Windows viruses.
There is a high rate of false positives.
Isolation/inoculation is poor.
And currently there are no known active Linux viruses (so there is essentially nothing to detect).

Reasons FOR antivirus on Ubuntu:
You are running a file or mail server with Windows clients.
You wish to scan files before transferring them, by email, flash drive, etc., to a Windows machine.


---

### Post by SeijiSensei on 2011-04-09
> **supershin said:**
> I believe he is concerned about a windows virus opened in linux somehow making its way to his other partitions, his windows via the storage one for example.

That's a *very* unlikely event.  You'd have to download a Windows executable, change its permissions so it's executable, and run it intentionally using WINE.  Even then the virus isn't going to know it's running in WINE and will try to alter the emulated registry.  Whatever it does is most likely going to remain within the confines of ~/.wine.  It's just not a plausible model for infection.

If you're really paranoid, unmount the Windows partition first.

---

### Post by listerdl on 2011-04-10
Id just leave linux alone and install malware bytes as an additional layer of security in windows. Take a system image of windows each week so when and if it goes wrong you can revert back to a good copy. Id just leave ubuntu alone - i am certain that it is solid out of the box as is - i.e. just for general use.

If you are paranoid and love to tinker then get involved with Snort and AV Clam for outgoing email attachments to windows users etc.

In short, keep it simple and back up each week!!

---

### Post by Duncan Williams on 2011-04-10
If you want a secure windows **do not** just use a scanner (malwarebytes).

Use Microsoft Security Essentials, Immunet (cloud anti-malware) and Comodo firewall (at least)

more info is available to secure windows for free:
[http://my.opera.com/internetsecurity](http://my.opera.com/internetsecurity)

There are many privacy and security issues in Windows.
So you need to clean out > caches, temps, registry and cookies, etc.  as well.
All free software to do this in above link.

Its not silly to use `firestarter' as a firewall in ubuntu.
Browser add-ons can help with security and privacy.

again available at mentioned link.

Windows malware can wreck your system (destroy data, stop it booting etc) allow hackers to use your accounts and access your private information and much more. Have a good look at different sections in mentioned link to secure windows.

Linux is not prone to malware, but you can still take measures to stop being tracked, keylogged etc....

---

### Post by listerdl on 2011-04-10
> **Duncan Williams said:**
> Linux is not prone to malware, but you can still take measures to stop being tracked, keylogged etc....

So what would use use to prevent or add security to stop keylogging in linux?

---

### Post by Duncan Williams on 2011-04-10
Using lastpass will stop any key logins occuring. 
(as it's all automated)

Setup firestarter (firewall)

OpenDNS - anti-malware DNS server. (Web Filtering, Phishing/Botnet Protection)
[http://www.opendns.com/start/](http://www.opendns.com/start/)
change DNS settings in Ubuntu: click

Bleachbit - frees disk space, removes hidden junk, guards privacy. Erase cache, delete cookies, clear Internet history ..
[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

Tracking Cookies. - forum thread.
[http://ubuntuforums.org/showthread.php?t=1714769](http://ubuntuforums.org/showthread.php?t=1714769)

**Browser Extensions.**

Last Pass - cloud based password management. 

xmarks - cloud based bookmark management.

Facebook Disconnect - stops facebook tracking you.

Anonymous Proxy - Uses anonymous proxy server to hide your IP. (opera)

Disconnect - Stop third parties/search engines tracking the webpages/searches you do.

Securing your browser.
note this will be updated for linux use soon.
Browser settings

Ubuntu Security - detailed introduction to linux security.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Backup/clone your system (inc dual-boot):
[http://www.easeus.com/disk-copy/feature.htm](http://www.easeus.com/disk-copy/feature.htm)

---

### Post by Duncan Williams on 2011-04-11
This site may be of use to you:
[http://www.linuxsecurity.com/](http://www.linuxsecurity.com/)

---

