---
title: "Software to monitor open/used ports for network switches"
date: 2007-05-31
forum: Server Platforms
---

### Post by sxturbo on 2007-05-31
Topic states what I'm looking for. 

I have several switches in different closets  and datacenters I'd like to monitor. I'd like to be able to see what ports are open....or a percentage of in use/open ports. Make it easier in case I'm heading to another building to make some connections, only to find out I needed another switch installed.

If anybody knows of a software that can do that for me, it would be much appreciated. I've had no luck the past few days searching around.

---

### Post by rickyjones on 2007-05-31
A lot will depend on the switch. What layer in the OSI model do they work in? Are they SNMP aware? Etc...

If it is the cheap switch that you got at the local store then I don't believe so. If it is an enterprise switch, maybe from Cisco for example, then you should be able to telnet into it and look at it.

-Richard

---

### Post by sxturbo on 2007-06-01
sorry, i can't beleive I left that info out.

they are cisco enterprise switches. We monitor them through SNMP. But like I said, i'd like a app that can run on my server and tell me what percentage of ports are open on a given switch.

---

### Post by rickyjones on 2007-06-01
Well, since they are capable of that then the first place I would look is Cisco. I know for a fact that Cisco provides software that you can run on your workstation that lets you connect to the switch and look at it (as in, physically look at it) - but this depends on the switch.

Other than that you can always telnet into it and issue the correct command and it will output what ports are active and which are not.

I have not done this because it's not in my job description (and they really won't let an intern in a different department do that...), but one of my fellow interns here does it all day long.

My advice? Call your Cisco vendor and have them walk you through how to do it.

-Richard

---

### Post by Me! on 2007-06-06
you can see this program "EtherApe"

---

