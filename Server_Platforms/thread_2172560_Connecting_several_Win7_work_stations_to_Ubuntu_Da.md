---
title: "Connecting several Win7 work stations to Ubuntu Data Server"
date: 2013-09-05
forum: Server Platforms
---

### Post by keith6 on 2013-09-05
Hi, hate to ask such n00b questions but:

I am about to replace an older Win Server 2003 machine with a brand new Dell T620 w/ 8TB storage space. This particular server will only be used to store data such as many GB's of video files in .avi format, photos in .jpg, and some docs in open office format. There will be about 5 or so Win7 desk top work stations that need to be able to connect and review the videos, photos, etc. All will be granted ability to add files. None of the Win7 boxes will need to use the U-server to connect to net or each other. They just need to be able to read the data on the U-server. The U-server will be independant from the other Win Ser. 2008 servers and not need to connect to them at this time. The desktops are connected to the old server for now until I begin the transition. Hope this makes sense. 

Any ideas if Ubuntu server would be best for this or other suggestions. Thanks!

---

### Post by matt_symes on 2013-09-05
Hi

Install Samba on the server to access the files on the Win boxes ?

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Another option is to install a media server but from your post, this may not be exactly what you want. However, Mediatomb is the Upnp server that i use..

[http://mediatomb.cc/](http://mediatomb.cc/)

Kind regards

---

### Post by keith6 on 2013-09-05
Thank you. I had thought about Samba but wasnt sure if it would be needed for this purpose. It might make things easier since all machines are on the LAN. I just dont need the data transfer between the Sever 2008 and the new Linux server. The Linux server only needs to be a file/data server for some Win7 machines. It wont even be used as an app server. BTW, the new Dell machine was shipped with no OS so it will be a fresh install. Will Ubuntu work fine for the purpose of a data server or should I look at RH or Suse. I havent messed with RH since the early 90's. Seems like ages ago.

---

### Post by Pha4drus on 2013-09-05
Hi Keith,

I just finished installing an Ubuntu file server. I have access to files via Samba on the local net and SFTP on the internet and am very satisfied. I access the fileserver with windows 7, windows xp, ubuntu linux and raspbmc. I think Ubuntu will work fine for you.

I would advise you to go for the Ubuntu server edition and maybe even choose to go with an LTS release for a production server. I also choose not to install any additional packages during installation of the OS and just added Samba and SSH later, keeping the system as lean as possible. That also means only commandline and no xwindows, but I'm happy I didn't go for a gui. The system is very fast (boot in 7 seconds), very small (less than 1GB) and I find it a lot of fun to learn to configure a server via commandline.

---

### Post by keith6 on 2013-09-06
Was trying to decide between Ubuntu and Suse so looks like the Ubuntu will be fine. Thanks for your help.

---

