---
title: "[SOLVED] Check sums don't match"
date: 2008-10-08
forum: Security
---

### Post by mregister on 2008-10-08
Hello All,

I originally posted this in the AB forum but this forum may be better.

I ran a tiger report and here is what I got:

> --WARN-- [osv004w] Unreleased Debian GNU/Linux version `lenny/sid'  

AND

> --FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.pcimap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.dep' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.ieee1394map' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.usbmap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.isapnpmap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.inputmap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.seriomap' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.alias' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.24-19-server/modules.symbols' checksum differs from installed package 'linux-image-2.6.24-19-server'.
--FAIL-- [lin005f] Installed file `/usr/share/php/.filemap' checksum differs from installed package 'php-pear'.
--FAIL-- [lin005f] Installed file `/usr/share/php/.depdb' checksum differs from installed package 'php-pear'. 


After looking around it seems that this may be ok but I am not sure. I have read that if the chekcsums don't match then there might be a problem. I ran rkhunter and it did not find anything and my access.log does not show anything unusual.

Should I be worried?

---

### Post by cariboo on 2008-10-08
You may need to update the digital signatures check the readme file in /usr/share/doc/tiger to find out how to do the update.

Jim

---

### Post by mregister on 2008-10-09
The two file used to do the check are mksig and mkfilelist but neither of those two file exist on my system. I will digg around some more and report back. I may end up just doing a compleate reload of the system (it's not yet in production) then get the right chekcsums from tiger. I installed and ran tiger after playing around a bit.

---

### Post by mregister on 2008-10-09
Ok it seems that the only thing to do within Ubuntu is run a report then use it for a template that tiger will use to chekc against. I have set this up and will report any errors.

---

### Post by doas777 on 2008-10-09
I got the same error, and started [this]("http://sudan.ubuntuforums.com/showthread.php?t=908771") thread on it. A number of other users had the same results so i believe it's a system-specific false positive. I haven't yet found anyone with an up to date hardy that didn't get these messages, so either you are safe or we are all screwed.

cheers,
Franklin

---

### Post by mregister on 2008-10-10
Yeah I think we are OK. It seems that for tiger to work right you have to run a report as soon as you install everything then run a report and use that report for a templete. 
I will mark this as solved.

---

