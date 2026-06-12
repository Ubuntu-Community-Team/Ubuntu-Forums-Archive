---
title: "New Server Ideas"
date: 2012-03-17
forum: Server Platforms
---

### Post by bubylou on 2012-03-17
I just built a new computer for myself and will be suing my old computer for a Ubuntu server. I already had a Ubuntu server on an old dell and this will be replacing it. However i don't know what i want to do with the old server. Any ideas? Some ideas i had were, proxy server to use for my new servers internet access, or maybe go with a full blown cluster setup. Let me know what you think

Old Server
dual core pentium
1.25gb
75gb

New Server
dual core athlon
4gb
750gb

---

### Post by d4m1r on 2012-03-17
Wordpress - blog software that makes for a great website
MediaWiki - wiki software
OpenVPN - VPN software
Teamspeak 3 - VoIP software

These are only examples of the many things you can run off a Ubuntu sever, check my site in my signature for a sample ;) Also, the standard things (Apache server to run the website, FTP to transfer files, etc) can be very useful in and of themselves.

---

### Post by bubylou on 2012-03-17
Im looking for something that will be beneficial to my other server not just generic packages i could install on any server.

---

### Post by 2F4U on 2012-03-18
You could setup the old server to monitor the other machines in your environment using software such as nagios or icinga.

---

### Post by bubylou on 2012-03-18
*I may look into that but im also looking into a cluster setup a the moment.*

---

### Post by Holdolin on 2012-03-18
A cluster setup for 2 computers seems like a lot of unnecesary work to me, though I have been very interested in the idea of clustering.  If you plan on adding on to your server farm, clustering would likely come more into play.

---

### Post by bubylou on 2012-03-18
Yea it would be a lot of work but i think would be a very good earning experience since it is used in almost all enterprise setups. Although i may just use it for dhcp or dns or a proxy just to give it some use. In any case i would like something on the old server that benefits the other new server. Having them communicate with each other or something along those lines. I may just end up giving them each different roles.

---

### Post by Dangertux on 2012-03-18
A word of warning with clustering like that (two machines) it's quite easy to end up with split brain syndrome. Where both machines think they are the master.

Usually more modern clustering techniques utilize three or more machines for this reason. To provide a sort of majority rule... If you will.

---

### Post by bubylou on 2012-03-18
Well maybe clustering is a step to far but i would like to do more than just have two servers running different things if possible

---

### Post by bubylou on 2012-03-18
bump

---

### Post by bubylou on 2012-03-19
I think i will explore options on my own for a while but for now it will be used as a test server.

---

### Post by SeijiSensei on 2012-03-19
Do you have a mail server?  I wouldn't trust my mail to an outside party.  I'm much happier with it residing on a box in my house. Plus I can use things like procmail as the delivery agent or run a listserver with majordomo.

Need an internal DNS server for your LAN?  That's another good use for a old machine.  Put that together with the mail server.  

File-sharing via NFS and Samba?

---

### Post by bubylou on 2012-03-19
A mail server might be a bit over kill for me but i will certainly look into it. What would be the purpose of an in house DNS server. I have never really thought about setting one up. I have samba on my other server.

---

