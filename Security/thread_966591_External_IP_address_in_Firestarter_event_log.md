---
title: "External IP address in Firestarter event log"
date: 2008-11-01
forum: Security
---

### Post by myth01 on 2008-11-01
Hi there, 

3 days ago I setup a webserver on one of the PCs on my LAN.  The router is set to forward port 80 to it and all is working well there.  But while trying to fix a problem with samba on my desktop PC, I was checking the Firestarter events to see what was going on and found references to 2 external IP addresses.  These were blocked but I'm now concerned that people can get through my router's firewall and can 'see' the LAN PC's, or that having port 80 forwarded has now opened up a hole in security.

Any help or light on the subject would be most, most appreciated.

Ubuntu 8.04.1 Hardy (yet to upgrade!)

---

### Post by myth01 on 2008-11-02
...bump...

---

### Post by myth01 on 2008-11-02
I never seem to have much luck on these forums....can anyone help please?!

---

### Post by brian_p on 2008-11-02
> **myth01 said:**
> Hi there, 

3 days ago I setup a webserver on one of the PCs on my LAN.  The router is set to forward port 80 to it and all is working well there.  But while trying to fix a problem with samba on my desktop PC, I was checking the Firestarter events to see what was going on and found references to 2 external IP addresses.  These were blocked but I'm now concerned that people can get through my router's firewall and can 'see' the LAN PC's, or that having port 80 forwarded has now opened up a hole in security.

Forwarding port 80 on the router means anyone can see the web server but cannot see the other PCs, assuming you have set up the web server competently. There is no security hole per se in serving web pages if that is what you want to do. Blocking external addresses negates that of course.

---

### Post by myth01 on 2008-11-02
Thanks Brian.  I'm not sure if I made it clear but the web server and the desktop PC are 2 different machines.  The server seems to be serving up pages just fine.  Its on the desktop PC that the external addresses have been blocked, I just wasn't expecting to see external IP's appear in the firestarter log of the desktop, I thought that they shouldn't get that far (ie through the router firewall).

Just a bit paranoid since starting the web server...

---

### Post by myth01 on 2008-11-02
Double post, apologies.

---

### Post by brian_p on 2008-11-02
> **myth01 said:**
> 

Its on the desktop PC that the external addresses have been blocked, I just wasn't expecting to see external IP's appear in the firestarter log of the desktop, I thought that they shouldn't get that far (ie through the router firewall). 

You are implying only port 80 on the router is being forwarded. Correct? Then nothing can get through to the desktop. You're doing NAT I expect.

Getting a look at what firestarter reports wouldn't be a bad thing.

---

### Post by myth01 on 2008-11-02
Yes only port 80 is forwarded to the server.  Here is the section of events from firestarter.

---

### Post by brian_p on 2008-11-02
> **myth01 said:**
> Yes only port 80 is forwarded to the server.

Which implies firestarter (which I do not use) is detecting outgoing requests from the PC or responses to those requests. The events page can be configured to display more data. It may be worthwhile.

Not on an Orange/Wanadoo network are you?

---

### Post by myth01 on 2008-11-02
I had looked at the extra information but none of them provided anything else useful (In - eth1, Out - blank, Destination - my LAN ip, Length - 52, 48, 52, 64, 48, 64, and ToS - 0x00).  I am on Orange but the first IP appeared to resolve to a subscriber (customer77.pool1.cardiff-SQL5075-BAS0001.orangehomedsl.co.uk) rather than the ISP, and the other IP is from a pool provided by a swedish ISP.

The times they appear showed nothing strange in either the server's access or error logs or in any system logs on the desktop.  Is port 22401 reserved for anything or is it random?

---

### Post by brian_p on 2008-11-02
> **myth01 said:**
> 

The times they appear showed nothing strange in either the server's access or error logs or in any system logs on the desktop.

Your major concern is opening port 80 on the router opens up your whole network. It simply cannot happen; at least I am unable to think of a way in which you could have engineered that. So perhaps keep an eye on what firestarter reports, if only for curiosity's sake.

> Is port 22401 reserved for anything or is it random?

Is it always that port? About the only application which uses it (it's not a reserved port) is stunnel.

---

### Post by myth01 on 2008-11-02
The six occassions the connection was blocked (shown in the pic) are the only attempts I've seen so far, and its the same port in every case.  Thanks for your time and help so far brian_p.  I'm moderately new to linux and ubuntu (converted about 2 months ago), and I'm trying to learn as much as I can as quickly as I can.  I already feel like I know more about my PC than when it was "vista'd".

The connections were blocked which makes me feel better about them, but its still the curiosity of how the external systems had a chance to even be blocked by firestarter, and not by the router...

---

