---
title: "eth0 is p135p1 does this effect connections? (also minecraft server help)"
date: 2014-04-21
forum: Server Platforms
---

### Post by Michael577 on 2014-04-21
Hi,
it's been a very long time since I've posted something here so be easy on me.

Anyway, I've been reinstalling my mincraft server that was using ubuntu 13.10. The reason for this was because I got new hardware for the server for it to run faster. This included a new motherboard, cpu, and ram. So I was installed ubuntu server 14.04lts and I noticed that I couldn't connect to it (giving me a "java.net.connection refused error on the minecraft client). However I was able to connect to webpages.

Keep in mind that I'm using the exact configuration from the old server (required ports on router open, noip for my dynamic ip, and ufw opened to the required ports for minecraft). After trying to figure it out for a day, I decided to downgraded it to 13.10 thinking it was something new to 14.04 that I wasn't aware of.

Same problem. So I now check the connections using ifconfig and I get this:
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:982864 (982.8 KB)  TX bytes:982864 (982.8 KB)

p135p1 Link encap:Ethernet  HWaddr e0:cb:4e:64:95:55
          inet addr:10.0.1.25  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe64:9555/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:167061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:227329412 (227.3 MB)  TX bytes:10399139 (10.3 MB)


```
I noticed the p135p1 instead of a eth0. I'm not sure if this is the case but I'm at a loss on what to do here. so as the topic says, does this effect the connection? if so, how do I change it. Or am I missing something that's not related to this. 

Please let me know as this was making me lose my sanity last night. Thanks for reading and thanks in advance for responding
EDIT:
I almost forgot. I'm using multicraft for hosting the server, but it didn't seem to make any difference as made a basic minecraft server without multicraft. Also, I said before, I'm able to access the webpages on my server, which is webmin, multicraft, and the default page. just throwing it out there.

---

### Post by dudumomo on 2014-04-22
Hi Michael577,

Strange to have p135p1 instead of eth0 indeed. Especially your IP is 10.0.1.25?
What is the content of your /etc/network/interfaces?

I've just installed Minecraft on my server using the very good [MineOS]("http://minecraft.codeemo.com/") (ISO fully dedicated to host Minecraft with optimized installation) and [wrote an article about it]("http://freedif.org/how-to-easily-host-a-minecraft-server-mineos-dedicated-os/"). It is very straightforward.

---

### Post by Michael577 on 2014-04-23
Turns out it was a my bad. The ip of the server was wrong...woops

---

### Post by Michael577 on 2014-04-23
Hey, thanks for replying!
I found out that my minecraft server was on the wrong ip adress this whole time! (Couldn't believe I missed that) So in the end it was me not paying attention to the mincraft server ip. it was supposed to be 0.0.0.0:25565. But it was 127.0.0.1:25565. Soo my bad!

And thanks for letting me know about this OS. I will definitaly try it. But I needed multicraft on there as the server is also my file shareing and web server. But thanks for telling me about this.

---

