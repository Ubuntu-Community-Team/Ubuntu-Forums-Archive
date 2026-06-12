---
title: "Share hard drive"
date: 2011-06-06
forum: Server Platforms
---

### Post by elliotbeken on 2011-06-06
hi all i have a HP microserver with ubuntu 11.04 64-bit server installed and all works fine i was just wondering how i can share a hard drive (/media/Data) on the network so i can map it as a network drive in windows and allow sharing over the network.

currently i have setup ssh and FTP so i can access the drive but i want to be able to allow other people in the lan map the drive...

i know i need something like samba but how to i set it up in server edition of ubuntu ?

thanks

---

### Post by mmad on 2011-06-06
Its fairly easy. Install samba (its probably already there) and then just configure it to share the folder/hard drive you want: [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide). If you don't want to manually mess about with configuration files then install **Webmin** and use its interface to add shares.

Then on Windows, you can easily access the machine e.g. if your server name is myubuntuserver and the shared drive is shared as sfolders then you can locally (on the same network) access it as //myubuntuserver/sfolders.

---

### Post by collisionystm on 2011-06-06
> **elliotbeken said:**
> hi all i have a HP microserver with ubuntu 11.04 64-bit server installed and all works fine i was just wondering how i can share a hard drive (/media/Data) on the network so i can map it as a network drive in windows and allow sharing over the network.

currently i have setup ssh and FTP so i can access the drive but i want to be able to allow other people in the lan map the drive...

i know i need something like samba but how to i set it up in server edition of ubuntu ?

thanks


Because your setup is already existing, I recommend just using Webmin. Its quick and to the point. Unless you have an urge to edit your smb.conf, which is actually quite easy, it all just depends on how lazy you are!

In the future take a look at Zentyal. [www.zentyal.com](www.zentyal.com)

It will make your  life much easier.

---

### Post by YesWeCan on 2011-06-06
I believe you can right-click on the directory icon that you wish to share and select "Sharing Options". Follow the instructions.

---

### Post by elliotbeken on 2011-06-06
I know the right click method but it's server edition therefore I only have ssh access to the server. 


I already have webmin, so I will give it a go thanks

---

### Post by collisionystm on 2011-06-06
> **elliotbeken said:**
> I know the right click method but it's server edition therefore I only have ssh access to the server. 


I already have webmin, so I will give it a go thanks


after you create your share in webmin, make sure to go back and edit it. There is some kind of additional options menu where you set the permission for the share...etc. For me just doing the initial 'share folder' never seemed to work

---

