---
title: "firestarter is blocking all traffic"
date: 2007-07-26
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-26
Hi all,

I have just reinstalled my server.  gone upto Feisty... I have put Firestarter on and it seems to kill all my internet traffic.  I can still ping the server from an internal computer (can get them to see the net yet (but thats another issue)....

anyway.. with firestarter off I can get webpages. but I turn it on and it all stops.

policies:

outbound = permissive with no rules
inbound = allow services: HTTP 80, DNS 53, DHCP 67-68 (the latter two being "when the source is" lan clients).

I am completely stumped.  I used to have a firewall that did the IP tables directly but thought I would give Firestarter a go as I have heard good things.

/feels a bit silly as it is supposed to be real simple.

the network cards are set up right: eth0 for external and eth1 for internal DHCP is running.

Thanks for any and all help :)

---

### Post by twistedtwig on 2007-07-29
Hi all

so I seem to have DHCP working and it is allowing the computers WITHIN the network to see the net but it firestarter wont allow the server to see the net.

as previously mentioned I have permissive by default selectd as outbound traffic with no denies.

in bound I have http port 80 everyone (site not working yet no idea)
DNS 53 localnetwork (lan)
DHCP 67-68 local (lan)

Has anyone else had this issue?

Thanks

---

### Post by koenn on 2007-07-29
You're gonna have to be a lot more precise (or just post the output of iptables -L). Packet filtering is delicate, and the way you summarize is very ambiguous. Or maybe firestarters "user-friendly" output is confusing. 

If you say
in bound I have http port 80 everyone (site not working yet no idea)

does that mean that traffic coming **to **port 80 of your server is allowed ? That would be OK if you run a web server on that machine, but doesn't help if you want to browse the web *from* that server. For web access you'd need to allow inbound trafic **coming from** port 80 (any address) - or (more general) allow incoming traffic on established connections (the connection is established during your request to get a web page). 

You see how just listing port numbers is insufficient to describe the situation ?

---

### Post by twistedtwig on 2007-07-29
Sorry you are right looking at it I was not very clear.

I have / will have my website (apache) up and running (apache is in with default page displayed).  This is what the HTTP inbound for everyone statement is for.

The reason I put the DNS and DHCP bits into firestarter was to try and get the local network working correctly, (i.e. local users can get a dynamic IP address).

At the moment I do not seem to be able to get the website to display (IP resolves, I am using easydns with ddclient which resolves to the correct IP), it tries to load but never gets there.  Would seem that it knows where to go but never gets a response.  If I do the Server IP for the local network (DNS is not working yet) apache returns pages.

I can connect and do all normal things on the net from any computer inside the network, but if I try  and connect to any page on the net from the server it does not get any page.  If I turn Firestarter off, the server can connect straight away, but then the other computers in the network can not connect to the server let alone the internet.

I will post the iptables -L results soon (as  soon as I get onto the server).  I have had a look at it but I really didn't understand it to be honest.

Thank you for your help :)

(I hope this is more along the lines you need for information)

---

### Post by koenn on 2007-07-29
OK, I'm beginning to se the picture, 
> **twistedtwig said:**
> 
inbound = allow services: HTTP 80, DNS 53, DHCP 67-68 (the latter two being "when the source is" lan clients).
If you want to browse the web from your server, you'll need an inbound rule that allows trafic from port 80 anywhere to your server, any tcp port > 1024, and/or a rule that says incoming trafic on related/established connection is allowed. 
Your browser sends out a request to a webserver:port80 from a random port on your server, and the reply should be able to reach your server on that same random port (higher than 1024).

> **twistedtwig said:**
>   If I turn Firestarter off, the server can connect straight away, but then the other computers in the network can not connect to the server let alone the internet.
Are you using that server to share your internet connection / single public IP address with the other PC's ? Then iptables is is probably doing NAT/MASQUERADING and turning it of would disallow the PC's access to the internet.

---

