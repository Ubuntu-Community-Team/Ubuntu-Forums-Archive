---
title: "Have one ubuntu comp. up, having trouble with the other"
date: 2005-10-06
forum: Server Platforms
---

### Post by {Rm}Gh0sT on 2005-10-06
I have a 2 Wire SBC Adsl Home portal that functions as a gateway (192.168.1.254) I enabled DMZplus for my first ubuntu box a while ago, it DHCP'd the IP and everything works fine, but i wanted to add another ubuntu box to my network.  So, i allowed DMZ in the firewall settings for my new linux box, but SBC's network did not give me an ip - i'm assuming that's because they have thousands of customers but can only have about 200 public ip's.  Thus, i searched around and found an enable public network option on the gui to the gateway.  I entered in the public gateway and subnet according to the information given to me in the details section of the broadband link.  The gateway was 67.125.136.254 and the subnet mask was 255.255.255.248 - which isn't normal, i don't know why it gave me that it should be 255.255.255.0, but i'll just use the settings that are given on the information area in the gateway.  I then allocated an ip address - not many were given and only a few actually worked - for the private machine.  This made it public and i can access it from the network.  Now, i tried to access it outside the network and it failed.  I then tried pinging the ip and that timed out.  I then tried pining other ip's along the lines of 67.125.136.x and found that some of them replied.  Of course, my primary box (67.125.136.3) still works and my secondary box (currently 67.125.136.253) doesn't.  It cannot be the firewall settings or ports because those are all open, but why can i ping certain ip's on the public gateway and not the allocated one.  Why can i only access this server from my lan network and not an outside on even though the ip given is not a private network ip.  Or is it because i'm running this off of what the gateway thinks is another gateway, but then, why can i access my primary server and not the other one?  Or is it just because i cannot have two ubuntu boxes on a dynamic ISP?  Does anyone have suggestions to resolve this problem?

---

### Post by Glut on 2005-10-06
Hi,
This is most likely an issue with your ISP. I strongly suggest you give them a call to sort it out, because your OS should be irrelevant in this case.

---

