---
title: "Ubuntu Server - Webmin local/remote connect problems"
date: 2009-07-11
forum: Server Platforms
---

### Post by rsainath on 2009-07-11
Hi people:
I'm an ubuntu/xubuntu rookie and enjoying every bit if it. I just finished installing ubuntu server, xubuntu, gnome and webmin. Got some good tips from website  [http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html) to install webmin as follows:
1) Install desktop Environment - sudo apt-get install xubuntu-desktop
2) Installed Ubuntu GUI gnome
3) Installed webmin and that's where I got stuck. Did everything mentioned all the way to the last step sudo apt-get install webmin . 
STEPS THAT I FOLLOWED: I'll call all this steps 3a, 3b etc
3a) sudo aptitude install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
3b) wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.470_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.470_all.deb) (I recall I had to use sudo)
3c) sudo dpkg -i webmin_1.470_all.deb
4) STEPS TO USE THE WEBMIN APT REPOSITORY:
4a)sudo vi /etc/apt/sources.list (I used gedit or nano wherever it says vi) and added the line
deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib
AND SAVED AND EXITED THE FILE sources.list
5)fetched and installed GPG key with which the repository is signed, 
5a)first with the commands : cd /root
5b)sudo wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)
5c)sudo apt-key add jcameron-key.asc
6) NOW INSTALLED WEBMIN WITH THE COMMANDS:
6a) sudo apt-get update
6b)sudo apt-get install webmin
THIS PER THE ubuntugeek website should have resolved all the dependencies.
AFTER COMPLETING THIS, I DID A RESTART

AND NOW TO MY PROBLEMS/ISSUES:
Two problems: (1) COULD NOT launch/view the secure website [https://iytherapy.no-ip.org:10000](https://iytherapy.no-ip.org:10000) on Firefox UNTIL I created an exception for a "missing" certificate (edit/preferences/advanced/encryption/view certificates). I thought wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc) (got to add sudo before the wget) followed by sudo apt-key add jcameron-key.asc should have taken care of the certificate problem.
(2) No able to remote access this secured site from another desktop. Even creating an exception for the "missing" certificate on the ubuntu server machine did not help.
(3) By the way the Airlink 101 router is configured with the following open ports in this ubuntu machine's static ip: 22, 80, 81, 10000 and 330
(4) No problem in accessing my server ip 192.168.1.101 or webaddress [http://iytherapy.no-ip.org](http://iytherapy.no-ip.org) (obviously this one does not need a security certificate)
(5) When I DELETED the above "exception" in edit/preferences/advanced/encryption/view certificates it's back to getting the same old message "Secure Connection Failed, iytherapy.no-ip.org:10000 uses an invalid security certificate, The certificate is not trusted because it is self signed.(Error code: sec_error_untrusted_issuer)
Any suggestions ? Have I missed anything?
If this problem has already been resolved (or any similar issues) and you have the links could you please post them here (in addition to any suggestions you might have)? Thanks people. This has been a great learning experience.

---

### Post by lockettpots on 2009-07-13
I had the same problem trying to install the deb package.

Resorted to downloading the 1.4980 tar from the webmin website and following the instructions at
[http://www.webmin.com/tgz.html](http://www.webmin.com/tgz.html)

Seems to be fine (BTW make a note of the url it generates to log on to your webmin instance - don't use [https://localhost:10000](https://localhost:10000))

John

---

### Post by halitech on 2009-07-13
from what I've heard, webmin doesn't work properly with Ubuntu and Debian and more people are recommending ebox over webmin because it works properly with the way Ubuntu and Debian package things now.

---

### Post by rsainath on 2009-07-13
> **lockettpots said:**
> I had the same problem trying to install the deb package.

Resorted to downloading the 1.4980 tar from the webmin website and following the instructions at
[http://www.webmin.com/tgz.html](http://www.webmin.com/tgz.html)

Seems to be fine (BTW make a note of the url it generates to log on to your webmin instance - don't use [https://localhost:10000](https://localhost:10000))

John

Thanks for the response. The "needle" in the haystack was the firewall configuration setting to allow the https file.  "tutsplus" link website [http://net.tutsplus.com/tutorials/other/enhancing-your-ubuntu-server/](http://net.tutsplus.com/tutorials/other/enhancing-your-ubuntu-server/) answered my problem. It was indeed a shorewall / webmin setting and once I followed the instructions I am now able to log on to my secure server by inputting my userid and password. Hope this is of help

---

### Post by rsainath on 2009-07-13
> **halitech said:**
> from what I've heard, webmin doesn't work properly with Ubuntu and Debian and more people are recommending ebox over webmin because it works properly with the way Ubuntu and Debian package things now.


Please see my response in this forum [http://ubuntuforums.org/showthread.php?p=7612412&posted=1#post7612412](http://ubuntuforums.org/showthread.php?p=7612412&posted=1#post7612412) on how I was able to find one possible solution. Hope this helps. I don't yet want to say "problem solved" I'll test it for a few days and then can provide feedback if solved.  Thanks people for responding and suggestions.

---

### Post by windependence on 2009-07-14
Recommendation? ssh. 

Learn the command line. You'll be glad you did.

-Tim

---

### Post by spynappels on 2009-07-15
+1 Windependence

That's what I did,(and am still doing).

---

