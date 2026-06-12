---
title: "[SOLVED] Backup/redundant isp"
date: 2008-07-06
forum: Server Platforms
---

### Post by mbeach on 2008-07-06
In a small retail business, with relatively low data requirements, when the current internet provider goes offline, the debit/credit card machines can fail over to a voice line, and they have a local synchronized copy of point of sale system enabled which pushes all the transactions back to the remote server upon re-connection.  Although that works, it's not always pretty - there is some manual intervention on the 'fail over', and subsequent switch back.

I'd like to have another ISP as a backup, which I could simply move the link from the main data switch over to in the case of an outage.  So I'd have two pipes, say one cable, one DSL, and when the cable fails, I'd plug into the router hanging off the DSL modem.  However, that would require some manual intervention as well - is there a 'cheap' way using a linux box setup as a gateway to be checking the heartbeat of two providers, and switching when necessary?  I'd like to try to do this without an separate appliance if possible.

I've tried searching on the topic, but seem to be pushed toward a separate appliance which is specifically made for this type of application.  I'm happy enough to go that route if necessary.

Anybody have a similar situation/solution?

---

### Post by pytheas22 on 2008-07-06
I don't see why something like this wouldn't work:

You set up a Linux box with three network interfaces as your gateway--one NIC, eth0, is connected to cable (primary ISP); the second, eth1, to DSL; and the third, eth2, goes back out to your local network.  Normally, you have an IP on eth0 and everything works great.  eth1 is kept asleep.

You also run a process to make sure that the primary ISP is still active.  This could be done in a number of different ways.  For instance, you could ping something and assume that no response means that the ISP is down, or you could exchange keep-alive packets.  These methods would involve a few seconds' delay; I don't know if that's acceptable.  If not, let us know how exactly you currently determine that your primary ISP is down, and maybe there's a better way to do this.

When the process decides that your primary ISP has gone down, you simply run a short script like:
```

ifconfig eth0 down
ifconfig eth1 up
dhclient eth1
```

which puts eth0 to sleep and replaces it with eth1, essentially doing the same thing as unplugging the cable to eth0 and plugging it into eth1.  You could work backwards to have the process seamlessly switch back to eth0 when the primary ISP comes back up, too.

If any of this doesn't make sense, please let me know.  And if you provide more specific information about your setup, this could be refined.

Depending on how much experience you have with Linux (really you don't need to know too much to implement this) and how much those special devices cost, this could be the way to go.  I'm sure that the special boxes are just doing basically the same thing described above (probably running Linux, too).

Another thing to keep in mind is redundancy...whether you buy the special appliance or do it yourself, you may want to have a backup gateway in case the main one goes down for some reason.

---

### Post by mbeach on 2008-07-07
thanks pythas22 -

Its a small retail shop so seconds delay is well within acceptable - I figure perhaps a ping every minute, then if no response, try again a couple of times, something like every 10 seconds for a minute, then if still no response, then flip over to the eth1.  

I currently determine when the ISP is down by the cashiers calling me saying, "Nothing is working".

I do have a decent little server (dell poweredge model escapes me), which currently has two cards, so for this to work, I'd really only need an extra card.

Currently the situation is
Cable Modem - Router[static ip]/Firewall - Switch - patch panel - all devices

I'm a tiny bit hesitant but not unwilling to change it to:
modem - gateway - switch - patch panel - all devices
Only real reason is a potential other use in another location for that server.  Probably wouldn't be a bad move though to put a machine in there as the gateway.  Wouldn't have to be that beefy a machine.

I recall reading through one of the scripts used for keeping dynamic dns up to date (checkip?) which has me thinking that perhaps I could actually keep my current setup, and have a script logon to the proper page for the router (wget or similar), change providers by filling in the form and submitting it.  Not sure how I'd know when to switch back in that scenario though.  I have a  static ip, and I believe there is an IP (one less in the last octet) which the tech said represented 'the wire' - not sure if he was trying to dumb it down for me, but perhaps I could check if that was available.  My own IP certainly would not be as the router would pick up the IP from the other provider.  

My problem in the fail-back is to test it - almost need an actual failure.  But switching back could occur outside of business hours, so not a big issue.

Thanks for the suggestion, got my brain moving again (a recent run of repetitive tasks has put me in 'no think' mode.)

---

### Post by mbeach on 2008-07-07
.... but thinking about that, the router is connected by cable to the cable modem, and would need to be connected to the dsl modem manual.  3 nic machine it is then - or perhaps 2 nic machine with the script changing the 2 nic's connection settings.  

I know I know - go get another card.

---

### Post by windependence on 2008-07-07
I might get flamed for this but I think Linux is a bit heavy for what you want to do. Try pfsense [http://www.pfsense.com/](http://www.pfsense.com/). It runs on BSD and is very small. It needs very little RAM or CPU and has a web interface. It can also handle multiple WAN interfaces which is what you want to do. You actually <could> run it on a 486 if you wanted to. Any old PC would do just fine for this and you won't need a monitor either.

-Tim

---

### Post by mbeach on 2008-07-10
no flames here, that actually looks quite interesting - one limitation on their website is listed as "Requires a minimum of three public IP addresses" which I don't have at the moment.  I had five, realized I was paying for 5 (had no real requirement for them), and dropped it down to 1.  I would be getting another which would bring it up to 2.  They say that limitation will be resolved in a future release - perhaps by the time I actually get around to doing this.  I know just the optiplex gx150 in the back of the closet for the job.

---

