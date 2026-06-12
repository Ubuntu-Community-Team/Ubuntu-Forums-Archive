---
title: "Chrome remote desktop keeps terminating after a few seconds"
date: 2012-11-30
forum: The Cafe
---

### Post by sdowney717 on 2012-11-30
has anyone any experience using this google app?

I can generate the share key on the win7 machine
Enter the key on the connect screen for Ubuntu machine
The session connects
I see the remote desktop
Then after 4 seconds or less, it terminates itself.

---

### Post by sdowney717 on 2012-11-30
I did some weird finagling on the win7 machine. clicked some buttons to enter in a 'pin number ' to enable remote sharing. this does not seem to be so obvious in the instructions, they leave this out???

So then you DO NOT ENTER AN ACCESS CODE on the ubuntu machine like you would intuitively think to do, dumb,,,,,

You look down lower where you see your machine listed
you click on the machine
it says enter your pin number
you enter it and it works!

I am streaming netflix with sound to my ubuntu machine

---

### Post by Copper Bezel on 2012-12-01
Yeah, I didn't have any problems with that step, but I'd read the instructions pretty thoroughly by the time I tried it out. I basically set put together my Windows VM specifically to try this out after finding out that remote access doesn't work on Linux. (I mean, desktop sharing works on Linux, but setting up a machine for permanent remote access doesn't.) 

It's a really nice little app, and after seeing that the machine can be accessed remotely even when it's not logged in, meaning that Chrome makes Windows constantly ready to accept a remote connection regardless of the user session, I kinda didn't want it on my Linux machine anymore, anyway. = )

---

### Post by sdowney717 on 2012-12-01
I think it uses the internet connection not the local lan.

I was trying to setup RDP. I used some tutorials but can never connect. My home network has 2 routers.

One base address is 192.168.1.101 and the other is 10.0.0.1
Both are doing DHCP.
So I have a computer at 192.168.1.103 and one at 10.0.0.2
I can ping eac

How would you get RDP working then?

win7 can ping ubuntu but ubuntu cant ping win7

---

### Post by sdowney717 on 2012-12-15
I solved problems by pulling the netgear router and using a verison 7501 router.

The gateway router needed a static route that pointed to the other router, but only for file sharing, not chrome remote desktop.

The pinging had issues with win7 setup of firewall and sharing.

The chrome desktop no longer disconnects after I pulled the netgear router.

---

