---
title: "Domain Controller"
date: 2007-10-08
forum: Server Platforms
---

### Post by codetiger on 2007-10-08
Hi, everyone...
                    Thanks for all you guys for helping me on setting up my serve. Now I am happy that I am already 80% in my server setup. I successfully configured 1) Internet sharing with firewall, 2) File Sharing with Xp machines using Samba, and 3) Blocking some websites in my network, 4) DHCP server, 5) LAMP server and few more in our studio.

No that I have not completely replaced my Win2k3 machine yet. Coz I still have the domain Controller left in my server. When I configure it with samba, it creates a workgroup instead of a Domain. I am struggling to do with with my samba config. Can anyone suggest an idea to do the following.

1) Create a domain
2) create user profiles for xp machines
3) now again I need to set privileges for file sharing for the users.

---

### Post by HermanAB on 2007-10-08
Samba can do Win2000 style domain control, but cannot do Win2003 domain control yet.  This feature is still experimental in Samba version 4: [http://news.samba.org/releases/4.0.0alpha1/](http://news.samba.org/releases/4.0.0alpha1/)

Cheers,

Herman

---

### Post by codetiger on 2007-10-08
ok, great thanks...

---

### Post by netlogic on 2007-10-08
Your current option is run it as a NT4 style domain, but using CIFS.
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

