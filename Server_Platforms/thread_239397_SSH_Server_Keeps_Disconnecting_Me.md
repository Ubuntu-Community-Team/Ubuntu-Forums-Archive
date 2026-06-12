---
title: "SSH Server Keeps Disconnecting Me"
date: 2006-08-19
forum: Server Platforms
---

### Post by crypticlabs on 2006-08-19
I recently installed UBUNTU 6.06 LTS Server on an old computer. I installed the openssh-server package and configured it to use a static IP address. I have not modified IP Tables, so there are no firewall rules setup at all.

The problem I am having is when I SSH from another computer (using PUTTY) into this computer, both from the outside of my LAN and from on the inside, I can connect and log in, but then I get disconnected with in a few seconds. I will start typing in some commands and then its as if PUTTY freezes but then I get a message saying the connection was lost. So then from within the LAN I try pinging the machine but it is if it is down, all that are sent out are lost. But when I will log in to the actually machine running the server, I have network connectivity, all network interfaces are up and properly configured and I can send IP packets in and out of the network. So this made me believe there was something wrong with my router but everything seems to be in place. I had a SLUG ([www.nslu2-linux.org](www.nslu2-linux.org)) running SSH for awhile with the same network/router settings and I never had this problem. The strange thing is if I want to get back into the machine, I either wait for an intermittent amount of time or it seems if I reboot my router, reboot the machine, or physically log into the machine and start created some network traffic, for instance ping google.com, I can SSH into my UBUNTU server, but again, only for a few seconds or so. 

Any ideas/advice would be greatly appreciated.

crypticlabs

---

