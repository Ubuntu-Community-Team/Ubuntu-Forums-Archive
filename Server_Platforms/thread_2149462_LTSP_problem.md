---
title: "LTSP problem"
date: 2013-05-28
forum: Server Platforms
---

### Post by klui on 2013-05-28
Hi  I have a problem with getting LTSP clients working properly. I first started with Ubuntu 12.04 LTS to play with net booting and got interested in LTSP thin clients.  PROBLEM: My thin clients can login but they don't have any applets so logging out is a bit of a hassle, having to resort to a terminal window.  Is what I've done supported?  
[LIST=1] 
[*]Installed Ubuntu Server x64 12.04 LTS - no Ubuntu Desktop 
[*]Installed dnsmasq - I don't want to mess with my current DHCP server and am using dnsmasq's proxyDHCP functionality 
[*]From 1-2, I was able to use PXE:tftp and iPXE:http 
[*]Installed ltsp-server (not standalone since I don't need DHCP, even though dhcp3 is installed) 
[*]Created thin client as --arch i386 
[*]Within the client image 
[LIST=1] 
[*]installed Ubuntu Desktop, Firefox, PuTTY 
[/LIST]
 
[/LIST]
  Do I need to install LTSP-server under Ubuntu Desktop instead of Server? I don't want to do this since I want to keep my server as lightweight as possible. Subsequently when I logged into a thin client, there are no applets. I don't see the date/time, my user id, network status, logout applet. Unity Dash is not functional as it's empty and search comes up empty. If I click on the Power settings, it exits the System Settings control panel. My host's directory is exported to the client. Sound and network are functional. My notebook's F-Keys work.  I also wanted to remove pae from the client kernel so older notebooks can netboot into LTSP. While I was successful in making this change, the applet problem has not improved.  Here's a screenshot: [http://i.imgur.com/F4st5Qt.png](http://i.imgur.com/F4st5Qt.png)  Thanks for any insights anyone could provide.  EDIT: Rebuilt the client so it is a fat client desktop and now things work.

---

### Post by klui on 2013-05-29
Updated original post.

---

