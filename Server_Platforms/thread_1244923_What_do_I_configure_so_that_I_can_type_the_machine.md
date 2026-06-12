---
title: "What do I configure so that I can type the machine name into the address bar"
date: 2009-08-20
forum: Server Platforms
---

### Post by TheOrangePeanut on 2009-08-20
Here is what I want to do.  I managed to set this up on my Arch machine but can't remember what I did.

Basically, I want to be able to open my web browser and type in the name of my web server on the network and be directed to the site it is serving.  As of now I have to type the IP address into the address bar.

As long as I'm asking a question, I've got another one.  Is Samba what is going to be necessary to map a folder on the network to a folder on the server in a Windows environment?  That is important for what I want to accomplish, and I'd like to avoid something as platform specific as Samba, but if that is my only choice then I need to know now so I can figure it out :)

Thanks

---

### Post by SoftwareExplorer on 2009-08-20
you need to edit /etc/hosts (you'll have to do that with sudo) and add a line that says
```
ip.add.res.s      nameYouWantToUse
```
on the machine you are running the browser on.

---

### Post by Bachstelze on 2009-08-20
> **TheOrangePeanut said:**
> 
As long as I'm asking a question, I've got another one.  Is Samba what is going to be necessary to map a folder on the network to a folder on the server in a Windows environment?  That is important for what I want to accomplish, and I'd like to avoid something as platform specific as Samba, but if that is my only choice then I need to know now so I can figure it out :)

Yes, but how is Samba "platform-specific"?

---

### Post by TheOrangePeanut on 2009-08-20
Forgive me, I thought smb was a MS protocol.  If I'm wrong, then thanks for setting me straight!

Is altering the hosts the only thing I can do?  Since this machine is basically going to be for 3 developers that is okay, but it'd be nice if I could set it up so every machine in the office could navigate to it without having to edit the hosts file manually...

---

### Post by cariboo on 2009-08-21
If you have a large enough network that editing the hosts file of every computer on the network is going to be a problem, have a look at dnsmasq, it is available in the repositories. Smb is a Microsoft protocol, but you need samba on the server so that the Windows computers can see it.

---

### Post by mbaas on 2009-08-21
Or, if you want to learn BIND, you could set up a BIND dns server.

[Here's]("https://help.ubuntu.com/9.04/serverguide/C/dns.html") the official ubuntu documentation on BIND

---

