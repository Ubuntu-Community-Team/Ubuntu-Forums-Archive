---
title: "Website/ssh unavailable from different networks"
date: 2008-03-24
forum: Server Platforms
---

### Post by awreneau on 2008-03-24
I'm pretty sure this isnt a Ubuntu problem but it certainly wont hurt to ask.

I'm unable to reach a web server/ssh server consistently (both are the same server) on my home network which has a public IP address and has a entry from the ISP and at my local firewall to allow HTTP traffic and ssh traffic. On some networks I can reach the site, from others I cannot.  I can reach the box via ssh and log in successfully, however if I do a LS on a dir w/ more than a few files the DIR never completes, it just hangs.  Also, if I attempt to browse the site from particular networks it will sit and in the status bar it will read "waiting for sitename"  sitename is the website.  I have tried this on physical server and on a VM server both have the same results.

The DNS is hosted by 1 and 1 hosting. On the server I'm using opendns.

I had another site running on my network on a RedHat machine for years but I've since ditched RH and have pledged allegiance to Ubuntu.  

Any help would be appreciated w/ this problem.

Thanks

---

### Post by twistedtwig on 2008-03-25
i can not answer your question (at this point) but a little more detail may very well help others understand the problem.

1) can you give examples of what networks you mean.

are you talking about internal (local area networks)?

are you talking about across the net?

2) Can you ping the server from each of these locations?

3) can you netstat is from each of these locations?  i.e. can you see the http and ssh port is open?

4) can you connect to the website from any of these locatins?  browser or telnet?

GL

---

### Post by Mr. C. on 2008-03-25
What is the output of :

```
ifconfig -a
```

We're looking for packet loss or errors.

---

### Post by awreneau on 2008-03-25
My apologies for the late reply, out of town....training.

1) can you give examples of what networks you mean.
I cant reach the site from the hotel network, nor my office network, only when I'm connected to my ISP's network.


2) Can you ping the server from each of these locations?
I've disabled ICMP replies and cant reach it out of town so I cant adjust those parameters.

3) can you netstat is from each of these locations? i.e. can you see the http and ssh port is open?  Yes, these ports are open, I can reach them so long as I am on the ISP network.  The names resolve correctly regardless of where I am.

4) can you connect to the website from any of these locatins? browser or telnet?
When I attempt to connect via browser I get "waiting for FQDN"  I can ssh into it but like I said in my original post, if I do a DIR or nano a lengthy file it stops....that one blows my mind.  That is the case if I use the FQDN or IP.

---

### Post by awreneau on 2008-03-26
Forgot to answer the question about the ifconfig -a question.

All I can get remotely is this:
eth0      Link encap:Ethernet  HWaddr 00:0C:29:3A:D9:F6
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe3a:d9f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1



Let me throw in another twist.


I'm on the same computer, the same hotel network (wireless) and cant get the output of the ipconfig -a command, and as a reminder I cant load the web page.

I can plug in my Cingular/AT&T card, connect and the pages load, ssh works everything seems fine.

So what sense does that make?





*************************edit***************************

On the cingular wireless card, like I said earlier, everything works just fine.

 Link encap:Ethernet  HWaddr 00:0C:29:3A:D9:F6
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe3a:d9f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:498196 (486.5 KB)  TX bytes:1499765 (1.4 MB)
          Interrupt:17 Base address:0x1400


the site is running on a private network, the firewall has port forwarding turned on.

---

### Post by Mr. C. on 2008-03-26
This sounds like an MTU problem.

You have ping disabled - how is that disabled?  It is important to not block all ICMP messages, as some are used to aid in correct networking.

Try lowering the MTU to 1380 for a first pass to see if this is the issue. You can increase it upwards to discover the correct limit later.
```

sudo ifconfig eth0 mtu 1380 
```

It is also possible this is an IPv6 problem, and that you need to disable IPv6 on your box.  After working through the above, see: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by awreneau on 2008-03-31
Sorry for the delay in replies, out of town...


OK, changed the MTU and turned off IPV6.....will see what happens now.

Thanks!

---

### Post by awreneau on 2008-03-31
No dice.....

Still just sits and waits.

---

