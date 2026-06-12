---
title: "ip changer"
date: 2009-07-04
forum: Security
---

### Post by SNOOPY817 on 2009-07-04
can anyone help me with a proxy to permanently change my ip or something 
because this dude keeps tracing my ip and any proxy i use still don't work
anyone have any suggestions?

---

### Post by SNOOPY817 on 2009-07-04
Okay, well i need to change my IP or get a very very good proxy so no one
can get my ip because this creepy dude keeps tracing my IP and i think hes
just going to far. O_O So if anyone can help me change my ip or help me out
with a good proxy i would really appreciate it,

Thank you.

---

### Post by Lucky. on 2009-07-04
Hey man,

Here are the ways I know how to change your IP address.  Unfortunately none of them are very good (I will explain why below).

1.  If you're using dial-up, disconnect, and reconnect.  You'll probably get a new IP address.

2.  If you're **directly connected** (no router between your computer and the Internet) to the net with DSL,Cable,Fiber, etc...turn off your computer and/or DSL/Cable Box, and turn them back on.  Or try the following from the command prompt:

```

sudo /etc/init.d/networking restart

```

You **might** get a new ip address.  However it may be better to do the following:

```

sudo /etc/init.d/networking stop

```

...then wait for a while, then type:

```

sudo /etc/init.d/networking start

```

This **might** get you a new IP address.

If your computer is behind a router, visit your router's web page and try to get it to release its IP address for a while (then get a new one later).  Or shut your router off for a while, reset it, etc.

Basically these methods take advantage of your ISP's DHCP server, which assigns you, your router, your modem, or your cable/dsl box an IP address (though most don't assign addresses to the boxes).  DHCP dishes out IP address from a list.  Extremely simplified (not accurate), user #1 gets xxx.xxx.xxx.1, and user #2 gets xxx.xxx.xxx.2, etc.  Essentially by disconnecting and reconnecting, you might get a different IP address.  With a modem, this will almost always happen easily since people are logging on and off of dial-up all the time (modems were a lifesaver when I'd troll on game servers back in the day and get banned).  With other more permanent broadband connections, IP addresses don't cycle very quickly.  Some take minutes, hours, or even days as long as everybody's boxes are turned on with no problems.

None of these are amazing ways to save yourself from somebody tracing your IP address.  Most of them won't work very well, and your address may only change slightly (like from xxx.xxx.xxx.74 to xxx.xxx.xxx.75).

If you're worried about security to your own machine, don't sweat it, especially if you're behind a router.  The network address translation on the router should keep somebody from accessing most (if not all) ports on your machine, making it very hard for somebody to hack you unless you willingly download some malware from them.

If you're directly connected to the Internet, yeah...I'd sweat a little.

If you're worried because somebody is tracking your general location due to your IP address (like a town or county), that's not going to change if you get a new IP address through one of the methods I described above.  That's because most location trackers are simply based on where the IP addresses are assigned in the world.  So if somebody tracks your xxx.xxx.xxx.74 address to your home town, changing to xxx.xxx.xxx.75 won't suddenly make it look like you're from another country...it will still be traceable to your town and ISP.

If this is due to some problems with an admin on a website, try using an anonymous web proxy like the anonymouse website (just do a search for anonymous web surfing).  Also I hear that [tor is pretty cool](https://help.ubuntu.com/community/TOR), but I haven't tried it.  If this is due to a game, you'll probably just have to deal with it.  Without routing your stuff through somebody else's proxy server (you can't set one up yourself or else he'll still have your IP address), people will know your IP address when you connect to servers.  They have to have it in order to send data back to you.

---

### Post by credobyte on 2009-07-04
You forgot to mention your connection type ;)
If you have a modem/router, leave it turned off for 10 minutes .. turn it on, reconnect and you should get a new IP ( applies only for DHCP ).

---

### Post by philcamlin on 2009-07-04
restart your router/ modem and youll get a new ip

---

### Post by wojox on 2009-07-04
Log into your router and release/renew the dhcp

---

### Post by philcamlin on 2009-07-05
> **wojox said:**
> Log into your router and release/renew the dhcp

cool my sister could use that instead of rebooting her router alot

---

### Post by JauntyJackalope88 on 2009-07-06
Try TOR (the onion router) [www.torproject.org]("http://www.torproject.org")
It gives you a new IP every time you log on.

---

