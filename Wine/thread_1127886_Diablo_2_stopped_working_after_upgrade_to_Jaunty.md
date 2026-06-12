---
title: "Diablo 2 stopped working after upgrade to Jaunty"
date: 2009-04-17
forum: Wine
---

### Post by Pollox on 2009-04-17
Diablo 2 was working fine in Intrepid, but stopped working when I upgraded to Jaunty.  It just shows a black screen when I try to run it fullscreen (windowed mode does work).  Running it from terminal, it gives me the error "fixme:advapi:SetSecurityInfo stub".  I haven't been able to find any information on how to deal with this error.  Help please?

---

### Post by NightMKoder on 2009-04-17
That's...not an error. Or rather, its a harmless error.

What is your wine version & graphics card/driver version?

---

### Post by Pollox on 2009-04-17
I'm running wine version 1.1.19, although I experienced the same problem with version 1.0.1, which I had been using before (I upgraded to see if this would resolve the problem).

I'm not sure how to check my graphics driver version, but I see that it's now using the open source driver for my ATI mobility Radeon X1400, when in Intrepid it was using the proprietary driver.  From what I can tell, there is no proprietary driver available for this in Jaunty.

---

### Post by NightMKoder on 2009-04-17
There...is always a restricted driver for ATI cards. That's why diablo is crashing - the open source drivers have bad (ie none) support for 3D.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Pollox on 2009-04-18
No restricted drivers appear in Administration -> Hardware Drivers.  I can install xorg-driver-fglrx, but with it installed the computer will not even get to the login screen.  I tried some of the stuff on that page you linked to, but it did not help.  Reading up a little on the issue (there seems to be a few threads about it here on the forums), some people seemed to be saying that the restricted driver does not work with the xserver, and I'm stuck with the open source one.  I also tried installing the driver from the ati site.  Version 9.3 doesn't appear to support Jaunty and version 9.4 does not appear to support my card.  So, it looks like I will have to wait until the open source driver works better to play Diablo on Ubuntu again.  Unless you have any more ideas on getting it working?  In any case, thanks for your help in figuring out this problem.

---

### Post by Pollox on 2009-04-18
Just as a side note, the open driver does work with the Compiz cube, so it does have some 3d support.

---

### Post by hikaricore on 2009-04-18
From what I've been reading there are known issues with ATI on more recent versions of X on many distros.
With any luck these regressions will be fixed when Jaunty is actually released next week.

---

### Post by dafallus on 2009-04-27
I just upgraded from Intrepid to Jaunty and I am also unable to get Diablo II to run now. I have an Intel video card, device manager says Mobile GM965/GL960 Integrated Graphics Controller. The following is what I get when I try to run the shortcut placed on my desktop during the install:

[HTML]
$ env WINEPREFIX="/home/$HOME/.wine" wine "C:\Games\Diablo II\Diablo II.exe" 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:SetSecurityInfo stub

$ X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  25683
  Current serial number in output stream:  25683
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub[/HTML]


Everything worked perfectly before.

---

### Post by Kareeser on 2009-04-27
Hm... that might have something to do with the i965 being blacklisted...

---

