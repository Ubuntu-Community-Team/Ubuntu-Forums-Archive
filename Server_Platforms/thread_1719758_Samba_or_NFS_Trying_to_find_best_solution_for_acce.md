---
title: "Samba or NFS? Trying to find best solution for accessing files locally and online"
date: 2011-04-02
forum: Server Platforms
---

### Post by aeboi80 on 2011-04-02
I am trying to determine the best solution for this sharing requirement.

First I am running 2 desktops with Windows 7, 1 laptop with Windows Vista and 1 desktop with Ubuntu 9.10

I am a web designer/developer and I work from multiple computers far too often and I am trying to centralize my files so that I can work on stuff in home office using the desktops, but I want to be able to access all of those files on my laptop when I hit the road.

I already have LAMP setup on Ubuntu simply for local testing purposes.  I have it setup so I can access the LAMP server over the Internet from my laptop when I am not in the office, but that is simply through FTP and is not reliable because if I was working on a file on one of the Windows desktops and saved it, but didn't FTP it over to the Ubuntu LAMP server I am out of luck when I am not in the office and want to work on the file on my laptop.

I would really like a file server to be installed so that when I create a new document that its immediately accessible to all my computers.  This would save me a lot of time of having to worry if I upload the file to the Ubuntu box, it would just already be there.

I have done some research on Samba and on NFS, but I am confused as to what is the best option...My Ubuntu box has 2 hard drives in it currently.

In addition to sharing photoshop, html, etc... files I would like to run a media server on the Ubuntu box as well.  Mainly I just want to centeralize my iTunes connection on Ubuntu (if thats even possible, I'm willing to forgo iTunes if there is a better solution).  It would be great to be able to listen to my entire mp3 collection on the go with my laptop(I realize that is what iPods are for, but I don't want that...I want to be able to access my entire collection).  I have looked at MediaTomb and I guess the now debunked Fire Fly Media server.


So what am I looking for?  I would appreciate recommendations on how to best achieve this wishlist of items.  I don't know if matters, but I am the only one who will be accessing the files.  I don't need a multi-user shared file environment.  Much appreciation would be given for anyone who can point me to a solution and possibly a tutorial.

Thanks,

Chad

---

### Post by fermulator on 2011-04-02
For a file server with mixed operating systems, you want to go with samba.

---

### Post by aeboi80 on 2011-04-02
But is samba going to allow me to access the file server outside of my local network? Ie over the internet?

---

### Post by HermanAB on 2011-04-03
Howdy,

Samba and NFS are for LAN use.  These protocols are not secure.  Also, Samba is not very suitable for use over a VPN, since it is a very chatty protocol.  

The usual method is to use NFS or Samba on a LAN and to use SSH over the internet.

---

### Post by songshu on 2011-04-03
as mentioned above both samba and nfs are for local networks only due to the security implications.

you could however bypass this by using a VPN connection when connecting over the internet.

another option that comes to mind is to use FTP or WebDAV, you could set these up to act like a "network drive", on Ubuntu go to Places -- connect to server, in windows you set it up in file explorer, something called "map network drive" or something.

think the last option would be the simplest for you since you already have the FTP server in place, working on the files through the FTP connection would save you the problem of uploading them everytime.

---

