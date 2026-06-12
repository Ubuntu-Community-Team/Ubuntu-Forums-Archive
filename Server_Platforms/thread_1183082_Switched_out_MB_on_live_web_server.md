---
title: "Switched out MB on live web server"
date: 2009-06-09
forum: Server Platforms
---

### Post by ktrainyo on 2009-06-09
I am running a live server that went down this morning. uname -r gives me back:
2.6.17-10-server - whichever version that is.

The problem with the server was the power plug on the motherboard. I replaced the motherboard with the exact same one with the same ram, etc. The only difference is obviously the MAC address will be different. It originally came up as eth1 so I deleted the eth0 entry in iftab.

My router now sees it and is set up to correctly divert all web traffic to the local IP and I am able to log on to my ftp settings from the other local computers.

What could have changed and how do I fix it?

I also may have changed my /etc/network/interfaces settings without completely understanding what I was doing...YAY!

---

### Post by ktrainyo on 2009-06-09
OK, so I loaded the backup copy of etc/network/interfaces and after several minutes all is well again.

This post could be deleted or marked solved.

---

### Post by windependence on 2009-06-09
You never said what the problem was. You say you can log on to it for ftp, and your router is set up correctly but you never say what the problem is.

-Tim

---

