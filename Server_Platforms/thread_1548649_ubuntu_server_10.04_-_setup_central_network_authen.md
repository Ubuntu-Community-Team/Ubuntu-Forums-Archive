---
title: "ubuntu server 10.04 - setup central network authentication"
date: 2010-08-08
forum: Server Platforms
---

### Post by willrowland on 2010-08-08
I want to use Ubuntu Server 10.04 as logon server and share authentication - like say a Windows Server running Active Directory.  I have located several items for older versions of server but thinking it would be best to have up to date information and a streamline process.

---

### Post by stlsaint on 2010-08-08
You are looking for[ kerberos]("https://help.ubuntu.com/community/Samba/Kerberos") with [openldap]("https://help.ubuntu.com/community/OpenLDAPServer"). hopefully :popcorn:

---

### Post by willrowland on 2010-08-08
I have setup krb5 but it seems to require Winodws AD to work.  I want to get away from Windows but looking for a way to have a single sign-on/access permissions from Windows Clients to Ubuntu servers - setting up domain authentication.  This will be the first steps to moving our clients from windows to Linux.  I am not a Certified Linux Administrator, however have a pretty good understanding.  I do not deploy anything that I have not tested on a DEV server first.  I am looking to deploy this option in the next month or so, I am hoping to find best practices.

I have setup SAMBA and shared with windows desktops, just permissions is the final thing to complete transition ability.  I have limited security with with smb.conf or complex file/continuous edit required with my understanding.

Does this make since?

---

### Post by davidg121 on 2010-08-08
My personal experience with all of this put me towards using SME Server for my domain controller, 2 file servers using ubuntu 10.04, and 1 ftp using ubuntu. I had a hell of a time setting up the domain controller the way i wanted it under ubuntu 10.04. It was mainly setting up a centralised login... SME server was just far easier considering by default it runs LDAP flawlessly. Literally, you go through the setup and give it the info it needs and it sets everything up for you. Then you can just point the fileservers (if you have any) towards the SME server. Granted yes you can do this with ubuntu 10.04, but I like easy and time efficient things. But if you still want to use ubuntu 10.04, id check these out...

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[http://ubuntuforums.org/showthread.php?t=1499753](http://ubuntuforums.org/showthread.php?t=1499753)

the second like is a simple stupid version of setting it up.

---

### Post by beetlejuice321 on 2010-08-08
Thanks so much for your post davidg121!  

I am also in search of a Linux server for file sharing and possibly central authentication.  I wasn't aware of SME Server before, which appears build on CentOS, but it looks like it will work well. 

[http://wiki.contribs.org/SME_Server:About](http://wiki.contribs.org/SME_Server:About)


You know, for all the work and promotions Canonical is putting into Ubuntu server.  Everything from their support agreements to [Landscape]("http://www.canonical.com/enterprise-services/landscape"), you would think there would be a lot more stuff that just works.

So far all I found easy to setup in Ubuntu is a LAMP (web-server), SSH or FTP server.  Thats not a lot.  Samba and LDAP are both almost completely absent.  Even remote management can be difficult, and I wish they included tools like Webmin in the repositories.

I wish there was more continuity with Linux servers.  I wanted to see Ubuntu become a real standard in the Linux server market, but I am beginning to have my doubts.

---

### Post by beetlejuice321 on 2010-08-09
I also wanted to point out EBox.  It hasn't been around as long as SME Server but it is based on Ubuntu and looks very promising.  Its open source and freely available, but the company behind it also offers paid support, which can be a good point for some smaller companies afraid to try Linux servers.

Per their site...

"eBox Platform can act as a Gateway, Infrastructure Manager, Unified Threat Manager, Office Server, Unified Communication Server or a combination of them. One single, easy-to-use platform to manage all your network services."

"eBox tries to provide a higher abstraction layer for the System Administrator. It's meant to be easily used by users who have never administrated a Unix system before."

This is a much needed niche in the Linux server market, so I am very glad to see someone taking initiative to make simpler server administration.

The stable version is currently 1.4 (based on Ubuntu 8.04), but the new beta 1.5 was just released which is based on Ubuntu 10.04.  Check it out.

[http://distrowatch.com/?newsid=06221](http://distrowatch.com/?newsid=06221)
[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

---

### Post by HermanAB on 2010-08-09
Mandriva and Suse both have Small Business Servers, where you can configure everything with a mouse, same as with a Windows Server.  The Ubuntu server edition is only good if your needs are simple, you want to learn, or if your time is worth nothing.

---

### Post by willrowland on 2010-08-09
Thank you for all the great post. I have started looking into eBox which seems to have UI interfaces, however still using the base Ubuntu program and commands (but in a UI). I will continue to investigate after download and install complete.  I am not a big RH fan just because I have primarily used Debian Linux - comfortable with Debian.  Is there any information which would make SME a better choice than eBox?

---

### Post by druhboruch on 2010-08-10
I found lots of resources here:

[http://www.opinsys.fi/en/itch-for-better-user-management-in-ubuntu](http://www.opinsys.fi/en/itch-for-better-user-management-in-ubuntu)

---

### Post by davidg121 on 2010-08-10
My problem with ebox is that its still using old versions of everything. Including samba, which gives more of a pain with expansion to windows 7 systems. Although i will admit that i did like the ebox UI a bit more than the SME Server.

---

### Post by beetlejuice321 on 2010-08-10
EBox follows LTS releases, which in my opinion is a good thing.  As business goes, you just want to install a server and not have to worry about it for a few years (other then security updates).  Version 1.4 is Ubuntu 8.04.  Version 1.5 is Ubuntu 10.04, which is very new as of today.

From what I have read SME Server has been around since 1999, is stable, and has a strong following. But I agree I prefer debian administration and  package management to RPM based systems.  So for us the only option I know of is EBox.  While EBox is new, it may be just as good as SME Server, but who knows.


**On a side note:**

I am new to these business server distro's, but they are a much needed niche!  Linux is great to customize with your desktop etc, but who really wants to mess around with a business systems where your customized installations can break with one OS update, or make things difficult to setup (you ever try to manually setup Samba + LDAP)? Besides time is money.  We all know that Microsoft Active Directory can't be beat for large corporate environments, there is just to much interoperability that makes administration so much easier for large networks.  

However on the other hand, small businesses are perfect for Linux servers.  They have little to no need for fancy policy enforcement to lock down workstations.  And Linux servers can meet their needs easily using Samba, LDAP, Apache, Groupware services, etc.  In fact Linux provides far more services than a traditional Windows Server right out of the box!

I really hope that projects like EBox and SME Linux start getting more popular.  In fact if Canonical wanted to really make money, they would start making a small business version of Ubuntu Server that actually worked, and start providing paid support targeted at small businesses.  If they did that I could/would actually start deploying Ubuntu in small businesses I support!

---

