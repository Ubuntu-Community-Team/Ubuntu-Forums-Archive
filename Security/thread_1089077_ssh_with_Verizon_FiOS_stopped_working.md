---
title: "ssh with Verizon FiOS stopped working??"
date: 2009-03-06
forum: Security
---

### Post by ctsdownloads on 2009-03-06
First off, it all started with my Internet going out last night. Took hours of screwing around, but FiOS finally was able to come alive again after a series of restarts.

This also meant having to re-setup my port forwarding/port redirection. Too bad this is not working any longer...sigh.

I have tried the following:

ssh into my target PC successfully from within my LAN no problem. Tested successful with both the typical port 22 and a few other tested ports as alternatives. So SSH is working just fine, with my provided keys. No passwords here.

Now, I have also established that all tested ports, including port 22, is open both with IPTables via Gufw AND in my router's settings. Now I should point out that I use my own Draytek router with the FiOS craptastic router as a bridge. This has NEVER been a problem in the past, the FiOS router is enabled as a bridge only without the firewall on at all.

And my own router is using both port redirection and open ports to allow pass through. So, all of the required ports are open both at the router level and at the target PC level.

Wait, it gets better...

I have tested telnet to my SSH server to all test ports from 22 on through to some others I tweaked in the SSH config for testing. In short, I am actually unable to even telnet to the SSH box outside of my LAN.

Yes, all non-LAN SSH attempts have been made on three different ISPs. And with each of them, there is no connectivity to any of the tested ports setup for SSH.

So here is what I have thus far:

1) SSH works, just not outside of my LAN.
2) SSH outside of my LAN on different ISPs fails with a refusal.
3) Telnet of the same related SSH ports provides me with a timeout failure, while I can telnet to the ports for SSH easily in LAN.
4) Based on the ISPs tested, it appears to be something with my router, not my own ISP. But the router is fine, never better. It is expensive too, not that cheap consumer level crap most people use.
5) While the IP address being used outside of the LAN for my router is not static, it has been tested as the correct one assigned and this method has worked in the past for years.
6) As a last ditched try, I DMZ'd the target PC in my router, turned off the gufw firewall completely and it STILL is not able to see the damned ports outside of my LAN!

So here is my problem. I know for a fact that the router is working fine, it's not an issue with it working. Clearly, I have it mis-configured somehow?

Could it be a problem with the fact that I am using both Port Redirection and Open Ports on the router? Heck, I even tried disabling sets of each to see if one or the other gave me some results. Frankly. I am at the end of my rope here. It's not like I can simply "reinstall" something here to fix this. I am out of ideas...please help.

---

### Post by ctsdownloads on 2009-03-06
Just did a 

nmap P0 external-ip-addy -p2222

(Testing port 2222 now)

Got back

PORT     STATE    SERVICE
2222/tcp filtered unknown

PORT     STATE  SERVICE
2222/tcp closed unknown

Yet as locahost...

PORT     STATE SERVICE
2222/tcp open  unknown

What the heck am I missing that is connect to my router then? Ports are opened and ports are being forwarded. :(

---

### Post by ctsdownloads on 2009-03-06
Okay, I might be asking a question that is simply too complex to answer. Understandable, this is something that is difficult to diagnose even for someone standing in front of it.

Let's try this one:

I have a suspicion that Verizon started blocking ports - lots of them, including port 22. But I need a means of testing this theory. Where can I go to do this?

Reaching for answers here folks, come on, please?

---

### Post by cariboo on 2009-03-07
Try [canyouseeme]("http://www.canyouseeme.org/") to test for open ports.

Jim

---

### Post by tgalati4 on 2009-03-07
Could be a hardware problem.  Find a FIOS neighbor to test.

---

### Post by topraamen on 2009-03-08
I have the same exact problem... Been diagnosing it for the past day and cant figure it out... I checked my friend's house who has FIOS as well but it works there and not here... But he lives 10 min away

So i think it might be a version thing, I even put my self on DMZ on my router and reset the thing and still no go on port 22 for SSH. What drives me nuts is that 2 days ago it was working perfectly fine just the past day it started acting up...

Anyone got any ideas? :(

---

### Post by tgalati4 on 2009-03-08
Is there any way to check the firmware versions of both boxes?  Sometimes an over-the-fiber upgrade that occurs at night can break things.

---

### Post by Tr10 on 2009-05-03
I have this same problem.

I live in MA if that helps anyone.
Seems to have just taken effect, doesn't matter the port, it's almost like they are sniffing the network all together.

---

