---
title: "Routing different traffic through different network card"
date: 2007-10-18
forum: Server Platforms
---

### Post by feenster on 2007-10-18
Hi all,
I have a data server that receives data via SSH from numerous users. This data is then sent on to another remote server, also be SSH. I was wondering whether it is possible to put another Gigabit network card in the server, and router outgoing traffic through it? I'm not sure how much real benefit this would bring, but it would be handy to maximise the throughput for both the incoming/outgoing connections.

Is it possible to do this, and will i see any benefit?

Matt

---

### Post by koenn on 2007-10-18
If all this is happening inside 1 network, i don't see how you can route. 
I suppose you could have 2 NICs (network cards) in that 1 server, which of course will each have an IP address, 
and:
1- the clienst will send to 1 ip adress
2- you could make that 2nd server connect to the 2nd ip address to retrieve the data. 

That should work. I doubt you'd benefit - the bottleneck might well be in data being written to and read from the hard disks on the server  where everything passes through, unless you have a RAID system in there optimized for speed.

---

### Post by feenster on 2007-10-18
> **koenn said:**
> If all this is happening inside 1 network, i don't see how you can route. 
I suppose you could have 2 NICs (network cards) in that 1 server, which of course will each have an IP address, 
and:
1- the clienst will send to 1 ip adress
2- you could make that 2nd server connect to the 2nd ip address to retrieve the data. 

That should work. I doubt you'd benefit - the bottleneck might well be in data being written to and read from the hard disks on the server  where everything passes through, unless you have a RAID system in there optimized for speed.

Hi, well I suspected it probably wouldn't be worth the hassle, and you've just confirmed that. 

Thanks for your advice,
   Matt

---

### Post by tkharris on 2007-10-19
Actually what you origionally said made perfect sense to me.  I imagine your first machine is load balancing all the connections to the numerous other machines and to prevent network saturation you want to add another nic server and have incoming and out going work on different eth devices.

You'd want to modify the ssh statement to go to the IP on the first nic card, then change the script that will push the data out and add "-b ip_of_second_nic" ( -b = bind to IP ).  You can find more information in `man ssh`.

---

### Post by feenster on 2007-11-01
Hi,
Sorry for the delay in replying. My use is slightly different now actually. I have two ADSL routers on different connections. I want to pump data out on a different connection to the one I receive it on. Therefore, you suggestion of binding SSH to a different IP address would work a treat.

Thanks for your help :-)

Matt

---

