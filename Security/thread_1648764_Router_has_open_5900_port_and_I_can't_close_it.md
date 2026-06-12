---
title: "Router has open 5900 port and I can't close it"
date: 2010-12-19
forum: Security
---

### Post by sleepee on 2010-12-19
Hello all.
I've recently been taking a look at my router settings and I've realized i have my vnc port open for some reason.
I don't know how or why it got opened because I've only used vnc within my private lan.
Anyway, the problem is I couldn't figure out how to close that port on my router, so I just uninstalled all the vnc software from my computer so it wouldn't act like a vnc server for anybody trying to access it from the outside.
So, effectively, I cannot vnc into my computer from outside my private lan, but when i port scan my public ip, the vnc port still appears open.

I'm wondering if there's something i'm missing.  I'm sure it must be something in the router that I haven't figured out... something that's keeping port 5900 open.  Any ideas?
Btw, I have a Thomson router, just in case.
Thanks

---

### Post by 12apennachi on 2010-12-19
You will have to go to your router settings and change it. You have to know your router's ip. Probably 192.168.1.1 type that into your browser url box. Then you will need to know your router's password to connect. Again, probably default settings like admin and pass or something. Then you can go to firewall, and close/open ports as you wish. BTW, what isp(Internet service provider) do you have?

---

### Post by CharlesA on 2010-12-19
Turn off UPNP on the router.

What VNC server were you using? It's likely that you enabled the "configure the network automagically" option in the Remote Desktop dialog box.

Check out this site: [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by SeijiSensei on 2010-12-19
The ultimate option is to push the little reset button on the back of the router and return to the factory defaults.  You'll probably have to go through set up procedures again if you have customizations like forwarded ports, though.

---

### Post by sleepee on 2010-12-19
> **CharlesA said:**
> Turn off UPNP on the router.

What VNC server were you using? It's likely that you enabled the "configure the network automagically" option in the Remote Desktop dialog box.

Check out this site: [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

I think you were right.  I disabled upnp and the vnc port was disabled.   I have no idea how it got enabled in the first place.  Thank god i found out now before anything happened.
Thanks a lot.

---

### Post by sleepee on 2010-12-19
> **12apennachi said:**
> You will have to go to your router settings and change it. You have to know your router's ip. Probably 192.168.1.1 type that into your browser url box. Then you will need to know your router's password to connect. Again, probably default settings like admin and pass or something. Then you can go to firewall, and close/open ports as you wish. BTW, what isp(Internet service provider) do you have?

I get my internet from the local phone company here.  It's called DMAX from Puerto Rico Telephone Company.

---

### Post by sleepee on 2010-12-19
> **SeijiSensei said:**
> The ultimate option is to push the little reset button on the back of the router and return to the factory defaults.  You'll probably have to go through set up procedures again if you have customizations like forwarded ports, though.

I was actually about to do that, but I wanted to see if I could figure it out so it wouldn't happen to me again.
Thanks.

---

