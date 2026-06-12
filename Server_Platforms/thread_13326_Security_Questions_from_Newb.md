---
title: "Security Questions from Newb"
date: 2005-01-30
forum: Server Platforms
---

### Post by Recked on 2005-01-30
Hello,

Just wondering if anyone might be able to shed some light on what types of security a new gnu/linux user needs to use to ensure their system is safe from outsiders etc.

Like many others I come from a number of years of Winslows and as such have in place many levels of security for our small home network and connected computers.

Just wondering what, if any, I need to add to our growing Ubuntu network? 

I have heard yes to firewall, no to firewall, yes to virus checkers, no to virus checkers so I am not sure what if any needs to be employed to ensure safe email and internet searching.

thanks very much for any help/suggestions.

---

### Post by mendicant on 2005-01-31
A firewall for your network won't hurt, and may make sure you don't leak any services to the outside world.  You don't necessarily have to install it on each individual computer.

Antivirus stuff might be important if you serve mail for Windows clients.

---

### Post by az on 2005-01-31
Do regular security updates. (synaptic smart upgrade) (or apt-get dist-upgrade)
A base Ubuntu system is designed to be secure.  Be aware of any packages that you install and know what they do.  Try to stick with packages that are supported (Ubuntu main archives)

---

### Post by brainstuff on 2005-02-02
Hi
I'm in the same boat. Whose idea was it to fill a boat with newbies anyway? :shock:

A friend of mine says that I should disable Telnet - but as I am still at the "crying at a terminal window" stage, is there an easy (gui?) way of doing this?

Btw I've tried to rtfm but it comes up blankety blank:
[http://www.ubuntulinux.org/search?SearchableText=telnet&path=%2Fplone.org](http://www.ubuntulinux.org/search?SearchableText=telnet&path=%2Fplone.org)
0 results :cry:

Edit: Self discovery is the path to true enlightenment!
[http://www.uwsg.iu.edu/hypermail/linux/net/9902.1/0189.html](http://www.uwsg.iu.edu/hypermail/linux/net/9902.1/0189.html)

cheers
brain

---

### Post by mendicant on 2005-02-02
The telnet daemon isn't installed by default.  I'm not sure that any distro installs it by default.

---

### Post by brainstuff on 2005-02-02
Ok, thanks. I think it's time I sat down with a "Duh, Linux" book and stopped asking silly questions :)

---

### Post by mendicant on 2005-02-02
Silly questions are fine--they help you learn before you know how to search for the answers yourself.  Of course, when you do know how to do the search, you should do that before you start asking the silly questions :)

---

### Post by reh on 2005-02-02
How secure is ubuntu out of the box? What services (if any) are on by default? I'm looking for a free linux distro that doesn't require a lot of tinkering to setup and secure.

I used Debian Linux somewhere around 1997/98 and found it be interesting. I learned a lot, but it wasn't exactly easy. I've been using Mac OS X and Windows mostly since then. I'm interested in playing around with linux again, as I'm sure there's been a lot of changes since '98. I'd also like to use it on a family member's computer. They are on a tight budget and have been plagued with the usual windows viruses and spyware. Ugh.

Thanks for the input. Hope I didn't hijack the thread too much... it seemed like a good fit.

---

### Post by az on 2005-02-02
"How secure is ubuntu out of the box? What services (if any) are on by default?"

It is pretty secure.  None of the services that run out of the box listen to the outside world.

It is assumed that you know what you are doing when you enable them to listen.  For example, postfix (MTA) only listens on localhost by default.  Samba will allow you to browse your windows network, but it does not allow the network to listen to it.  You need to install the other samba packages for that (apt-get install samba).
The same goes for ssh.  You can ssh out, but to ssh in you need to install more packages.

apt-get install ssh

---

### Post by reh on 2005-02-02
[QUOTE=azz]It is pretty secure.  None of the services that run out of the box listen to the outside world.[/QUOTE]
Thanks. That's what I was hoping for. I'm gonna download it and it give ubuntu a whirl.

---

### Post by brainstuff on 2005-02-02
you know it makes sense!

this crowd is friendly too, and they suffered me gladly so far  :D

---

### Post by Mute on 2005-02-10
I would also suggest that if you are worried about security and what the outside world can see, you download and install Nessus (new to Ubuntu not sure if it is part of the distro ;)) [http://www.nessus.org/](http://www.nessus.org/) and run it against your own machine, it will tell you what can be seen from the outside world, the threat level, and suggestions about what should be done about the service.  

-Mute

Just MHO.  Take of it what you will.

---

