---
title: "Help with Traceroute command??"
date: 2007-05-10
forum: The Cafe
---

### Post by kevdog on 2007-05-10
I thought I knew a lot about the traceroute (or tracert) command, however Im beginning to feel really like a novice.  My own LAN network from my computer to the outside world is connected through a wired router, which is connected to a wireless router, which is then connected to the comcast digital modem.

When I use the traceroute command the IP address of the wireless router is shown first (192.168.1.1) and then the second line is *****, and the 3rd is an outside host.

Why doesnt the IP address of the digital modem show up???

Thanks

---

### Post by ArtificialSynapse on 2007-05-10
It's because your router forwards you to the outside world through the gateway, the modem just allows you to connect to your ISP, it doesn't actually have an assigned IP address persay. =O

---

### Post by ice60 on 2007-05-10
maybe the FW is blocking it?? you could try tcptraceroute which uses port 80 i think, it might be less lightly dropped. i'm not sure. but tcptraceroute is in the repos.

---

### Post by kevdog on 2007-05-10
I remember way back when I installed the cable modem I used my web browser and it brought up some info screen.  No configurable options.  I cant remember how I did that??

---

### Post by elcasey on 2007-05-10
You could try punching your public IP into your browser and see what comes up. But if there's no config options, not sure why you'd want to do that.

You might also have your wired router set to not respond to pings (security measure). Do both of your routers support RIP (Routing Information Protocol)? Check out the docs for both of your routers (not quickstarts).

---

