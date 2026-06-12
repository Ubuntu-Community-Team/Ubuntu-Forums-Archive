---
title: "Resource for giving you tasks and projects"
date: 2021-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by deads2 on 2021-10-17
Hi everyone,

I'm curious to know if anyone could point me to any resource that would be able to give you projects/tasks that you carry out.

The thing with being new to Ubuntu/Linux is that I'm not fully aware of all the possibilities that are capable with Linux. I learn by doing and having fun (as most people do). 

So I'm keen to have a resource give me different project to do with minimal assistance so that I am forced to find the answers, build and figure stuff out myself.

Anyone have any suggestions?

Even if someone had a list of different capabilities/projects that can be carried out on Linux that I could sink my teeth into. Doesn't have to be fully comprehensive, but a decent list to allow me to get started.

---

### Post by vanadium on 2021-10-17
Not quite clear to me what you are actually looking for.

---

### Post by deads2 on 2021-10-17
Essentially to be told to create/do something using Ubuntu.  

I'm not aware of everything that can be done. So basically maybe a mentor or tutor that gives you different projects... or a course.

I just don't know where to start. I've learned basic commands. I know how to navigate my way around the system in the terminal... but so far that's it. I want to actually use Ubuntu to do some cool stuff with. Again, I don't know what is possible and don't know where to start.

Random question I know haha, but I'm just looking to learn by doing. But don't know what can be done.

---

### Post by coffeecat on 2021-10-17
Not a tutorial. *Thread moved to **Ubuntu, Linux & OS Chat**.*

---

### Post by deads2 on 2021-10-17
Edit to anyone thinking of a reply. I'm looking to get into network administration and ultimately specialize in cyber security. So I guess my question is, what kind of abilities should I have on a linux to be able to go in that direction?

---

### Post by TheFu on 2021-10-17
> **deads2 said:**
> Edit to anyone thinking of a reply. I'm looking to get into network administration and ultimately specialize in cyber security. So I guess my question is, what kind of abilities should I have on a linux to be able to go in that direction?

Join your local DefCon group and become part of that community. Ask there.
For Linux administration, I have a list of beginner projects: [https://blog.jdpfu.com/2010/12/10/linux-related-presentation-ideas-needed](https://blog.jdpfu.com/2010/12/10/linux-related-presentation-ideas-needed) - there's about 50 ideas there.  If you get a book for almost any Linux Certification program, there are lots and lots of "projects" to learn.  I have the _LPI Linux Cert_ book from O'Reilly.  Plenty in there.

But the list is almost endless.  Setup a vpn - use at least 3 different VPN tools with 1 being a mesh VPN.  Connect your tablet, phone, Windows and Linux computers to the VPN.  Setup different network zones for VPN access - limit different users to those different zones.
Setup centralized LDAP authentication for Linux.  Don't use MS-AD or any php webapps.
Setup print servers that are automatically discovered by Windows and Linux. Make the Windows drivers automatically installed.
Do you have a media center, music server, read-it-later server, wiki server, corporate document management or file replication tool (seafile, owncloud, nextcloud). Do you have an email server for sending and receiving internet email?  A reverse proxy? A VoIP server?
Setup a backup server that "pulls" backups from all the clients on the network.  Why are "pulled" backups required? Don't use any file sharing protocol like CIFS or NFS or AFS or DFS for this solution.  Restore a system from your backups, to the state it was last month.

---

### Post by deads2 on 2021-10-18
> **TheFu said:**
> Join your local DefCon group and become part of that community. Ask there.
For Linux administration, I have a list of beginner projects: [https://blog.jdpfu.com/2010/12/10/linux-related-presentation-ideas-needed](https://blog.jdpfu.com/2010/12/10/linux-related-presentation-ideas-needed) - there's about 50 ideas there.  If you get a book for almost any Linux Certification program, there are lots and lots of "projects" to learn.  I have the _LPI Linux Cert_ book from O'Reilly.  Plenty in there.

But the list is almost endless.  Setup a vpn - use at least 3 different VPN tools with 1 being a mesh VPN.  Connect your tablet, phone, Windows and Linux computers to the VPN.  Setup different network zones for VPN access - limit different users to those different zones.
Setup centralized LDAP authentication for Linux.  Don't use MS-AD or any php webapps.
Setup print servers that are automatically discovered by Windows and Linux. Make the Windows drivers automatically installed.
Do you have a media center, music server, read-it-later server, wiki server, corporate document management or file replication tool (seafile, owncloud, nextcloud). Do you have an email server for sending and receiving internet email?  A reverse proxy? A VoIP server?
Setup a backup server that "pulls" backups from all the clients on the network.  Why are "pulled" backups required? Don't use any file sharing protocol like CIFS or NFS or AFS or DFS for this solution.  Restore a system from your backups, to the state it was last month.

Thanks man. Exactly the kind of answer I was hoping for.

---

### Post by TheFu on 2021-10-18
> **deads2 said:**
> Thanks man. Exactly the kind of answer I was hoping for.

And never forget, just because you follow some guide on the internet, no matter who wrote it, never, ever, assume it is actually secure.  Run your own attacks against any service you make available on the internet. If you can get in, it will be trivial for others to get in as well, even if they don't know your LAN setup.  Figuring out a LAN setup isn't THAT hard once the router is pwn'd.   Er ... so I hear.  Of course, I wouldn't actually know anything about it.

If you care about security, don't put web sites on the internet.  Access to anything you run should have to use some sort of network authentication even to connect to those services.  Once someone gets into 1 system/container/whatever, they can use that to attack everything else on the same LAN, including the router.  So ... imagine someone gets you to use a full featured browser with local objects and javascript enabled (which is default for most browsers), now they can have part of that website perform network scanning to find other devices on the LAN.  With just the MAC for other devices, they can make a good guess about the equipment and look up vulnerabilities.  To keep you from noticing, they can compress the information and burst send it daily. 99.999% of people and companies wouldn't notice when 1MB gets pushed via an HTTPS POST somewhere. Light encryption can be implemented in javascript - doesn't need to be THAT great, just something more than ROT13 and compressed. There's all sorts of mischief possible if someone allows javascript and doesn't carefully firewall outbound traffic.  Everyone firewalls inbound traffic, but only paranoid network security guys firewall outbound traffic at home.  I do some of that, but not nearly enough.

Average people, including 90% of Linux users just don't know.

---

