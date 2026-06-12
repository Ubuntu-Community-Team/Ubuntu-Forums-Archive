---
title: "Recover OpenLDAP - Samba Domain Controller"
date: 2009-04-13
forum: Server Platforms
---

### Post by ifkm on 2009-04-13
Hello,

thanks to this great forum, helping me a lot! Especially the great tutorial for an OpenLDAP - Samba Domain Controller found here: [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

But there was some problem that I had to reinstall the server - following again the tutorial and now I wonder how I can restore my authentications settings. 

I thought that it should be enough to copy the content of /var/lib/ldap/* - but I guess this alone wont do it. So what else I have to recover (I have all the files from my last server) to get this working? DNS is working, also the samba file shares (with the proper restrictions).

Could it be a problem, that the server now has a new SID? How to recover the necessary parts?

Thank you in advance,

ifkm

---

### Post by ifkm on 2009-04-13
> **ifkm said:**
> Could it be a problem, that the server now has a new SID? How to recover the necessary parts?
I just found /var/lib/samba - copied the old working files there gave me at least now the same SID for the new installation like the old had - but didn't solved any of the problems.

My main problem is, that the windows xp workstations are not connecting to the domain - I can login only as a local user, but then opening the samba share with the samba/ldap user works fine. SO networking and DNS is working, also the users are existing.

Trying to login on the server with the old LDAP users shows me something like this:

> You are required to change your password immediatley (password aged)
Authentication information cannot be recovered
I think the first line was normal - not a problem, I guess the second line could have something to do with this.
But new created users works local just fine - but also not on the windows workstations, what is quite normal thinking that they are not proper connected to the domain.

I also tried to rejoin a workstation, also under a different name, to the Domain, also not working: Access denied. Of course, even if it would work, there should be a possibility to recover the old setup so that I don't have to rejoin them. So there is still some problem with the LDAP setup on the server. Any ideas?

---

### Post by ifkm on 2009-04-13
After some hours, restoring everything I could it still not worked, so I made a total new server by hand. Now I now, that I need a different backup solution.

Does somebody has an idea for an easy to use and working backup solution which is able to create a working server (so that even the windows workstation doesn't have to be rejoined) when everything breaks?

---

### Post by josir on 2009-06-05
Hi ifkm, I never achieve to backup a LDAP installation.

People says: backup is easy - just slapadd.
But restore is impossible :)

What is my solution: virtualization. I have an identical image of the server and every week, I create a new one. 

I have two partitions: a smaller one (2Gb) with the system and another with data. The data is backup with rsync twice a day. 

If something bad happens, I restore my backup image.
And then point the second partition to the backup image.

I think it's much simpler than this LDAP hell...

Just an insight.
Good Lucky,
Josir

---

