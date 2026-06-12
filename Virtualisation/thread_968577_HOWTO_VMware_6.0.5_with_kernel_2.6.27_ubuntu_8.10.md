---
title: "HOWTO: VMware 6.0.5 with kernel 2.6.27 ubuntu 8.10"
date: 2008-11-02
forum: Virtualisation
---

### Post by sleemanj on 2008-11-02
After much searching and messing about I have found the way to install 6.0.5 with kernel 2.6.27 such as in 8.10.

First,
[ go here and download the three tar files in the first post]("http://forum.ubuntu.org.cn/viewtopic.php?p=913873&sid=8b8d9aa85dd0ccd8ff0f4708d37d6dfd")

vmmon.tar, vmnet.tar and vmblock.tar

These were mentioned in an archived thread here but the links were 404'd, these links work, hooray!

Now install Vmware 6.0.5 as normal (if you don't have it already). When you get to the config stage it will fail to compile vmmon.

Copy the three tar files to /usr/lib/vmware/modules/source (or if you installed to a different place, then copy to that appropriate place).

Now run vmware-config.pl

Enjoy a working VMWare again!

---

### Post by suzypeppercorn on 2008-11-03
i had a different error when trying to compile but i gave this a shot and it worked. Thanks for the great instructions and the links to the files

---

### Post by bigboss2200 on 2008-11-18
A big thanks from a Fedora user to u ^^ .. your method worked flowlesly & VMware is working great under the 2.6.27.5-3 kernel..

thanks again

---

### Post by schnutz122 on 2008-11-27
> **sleemanj said:**
> After much searching and messing about I have found the way to install 6.0.5 with kernel 2.6.27 such as in 8.10.

YOU ROCK. Thank you for the links! I had been looking for a solution to my situation where bridging wasn't working to my wireless interface. In my case (running VMWare Server 1.0.8 with Ubuntu Intreped kernel 2.6.27) I simply copied the updated vmnet.tar file and bridging to wireless works as it should!

---

### Post by rihad on 2008-12-12
Thanks to your post modules build and load just fine (I copied them to vmware-any-any-update-116/ and ran the ./runme.pl script which copied them to /usr/lib/vmware/modules/source/ itself). But WS 6.0.0 won't start :( No error whatsoever. When I click the icon the KDE sandbox just twirls for a while, and that's it.

OS: Debian Sarge.

---

