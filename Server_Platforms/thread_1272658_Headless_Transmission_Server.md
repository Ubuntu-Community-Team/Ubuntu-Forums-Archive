---
title: "Headless Transmission Server"
date: 2009-09-22
forum: Server Platforms
---

### Post by danielgroves on 2009-09-22
Hi,

I have [a guide]("http://forum.transmissionbt.com/viewtopic.php?f=8&t=8361") to make a headless installation of transmission.  I can now access it's web interface by going to [http://192.168.1.81:9091/transmission/web/](http://192.168.1.81:9091/transmission/web/) on my local network, yet once I have logged I none of the buttons work so I cannot start any torrents off.  
I would be hugely grateful if anyone can help me out here!  
Thanks,
Dan.

---

### Post by Lars Noodén on 2009-09-23
What about using the shell interface for Transmission?

[transmission-cli]("http://packages.ubuntu.com/search?keywords=transmission-cli")
[http://packages.ubuntu.com/search?keywords=transmission-cli](http://packages.ubuntu.com/search?keywords=transmission-cli)


There are also completely headless torrent clients like [btpd]("http://packages.ubuntu.com/search?keywords=btpd")
[http://packages.ubuntu.com/search?keywords=btpd](http://packages.ubuntu.com/search?keywords=btpd)

---

### Post by danielgroves on 2009-09-23
> **Lars Noodén said:**
> What about using the shell interface for Transmission?


Because I need to be able to access the web interface when away from home.  Also it is no use for other people who are not so good with a computer.

---

### Post by Lars Noodén on 2009-09-23
Ok.  Are you using [transmission-daemon](http://packages.ubuntu.com/jaunty/transmission-daemon)?  I see it in the guide you mentioned and installed it on a machine.  It seems to work out of the box.  

Just a wild guess: do the directories assigned in /etc/transmission-daemon/settings.json have the right permissions?

Have you tried it with the --foreground option to run it in the foreground so you can see any errors?

---

### Post by danielgroves on 2009-09-23
> **Lars Noodén said:**
> Ok.  Are you using [transmission-daemon](http://packages.ubuntu.com/jaunty/transmission-daemon)?  I see it in the guide you mentioned and installed it on a machine.  It seems to work out of the box.  

Just a wild guess: do the directories assigned in /etc/transmission-daemon/settings.json have the right permissions?

Have you tried it with the --foreground option to run it in the foreground so you can see any errors?

Yes, they have the right permissions.  what do you mean the --forground option

---

### Post by Lars Noodén on 2009-09-23
```

sudo /etc/init.d/transmission-daemon stop

sudo -u debian-transmission /usr/bin/transmission-daemon  \
 --auth \
 --config-dir /var/lib/transmission-daemon/info \
 --foreground

```

It allows you to watch what's going on when you click on the web interface in another window.

---

### Post by danielgroves on 2009-09-23
> **Lars Noodén said:**
> ```

sudo /etc/init.d/transmission-daemon stop

sudo -u debian-transmission /usr/bin/transmission-daemon  \
 --auth \
 --config-dir /var/lib/transmission-daemon/info \
 --foreground

```

It allows you to watch what's going on when you click on the web interface in another window.

OK, I ran that and I got he following output:  

```
[19:04:14.227] RPC Server: Adding address to whitelist: *.*.*.*
[19:04:14.227] RPC Server: Serving RPC and Web requests on port 9091
[19:04:14.227] RPC Server: Whitelist enabled
[19:04:14.227] RPC Server: Password required
[19:04:14.227] Transmission 1.51 (7963) started
[19:04:14.326] transmission-daemon: requiring authentication
[19:04:15.234] Port Forwarding: Opened port 51413 on :: to listen for incoming peer connections
[19:04:15.234] Port Forwarding: Opened port 51413 on 0.0.0.0 to listen for incoming peer connections
[19:04:43.897] Searching for web interface file "/home/danielgroves/.local/share/transmission/web/javascript/transmission.js"
[19:04:44.237] Searching for web interface file "/usr/share/transmission/web/javascript/transmission.js"
```

I clicked all the buttons in the web interface and nothing changed while I did so.

---

### Post by Lars Noodén on 2009-09-23
I was hoping that it would show some kind of warning or error when you are trying the buttons that don't work.  But I'm stumped, since I myself have been unable to duplicate the problem described and can only flail about a little.  

---

In lieu of a real solution, some lame work-arounds might include remote desktop access.  They can be tunneled over SSH if need be.

[http://packages.ubuntu.com/jaunty/krdc](http://packages.ubuntu.com/jaunty/krdc)
[http://packages.ubuntu.com/jaunty/krfb](http://packages.ubuntu.com/jaunty/krfb)

[http://packages.ubuntu.com/jaunty/tightvnc-java](http://packages.ubuntu.com/jaunty/tightvnc-java)
[http://packages.ubuntu.com/jaunty/tightvncserver](http://packages.ubuntu.com/jaunty/tightvncserver)
[http://packages.ubuntu.com/jaunty/xtightvncviewer](http://packages.ubuntu.com/jaunty/xtightvncviewer)

---

### Post by danielgroves on 2009-09-23
> **Lars Noodén said:**
> 
In lieu of a real solution, some lame work-arounds might include remote desktop access.  They can be tunneled over SSH if need be.

[http://packages.ubuntu.com/jaunty/krdc](http://packages.ubuntu.com/jaunty/krdc)
[http://packages.ubuntu.com/jaunty/krfb](http://packages.ubuntu.com/jaunty/krfb)

[http://packages.ubuntu.com/jaunty/tightvnc-java](http://packages.ubuntu.com/jaunty/tightvnc-java)
[http://packages.ubuntu.com/jaunty/tightvncserver](http://packages.ubuntu.com/jaunty/tightvncserver)
[http://packages.ubuntu.com/jaunty/xtightvncviewer](http://packages.ubuntu.com/jaunty/xtightvncviewer)

I'm working with it via SSH now.

---

### Post by danielgroves on 2009-09-23
@Lars Thanks for your help anyhow.

---

### Post by not2slo128 on 2010-01-22
Guys, any ideas on getting the web interface to work?  I have the EXACT same issue as the OP and have been up for several nights trying different combinations.

I can access the service from outside and from within but the buttons (including the 'Open' button) are disabled.

Transmission 1.51
Ubuntu 9.04

TIA

---

### Post by BobVila on 2010-01-22
fwiw, I've been using rtorrent with the wTorrent web interface and love it. Might be easier than getting transmission working. A cursory googling will find some good scripts that you can adapt to your own purposes.

---

### Post by tr333 on 2010-01-22
Have you checked JavaScript/NoScript settings?  If you have JavaScript disabled or NoScript enabled for that domain/port then the buttons on the transmission web page won't work.

---

