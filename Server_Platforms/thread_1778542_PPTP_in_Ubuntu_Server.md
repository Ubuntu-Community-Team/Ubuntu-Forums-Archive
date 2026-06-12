---
title: "PPTP in Ubuntu Server"
date: 2011-06-09
forum: Server Platforms
---

### Post by kevpatts on 2011-06-09
Hey, how do I connect to a PPTP VPN (router) using Ubuntu server (Maverick/Natty)?

---

### Post by Lars Noodén on 2011-06-09
If you're just getting started then it will be more secure and easier to configure to begin with [IPSec or SSL VPN](http://www.vpnc.org/vpn-standards.html).  PPTP is hard to configure and cannot be made secure except by tunneling it, in which case you're back to IPSec or SSL anyway.

---

### Post by kevpatts on 2011-06-09
It needs to be PPTP, I'm connecting to an existing PPTP server. It's very easy on the desktop platform to set this up, why is it so difficult on the server install?

---

### Post by poolet on 2011-06-09
[LEFT]As Lars Nooden says, I will suggest to used IPSec... First because it's easier to setup and       second it's offers confidentiality and authentication at the packet level between hosts and networks..
  
Now,if you still need more info about pptp I have refers some links below::::

[http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html]("http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html") 

[http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html]("http://www.ubuntugeek.com/howto-configure-pptp-vpn-in-ubuntu-intrepid-and-jaunty.html")

[http://pptpclient.sourceforge.net/howto-ubuntu.phtml]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml")

[http://pigtail.net/nicholas/pptp/]("http://pigtail.net/nicholas/pptp/")[/LEFT]

---

