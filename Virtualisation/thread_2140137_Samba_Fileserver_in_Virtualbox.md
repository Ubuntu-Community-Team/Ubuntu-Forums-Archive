---
title: "Samba Fileserver in Virtualbox"
date: 2013-04-28
forum: Virtualisation
---

### Post by matos2344 on 2013-04-28
My questions are this:

1.  Im using ubuntu 12.10 in virtualbox.  I want my host machine(Win8) to be able to access a fileshare on the ubuntu server.  I also want a laptop on my network to use the fileshare aswell.
     
I have created users in ubuntu, and then created those users in samba.  

The problem that i am running into is that i dont want to use the shared folders in virtual box, i want to share via the network.

I can not seem to find the folder from either my host pc or the laptop.

I think my problem is some things that i have not configured in my smb.conf file.
 
Any advice would be greatly appreciated, i have been trying use the internet but there are a lot of conflicting ideas, and they just dont answer my exact question.

---

### Post by lmarmisa on 2013-04-28
Check in VirtualBox Network menu of your VM if you have selected the bridged adapter mode. Do not use NAT.

---

### Post by matos2344 on 2013-04-28
i should have stated that earlier, i have it on bridged.  One other thing that might be of some relevance is that ubuntu(virtualbox) is able to connect to the internet, but does not show any active connections in the OS itself.  Im not sure if that is my problem or not.

---

