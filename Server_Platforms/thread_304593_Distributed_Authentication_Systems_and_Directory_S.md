---
title: "Distributed Authentication Systems and Directory Services"
date: 2006-11-22
forum: Server Platforms
---

### Post by charlie. on 2006-11-22
A few years ago, I had never heard of Linux.

A few months ago, I had never used Linux.

A few weeks ago, I had only used Linux from the command line, through SSH, on a single Intranet web-server.

A few days ago, this all changed!

I have moved 99% of my development-and-administration work flow to my shiny-new-edgy-desktop. My Linux server is still up and kicking and doing a whole lot more than serving its original reason for being: our corporate Intranet. I've even ported my C++ code to Linux, learned sCons and bludgeoned my project into a state where it compiles, links, run and passes the tests on GCC 4.1. Perhaps there's some hope for Tux after all.

Operating systems are like cars. Once you've upgraded, you can't go back to that old bucket-o'-bolts. This is becoming increasingly apparent - every time I have to fight with my Windows desktops and domain controller on this network. I have seen a future for Linux on my network and my No.1 goal is to kill Active Directory. (AD is actually not the problem, it's all the **** that you have to run to make it work, like M$ solutions for DHCP and DNS that simply don't work properly or stop working intermittently for no apparent reason!)

My first goal is to learn a bit more about authentication (specifically distributed authentication schemes) on Linux - how it's supposed to be done. I started down this path by reading up on passwd, then an old dinosaur called NIS or Sun Yellow Pages. Neither of these appeared to be (A) modern or (B) particularly secure. I'm not quite sure where to go next.

What authentication systems should I be researching? Which ones are used today? In this age, the age of SSH and Kerberos, I expect something a little more elegant than NIS, with its unencrypted traffic and text file data storage.

Ultimately, I will have to find a way to allow my windows clients to authenticate against my Linux directory service.

Please help me know where to look next.

---

### Post by Koybe on 2006-11-23
I would tell you to have a look to an LDAP authentication. You can centralized authentication for a large number of service using this... finally it's a directory server.

- Just have a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=179556")
- [A nice project]("http://directory.fedora.redhat.com/") (linked to fedora instead of ubuntu)

NIS is nice for a full linux environnement.

---

### Post by charlie. on 2006-11-24
Windows can authenticate against Kerberos, or Active Directory (which is built on LDAP and Kerberos) but not LDAP alone.

I've managed to get Kerberos up and running on its own, but I don't see why LDAP is necessary. If Kerberos is providing your authentication, LDAP only provides a directory service, which would be redundant in our business because of the CRM system we run.

Perhaps I'm not seeing the whole picture here...

---

### Post by Koybe on 2006-11-24
I'm not sure I understand all your needs. But then you'll need authentication trough a workgroup or a domain which only can be done via samba... 
There is no way to authenticate windows users trough NIS... or if so i'd like to know how! :)

---

### Post by charlie. on 2006-11-24
You can use command-line tools from the Windows XP disk to configure windows to authenticate to ANY Kerberos KDC. You don't need Samba or Active Directory.

Microsoft's Sevices for Unix do (apparently) include a NIS client and, believe it or not, server! (I think they charge for those, however - which is probably a violation of a whole bunch of open source licenses)

---

### Post by elst on 2006-11-24
A lot of different network applications can use information attached to the user records in an LDAP directory, which is a critical advantage. For example LDAP is now the standard for contact directories, so your IM, VoIP and e-mail systems from different vendors can all potentially use the same directory that stores user accounts for Kerberos.

More broadly, LDAP is a heirarchical storage system that can store other interesting information that is not related to user accounts, such as configuration settings for client operating systems.

The Ubuntu Directory Services team is currently starting to pull the pieces together for manageable Kerberos and LDAP services on Ubuntu, but there's a long way to go before LDAP and Kerberos on Linux are as integrated and easy as on the Microsoft platform.

FWIW, I beleive that Microsoft's SFU is based on BSD licensed code, so it's a legitimate product. I haven't used it myself, so couldn't comment on how well it actually works etc.

---

