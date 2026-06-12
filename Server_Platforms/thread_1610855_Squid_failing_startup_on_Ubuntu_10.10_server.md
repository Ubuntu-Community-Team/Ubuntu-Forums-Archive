---
title: "Squid failing startup on Ubuntu 10.10 server"
date: 2010-11-01
forum: Server Platforms
---

### Post by ssouter on 2010-11-01
I've just built a home server/router with an Atom processor and Viking  ADSL card, with the intension of running a content filter and providing a  file server, and possible a mail server in the future.

I am not totally new to Linux having used desktop for about 9mths and  have played with a testbed with server 10.04 32 bit. I had  Squid/Dansguardian and ClamAV working on the testbed.

I've got Ubuntu Server 10.10 64bit (Rats should have downloaded 10.04 LTS but didn't dawn on me until most servers were up and running) running with OpenSSH, Webmin. I've  set up the ADSL card as a bridge and PPPOE running. Masquerading using IPtables  is  setup. A DHCP server using DHCP3 is running. SAMBA is running. My home network of 2 dual  load PCs (a desktop and a laptop) are both running without incident. 

When I try install Squid I get the following at the end of the process. 

Setting up squid (2.7.STABLE9-2ubuntu5) ...
start: Job failed to start
dpkg: error processing squid (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 squid
E: Sub-process /usr/bin/dpkg returned an error code (1)

If I set the desktop PC proxy settings to direct traffic to the proxy on the server it tells me:

"The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing connections.
    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is
          working."

If I look in /etc/init.d squid isn't there?? but a locate squid shows squid files all over the disk.

I've tried remove and install again and also loaded Tinyproxy all to no avail.

I can't get Dansguardian working without a proxy server. I'm at a loss.

Suggestions?

---

### Post by garukun on 2010-11-03
I have a similar problem with this as well. I was able to run "apt-get install squid" successfully, and the proxy seems to be running. But the squid executable is not in the /etc/init.d directory for some reason.

When I ran chkconfig --add squid, I got: squid: unknown service.

Doesn't look like run the command to properly restart the service.

---

### Post by ssouter on 2010-11-03
Pulled everything out with apt-get remove. used clean and autoremove and re installed. Had to change Dansgurdian socket to 8888. Now is working and blocking content. Not sure what I did to fix it as I had already tried to remove and re install. Going to close thread.

---

