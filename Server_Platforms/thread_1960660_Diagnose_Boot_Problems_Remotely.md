---
title: "Diagnose Boot Problems Remotely"
date: 2012-04-17
forum: Server Platforms
---

### Post by GuitarRocker2562 on 2012-04-17
I am running a headless server in my house ~500 miles away from where I go to school (I'm a college student). Every once in a while the server will not boot and I'll have to wait until I get home to fix it (sometimes week). Usually it's just a grub problem or it hangs at the menu or something. Is there anyway to diagnose boot problems remotely? For example I know you can use a serial console with grub but is there anyway to do something like that over the Internet?

---

### Post by sj1410 on 2012-04-18
if this server hardware support IPMI than you can power recycle it from internet, or even can get a remote display with control of the server.

when it does not boot, is there some error on the display, or just showing the menu?

---

### Post by GuitarRocker2562 on 2012-04-21
No, it doesn't have that kind of stuff. It's just an old cheap desktop. When it doesn't boot sometimes it hangs at the grub menu waiting to press enter (there is a way to prevent this but you have to manually update-grub after a kernel upgrade) or sometimes it won't boot so I have to boot into recovery mode. 

Basically I need a way to see the grub menu at boot time from 500+ miles away. A software solution probably. It's worth noting my router runs DD-WRT (which is Linux-based) so if I could log into the router and use that to make a connection over Ethernet to my server. I just don't know a way to view GRUB remotely or even on LAN.

---

### Post by GuitarRocker2562 on 2012-04-24
Bump

---

### Post by Jonathan L on 2012-04-25
Hi Guitar Rocker

> I need a way to see the grub menu at boot time from 500+ miles away. A software solution probably. It's worth noting my router runs DD-WRT (which is Linux-based) so if I could log into the router and use that to make a connection over Ethernet to my server. I just don't know a way to view GRUB remotely or even on LAN.

The classical way for servers and similar is to connect to their serial port from your router.  Most upscale routers (Cisco for example) have serial ports you can use for this in what they call "reverse telnet".  You telnet to the router on a particular port number and you're connected out of the serial port ... which is wired to the serial console of your server.  You can also buy specific "terminial servers" or "serial device servers" which are specifically for this.  I've had great experience with Lantronix ones (don't need any of their supplied software, just telnet to them to configure) but they're expensive.

If your router doesn't provide this, then you could consider another computer of course (which is silly, I know, because you've already said the server is a cheap old desktop), or I've had good use of Arduino hardware if you like a bit of DIY hardware.  You mention you're running DD-WRT, so it's just possible you've got a USB socket and could coax it into talking to a serial port in the way I've described above.

As a last ditch ... I've had webcams pointing at screens and I've used remote control fingers (staff with telephones) to press the right buttons.

I'm sure none of that helps in your case, but just maybe!

Kind regards,
Jonathan.

---

