---
title: "Share iTunes library and filesharing to mac network?"
date: 2007-10-24
forum: Server Platforms
---

### Post by Alixul on 2007-10-24
Hello,
I'm need some helpt to seet up a server for my home network witch is just mac computers and 2 ubuntu "servers".
I configured everything except two things.
1. Filesharing
What would I use here? I want do make it possible to make so that I share different things so different users(login required).

2. iTunes sharing
To have the ubuntu server share the iTunes library so the macs can play it.
I tried mt-daap but I didn't like it because it installed it's own webserver and that makes my server more insecure so what I need is a iTunes sharing server that can be installed so it's uses the apache webserver,
Also if I can set the ranking on the songs to it would be great. ;D

Thanks~.
Alixul.

---

### Post by kidders on 2007-10-25
Hi there,


> **Alixul said:**
> 1. FilesharingI would use AFP or NFS, depending on the purpose of the shares. For instance, NFS might be best for a centralised /Users directory, but would probably just be irritating to use otherwise.

> **Alixul said:**
> 2. iTunes sharingDAAP servers typically come with their own web server. I don't think you'll find one that doesn't. That won't make your computer less secure ... unless of course your local network is untrusted (in which case you shouldn't be sharing files over it anyway).

---

### Post by bobosky on 2008-01-10
Okay. I am very new to all this so please give me a great deal of detail.

I have two PowerBook G4s on a wireless net with my Ubuntu 7.10 on the net work with an Ethernet cable.

I have all my external hard drives plugged into the Ubuntu box and I want to be able to access them from the two laptops over the wireless network. The goal is also to let iTunes play movies and music over the network from these USB hard drives plugged into the Ubuntu machine. This seems to be what you guys have done but I would need to step by step walk through on how to make this work.

Thanks for you time!

---

### Post by sciurus on 2008-01-11
If you want to share files in Ubuntu

1) Go to your Ubuntu computer.
2) Go to system -> administration -> shared folders then select the folders you want to share. If asked, install samba.
3) RIght click on network manager's icon, select connection information, and write down the Ubuntu computer's ip address.
4) Go to your Mac.
5) Open the Finder and clicking Go -> Connect to Server.
6) Type smb:// followed by the ip address from step 3. For example, smb://192.168.1.100

Now you can connect to the share and open the flies from any program on OS X.

If you want media files to automatically appear as shared in any computer running iTunes on your network, install the program mt-daapd. After install, edit the file */etc/mt-daapd.conf* to configure the passwords and shared directories. Then run *sudo /etc/init.d/mt-daapd start*. Now in your web browser go to [http://localhost:3689](http://localhost:3689) to control it. After you tell it to scan for media files, any shared files should magically appear in iTunes.

---

