---
title: "managing a server"
date: 2009-04-19
forum: Server Platforms
---

### Post by sparkles on 2009-04-19
We have a server at work serving some customers' websites that is still running 5.04. It's (un)managed by the people who maintain the websites (and they don't do that particularly well either) but because I'm the resident linux guru I'm trying to help them out with some apache problems they're experiencing at the moment.

My linux experience consists of running my own server at home, a server at work for development stuff and as a desktop at home and work, so I've never ever come close to managing public facing servers.

I'm trying to put together some basic rules for them to follow and considering my lack of experience I was hoping for some advice on how to manage the non application specific stuff like...

- only use official ubuntu repositories or mirrors
- install all security updates
- enforce password complicated-ness
- only upgrade to the LTS releases
- don't add every user to sudoers

Does that sound reasonable? Is there any other big picture stuff you could suggest? I'm particularly interested in how people decide to upgrade distro releases (if at all).

TIA

---

### Post by Waappu on 2009-04-19
Hi

I think those are good basic rules.

I'm upgrading LTS release when support ends to version I'm using

---

### Post by Thirtysixway on 2009-04-19
I used to upgrade my server on each release, but then I got to 8.04 and decided to stick to an LTS.  It's a lot easier because security updates are around for 5 years.

Another rule you could use is watch out who has access to config files (which would be covered by the sudoers rule you have already.)

---

### Post by daboroe on 2009-04-19
I agree. Only allow certain users the ability to see and edit configuration files. If a regular user gets them they can really mess things up. 

If you are using the server for a web server, utilize virtual hosts. That way it is very easy to keep everything organized for the different sites or sub domains. I plan on doing that on mine. If someone is wanting you to edit something in lets say php.ini make sure if you turn it on it will not put the server or other sites in risk.

What about backups? You can backup your server every so often. I would do an initial complete back up and then incremental backups or complete backups every week or so.

---

