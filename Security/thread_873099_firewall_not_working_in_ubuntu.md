---
title: "firewall not working in ubuntu"
date: 2008-07-28
forum: Security
---

### Post by markling on 2008-07-28
hello

help request from non-techie here.

the ubuntu help pages said users who wanted to setup a firewall should download firestarter.

i followed the instructions for intsalling the firestarter firewall on the firestarter pages.

it doesn't work. and it display some unexpected activity (not that my expectations are based on anything but what the help pages lead me to expect, but what i have is different to what i am told should be there).

the help screen says that firestarter should probably have eth0 selected as the network device for a DSL modem. but this didn't work on my machine.

my firewall status dialogue lists 4 devices: 

wifi0
auth0
eth0
irda0

as far as i'm aware, i am only connected to one network device: my wifi DSL modem.

so i tried selected wifi0. that didn't work either.

when my browser is browsing the status dialogue shows almost simultaneous and almost identical levels of activity for both wifi0 and auth0.

if i select auth0, the firewall comes on, but i don't know what the heavens auth0 is.

is it kosher? and what's irda0 - should it be there? is my computer safe?

thanks.

m.

---

### Post by brian_p on 2008-07-28
> **markling said:**
> 

if i select auth0, the firewall comes on, but i don't know what the heavens auth0 is.

Should that be ath0?

> . . . . is my computer safe?


Absolutely.

---

### Post by hyper_ch on 2008-07-29
firestarter is no firewall. are you sure you need to change default settings?

---

### Post by markling on 2008-07-29
thanks for responding.

yes brian, i did mean ath0 rather.

no hyper, i'm not sure i need to change the default settings. i wasn't sure that i had changed them. i left well alone, but when it didn't work, i changed according to the activity i observed - that was activity in wifi0 and ath0. it didn't work when i selected wifi0, even though the only access i have is over wifi, but it did work on ath0, so i've got it set to that.

it now appears to be working, but how can i be reassured its safe. the help pages dont say nuffink about no ath0, and why should i have two devices connected and active at the same time in the device list when i've only got one device connected?

and you say its not a firewall?

cheers

m.

---

### Post by The Cog on 2008-07-29
In what way does the firewall "not work"?

ath0 is an Atheros wireless interface, I think. I guess wifi0 is also something to do with wireless. I don't know which you should apply the firewall to.

---

### Post by smalldog on 2008-07-29
if you have an Atheros WLAN card, the wireless interface should be athx(x can be 0, 1, 2.....). It is VAP created by wlanconfig. and wifi0 is for parameter setup of the wireless interface.

---

### Post by hyper_ch on 2008-07-29
well, generally you don't have to worry about configuring the firewall. Only when you start installing daemons/services you might want to start considering. However most daemons/services actually do want allow access from outside e.g. you want to install a ssh server so that you can login from everywhere into your computer through the command line. In that case you do want it to be open. However you may want to restrict then what IPs can connect to. For that multiple solutions are available.
Same goes for a bittorrent program. You do want it to be accessible... if you don't seed anything at all you might not leech  - even more so on private trackers.
However you might want to setup apache and mysql for local development only. In that case you might want to block outside access completly.

Generally I can say:
- you don't need to twinker with iptables (firewall)
- you don't even less to think about it if you have a router and have disabled UPnP on it and only do port-forwarding for certain stuff
- you may want to consider the firewall settings if you are not behind a router and run services or if you have UPnP enabled and run services or if you run stuff like ssh server and have forwarded it from the router to you server.

---

### Post by markling on 2008-07-29
actually the firewall is working. so the header of this thread is misleading. sorry. my mistake.

( when i started writing the original post, the firewall wasn't working, but i hesitated before sending, tried a few intuitive knocks of my boot on the firewall settings and though it started working, still had some reservations, so wrote and sent the message without thinking to change the header - phew! )

as for the rest, hyper, i'll take your word for it. it's all dutch to me. i wouldn't even know if the wireless dsl modem box that BT sent me is called a router or something else, and i wouldn't know UPnP and port forwarding if they came and pinched me on the nose.

i merely have this computer thing i use to do my work, and that sometimes does strange things.

so anyway, i assume then that i shouldn't need to worry that the firewall only lets me choose one device, yet shows two devices (ath0 and wifi0) sending and receiving data?

---

