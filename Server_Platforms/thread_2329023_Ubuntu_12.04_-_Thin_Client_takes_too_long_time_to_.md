---
title: "Ubuntu 12.04 - Thin Client takes too long time to display the login screen"
date: 2016-06-27
forum: Server Platforms
---

### Post by prasadvj on 2016-06-27
Hello Everyone,

I have installed Ubuntu-12.04 LTS with LTSP and configured the dhcpd.conf file to boot . When I boot the Thin Client it detects the server and then starts the process of loading the login page, but this process takes too long (around 20 - 30 mins). 

But once the login screen is displayed and username and password is provided it immediately load the desktop and working with application is quick and smooth. 

How can I reduce the time of loading the login page. I have existing Ubuntu 10.10 server implemented and the thin client boots very quickly (within 10 -15 Secs)

Thanks in advance,

Prasad

---

### Post by MAFoElffen on 2016-06-27
Moved to the Server Section were it will get appropriate exposure.

Even with a PXE boot > DHCP > TFTP dl of the image ... 3-5 minutes. And for me, between the dhcp tp Login screen seemed like it was taking forever...

But 20-30 minutes??? I feel like mine was really fast compared to that. Something is really wrong there. I know it is thin client, but what is the specs of your LTSP server and and your client?

---

### Post by prasadvj on 2016-06-28
Thanks for your reply.
**The spec of LTSP Server is as below:**
root@ubuntu1204:/var/log# dpkg -l | grep ltsp
ii  ltsp-server                                 5.3.7-0ubuntu2.8                    Basic LTSP server environment
ii  ltsp-server-standalone                      5.3.7-0ubuntu2.8                    Complete LTSP server environment
ii  ltspfs                                      1.1-2                               Fuse based remote filesystem for LTSP thin clients
[B]The spec of Thin Client is as below:
[/B][SIZE=-1][FONT=Comic Sans MS]Atom 1.8 (Digilink Intel D425 chipset), 2 Gb RAM[/FONT][/SIZE]

---

### Post by MAFoElffen on 2016-06-28
Specifically:
-CPU, memory and NIC's of the LTSP server.
- NIC in the Thin Clint.

I'm assuming that there are 2 NIC's in the LTSP Server, Once connected to the outside world. One connected to a different NID, that just contains LTSP Clients.

That way the dhcp request from the clients only hit one dhcp server. (No confusion, almost direct connect kind of logic). Then the internet connection of the clients are routed through the LTSP server (requiring less hardware and simplified net config).

If not, then you can do the same with vlan's, but that starts adding more complexity to the configs.

With that topology, then the limiting factor is the spped of the link on the LTSP and the network switch. 

Since I see an Atom CPU. Is perfect for a thin client. It should be able to process what it needs to in a timely manner (as a CPU)... But being the kinds of devices that Atom's are installed in, I'm wondering if the network connection is wired or wireless. If wireless, then what protocol (ie 801.n)? If wired, then what speed (ie 10/100/1000)?

---

### Post by prasadvj on 2016-06-29
Thanks for the reply.

There is only one NIC in the LTSP Server i.e. used for both Internal & External connection.

Also the dhcp server gets detected immediately, but takes too long to display the login page.

As I have already mentioned in earlier post, I have a similar setup of Ubuntu 10.10 Server and that works fine.

The problem is only when the thin client is booting, but the server get booted immediately and the login page is displayed without any delay.

Thanks,

Prasad

---

### Post by prasadvj on 2016-07-06
Hello Everyone,

I also tried by copying one of the previous image from the Ubuntu 10.10 server but still no luck.
I've rebuild the image many a time but the time taken for booting is not reducing.
Please help.

Regards
Prasad

---

### Post by MAFoElffen on 2016-07-06
So, you said it takes a while (20 minutes), but it does finally work? Right?

I'm wondering if you build an image with systemd's bootchart... That way, after the bootup succeeds, then you would have chart to easily and quickly see what processes are taking how long. That way we can what is happening behind the scenes. That is a tool we used in the Ubuntu Development Cycle Testing when something like this came up.

---

### Post by prasadvj on 2016-07-08
Yes, it works but the time taken is too long, that is not affordable in production environment.
One more thing I tried that the thin client gets booted immediately if I connect the server and the client on a separate switch and create a different LAN.
Now I'm not understanding why the same setup is working through my existing LAN.

Would like to hear from someone who is facing the same problem.

Thanks 
Prasad

---

### Post by MAFoElffen on 2016-07-09
> **prasadvj said:**
> One more thing I tried that the thin client gets booted immediately if I connect the server and the client on a separate switch and create a different LAN.
Ahoy! That is one thing that I mentioned. I guess you missed or didn't understand that.

You said you only have one NIC in that server. I said to do it effectively you would need two, with the thin clients on their own NID, routing from that server to the rest of your network's NID.

In your last post you said you didn't understand, so I will explain from a different perspective.

In a thin client, it gets a PXE boot > broadcasts a dhcp request...

This gets into broadcast domains. A broadcast domain goes beyond a switch, but does not go beyond a router. If not a another NIC, then a hardware router to do the same. For each to know each side of the route, you just use router RIP, or a static route hop. For thin-clients that do not need to contacted by the outside, then the route only has to be a gateway to your net (one way route hop).

If on the same NID as the rest of your network, then that request goes to all dhcp servers handing out dhcp leases. Then the download of the image also competes with all traffic of the rest of your network. That is the max network load of that kind of system. So if on the same net segment, that load also affects anything else on that segment (i.e thick clients on that segment).

The basic of that is... isolate your LTSP net for clients to talk with it's server. Provide a route to the rest of your net.

---

