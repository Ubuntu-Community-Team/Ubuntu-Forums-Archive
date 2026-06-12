---
title: "Which firewall should I use?"
date: 2008-11-17
forum: Security
---

### Post by jdunn on 2008-11-17
I have a laptop running Ubuntu that I plan to connect to a wireless network at home (behind a dedicated HW firewall) as well as to wireless networks in public areas.  Its been a long time since I've used and setup iptables.  What are some good choices for firewall software these days?  I don't want something overly complex or intrusive.  I just want something that provides good security.

---

### Post by scragar on 2008-11-17
Well most suggestions will actualy just be addons to IPtables, personaly I like firestarter, because it's a nice gui, but UFW is a nice command line choice, very easy to use.

---

### Post by cariboo on 2008-11-17
GUFW is now the preferred gui firewall interface in Intrepid. Firestarter is no longer being maintained.

Jim

---

### Post by bodhi.zazen on 2008-11-17
> **jdunn said:**
> I have a laptop running Ubuntu that I plan to connect to a wireless network at home (behind a dedicated HW firewall) as well as to wireless networks in public areas.  Its been a long time since I've used and setup iptables.  What are some good choices for firewall software these days?  I don't want something overly complex or intrusive.  I just want something that provides good security.

I think a better question is what are you wanting a firewall to do for you exactly ?

A default installation has no open ports.

FYI GUFW is now in the (intrepid) repos.

---

### Post by Kinstonian on 2008-11-17
> **bodhi.zazen said:**
> I think a better question is what are you wanting a firewall to do for you exactly ?

A default installation has no open ports.

FYI GUFW is now in the (intrepid) repos.

That's a common point made, but I think it makes a few false assumptions.

1.  *Firewalls are only useful for filtering inbound connections*:  If you only look at a firewall as filtering inbound connections, you only see half of it's potential.  What about filtering **outbound** connections to known bad IPs like the [Russian Business Network](http://en.wikipedia.org/wiki/Russian_Business_Network)?

2.  *All protocols use ports*:  There are protocols like ICMP which don't use ports.  It's not only commonly used for information gathering for attacks, but it's not unreasonable to think that there could be a vulnerability in the way it's handled by the OS.

3.  *Firewalls are only for preventing attacks*:  While they are no doubt prevenative controls, by analyzing the logs they generate they can detect both failed and successful attacks.  If you look at firewall logs from inbound traffic you can detect attacks and take actions.  If you look at firewall logs from outbound traffic like outbound IRC or SMTP traffic to China was blocked, you could have detected an incident.

If someone wants to use a firewall, I say go for it...

---

### Post by bodhi.zazen on 2008-11-17
> **Kinstonian said:**
> That's a common point made, but I think it makes a few false assumptions.

I did not make any assumptions, I only asked what the OP wanted to use a firewall for. My concern is that people coming from other OS feel they need to install a firewall without understanding basic (linux) security. Best make sure we are providing the best tools for the task at hand.

---

### Post by Kinstonian on 2008-11-17
> **bodhi.zazen said:**
> I did not make any assumptions, I only asked what the OP wanted to use a firewall for. My concern is that people coming from other OS feel they need to install a firewall without understanding basic (linux) security. Best make sure we are providing the best tools for the task at hand.

Fair enough.  Looks like **I** falsely assumed you were in the whole Ubuntu doesn't need a firewall crowd. :)

---

### Post by bodhi.zazen on 2008-11-17
> **Kinstonian said:**
> Fair enough.  Looks like **I** falsely assumed you were in the whole Ubuntu doesn't need a firewall crowd. :)

:lolflag: No, not at all. I am in the "what for" crowd, ie education :twisted:

---

### Post by brandon88tube on 2008-11-17
I'm going to jump in here and ask a question instead of making a new thread. I wanted to know if I should enable ufw or not. I know that nothing should be listening in on the ports, but I want to make sure when I install new programs that I have never used before are not using ports unless I tell it to.

---

### Post by bodhi.zazen on 2008-11-17
> **brandon88tube said:**
> I'm going to jump in here and ask a question instead of making a new thread. I wanted to know if I should enable ufw or not. I know that nothing should be listening in on the ports, but I want to make sure when I install new programs that I have never used before are not using ports unless I tell it to.

ufw is easy to enable / disable you will do no harm if you enable it.

---

### Post by brandon88tube on 2008-11-17
Ok, thanks.

---

### Post by hyper_ch on 2008-11-18
if you are behind a dedicated hw firewall, what do you need another one setup on your computer?

---

### Post by jdunn on 2008-11-18
> **hyper_ch said:**
> if you are behind a dedicated hw firewall, what do you need another one setup on your computer?

I'm running a laptop.  At home, I'm on wifi behind a dedicated hw firewall.  However, the rest of the time I'm on wifi at the local Panera, Whole Foods or on a university campus.  I do a lot of programming and I also use a bittorrent client.  I've had to write and test some programs that do remote procedure calls. I may also install SAMBA which I realize, has its own security measures.

I know that linux is much more secure than Windows.  I'd just rather be safe than sorry.  Thanks to the advice from this thread, I decided to go with Gufw.

---

