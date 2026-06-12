---
title: "Active Directory logon &quot;No logon servers&quot; for a few minutes after starting up"
date: 2007-11-09
forum: Server Platforms
---

### Post by inselaffe on 2007-11-09
I have winbind, samba and pam configured so that I can log on with an active directory account. Whilst this does work, I have to wait a few minutes after Ubuntu has started before I can log on; if I attempt this sooner, I get a popup saying "no logon servers". There is no question that the server is not available at the time.

---

### Post by HermanAB on 2007-11-09
Uhmm, I have heard of that, but haven't experienced it.  Test your DNS responsiveness and pick a faster one, or change the password server entry in smb.conf to an IP address, so it doesn't have to do a DNS lookup.

---

### Post by vuul on 2008-03-27
I had this problem too on Gutsy
I solved it by adding this:

```
auto eth0
iface eth0 inet dhcp
```

to: /etc/network/interfaces

I assume that it was not in there by default because everything is being done through the Network Manager now.

---

### Post by bmobley on 2008-04-01
When I add the above line from the last post, I do not get a DHCP address assigned for some strange reason. I too have to log in locally and wait a few minutes before I can log into the domain. I am going to try a static IP and see if that will work.

---

### Post by bmobley on 2008-04-01
Even stranger: If I
sudo /etc/init.d/networking restart
The interface gets DHCP. 
So I guess this is where I went wrong:
I changed /etc/network/interfaces but instead of downing the interface or rebooting I just logged out and back on. I guess this just hosed the config somehow.

---

