---
title: "Apache only serves LAN side requests-help"
date: 2008-11-25
forum: Server Platforms
---

### Post by three_jeeps on 2008-11-25
Hi:
This one has me scratching my head, any insight would be appreciated...

Installed 8.04 with the generic Apache install.  Set up a few webpages in htdoc, could access from LAN side (e.g. localhost, and 192.168.0.xxx).  Set up router to port forward http requests on port 80, set up domain redirect on dyndns.  Worked fine for 2 months.  SSH connections from LAN side and WAN side work fine as well.
Installed: Hylafax (fax server), then, to accommodate a USB modem, I did the following:
Installed linux-headers-2.6.24-19-server to
/usr/src/ 
I then installed the modem package:
dgcmodem_1.08_k2.6.24_19_server_ubuntu_i386.deb.zip

Ubuntu now recognizes my modem, but .....external (e.g. WAN) https requests are not displayed...e.g. the web pages dont show up in the browser when I go to my domain website.

I am trying to figure out what changed the above installs apparently did to prevent external web page requests.  Any ideas? Any suggestions on how to begin tracking this down?
SSH still works on both LAN and WAN sides.


Firefox provides the following messages:
Firefox can't establish a connection to the server at ubuntuserver.homeunix.com.
Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing

The apache log file appears normal.  Any suggestions? This really has me baffled....
Thanks
John

---

### Post by madverb on 2008-11-25
> Ubuntu now recognizes my modem, but .....external (e.g. WAN) https requests are not displayed...e.g. the web pages dont show up in the browser when I go to my domain website.

HTTPS uses port 443 by default.

---

### Post by three_jeeps on 2008-11-25
> **madverb said:**
> HTTPS uses port 443 by default.

Whoops, a typeo...I am only dealing with http requests, not https requests.  http is set up on the standard port, 80.

---

### Post by madverb on 2008-11-26
is iptables blocking them?

---

### Post by three_jeeps on 2008-11-26
I believe the iptables are fine.  

is there any type of instrumentation I can install to see how far the request actually goes?  I was thinking traceroute, but haven't used that before.

Also, not sure, maybe something with DNS or DHCP (although my ubuntu box is set up with a static address, and that address is spelled out in my router as a static address.  It was working that way since day 1, and nothing in the router has changed....
thanks for the suggestions

---

### Post by madverb on 2008-11-27
Something has to be blocking the port or possibly apache isn't listening on the port anymore for some reason.

Have you tried changing the port Apache is listening on?

---

