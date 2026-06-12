---
title: "Can't connect to web server through external ip"
date: 2011-10-20
forum: Server Platforms
---

### Post by benp6 on 2011-10-20
Hi all, this is my first post on here :)

I recently set up my first web server running ubuntu server. 
At first i was just using it on my lan and then i forwarded the relevant posts so i could access it externally. All worked fine. However for some reason my external ip has now changed and i can no longer connect to my website or connect to the server via ssh.

Any ideas?

Kindest regards

Ben

---

### Post by haqking on 2011-10-20
> **benp6 said:**
> Hi all, this is my first post on here :)

I recently set up my first web server running ubuntu server. 
At first i was just using it on my lan and then i forwarded the relevant posts so i could access it externally. All worked fine. However for some reason my external ip has now changed and i can no longer connect to my website or connect to the server via ssh.

Any ideas?

Kindest regards

Ben

Welcome to the forums,

your IP changed because ISP tend to assign a dynamic address, or you have to purchase or ask for a Static one.

So you are saying you dont know the new address ? why cant you check it ?

And in future either get a static or use a service such as dyndns.org to use a hostname that tracks the IP.

---

### Post by papibe on 2011-10-20
Hi benp6. Welcome to the forums!

That's a pretty common situation.

Most ISP accounts work with some sort of DHCP. Just like your router may assign a different LAN IP to a local machine (although I have to say that most modern routers have good memory).

What you need is to subscribe a Dynamic DNS service. I use DynDNS but they are several services supported by Ubuntu. First you create an account with them, and then you install the ddclient (it is in the repositories).

Take a look at this [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video tutorial from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

Hope it helps. Let us know how it goes.
Regards.

EDIT: haqking, you are fast!

---

### Post by benp6 on 2011-10-20
Hi and thank you for the welcome.

Yes i do know the ip address. However, when i type this into my browser it does nothing, just cant load a page. Are there any configuration settings i need to change on my web server, i just dont understand why external traffic cant now be routed to my web server through my ip? surly it shouldnt matter if the ip changes so long as i know what it has changed too?

---

### Post by papibe on 2011-10-20
Just to be clear: as a prerequisite, you need to set your server to a static LAN IP (for example 192.168.1.5). And forward the necessary ports to the it.

As I said before, most modern routers won't bother you with that, but it is the right way to go before trying to access your server from the Internet.

Could you give us more details what is not working?

Another important point: you can't access your own server using its public IP from the LAN itself. That ability is called **NAT loopback** (read about it [here]("http://www.dyndns.com/support/kb/loopback_connections.html")). Most consumer's routers don't support it.

Is that help?
Regards.

---

### Post by benp6 on 2011-10-20
> **papibe said:**
> Hi benp6. Welcome to the forums!

That's a pretty common situation.

Most ISP accounts work with some sort of DHCP. Just like your router may assign a different LAN IP to a local machine (although I have to say that most modern routers have good memory).

What you need is to subscribe a Dynamic DNS service. I use DynDNS but they are several services supported by Ubuntu. First you create an account with them, and then you install the ddclient (it is in the repositories).

Take a look at this [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video tutorial from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

Hope it helps. Let us know how it goes.
Regards.

EDIT: haqking, you are fast!

Thanks for the help. Looks great. However this doesnt change the fact that i still cant acces my website even with the current correct ip address, i just get no-were?

---

### Post by benp6 on 2011-10-20
> **papibe said:**
> Just to be clear: as a prerequisite, you need to set your server to a static LAN IP (for example 192.168.1.5). And forward the necessary ports to the it.

As I said before, most modern routers won't bother you with that, but it is the right way to go before trying to access your server from the Internet.

Could you give us more details what is not working?

Another important point: you can't access your own server using its public IP from the LAN itself. That ability is called NAT loopback (read about it [here]("http://www.dyndns.com/support/kb/loopback_connections.html")). Most consumer's routers don't support it.

Is that help?
Regards.

Hi sorry for the lack of knowledge, i can access it from outside my lan i just checked, however i could access it from inside before, but i now cant. Also when i try and connect over ssh with the new ip for my router, it just times out?

---

### Post by papibe on 2011-10-20
Are you using the standard port 22? 
Did you forward it to your server?

If all OK, try checking if you have some sort of ISP port restriction by making test here: [CanYouSeeMe]("http://canyouseeme.org/"). It may be necessary to change the port for a non usual (and higher) port number.

Tell us how it goes.
Regards.

---

### Post by benp6 on 2011-10-20
Yes i have forwarded port 22 and 80 to the server, and untill my router obtained a new ip i could connect over ssh? strange?
i am just in the process of setting up a static ip on my server through /etc/network/interfaces
are the only ips i need to include; address, netmask and broadcast?
Also is there any correlation between the broadcast and the adress?

Thanks 

Ben :)

---

### Post by papibe on 2011-10-20
Yes, of course they are related. All that info can be obtained from a few commands before you make the change:
[LIST]
[*]Use ifconfig to obtain broadcast and netmask.
[*]Use 'route -n' to get the network id, and default route.
[/LIST]
Also check this tutorial [here]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html").

Note: the **easiest** way to do this is to check if your router have support to set static IPs (actually DHCP reservation). That way you won't have to do anything in your server's network configuration.

Regards.

---

### Post by benp6 on 2011-10-20
it has an "always use this ip adress option". does this eliminate the need to set up a static ip on my router?

regards
ben

---

### Post by papibe on 2011-10-20
Where does it say that?

If it's on the router, you don't need to anything in your machine.

Regards.

---

### Post by benp6 on 2011-10-20
I think i have worked it out.

I made my computer fore the same ip onto my machine.
I then set up dyndns within my router.
I then did a url redirect to the dyndns url.

So hopefully i should always be able to connect now.

seems messy but it works.

Thank you very much for your assistance!

Ben

---

