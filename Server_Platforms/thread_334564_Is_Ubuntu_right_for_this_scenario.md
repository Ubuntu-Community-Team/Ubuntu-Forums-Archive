---
title: "Is Ubuntu right for this scenario?"
date: 2007-01-09
forum: Server Platforms
---

### Post by emid on 2007-01-09
I was recently having a conversation with a friend of mine who has an office with 7 employees.  Their server had just died and they were replacing it with a new box.  He told me that they basically just need a file server so everyone can access documents etc. from a central location.  He asked me what OS they should get.  I was thinking that perhaps he could use linux instead of Windows Server 2003 since they really aren't doing anything MS centric.  I was wondering if anyone could tell me of any caveats or issues that they should be aware of (if any at all).  All the workstations are running XP, but I know I share directories on my home network with Ubuntu all the time and it works well.

- Beyond the file sharing I believe they also have one of those large free standing network printers (a Ricoh I think).  Would this be difficult to setup?

- Another big issue is backup.  Their new box is supposed to be setup in a RAID 5 array, but they also want to have an offsite backup.  When their old server died they lost a month or so of work because no one remembered to back the server up.  For this reason I was wondering how difficult it would be to automate the backup process to help them avoid another fiasco.

- Last but not least, a vpn.  What would be recommended for a vpn?  Is it very risky to run a vpn server on the same box so that they could have remote access to their files from outside the office?  If it is acceptable, which vpn would be recommended so that the employess can access the server from windows clients?

Also, should they install the desktop build or the server build?  In addition to that should they go with Dapper or Edgy?  Is Dapper's stability more important than the newer packages available for Edgy (i.e. is Edgy not reliable enough)?

Since its not a large office and they really don't need any Active Directory type features or anything like that, I thought Ubuntu might be a good fit for them.  Any comments or suggestions are greatly appreciated.

---

### Post by kd7swh on 2007-01-09
My opinion is:

Ubuntu would do fine. Dapper Server would be my recommendation. The Printer will need drivers, that maybe hard to find. (look for it before the linux install) I would use samba to share files with the windows clients. As far as VPN goes, I would not recommend using the file server for it. VPN is usually on the outside of the firewall while file server is behind it.  If there is no firewall it doesn't matter. I have heard OpenSwan VPN is good. But I have only used CISCO.

---

### Post by Soarer on 2007-01-09
> **emid said:**
> I was recently having a conversation with a friend of mine who has an office with 7 employees.  Their server had just died and they were replacing it with a new box.  He told me that they basically just need a file server so everyone can access documents etc. from a central location.  He asked me what OS they should get.  I was thinking that perhaps he could use linux instead of Windows Server 2003 since they really aren't doing anything MS centric.  I was wondering if anyone could tell me of any caveats or issues that they should be aware of (if any at all).  All the workstations are running XP, but I know I share directories on my home network with Ubuntu all the time and it works well.

Should be fine with appropriate configuration

> **emid said:**
> - Beyond the file sharing I believe they also have one of those large free standing network printers (a Ricoh I think).  Would this be difficult to setup?

Look it up on [www.linuxprinting.org](www.linuxprinting.org). That will tell you if there is a driver available. Assuming there is, printer sharing is easy.

> **emid said:**
> - Another big issue is backup.  Their new box is supposed to be setup in a RAID 5 array, but they also want to have an offsite backup.  When their old server died they lost a month or so of work because no one remembered to back the server up.  For this reason I was wondering how difficult it would be to automate the backup process to help them avoid another fiasco.

Easy, lots of tools available. Can't auto change tapes though :)

> **emid said:**
> - Last but not least, a vpn.  What would be recommended for a vpn?  Is it very risky to run a vpn server on the same box so that they could have remote access to their files from outside the office?  If it is acceptable, which vpn would be recommended so that the employess can access the server from windows clients?

I don't do this, so I can't comment. There is ALWAYS an increased security risk once you allow incoming connections to a server with valuable files on it.

> **emid said:**
> Also, should they install the desktop build or the server build?  In addition to that should they go with Dapper or Edgy?  Is Dapper's stability more important than the newer packages available for Edgy (i.e. is Edgy not reliable enough)?

Dapper has long term support - I would go with that. They don't sound like they need the latest & greatest (and most unstable) packages. Server build with Webmin would be my choice, but a gnome desktop isn't a huge overhead and could make life easier for the Admin.

> **emid said:**
> Since its not a large office and they really don't need any Active Directory type features or anything like that, I thought Ubuntu might be a good fit for them.  Any comments or suggestions are greatly appreciated.

It doesn't sound like they need anything which isn't easy enough on Ubuntu (and you can't beat the price). Don't forget paid support is available from Canonical.

---

### Post by emid on 2007-01-09
Thanks for the replies.  I realize that the VPN situation is not ideal, but I'm not sure how else they would be able to do it.  I was thinking that they would just forward the appropriate ports to allow access to the vpn service.  That would be the only thing exposed and with strong enough authentication they would probably be decently protected against randomly initiated attacks.  Not the best situation to be sure, but probably ok (unless I'm wrong, let me know).  I've heard of OpenSWAN, are there windows clients available?

Does anyone know of any commercial offsite backup services that they would be able to integrate with a linux box?   The one they had used in the past required software to be installed on the server and it was all exclusively windows based.

Once again, you guys are awesome and I appreciate the feedback!

---

### Post by kd7swh on 2007-01-11
There are clients out there for windows. One site I saw said that Windows could support some openswan setups with additional software. Xelerance Software has some VPN solutions that maybe helpful. 

I will include a link to there site as well as a How To page on configuring VPN on Windows XP at the bottom of this post.

Port forwarding would work to make the VPN available outside of the local area network, but you may also look in to taking other security measures if there is any sensitive information flowing through the VPN tunnel. My router and firewall both support MAC address filtering. Using this feature would limit access to the network to computers in a list of "trusted" MAC addresses. This still works with laptops that change location and or login from outside networks. (Good Idea)

I hope this helps :) 

[http://www.xelerance.com/software/](http://www.xelerance.com/software/)
[http://www.windowsecurity.com/articles/Configure-VPN-Connection-Windows-XP.html](http://www.windowsecurity.com/articles/Configure-VPN-Connection-Windows-XP.html)

---

### Post by kd7swh on 2007-01-11
something like this might work for backup

[http://www.vembu.com/](http://www.vembu.com/)

its cross platform

---

### Post by Modernity on 2007-01-11
Depending on how involved you want to get into the back up process, you could have the server back up to another Linux server off site, (depending on how fast your connections are on both ends). We use this method for backing up some of our clients. We take their CentOS machine and backup to our Suse machine in our office. So, it is possible to do this yourself, if you are willing to set it all up.

---

