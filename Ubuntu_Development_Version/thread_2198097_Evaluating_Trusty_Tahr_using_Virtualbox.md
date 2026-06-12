---
title: "Evaluating Trusty Tahr using Virtualbox"
date: 2014-01-07
forum: Ubuntu Development Version
---

### Post by jozamm on 2014-01-07
Hi all,

I am evaluating ubuntu 14.04 in a Virtualbox environment. I did a release upgrade and it went ok. However when I restart I get the login screen and when I type my password I get redirected back to the login screen. Maybe version 14.04 is not supported by virtualbox right now?

What could be wrong? Any suggestions would be appreciated.

Regards,

Joseph

---

### Post by JMB74 on 2014-01-07
Could be that X is crashing and repspawning (as it often should on a crash), so returning you to the login screen.

Have you switched to a VT and looked at /var/log/Xorg.0.log.old ? That gives the Xorg log for the previous session, which if a crash should be the one where the crash occurred.

---

### Post by d-cosner on 2014-01-07
I had trouble running 14.04 in Virtualbox, it usually took several tries to get the virtual machine to run. I was using the version found in the 13.10 repos, not the latest from Oracle so that might have made some difference.

---

### Post by fjgaude on 2014-01-07
VBox works for me under 14.04 just fine. I haven't tried the reverse, never do.

---

### Post by QIII on 2014-01-07
It's running fine for me as a guest.

You may be running into a mundane .Xauthority/.ICEauthority issue.

---

### Post by rocky-oceans on 2014-01-11
I had the same problem when running on 13.10 and testing 13.10 (testing other things on a fresh install). I could never figure out what the problem was.

---

### Post by ajgreeny on 2014-01-11
I also have Xubuntu 14.04 64bit running fine in the PUEL Oracle version of VB with all guest additions included and it's hard to see a difference between that and my default installed version of Xubuntu 12.04 64bit.  Both run verry fast on my i5-3570K with integrated HD4000 graphics and 8GB ram (2GB ram set for the VM).

I had no problems installing direct from the downloaded iso image file on my hard disk, and my only problem so far, not being a great VB expert, was that I did not realise I needed to install the guest additions again when kernel 3.13 came along a few days ago, so I lost the full screen graphics.

---

### Post by cresnik on 2014-03-13
I was running Trusty on virtualbox. After the initial install, I had a decent screen size but after the usual apt-get update and apt-get dist-upgrade I only got a 640x480 resolution. Installing the guest additions fixed that. Thanks for the hint!

---

