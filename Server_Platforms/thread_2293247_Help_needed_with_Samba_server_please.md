---
title: "Help needed with Samba server please"
date: 2015-09-03
forum: Server Platforms
---

### Post by Jay_Conroy on 2015-09-03
Hi,

I am new to ubuntu and I am currently trying to get a samba server up and running. I am running virtual ubuntu with VMware player on Windows 10. I have created a samba server that I thought was working until I tried to locate it on other computers in my house and it was not appearing under Networking on Windows 7/10. It does appear and is working perfectly on the PC that I am running the virtual ubuntu from (Windows 10). I followed this guide on this site to create the server: [http://www.liberiangeek.net/2014/07/ubuntu-tips-create-samba-file-server-ubuntu-14-04/](http://www.liberiangeek.net/2014/07/ubuntu-tips-create-samba-file-server-ubuntu-14-04/) Here is my config file for Samba:
```
[global] 
workgroup = WORKGROUP
 server string = Samba Server %v
 netbios name = srvr1
 security = user
 map to guest = bad user
 name resolve order = bcast host
 dns proxy = no


[allaccess]
 path = /samba/allaccess
 browsable = yes
 writable = yes
 guest ok = yes
 read only = no
```

So, basically, I can copy files to and from my Windows 10 PC and the virtual ubuntu OS (running from the Win 10 PC) with no problems but when I try out other laptops (Windows 7 and 10) in my house (using both wifi and ethernet connected to modem) the server does not appear under Networking where it should.

I would be very appreciative of any help with this, I am new to ubuntu and I am enjoying the things I can do with it so far.


Cheers,
Jay.

---

### Post by TheFu on 2015-09-03
How is the network connection for the VM setup - bridged? Yes?

[https://www.samba.org/samba/docs/using_samba/ch07.html](https://www.samba.org/samba/docs/using_samba/ch07.html) seems related too.
I've never used "name resolve order" ... ever.

---

### Post by nerdtron on 2015-09-04
Setup your VM to use bridged networking (in virtualbox settings, if you use virtualbox). Then on the Virutal machine you should see the same IP assigned on your local network IP block.

---

