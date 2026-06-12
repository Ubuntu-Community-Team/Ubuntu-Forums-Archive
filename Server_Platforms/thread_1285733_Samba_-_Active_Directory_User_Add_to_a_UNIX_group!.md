---
title: "Samba - Active Directory User Add to a UNIX group!"
date: 2009-10-08
forum: Server Platforms
---

### Post by ksudbury on 2009-10-08
Hi Guys, 

Let me explain my setup... We have a 2003 SBS box and a Samba server, the 2003 Server does the Active Directory authentication for the Linux box, which is working fine for samba and local auth and SSH. 

However, I need to add a user from Active Directory (a virtual user really), to a local group. Now this does not seem to be easy, I can't just usermod the Active Directory user to add a group as I get "User not found in /etc/passwd" or similar error. 

Having poked around on google I have found that most people are saying you need to do this from the Active Directory server, but how is the AD server going to be aware of the Groups on my Linux server?? 

Thanks In Advance!

---

### Post by ksudbury on 2009-10-09
Anyone?

---

### Post by HermanAB on 2009-10-09
You have to create the group in the directory server in the same OU as the user account and make the user a member of the group.  When the user logs in to Linux again, this information will be available.

---

