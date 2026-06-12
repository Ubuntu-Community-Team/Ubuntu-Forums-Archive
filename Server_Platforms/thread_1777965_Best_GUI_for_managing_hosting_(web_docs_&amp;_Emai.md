---
title: "Best GUI for managing hosting (web docs &amp; Email)"
date: 2011-06-08
forum: Server Platforms
---

### Post by NetDoc on 2011-06-08
Hey gang, 

I just installed an Ubuntu 11 server with SSH, LAMP and E-Mail Server. Easy to do and configure. Now I want an open source GUI to manage hosting like Plesk or CPanel. I see that Ubuntu frowns on WebMin and I don't know anything about ebox. I have some time before I have to deploy this server... what are your thoughts? 

I want to use virtual hosting.
I want to offer Horde or the like for Web Mail. 
I want to allow other admins access to the backend.

I don't like how Plesk takes over the entire server. Very restrictive. I also don't like the way it kludges up the system. I haven't used CPanel in a long time, but I didn't like it then and I don't like being hostage to either financially.

---

### Post by NetDoc on 2011-06-08
No ideas at all? Are there really no options here?

---

### Post by arrrghhh on 2011-06-08
> **NetDoc said:**
> No ideas at all? Are there really no options here?

Well I would wait *at least* 24 hours before bumping a thread, it's just courteous.

Second, I was going to respond to this thread and recommend WebMin, but it seems you've already explored that avenue and ruled it out.

People talk about Zentyal a lot around here, but I'm not very well versed in it - and as I understand it, you can't just 'install' Zentyal on an already existing server, you'd have to pillage and start over.  (Don't quote me on that, it's just my understanding from what I've gleaned ;)).

---

### Post by NetDoc on 2011-06-11
It wasn't meant to be a "bump" but to express my frustration at having absolutely no good alternatives out there. Ubuntu does not like Webmin and you have to go through hoops to install it. 

If anyone has used either Webmin or Ebox, please comment on their advantages and disadvantages. This is on a server with 2 quad core 3.0 Ghtz Xeon processors, 16 Gigs of RAM and 4 1Tbyte SATA drives set in a 10 RAID. It will be a LAMP and Email server for about 75 domains. I will be moving away from a Plesk server and then reformatting it and turning it into a SmartHost for SMTP.

---

### Post by arrrghhh on 2011-06-11
> **NetDoc said:**
> It wasn't meant to be a "bump" but to express my frustration at having absolutely no good alternatives out there. Ubuntu does not like Webmin and you have to go through hoops to install it. 

If anyone has used either Webmin or Ebox, please comment on their advantages and disadvantages. This is on a server with 2 quad core 3.0 Ghtz Xeon processors, 16 Gigs of RAM and 4 1Tbyte SATA drives set in a 10 RAID. It will be a LAMP and Email server for about 75 domains. I will be moving away from a Plesk server and then reformatting it and turning it into a SmartHost for SMTP.

Hrm... I didn't have to jump through any hoops for Webmin.  Download the .deb from their homepage, dpkg -i it... that was pretty much it for installing.

If it fits your needs, there shouldn't be any issues installing/using it - one caveat, do not update your system using Webmin.  I think that's why Ubuntu stopped supporting/recommending it, their update system broke away from the standard - someone correct me if I'm wrong here, but I use Webmin for checking the status of my system and configuring stuff like Samba.

I don't use it frequently, but it should fit your needs - it's pretty flexible.

---

### Post by NetDoc on 2011-06-23
> **arrrghhh said:**
> I don't use it frequently, but it should fit your needs - it's pretty flexible. Since it seems to be the only thing out there, I tried it. As for letting it "update" my system, it did a pretty good job of it. I am fairly new to Ubuntu/Linux administration at this level since I usually have others do it for me. This is my first LAMP server and the learning curve is high at the moment. I have installed the first domain, and it works. I don't like the root directory I have given it (I forgot to use httpdocs or similar) and will probably recreate it to be a bit more uniform for the future.

---

### Post by NetDoc on 2011-06-23
Oh yeah, I haven't got it's email function worked out yet, but I am certain I will. Are there any really good tutorials for Webmin?

---

### Post by i.r.id10t on 2011-06-23
I'd ditch webmin and go for ISPConfig

Does it all - DNS, mail, mx records if needed, web space, email login, etc.

---

### Post by arrrghhh on 2011-06-23
> **i.r.id10t said:**
> I'd ditch webmin and go for ISPConfig

Does it all - DNS, mail, mx records if needed, web space, email login, etc.

What about SMART monitoring?  Or some of the other server management pieces like samba and NFS?

I don't really use webmin frequently, but that is why I use it...

Edit - 
To NetDoc - as for tuts, I never needed one but googling around turns up...

[Use Webmin for Linux Administration](http://www.sitepoint.com/webmin-linux-administration-1/) and [System Administration with Webmin](http://www.linuxjunkies.org/adminstration%20Howto/webminguide/book1.htm)

---

### Post by OKKARE on 2012-04-09
If you're running your system with a GUI, there is Rapache for setting up your sites. ([http://www.webmaster-forums.net/server-management/apache-gui-ubuntu](http://www.webmaster-forums.net/server-management/apache-gui-ubuntu)) Looks pretty easy, I might try it, and I like that it's pretty minimal and not cluttered with features I'll get lost in like other web-based ones.

I also recall something called mysql administrator or the like that you can run on your home PC (not on the server) to access it. Can't find the link now, but it may be in the Ubuntu repos.

As for mail, looked to hard yet.

---

