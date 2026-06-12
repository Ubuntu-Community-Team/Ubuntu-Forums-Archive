---
title: "Help Ubuntu LTSP Server"
date: 2008-11-07
forum: Server Platforms
---

### Post by glynallinson on 2008-11-07
I'm wanting to set up a Ubuntu LTSP server without the DHCP Server. As all DHCP is set by my router and not allowed to change the settings (partners orders) :(
I've installed Ubuntu LTSP and tried different tips from the forums, yes even google. But i'm at a stand still.
Hope someone has some advice. Thanks.

[IMG]http://ubuntuforums.org/picture.php?albumid=682&pictureid=2266[/IMG]

Picture of how my network is setup.

---

### Post by mike010 on 2008-11-07
in setting up my LSTP server i have learned DHCP is not a necessary function for the LTSP server If you already have a DHCP server and you want to use that one instead of the LTSP server machine you can set up your already existing DHCP server to direct requests to the LTSP server address.it's a good idea to remove the DHCP package from the LTSP server machine. 

to remove DHCP package from the LTSP server machine try this

sudo apt-get remove dhcp3-server

also check out this 

[http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg33980.html](http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg33980.html)

---

### Post by glynallinson on 2008-11-07
Thanks mike I'll give this ago and post how it works out.

---

