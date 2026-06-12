---
title: "Samba PDC &amp; Windows 7 RC"
date: 2009-05-18
forum: Server Platforms
---

### Post by loxxol on 2009-05-18
Hi,
 
Does anyone know if / when samba 3.3.4 will be released for Jaunty (or better still for Intrepid)?
 
I am busting a gut to try and get samba 3.3.4 compiled, but not enjoying much success.
 
Unfortunately, Windows 7 Release Candidate cannot authenticate to the domain unless samba 3.3.4 is running as a minimum.
 
so - my questions are as follows:
 
1) any idea on when / if samba 3.3.4 will be available in jaunty?
2) anyone got any experience of compiling samba 3.3.4 to work in the same way as normal "packaged" versions
3) can the patches from samba.org be applied to ubuntu samba 3.3.2 packages?
 
Thanks in advance.... :)

---

### Post by Gweniviere on 2009-05-19
I Am wondering the same thing. My company is eager to embrace Win 7 (as opposed to Vista) and my inability to add them to the domain is starting to create some grumbles.

---

### Post by loxxol on 2009-05-21
OK....
 
So far I have tried the following:
 
0) added windows 7 host to intrepid (standard samba 3.2.3)
1) adding Karmic repositories to jaunty, and upgrading to samba 3.3.4
2) fresh Karmic installation (including samba 3.3.4)
 
Both the above steps, i have modified windows 7 registry as follows:
 
HKLM\System\CCS\Services\LanmanWorkstation\Parameters 
 DWORD DomainCompatibilityMode = 1 
DWORD DNSNameResolutionRequired = 0 
 
 HKLM\System\CCS\Services\Netlogon\Parameters 
 DWORD RequireSignOnSeal = 0 
 DWORD RequireStrongKey = 0 
 
 
In all cases, I am able to join the windows 7 host to the domain, but when adding any user accounts I get a message stating that the trust between the two computers has failed.
 
I have read on a couple of other forums that modification of the windows 7 keys should be enough, but in this case it doesnt appear to work.
 
I don't think I am doing anything weird or whacky in my smb configuration - and have been running for quite some time :)
 
Any ideas.....?

---

### Post by kimnzl on 2009-07-31
Hi All,
I have replied on another thread on this issue with build instructions.
You need 3.3.4 for windows 7 to work currently.
[http://ubuntuforums.org/showthread.php?t=1225500](http://ubuntuforums.org/showthread.php?t=1225500)

Have fun!

This message is for completeness as the other thread is not necessarily in the right place and for people searching.

---

