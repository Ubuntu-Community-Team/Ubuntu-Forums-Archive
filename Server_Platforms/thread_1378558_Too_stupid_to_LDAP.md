---
title: "Too stupid to LDAP?"
date: 2010-01-11
forum: Server Platforms
---

### Post by RichardCL on 2010-01-11
Dear Forum,

I've been struggling for some time now with what I thought would be a simple task. It seems that Ubuntu can be used for all sorts of really advanced stuff but the basics are missing... or perhaps I'm just missing something obvious.

I just need a tutorial that will help my store my contacts on an Ubuntu server so that Evolution (on my Ubuntu machines) and Outlook (on my Windows machines) are always up to date.

Anyone point me to a tutorial for installing SQL or LDAP such that I can use the address book with multiple email clients and possibly a cell phone?

Everything that I've found so far is talking about authentication over ldap and lots of config work. Surely there is a simple installable package...???

I'm using Karmic server.

---

### Post by cariboo on 2010-01-11
Moved to server platforms, as the question is server related.

---

### Post by Iowan on 2010-01-11
[Here]("https://help.ubuntu.com/community/OpenLDAPServer") is a help page for LDAP server, an [old one]("https://help.ubuntu.com/community/LDAPClientAuthentication") on client authentication, and another [kinda-old]("https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html") one on Samba/LDAP. LDAP is still on my To-Do list... I'm claiming time shortage as an excuse... ;)

---

### Post by RichardCL on 2010-01-15
> **Iowan said:**
> [Here]("https://help.ubuntu.com/community/OpenLDAPServer") is a help page for LDAP server, an [old one]("https://help.ubuntu.com/community/LDAPClientAuthentication") on client authentication, and another [kinda-old]("https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html") one on Samba/LDAP. LDAP is still on my To-Do list... I'm claiming time shortage as an excuse... ;)

That is great. The thread link from the tutorial seems to be what I need. I'm just missing two things

dc=example, dc=com
Here I have a server that is used on a local network. I just plugged everything in and starting to learn so I don't have a domain name on the server. I use the IP address 192.168.*.25 to access the server and that works e.g. for SSH. The router is configured to use DCHP and always assign the same names by MAC address. Can I use dc=192.168...?

I also have a dynDNS account but would need to know which ports to forward in the router if LDAP wants to attach by internet. The address would be example.dyndns.com do I then use dc=example, dc=dyndns, dc=com?

Is there not a central place to enter the domain? At the moment I'm searching all the config files to find the dc= and o: not very user friendly.


All I want to do is have an address book on my server that Outlook and Evolution can work with. The tutorials all begin with user admin and website passwords. I use mySQL for the web and Ubuntu manages passwords nicely. Can I just install LDAP for Outlook?

---

### Post by munky99999 on 2010-01-15
Afaik you cant setup OLDAP on karmic easily. There's a fairly manual procedure for setting it up.

[http://ubuntuforums.org/showthread.php?t=1313472](http://ubuntuforums.org/showthread.php?t=1313472)

I have done what's in that post and do believe I got it running. My ultimate purpose for getting oldap running was all busted up; so I'm not certain.

---

### Post by RichardCL on 2010-01-16
Weird really, so many complicated tasks are easy in Ubuntu. I know very little about computers but managed to configure, compile and install my WLAN drivers. I have a website running on my own server with SQL.

It seems Ubuntu is missing the basic requirements for business application (decent contacts management and a good "Powerpoint").

I must be missing something.

It seems I'm going to have to wait for the next LTS and then compile Zimbra because I can't go back to 8.04, it doesn't support my web applications.

Every cheap mobile phone has a basic contacts sync.

---

### Post by samosamo on 2010-01-16
Linux is weak in the area of "groupware."  Installing LDAP is easy.  Building and using the directory it serves you is difficult.  Just use a groupware solution like Microsoft AD, etc.

---

### Post by RichardCL on 2010-01-16
I sort of got it to work so far:

1. Change the "9.10-style" installation to "Jaunty-style" using this [http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala]("http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala")

2. Add a user and match with Evolution [http://www.debian-administration.org/users/lee/weblog/32]("http://www.debian-administration.org/users/lee/weblog/32")

Now I can see the database from inside evolution but can't write to it.

---

### Post by frenchn00b on 2010-01-17
> **RichardCL said:**
> Dear Forum,

I've been struggling for some time now with what I thought would be a simple task. It seems that Ubuntu can be used for all sorts of really advanced stuff but the basics are missing... or perhaps I'm just missing something obvious.

I just need a tutorial that will help my store my contacts on an Ubuntu server so that Evolution (on my Ubuntu machines) and Outlook (on my Windows machines) are always up to date.

Anyone point me to a tutorial for installing SQL or LDAP such that I can use the address book with multiple email clients and possibly a cell phone?

Everything that I've found so far is talking about authentication over ldap and lots of config work. Surely there is a simple installable package...???

I'm using Karmic server.


I am developping an installer for LDAP and many server services, but still it doesnt work perfect. maybe in some time LDAP will easy to be installed with it:
[http://easyldap.exofire.net/files/installer/easyldap-installer.sh](http://easyldap.exofire.net/files/installer/easyldap-installer.sh)
 
[screenshot]("http://easyldap.exofire.net/files/installer/shot01.jpg")

---

