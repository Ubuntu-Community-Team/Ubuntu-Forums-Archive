---
title: "New Server set, need some info..."
date: 2012-08-03
forum: Server Platforms
---

### Post by SHRIKEE on 2012-08-03
Hi All,

For the past 5 years I've been running 2 Mac OS Servers. With the latest Incarnation of it I'm finally fed up with it and ordered a Asus mainboard with a onboard Atom D525 CPU to run a small Ubuntu server.

I've used Ubuntu desktop for a while a few years ago. But server is relatively new to me.

**I'm wondering:**
- For Atom CPU's can i just use the Ubuntu 64bit image? Or do i need something special?
- Is there a administration panel (App/webbased) to manage services the server will provide?
-- This, for now, is DHCP, DNS and VPN
-- Perhaps later, development server or related
- Can I easily install from a USB harddisk? It seems possible but didn't quite find a clear answer.
- Does VPN Server work outside the user desktop? I remember that if you're not logged in Clients can't connect (this was Ubuntu 8 or so).


Thanks for your answers and insights.

---

### Post by darkod on 2012-08-03
1. Atom is 64bit, so yes, you can install the 64bit version.

2. Web based GUI for administering the server is webmin or ebox, among others. I think those are most widely known, never used them though.
[http://www.webmin.com/](http://www.webmin.com/)
I think webmin is not in the repositories so you will need to install with the instructions on their website.
It seems ebox has been replaced with Zentyal, but that is a whole install, separate image instead of installing ubuntu server and adding the ebox package. In case you want to consider it:
[http://www.zentyal.org/](http://www.zentyal.org/)
Note that some thing might be different from ubuntu, I am not sure.

3. You can install from USB as long as you can boot from it, but google first for the procedure about installing ubuntu server from usb stick. The installation stops at one point looking for a cd-rom drive although it has all files on the usb and it booted from it. It keeps asking for cd-rom, there was a short procedure how to continue.

4. I am not sure about the VPN server but this is ubuntu server OS you are installing and it is designed to run without a user logged in. If you have worked earlier with the VPN server and the desktop OS, it might be different when no one is logged in. But with the server version, not having a user logged in is the standard way of operating I would say.

---

### Post by SHRIKEE on 2012-08-03
1. Cool

2. I'll look into that, and now that you mention Zentyal, i remember another - ClearOS ([http://www.clearfoundation.com/Community/Home.html](http://www.clearfoundation.com/Community/Home.html)). Will have a look at both.

3. Great, as i expected.

4. Yes ofcourse, just a command prompt and all that. But if possible I'd like a simple desktop to control things. Since it's gonna be a server there's no display. Thus i need VNC. But if VNC isn't active if I don't log in i can never log in because i have no display to log in locally. So VNC needs to be available on the login screen. Which it wasn't in 8.04 and older.

Thanks for your answers and ideas.

---

### Post by SHRIKEE on 2012-08-03
Actually Zentyal looks a lot better than ClearOS atleast their site works properly :)

---

### Post by darkod on 2012-08-03
VPN or VNC? You said VPN in your first post and that's a whole different ball game from VNC.

If VNC is only for remote control, I can't see much point if you are familiar with the CLI.

You can control the server remotely with SSH at CLI level, and on top of that you have the option for webmin. With these options, I wonder if VNC access is needed at all. But you know better what you need I guess.

I am sure there is a way to have VNC access to a headless ubuntu server.

---

### Post by SHRIKEE on 2012-08-03
Aw crap, yes i see now. I meant VNC... Silly me.

Yes a decent web panel would suffice, but to keep as much options open right now I'm gathering as much info as i can.

The idea is that the server mainly will provide networking services: DHCP, DNS and VPN.
For management I'm looking for a good way to do it. Ofcourse I can use CLI and I'm sure it will work fine. But personally i find CLI a bit clumsy (spoiled by Apples admin tools?). Hence my requirement for a web panel or desktop.

Webmin or Zentyal are looking good but won't let me install my "own" things, imagine i want to run something that is not offered by default by those 2 like run a Ventrilo (voice) server or something.
The problem with VNC in Linux is though, that when the computer boots and needs to login to its desktop, VNC is not yet active because the user is not logged in. So i was wondering if anything changed on that end.

---

### Post by darkod on 2012-08-03
I haven't tried it, but I expect if you install VNC server onto Ubuntu server, that service to be up and running together with the server. Hell, even windows servers boot all the services completely without anyone logged in.

The VNC server is just another service, and it should load on a server OS, at least in my logic. :)

PS. Even if it doesn't do it by default, you can always put it in something like /etc/rc.local and it will load it at boot.

---

### Post by SHRIKEE on 2012-08-03
Ah yes, i can always add it to a earlier boot stage. Good idea.

I just got note that my server hardware shipped. I'll be building a server tomorrow i guess :)

Gonna try Zentyal first and experiment from there.

Thanks for your ideas.

---

### Post by CharlesA on 2012-08-03
If you want a desktop, or GUI, just install Ubuntu desktop and add services as you need them.

I would suggest using NX to connect to the GUI instead of VNC, because VNC is pathetically insecure. If you are connecting over a local network VNC is "ok" but NX is better as it goes over SSH itself.

---

### Post by SHRIKEE on 2012-08-04
I've installed Zentyal today and it seems to do exactly what I want it to do. :) 

Thanks!

---

