---
title: "Accessing ubuntu server remotely"
date: 2015-12-15
forum: Server Platforms
---

### Post by tonyball1975 on 2015-12-15
Hi everyone,  I am in the process of building my own NAS which will have ubuntu server 14.04 as it's OS.  I want to use this NAS as :

1) A media server - Plex is my current choice
2) File server using Samba shares.

Whilst I am waiting for my hardware components to arrive I have been playing around with ubuntu server in a VM to ensure I can configure it etc.   I have everything working, I think,  but one thing I am unsure of is what would be the best way to access the server outside of my LAN.  I am more interested in accessing my samba shares as Plex has built in remote access it would seem.  

In the main I would need to access the shares from my iphone/ipad and I have been trying out an app called FileExplorer (free version) which works well on my LAN.  It would be good if I could also edit files though thats probably more for access from a PC.   So really after some ideas and pointers to what would be the best route to take for this and any setup guides that you may have written/used.   

I have setup SSH access on my test VM so I am able to use Putty | FileZilla but again this only works currently on my LAN.  I have seen openVPN mentioned but not sure if that would allow me to use the iphone app.

Any assistance/advise would be great.

Thanks

---

### Post by mastablasta on 2015-12-15
> **tonyball1975 said:**
> 
In the main I would need to access the shares from my iphone/ipad and I have been trying out an app called FileExplorer (free version) which works well on my LAN.  It would be good if I could also edit files though thats probably more for access from a PC.   So really after some ideas and pointers to what would be the best route to take for this and any setup guides that you may have written/used.   

I have setup SSH access on my test VM so I am able to use Putty | FileZilla but again this only works currently on my LAN.  I have seen openVPN mentioned but not sure if that would allow me to use the iphone app.


search for sFTp client for IOS or Android (e.g. Turbo FTP client & SFTP client).

Make sure you use SSH with keys. you are on the right track.

you will need to open SSH port to internet. make sure you also install and configure Fail2ban or a similar service, to block hacking attempts. if Fail2 ban you need to configure a persistant jail. if Access is doen via static IP then white listing the IP might be is a good way.

---

### Post by tonyball1975 on 2015-12-15
> **mastablasta said:**
> search for sFTp client for IOS or Android (e.g. Turbo FTP client & SFTP client).

Make sure you use SSH with keys. you are on the right track.

you will need to open SSH port to internet. make sure you also install and configure Fail2ban or a similar service, to block hacking attempts. if Fail2 ban you need to configure a persistant jail. if Access is doen via static IP then white listing the IP might be is a good way.

Thank you very much for that,  and your suggestions seems to be best idea.  I already had SSH setup with keys and I could access this via Putty/Filezilla fine from my LAN.  I have a free DNS which I am using and have added the port forwarding on my router for the SSH port I set in sshd_conf.  However if I try to sftp from another network using this info and my SSH key (*.ppk) I get a connection refused.  Any ideas what might be the issue?

---

### Post by steeldriver on 2015-12-15
> **tonyball1975 said:**
> using this info and my SSH key (*.ppk)

How, exactly? A common stumbling block is that different clients use different keyfile formats

---

### Post by tonyball1975 on 2015-12-15
> **steeldriver said:**
> How, exactly? A common stumbling block is that different clients use different keyfile formats

I think the issue is I didn't have the necessary port open through the UFW.  Also I have a feeling I am getting issues with this currently being a VM and having IP conflicts.   I will wait to get the hardware setup and ubuntu installed on this and see how I go with SSH from outside my LAN - but I think this will give me what I am after :D

For info though - I have Filezilla working within my LAN working fine with sFTP using a .ppk generated from Puttygen and I now have an sftp ios app working (again with my LAN) using a .pem key I generated from Puttygen using the Conversions | Export OpenSSH key option.   Just need to find the best sFTP iOS app I can from the choices which are available.

---

