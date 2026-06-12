---
title: "Shared Folders on Vbox Ubuntu Host Winxp Guest"
date: 2011-06-15
forum: Virtualisation
---

### Post by Jake.Debord on 2011-06-15
My setup:

Host = Ubuntu 10.10 server HEADLESS
Guest = Windows XP

Have a share setup with vboxsrv /mnt/qbdata

The guest can access it just fine. BUT, I need for other computers on the network to be able to share this folder as well... What is the best way to go about accomplishing this? 

TIA

---

### Post by collisionystm on 2011-06-15
Use samba or have your XP guest share the folder.

---

### Post by Jake.Debord on 2011-06-15
I thought about using Samba to share it, but that it what I am trying to get away from. Samba is not compatible with quickbooks, it will not allow for more than one person to use the file at a time... 

I would prefer to have the Windows guest share the file, but have not been successful in doing so... How would you recommend I do that?

---

### Post by Jake.Debord on 2011-06-15
I would much prefer to have a Folder on the XP setup as a share... BUT the only tuts I found made me create a folder on the host and set it up as a share that the guest could see.

If I could setup a shared folder on the XP that other computers could see that would be perfect. I have a folder right now that is setup as a share, but can't see it from any other computers :(

---

### Post by Jake.Debord on 2011-06-15
Well, I shared it with samba and it appears to be working... So, I guess I'll continue to use Samba unless someone can point out a better solution to share a folder created on the Winxp guest.

---

### Post by collisionystm on 2011-06-16
All you have to do in Windows XP is right click on the folder and go to sharing. Hit the share folder button. Its very easy lol.

---

### Post by collisionystm on 2011-06-16
OH, but you need to make sure you map the drive first.

---

### Post by Jake.Debord on 2011-06-16
You would think that would work, but it doesn't... The other computers can't see it

---

### Post by collisionystm on 2011-06-16
I bet your VBox windows XP is using NAT for its network interface. Change it to bridged and I am sure it will work.

---

