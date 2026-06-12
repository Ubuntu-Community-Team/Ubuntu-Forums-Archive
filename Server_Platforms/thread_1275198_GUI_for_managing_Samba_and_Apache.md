---
title: "GUI for managing Samba and Apache"
date: 2009-09-25
forum: Server Platforms
---

### Post by Dragonbite on 2009-09-25
I have an Ubuntu Server 8.04 LTS set up and running with a CLI and am thinking of moving the server over to another box (in part because the power supply is making some nasty noises lately).

While I used it before with the CLI, this time around I am thinking that I will want some basic GUI interface (now that I have enough monitors to give one to the server).

When I've used CentOS before, they had a couple of GUI programs for helping to manage Apache and Samba (and maybe more). If I'm looking at going with a GUI for the server then these tools would be very helpful, I think, as I get more comfortable with running a server (in general).

***Are there any GUI applications for managing Samba, Apache and/or domain controls (DNS, etc.)?*** 

Otherwise I will be interested in looking at some web interface.

I had picked up and been using _Beginning Ubuntu LTS Server Administration_, which has been a big help. So the Command Line doesn't scare me, and I plan on using that as a backup, to help me to know what it is I am doing.

Thanks

---

### Post by adramalech on 2009-09-25
you could use webmin...it is a gui admin tool to monitor and modify most services in your server....

---

### Post by lykwydchykyn on 2009-09-25
The gadmin suite has GUIs for most of the more common services, but TBH I've never liked them. They seem to want to set things up a certain way that doesn't exactly jibe with the way Ubuntu sets things up by default.

Personally I use webmin in combination with CLI tools.  Webmin is  by far the most comprehensive tool of its kind, and IMHO does a better job of working with existing configurations than tools like ebox or gadmin.

---

### Post by Dragonbite on 2009-09-25
Webadmin just sets the config files? So if I want to go in and tinker "by hand" it won't mess up Webadmin and vice-verse?

I'm thinking of going the Webadmin route, I've just have had mixed results on setting up frameworks.

---

### Post by lykwydchykyn on 2009-09-25
> **Dragonbite said:**
> Webadmin just sets the config files? So if I want to go in and tinker "by hand" it won't mess up Webadmin and vice-verse?

I'm thinking of going the Webadmin route, I've just have had mixed results on setting up frameworks.

Pretty much, though there have been a few times when it didn't know how to handle advanced stuff (like when I put procedural logic in the DHCP config file), but for the most part it just parses and writes back to existing configs. It doesn't have "meta-configuration" data anywhere (a la YAST), as far as I know.

BTW it's just "webmin", so you don't get confused looking for it.

---

### Post by doas777 on 2009-09-25
i tried a samba conf gui last year called gsambaadmin or some such, but it just broke my samba. I think it may have been that i only needed a handful of settings, but when i reopened my config file, it had created blank settings entries for like every possible setting for samba. 

who knows, mabey it works now, or you can figure out how to use it better than I did.

there are a few admin consoles listed here:
[http://swik.net/gui+samba](http://swik.net/gui+samba)

good luck

---

### Post by lykwydchykyn on 2009-09-25
> **doas777 said:**
> i tried a samba conf gui last year called gsambaadmin or some such, but it just broke my samba. I think it may have been that i only needed a handful of settings, but when i reopened my config file, it had created blank settings entries for like every possible setting for samba. 


Yep, that's part of the gadmin suite.  I've tried several of those tools in Debian and Ubuntu and had more or less the same experience.  I don't know how they work for other distros, but they don't seem to do well on Debian based ones IMHO.

---

