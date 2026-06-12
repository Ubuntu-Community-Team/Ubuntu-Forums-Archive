---
title: "Anyone have updated info?"
date: 2008-02-14
forum: Server Platforms
---

### Post by sokraski on 2008-02-14
I have read through and tried many different ways of joining a MS AD.  Some posts are for previous versions, some were for other distros, etc...  I got it working once, but lost it on a reboot and now cannot reconnect.  I have reloaded and started from scratch several times.  Some posts use krb5-config, krb5-user, krb5-client, etc.. and some just use krb5-config.  Also some posts modify PAM and some don't. 

 Bottom line is, does anyone have an outline of exactly what needs to be changed, when to start/stop what service, what dependencies do I need,  what order to make changes, etc.. for gutsy and AD 2003.  This is putting the brakes on for getting linux into the work environment.  

I would like to start small, just a file and print server.  All logins should be handled by the AD so anyone logged into the AD can access the files and printer without having to log in to the ubuntu box separately.  Also, to keep all settings after a reboot (this seemed like a problem on a lot of posts.)

Also, thoughts on using something like sadms or likewise open.  I have tried both and both never seem to get it right.  

Any help would be greatly appreciated!  Please help me get linux in/MS out!  Thanks.

This may help if anyone would like to give me some examples (please mind UPPER/lowercases as this also seems to be conflicting in many posts):

AD,DNS, ETC...            server1.domain.com            192.168.1.10
Backup DNS                  server2.domain.com            192.168.1.11
Ubuntu File Server        ubuntu.domain.com            192.168.1.20

---

