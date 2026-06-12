---
title: "How to install NFS security realm : KERBEROS?"
date: 2009-09-13
forum: Server Platforms
---

### Post by frenchn00b on 2009-09-13
Hello

I followed this howto, but the security is only based on DNS, thtat's all.

I would like to not to base it on DNS but only on teh mac address
[https://help.ubuntu.com/community/Samba/Kerberos](https://help.ubuntu.com/community/Samba/Kerberos)

is that possible? would you have any configuration that u are using and working.?

thank you:guitar:

---

### Post by tlarkin on 2009-09-14
May I ask why you want to run it by MAC address?  Those can be spoofed rather easily.  Really, DNS is the way to go.  Besides in your DNS database you are assigning a static IP, and a FQDN to a MAC address anyway.

---

### Post by frenchn00b on 2009-09-14
> **tlarkin said:**
> May I ask why you want to run it by MAC address?  Those can be spoofed rather easily.  Really, DNS is the way to go.  Besides in your DNS database you are assigning a static IP, and a FQDN to a MAC address anyway.

ahh so kerberos means automatically that I install a DNS server? but the router does it? 
would you have good advices for kerberos install? I pass up to testing in the thread , but testing still not done. I cant with those key or authorization ... :(

---

### Post by tlarkin on 2009-09-14
Well kerberos just issues tickets to clients after they authenticate to a specific server.  So if you were running some sort of directory services that was fully "kerberized" then once your user account authenticated you would be issued a kerberos ticket.

I can't say that I know everything about networking but from what I do know, I have always set up kerberos realms by DNS names.

Are you trying to issue kerberos tickets to map NFS shares?

You can have your router run DNS, just point your clients to the IP of the router for their DNS servers.

---

