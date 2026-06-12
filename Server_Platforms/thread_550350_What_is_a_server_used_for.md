---
title: "What is a server used for?"
date: 2007-09-13
forum: Server Platforms
---

### Post by acelin on 2007-09-13
Yeh- i dont know- I know they use it in mass computing situations, like libraries and computer labs-

What sort of use would a user at home have for it?

---

### Post by PilotJLR on 2007-09-13
This isn't meant to be sarcastic! But servers simply "serve" some content or service to a user. This can be many, many things.

In a home setting, this is often media, like audio/music files or movies. For example, in my home, I serve up mp3 and mpeg videos to other rooms. For me, that's enough.

In a corporate setting, you have file servers, proxy servers, dhcp, dns, etc etc.

It all depends on what you need accomplished.

---

### Post by bodhi.zazen on 2007-09-13
In a nut shell you can think of a server as a warehouse. You store information on a server and access the information from clients.

You use various protocols to access data. ftp, http (web pages for example), nfs, samba, VNC, ssh all are examples of protocols to access data on the server.

Servers can perform other tasks. dhcp = assign and manage your LAN (like a router). You can add a proxy such a squid or dansguardian.

HTH

---

### Post by towerofpower256 on 2007-09-13
In my case, I have two main computers. One that is only on when it's needed (games, playing music and movies, surfing the web) and one thats always on and does the time consuming work that doesn't need to be watched (downloading stuff like Ubuntu ISO's, holding files, web server, etc, etc...)

---

### Post by acelin on 2007-09-13
i was thinking I could use my current computer teo do the same thing, and once I get a MacBook Pro use it for my main stuff.. 

If I had a server on the internet,  could I connect another computer to that and use it on the internet too?

Can I use a current Ubuntu installation to do server type things?

---

### Post by towerofpower256 on 2007-09-13
> 
If I had a server on the internet, could I connect another computer to that and use it on the internet too?

I'm gonna take a stab and guess that the computer you're using is directly connected to the net and doesn't go through a router or something like that. Then yea I know that Ubuntu can become an internet gateway and do server-like stuff, most importantly DHCP so the MacBook knows how to get on the net.

The main difference between a Desktop and Server installation is the user interface. A server doesn't need one and works faster when it's not drawing a million fancy pictures an hour. If you put the server programs on a desktop installation, it can do the same stuff as a server.

---

### Post by acelin on 2007-09-13
Excellent - cause i dont want to uninstall my Ubuntu for a server edition- 
So I could use both on the net?

I cant use a router because of my schools internet policy- straight from ethernet

---

### Post by towerofpower256 on 2007-09-13
Ah, so it comes from an Ethernet cable. Then they are probably already using their own Router/Gateway/Switch/Doobywhacker to let everyone use the net. 

If your school's policy allows it, you could just get a simple 8-way hub (I think that's as small as they come nowadays) and use that. Plug the 'internet' Ethernet cable into one of the ports and your computers into the rest.

---

### Post by acelin on 2007-09-14
They dont allow use of any hubs, routers, or wireless systems-

Can I just use one computer and use it to connect another to the internet?

---

### Post by UbuWu on 2007-09-14
> **acelin said:**
> They dont allow use of any hubs, routers, or wireless systems-

Can I just use one computer and use it to connect another to the internet?

You mean connect one pc to the internet and then connecting another pc to that pc to also let it use the internet connection? That is possible, see here:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by acelin on 2007-09-14
How would I connect it though? Ethernet, phone cable, wireless router not directly connected to the wall, etc. ...

---

