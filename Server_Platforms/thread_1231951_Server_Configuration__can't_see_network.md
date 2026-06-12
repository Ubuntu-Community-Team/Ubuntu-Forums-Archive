---
title: "Server Configuration / can't see network"
date: 2009-08-05
forum: Server Platforms
---

### Post by mealies on 2009-08-05
Hi

I have just bought a HP 110 server and installed ubuntu server 9.04

At the moment my network consists of:
   Windows7 PC
   Xbo360
   Ubuntu Server

I ran through the install ok, logged in and installed ubuntu-desktop and then installed ushare. The server can see and stream media to the xbox successfully, however i cannot seem to get the PC or the server to see each others drives.

I have installed both SAMBA & the SAMBA client.  The machines can ping each other and i can logon to the server from the pc using Putty.  

What do i need to do in order to get both machines to be able to see each others drives, and for the server to automatically backup the usual folders (Doc, Pictures, Music, etc)

Thanks 

Andrew

---

### Post by matteocisilino on 2009-08-05
you must be shure that samba is started , at least installed .
you can check with : 
$ps ax | grep smb
or connecting to samba share using stanrd method via risources : 
smb:\\IP\

if you cannot connect the main problem will be samba ( maybe not running or non intalled )

$sudo apt-get install samba swat
( [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/) )

S.W.A.T ( Samba Web Administration Tool ) is a simple web configuration tool for samba ( [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html) )

connect with your prefered browser to : [http://IP:901](http://IP:901)
and start configure ( it's very simple )
:popcorn:

---

### Post by mealies on 2009-08-05
Thanks for the quick reply, i will try your suggestions when i get home tonight.

Andrew

---

