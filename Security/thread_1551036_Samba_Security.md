---
title: "Samba Security"
date: 2010-08-11
forum: Security
---

### Post by needhelppeeps on 2010-08-11
I like samba because it makes file sharing so easy.
So far
1) I have samba set to accept connections from only 127.0.0.1 and 3 static (private) IPs on my LAN.
2) No ports are open on the router's WAN interface

How do I also set an account lockout after X attempts? I have PAM running and it does this on console logins. I want to find something that does this with smb. I hate leaving anything out there with no brute force protection even if the odds of anyone jumping on my LAN with one of those 3 IPs is unthinkably low.

---

### Post by bodhi.zazen on 2010-08-11
I think the easiest method would be using iptables to drop attempted new connections after 3 or 5.

You can possibly adapt a rule set if you wish.

[http://bodhizazen.net/Tutorials/iptables/#Additional_Tips](http://bodhizazen.net/Tutorials/iptables/#Additional_Tips)

scroll down a bit to the ssh section.

---

### Post by HermanAB on 2010-08-12
Samba easy!?

One day, you should do yourself a favour and try NFS.  When you look on the web for tutorials and guides on NFS, you will find that there aren't any - it is so simple that nobody bothers to write anything about it...

---

### Post by cariboo on 2010-08-12
The first time I setup samba several years ago, it took me several hours, but now it's just set and forget. I have been using the same basic smb.conf file for years, it just a matter of doing a bit of editing for each different situation.

---

### Post by bodhi.zazen on 2010-08-12
> **HermanAB said:**
> Samba easy!?

One day, you should do yourself a favour and try NFS.  When you look on the web for tutorials and guides on NFS, you will find that there aren't any - it is so simple that nobody bothers to write anything about it...

> **cariboo907 said:**
> The first time I setup samba several years ago, it took me several hours, but now it's just set and forget. I have been using the same basic smb.conf file for years, it just a matter of doing a bit of editing for each different situation.

Depends on what you are familiar with and what, if any, configuration options you need. It also depends on if your clients are all Linux or windows as well, and also if you need kerberos.

I can set up NFS or samba on a small LAN (linux only) with kerberos in 15-20 minutes (server side), takes 5-10 minutes client side (each).

Recently I discovered autofs, which I find to be a very nice option.

If you are a new user in a mixed linux / Windows clients expect to spend a little time with configuration. The basics can all be done via a graphical interface.

---

### Post by cariboo on 2010-08-13
For my personal network, I have a mix of Linux and Windows systems, I use samba for the windows systems mostly for backups, and nfs for the linux systems. depending what the system is used for, some shares are mounted using /etc/fstab, and others system they only get mounted as needed.

When I first started using samba, I used swat, it's in the repositories, to set up shares. The reason I stopped using it was that it has to be run as root via a web browser.

---

