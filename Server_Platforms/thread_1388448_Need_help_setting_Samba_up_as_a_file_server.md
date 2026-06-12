---
title: "Need help setting Samba up as a file server"
date: 2010-01-23
forum: Server Platforms
---

### Post by cilbuper on 2010-01-23
Greetings,

I have been trying to figure out how to set Samba up as a file server. I installed 9.10 64Bit Server w/ Samba.  I added 5 500Gb drives, each with 2 partitions, and added them to my fstab and have them auto mounting to the /mnt/XXXXX location.  

What I need to do is the following:
Restrict the computers that can log into my Samba Server (Iptablers?) I would like to do this with IP addy, COmputer Name, and or MAC address (all 3 would be great).

I need to create shares for each of the 10 mount points I have created.  I want to create an account that will have RWX privlidges, others with R-X.  

Can I specify which Windows users have access to each specific folder?  Do I need to do anything with ACL's?  Is there a way to give one user global access to all of the folders within Samba?

Finally I would like to set up encryption for a few of the mount points if that is possible.  Is that an option with Samba?

Thanks to anyone who can help!

---

### Post by Morbius1 on 2010-01-23
> What I need to do is the following:
Restrict the computers that can log into my Samba Server (Iptablers?) I would like to do this with IP addy, COmputer Name, and or MAC address (all 3 would be great).```
**hosts allow =**
```This parameter in you smb.conf can restrict which host can access the server resources. Can be a string of ip address, a range of ip address, or machine names. Can be placed in the global section to apply to all shares or placed on a per share basis.
> I need to create shares for each of the 10 mount points I have created. I want to create an account that will have RWX privlidges, others with R-X.**read only = yes** OR **read only = no **should do it.
> Can I specify which Windows users have access to each specific folder?```
valid users =
```These and other fun facts are available here: [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

Just in case you don't know there are two completely different methods of sharing folders in Linux with completely different configuration files. Classic shares and Nautilus-share ( Nautilus > Sharing Options). Some of the things you want to do can be accommodated in Nautilus-share but those things that require per share authentication cannot. So stick with Classic Sharing - smb.conf.

---

