---
title: "Web server behind VPN"
date: 2011-05-23
forum: Server Platforms
---

### Post by revolutionären on 2011-05-23
Hello!

I'm setting up a LAMP (Ubuntu OS) web server hosted behind vpn. As soon as I connect to an OpenVPN service I'm paying for I can't connect to my anonymous ip adress from another computer.

When **I'm not connected to OpenVPN the webserver works fine**. And I know that **the OpenVPN provider not have restricted any ports**.

Does anyone know how to solve this problem? :)

Best wishes

---

### Post by spynappels on 2011-05-23
I'm sorry, but could you explain a little more? Is the server generally web accessible or only through the VPN tunnel?

A diagram of your setup may help....

---

### Post by revolutionären on 2011-05-23
I have my ISP IP. When connecting to it at port 80 the server works (Apache default html-page shows). But when I connect to an OpenVPN service I can't connect to my new anonymous IP provided by the VPN service.

So yeah. It is like you say.

---

### Post by spynappels on 2011-05-23
Is the web server bound to the ISP or LAN IP only? Then it won't respond to the tun0 interface. (I presume here that you are connecting the server directly to the OpenVPN service as well?)

Try telling Apache to listen on the tun0 interface as well.

If you have a VPN gateway device instead of connecting the server to the VPN directly, disregard what I just said.

---

### Post by revolutionären on 2011-05-23
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192961&stc=1&d=1306150162[/IMG]

---

### Post by revolutionären on 2011-05-23
> **spynappels said:**
> 
Try telling Apache to listen on the tun0 interface as well.


Sounds like a good idea. How do I do that? :-)

---

### Post by spynappels on 2011-05-23
Are you using virtual hosts? or just one single site on the server?

---

### Post by revolutionären on 2011-05-23
I have default apache conf. No virtual hosts right now.

---

### Post by Grenage on 2011-05-23
Anonymous, eh? ;)

Can you connect to other sites, or are there problems with only that one server?

---

### Post by spynappels on 2011-05-23
Just a quick thought, are you accessing it using the VPN IP address or still using the LAN IP address, and is port forwarding enabled in the VPN service?

---

### Post by revolutionären on 2011-05-23
> **spynappels said:**
> Just a quick thought, are you accessing it using the VPN IP address or still using the LAN IP address, and is port forwarding enabled in the VPN service?

I try to access the VPN ip of course. :-) Then my browser after a minute or so says connection timed out.

---

### Post by revolutionären on 2011-05-23
The idea is cool -- to host behind vpn. The site that might be comming up this was is a torrent tracker. If my hosting provider decides it want to shut my site down.

---

### Post by revolutionären on 2011-05-23
SOLVED!

It was the VPN provider that had blocket port 80 for incoming... changed the port and everything works fine!

---

