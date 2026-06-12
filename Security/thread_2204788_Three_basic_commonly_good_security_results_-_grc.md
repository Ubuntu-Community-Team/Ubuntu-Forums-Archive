---
title: "Three basic commonly good security results - grc"
date: 2014-02-10
forum: Security
---

### Post by ventrical on 2014-02-10
Here is a test (and results) for those who are worried about their security. Although there are no guarantees, GRC is a very solid test.

Simply go to:

[www.grc.com]("http://www.grc.com")

and run the "Shields Up" and examine the first three tests, File Sharing, Common Ports and All Service Ports.

  A secure system (with a good router) should produce results such as the below. The reason I am posting this is to give other end_users a starting point if they are investigating security problems on their systems.

---

### Post by ventrical on 2014-02-10
If you have been running a Windows OS and had been hacked in the past then it can be likely that you router has been hacked. If you run Sheilds Up and notice some failures, open ports, closed ports .. etc.. then it is your router and not Ubuntu that is the problem.


Regards

---

### Post by Lars Noodén on 2014-02-10
> **ventrical said:**
> A secure system (with a good router) should produce results such as these:

Not necessarily. The scan analysis appears to mistake using reject, rather than drop, as a problem.  Many do not view it that way:

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

Using drop does not 'stealth' the firewall nor does it add security nor add performance.  A case can be made that it reduces performance, which is certainly true for legimate users.  

Then there is the question of ping.  Without ping, the net is broken.  Again, blocking ping doesn't 'stealth' the firewall nor does it add security nor add performance.  Actually it reduces reliability and performance. 

That said, it was interesting to try the scan.  What is your connection with the site?

---

### Post by ventrical on 2014-02-10
> **Lars Noodén said:**
> Not necessarily. The scan analysis appears to mistake using reject, rather than drop, as a problem.  Many do not view it that way:

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

Using drop does not 'stealth' the firewall nor does it add security nor add performance.  A case can be made that it reduces performance, which is certainly true for legimate users.  

Then there is the question of ping.  Without ping, the net is broken.  Again, blocking ping doesn't 'stealth' the firewall nor does it add security nor add performance.  Actually it reduces reliability and performance. 

That said, it was interesting to try the scan.  What is your connection with the site?

  I have used the site while servicing customers of infected Windows Operating systems and running various firewalls and AV software. I am not connected directly to the site in a buisness manner.

 Also .. when using terms such as 'myths' which is inferred by one of the links you had presented I find that those arguments lack credibility. Counter pinging a ping reveals a port for discovery , it does not stealth it.

  However, there is a method where an end_user can drop the protection from the router and then run the test and see what actual ports are open or vulnerable.  The counter argument is that using drop provides to the hacker/prober that the port simply does not exist. (therefore stealthed by the router).. but I would not go as far as to say that the  PC is immune from attack, however , in my years of testing so far I have yet to see a break in the security of my machines from any malware source. The authentication process makes the actual PC pretty well impermeable. 

 I am able to run various AV software for  linux on Ubuntu , verifying with EICAR.. etc.. and it is a rare occasion that anything gets through , and if a malware does get through , it is rendered usless  by the infrastructure of the operating system (unless it is directed to attack a linux system specifically).


  I am not trying to give anyone a false  hope of security, just a starting point to be less paranoid about malware and how Ubuntu has handled security on my specific installs.

regards.. and thank-you for the very informative links..

---

### Post by CharlesA on 2014-02-10
Drop ("stealth") and reject do exactly the same thing except drop discards packets silently while reject sends a respond that that port isn't open.

They are equally secure. It does not matter if the server sends a response or not, the port is still closed.

As far as Shields Up! goes, it only scans whatever device is attached to your connection, which is usually a router, so anything behind that router isn't seen or tested.

If you really want to check what ports are open on the machines inside your LAN, make nmap your friend.

---

### Post by ventrical on 2014-02-10
Umit , for noobs :)

---

### Post by CharlesA on 2014-02-10
> **ventrical said:**
> Umit , for noobs :)

Found a better explanation. :)
[http://www.insanitybit.com/2012/05/30/stealth-ports-or-closed/](http://www.insanitybit.com/2012/05/30/stealth-ports-or-closed/)

---

### Post by The Cog on 2014-02-10
I'm with CharlesA and Lars Noodén. IMHO, "stealth" is a sales term dreamed up by GRC in order to sell firewall software to nervous windows users who are connected directly to the internet, not even via a router. If you are going to block with iptables, it is probably better to use -j REJECT rather than -j DROP so that you can more easily debug network connectivity problems. Firewalls that drop packets waste loads of debugging time.

---

### Post by ventrical on 2014-02-10
There is no prerequisite to use GRC.  If you are worried about your security and need a starting point then I just made the suggestion that it may be of some help to noobs. I am not here to debate it's commerciality.

Regards..

---

### Post by The Cog on 2014-02-10
Oh I agree that the GRC web site is very useful for checking yourself for open ports. Well worth knowing about and using. 

It's the pushing of stealth as good and closed as somehow bad that I disagree with. And people using it should be aware that unless they have set up port forwarding, they are probably just scanning their router.

---

### Post by ventrical on 2014-02-11
> **The Cog said:**
> And people using it should be aware that unless they have set up port forwarding, they are probably just scanning their router.

  That was the intention of my original post .. (with a good router).

"
  A secure system (with a good router) should produce results such as  the below. The reason I am posting this is to give other end_users a  starting point if they are investigating security problems on their  systems."

---

### Post by linuxyogi on 2014-03-17
> **ventrical said:**
> That was the intention of my original post .. (with a good router).

"
  A secure system (with a good router) should produce results such as  the below. The reason I am posting this is to give other end_users a  starting point if they are investigating security problems on their  systems."

I dont know what you mean by a good router. I am using DLINK GLB 502 T. 

After reading about the subject I realized that there is not much of a diffence between closed and stealth.

The point is all ports on the router side are in stealth mode (I use grc.com too.) but still I find incoming connection getting blocked on the Linux side (Ubuntu/openSUSE) which means some advanced attackers are able to penetrate my router.

So as you can see stealth is mostly hype.

I looked the IPs from where the attacks were coming at that time. Countries included Ukraine, Australia, Bosnia, etc.

---

### Post by CharlesA on 2014-03-17
> **linuxyogi said:**
> 
So as you can see stealth is mostly hype.

The only difference between "Stealth" and "closed" is which rule you use in iptables. Drop vs Reject. I use reject now, but I used to use drop and it made troubleshooting a royal pain in the butt. However, the all purposes, they act the same, if a port is closed, it is closed.

There is no such thing as stealth outside of Gibson's definition of it and his "security scanner" but wouldn't you do that to get more people to use your site?

---

