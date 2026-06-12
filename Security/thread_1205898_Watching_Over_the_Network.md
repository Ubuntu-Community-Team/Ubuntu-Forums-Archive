---
title: "Watching Over the Network"
date: 2009-07-06
forum: Security
---

### Post by kayn786 on 2009-07-06
I have my linux box setup as my primary server, but I am also dual booting xp. What I want to be able to do is monitor all activity over the network (any sites, stream, connections made) from anywhere that is connected to the wireless router's connection. I'm not doing this to spy, but to verify all the connections being made to and from my house for certain reasons. Now, the problem is that I dont just want to monitor computers either, but also cell phones, media receivers, tv boxs, and everything that is connected to the wireless network. Yes, I am more than just a little paranoid...

This is very important for me, so any help it at all would be great!

EDIT: Ps. Is this even possible?

---

### Post by Nepherte on 2009-07-06
Monitoring the network is certainly possible, you only have to pay attention as to where exactly in your network setup you are monitoring the network traffic. Wireshark is a program with wich you can monitor your network traffic. It inspects the network packages sent over your network.

---

### Post by nateperson on 2009-07-06
Sure its possible.  You can set up a packet sniffer between the wall and router and monitor and track everything, or plug one into the maintenance   ports.  But between encryption and not really knowing what your doing, the easiest thing to do would be to lock down your wireless router properly so that only specified connections can connect, on most that's done via MAC addresses.

And no, cell phones won't be connecting through your wireless router

---

### Post by kayn786 on 2009-07-06
Lol, I mean using wifi on my cellphone =P.  Well, after I posted this I discovered wireshark, and it's actually pretty simple. Although I've used packet sniffers in the past, I never realized how they could be used over the entire network... 

And Nate, I'm not trying to do anything of that sort, I really just want to see what's going on. Not block anything. 

Thank you both very much for your input. Any further help would also be appreciated.

---

### Post by juancarlospaco on 2009-07-06
From [WireShark]("apt:/wireshark") to [Driftnet]("apt:/driftnet") all is yours.

---

