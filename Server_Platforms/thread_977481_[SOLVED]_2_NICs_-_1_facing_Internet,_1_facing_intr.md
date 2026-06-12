---
title: "[SOLVED] 2 NICs - 1 facing Internet, 1 facing intranet"
date: 2008-11-10
forum: Server Platforms
---

### Post by stanleytberry on 2008-11-10
I originally configured the server (v8.04) attached to my intranet through eth0.  I moved the box to my Internet through eth0.  It works as a web server.  I cannot, however get APT-GET to work (firewall).

I have a second NIC in the machine.  I would like to attach it to my intranet ... but I haven't yet done so.

I would like to use the intranet NIC (eth1) for updates to the server ... APT, web content, ...

I would like to use the Internet NIC (eth0) as my web site (as I'm now doing).

Both subnets would be (eth0 already is) connected to a machine running only ipCop.  The intranet is ipCop's Green net, the Internet is ipCop's Orange net.  The actual external connection is ipCop's Red net.

**How do I (do I need to do anything to) make APT use eth1 (and only eth1)?**

How much trouble am I going to get into ... from a security point of view?

Can I disable eth0 and enable eth1 using a script, and the do the reverse using a script?

Any help would be appreciated.

Thanks,
Stan

---

### Post by devonps on 2008-11-10
> **stanleytberry said:**
> I originally configured the server (v8.04) attached to my intranet through eth0.  I moved the box to my Internet through eth0.  It works as a web server.  I cannot, however get APT-GET to work (firewall).

I'm assmuing that you still have web traffic flowing?

Can you ping your web server from within your network and from outside your network?

I believe APT-GET uses port 80 to download updates more specifically it uses the TCP protocol, so am not sure why this is getting blocked, have you reviewed your firewall logs?

> **stanleytberry said:**
> Can I disable eth0 and enable eth1 using a script, and the do the reverse using a script?

You can use IFUP eth0 or IFDOWN eth1 to bring up/down a network interface, from the command line, remember to do a /etc/network/interfaces restart command. You might need to prefix that command with SUDO if you're not logged on as root. So you should be able to put that in a script.

I don't have any experience with IPcop so can't help there.

Hope some of this helps,
Steve.

---

### Post by stanleytberry on 2008-11-11
Steve,
This command
> /etc/network/interfaces restart
doesn't exist on my UBUNTU v8.04 server.  However ... it doesn't matter because IFUP and IFDOWN seem to take care of whatever needs doing.  I've tested it.

Since I'm the only one updating the server, manually enabling and disabling the NICs around an update doesn't pose any major problem ... in fact, it'll slow me down just enough to make me think it through any time I make a change.  That's a good thing.

Thanks again.
Stan

---

### Post by oneloveamaru on 2008-11-11
It says solved at the top but i don't see anything being solved in the thread. Having 2 NIC's is great for certain things but adds a bit of complexity  with networking. You want to be able to get to the internet but then also be able to get to your intranet. This is pretty easy with the right configuration.

Edit /etc/network/interfaces for eth0 and eth1. Whichever you make the internet NIC, make sure you put a default gateway in there. The one you make the intreanet, DO NOT put a gateway line in there. When you have 2 gateways, your server will send our packets on either nic. This is probably why you can't do an apt-get update, because it's not going out on the internet gateway.

For the intranet, we will make a couple custom routes for when something does need to go out on that NIC, Ubuntu knows which NIC to send it out.

I use these lines for eth1, because eth1 is our intranet, going from one site to the other and cannot get out to the internet. eth0 on the other hand can get out to the internet.

I added this to the bottom of my /etc/network/interfaces file. Keep in mind, you will need to replace the IP's and gateway with your IP's.

I think the break down of those lines is self explanatory, so I won't go into much detail. You can run these from the command line and get the same results but after a reboot, they will be gone. If you do run these from the command line, omit "up", since that's not a command. :) The routes these add will be forever created on reboot until you comment them or delete them out of your /etc/network/interfaces file. Enjoy.

#Static routes for Intranet

        up route add -net 10.103.128.56/29 gw 10.103.128.57 dev eth1
        up route add -net 10.101.128.120/29 gw 10.103.128.57 dev eth1

---

### Post by stanleytberry on 2008-11-11
The original questions
> How do I (do I need to do anything to) make APT use eth1 (and only eth1)?

How much trouble am I going to get into ... from a security point of view?

Can I disable eth0 and enable eth1 using a script, and the do the reverse using a script?
have been answered.

APT uses the active interface.  If I disable the interface attached to the Internet I don't get into trouble.  The commands that Steve proposed, IFUP and IFDOWN, do the job for my situation.  I don't really need the interface attached to my intranet active on that server except when I want to update the server.  Hence my previous post:

> Since I'm the only one updating the server, manually enabling and disabling the NICs around an update doesn't pose any major problem ... in fact, it'll slow me down just enough to make me think it through any time I make a change. That's a good thing.

As far as I'm concerned it is solved.

---

### Post by stanleytberry on 2008-11-11
Ah ... it might help you to understand that my intranet has external access ... it is ipCop's GREEN net (to which the eth1 NIC on my server is attached) and it is much more protected than ipCop's ORANGE net (the DMZ, to which the eth0 NIC on my server is attached).  I did not want to take a chance on bypassing ipCop ... but if I
[LIST=1]
[*]disable eth0,
[*]then enable eth1,
[*]then update my server through eth1,
[*]then disable eth1, and
[*]then enable eth0 again,
[/LIST]
I think I'll be safe.

And **my** problem is solved.

---

### Post by oneloveamaru on 2008-11-11
Hmm... I guess I just didn't like his solutions, as running ifup and ifdown doesn't really seem like a solution to me. Why enable and disable NIC's when you can do it the right way? That's like banging a nail in with the end of a wrench instead of using a hammer.

If you do an ifdown eth0 you disconnect anyone or anything(web crawlers) that are on your site. That puts downtime on your site, which I guess for me, since I work for a dot com company would be unacceptable. Adding custom routes would be the sure way to do it.

Now if you are running both NIC's on the same subnet, then none of this makes sense because you can do EVERYTHING you want with the firewall, which is even easier.

---

### Post by oneloveamaru on 2008-11-11
Hah, you made another post while I still had my web page on the reply screen. Hehe.

Well i guess for security that makes sense but then again it doesn't make sense. Running updates only requires going out on the internet on port 80 and download some files. If you will be going through your firewall to SSH into the box and want it limited to the 2nd nic, then all you need to do is open port 22 to ONLY your IP address. That solves the security problem.

---

### Post by walkerk on 2008-11-11
> **stanleytberry said:**
> Steve,
This command

doesn't exist on my UBUNTU v8.04 server.  However ... it doesn't matter because IFUP and IFDOWN seem to take care of whatever needs doing.  I've tested it.

Since I'm the only one updating the server, manually enabling and disabling the NICs around an update doesn't pose any major problem ... in fact, it'll slow me down just enough to make me think it through any time I make a change.  That's a good thing.

Thanks again.
Stan

This thread is marked solved but for clarity:

```

sudo /etc/init.d/networking restart

```

---

