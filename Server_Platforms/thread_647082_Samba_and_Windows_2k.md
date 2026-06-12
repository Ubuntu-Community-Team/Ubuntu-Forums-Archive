---
title: "Samba and Windows 2k"
date: 2007-12-21
forum: Server Platforms
---

### Post by sinverarity on 2007-12-21
I feel really stupid as they'res hundreds of samba setup websites out there, but none of them are really answering what I need to know, and I'm not sure if this is the location to start this topic.. 

Here is my problem, I'm using a Windows 2k server, for domain admin, dhcp, dns, etc, and want to migrate my file server into a ubuntu server. 

I want to be able to assign users folders, or a general public folder, and assign rights via the Windows 2k AD. 

Help.. This is where I get screwed up.. Do I need to install LDAP for authentication, or can I use Samba to share the directory and assign security with Windows. 

And this is really bad, as I'm linux stupid, but getting better. I setup the LDAP once and blew out my AD on Win2k. 

Help guys, I've tried to search, but I'm not finding enough information to answer my question, or simply not understanding what I am reading. 

Thanks..

---

### Post by sinverarity on 2007-12-21
I just wanted to add.. I don't require users to log into the linux server, ever. All authentication will happen via Win2k..

---

### Post by HermanAB on 2007-12-21
Go to the Samba web site and read the Official Howto.  It is all in there.

Cheers,

Herman

---

### Post by koenn on 2007-12-22
here's a quick start guide :
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)

---

