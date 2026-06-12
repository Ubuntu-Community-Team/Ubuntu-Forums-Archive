---
title: "Joining Vista client to Windows domain"
date: 2008-05-24
forum: Virtualisation
---

### Post by trspencer on 2008-05-24
While I would love nothing more than to kick Windows to the curb, for work purposes I have Vista running via VirtualBox inside Hardy. Thanks to this forum, I've got _most_ of what I need up and running, the only thing I can't do is join Vista to my corporate domain.

Note: I am able to connect via VPN, no problems there. I just need to get Vista joined to the domain so Office Communicator (and pieces of Outlook) function properly. 

Whenever I do try and join the domain, I get the following error:

```
The following error occurred when DNS was queried for the service location (SRV) resource record used to locate an Active Directory Domain Controller for domain myWorkDomain.com:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.myWorkDomain.com

Common causes of this error include the following:

- The DNS SRV records required to locate a AD DC for the domain are not registered in DNS. These records are registered with a DNS server automatically when a AD DC is added to a domain. They are updated by the AD DC at set intervals. This computer is configured to use DNS servers with the following IP addresses:

10.0.2.3

- One or more of the following zones do not include delegation to its child zone:

myWorkDomain.com
. (the root zone)

For information about correcting this problem, click Help.
```

I've also tried joining the domain while physically on the LAN, unfortunately to no avail. I've seen a number of posts in the forum about Samba, but I've had no luck there, either. Has anyone been able to do this? I would appreciate any guidance anyone has to offer. Thanks in advance for your time. 

Tim

---

### Post by MaindotC on 2008-05-24
I can tell you from experience that it has nothing to do with DNS.  When you're on the same LAN the client should be able to contact the domain controller (DC) via NetBIOS communication.  I've run into this problem before before because I took an Active Directory class.  I can't remember precisely what it was - I think it has something to do with the protocols you install in Network Settings for the specified connection (not sure what its called in Vista).

I'll try and get an answer for you soon but other please suggest as events warrant.

---

### Post by MaindotC on 2008-05-24
I'm sorry - actually I was doing this in a lab environment with a client joining a domain and it required manipulating the installation of Active Directory.  I sincerely doubt in a corporate environment you have access to that.

In a corporate environment it may very well be related to DNS.  So far I've found a lot in Google but nothing you probably haven't found yet.

I'm sorry - I forgot you were in a corporate environment.  I'm not able to help you.  Again, I apologize.

---

### Post by trspencer on 2008-05-24
strAlan...no worries, thanks for looking into this. 

FWIW, I do have some fairly liberal access to the environment, so I can root around in the network probably a little more than I should ;-)

I'll keep rooting around to see what I can find. I'm hell-bent on proving to our network admins that this environment (Hardy/xVM/Vista) can work, and I HATE to lose, so if I find a solution I will certainly post it here.

---

### Post by MaindotC on 2008-05-24
We used [this book]("http://www.course.com/catalog/product.cfm?isbn=978-0-619-21755-6&CFID=8440736&CFTOKEN=46655093") to do the AD labs and I swear to god everyone who did the labs had the exact same problem and it was easily resolved.

From a physical standpoint, we just had 2003 Server as a DC and we didn't deal with a router or a switch or anything like that - just connected other servers with a cat 5 cable and joined them to the domain.  I remember when we tried joining them it gave us the exact same problem at first, but we didn't do anything with DNS - we hadn't even learned DNS at the time.

I think it's NetBIOS and let's discuss why before you do it.  Our professor saw the problem and said "well, let's identify the problem.  How DOES a server join a Win2K domain?"

Concentrate with me here.  Does the layer 2 communication make sense?  Here's what I'm thinking.  The server (or client) you're trying to get to join the domain - when you tell it to join the domain it sends out a request to contact the domain controller for authorization.  It can do that via DNS on Layer 7, but I think it could also do it via NetBIOS on Layer 2.  I'm not 100 sure what NetBIOS traffic looks like - I could probably google some but not till later - so I'm not sure what is included in the frames.  Yes, we should be dealing with frames not packets.

For the above that I just stated, I would advise enabling NetBIOS protocol in the network settings for the DC (if you can) and on the client you're trying to get to join the domain.  Check my thinking.

If you cannot modify the DC, I would then try checking the DNS records on the DNS server.  I've run into a problem with DNS in Linux where it doesn't allow outside queries by default but DNS running on Server 2008 does allow outside queries by default so if there's an entry for your machine and an entry for the DC (there better be) I would run a sniffer on the DC and see if the request is reaching the DC.  If you don't see anything arriving then try sniffing from the node you're joining to the domain - make sure it's actually sending out a request.

I swear to god it was something really, really easy and simple, but that was for a lab environment that I described - just two boxes talking to each other, no DNS, no routers, switches, etc.  I wish I could go set it up but I'm locked out of the comp lab till Tuesday.

Damn it I wish I could help you.  I'll keep googling.  You know what, I think in that book it actually says "if you run into this common problem, this is why and how to fix it" but I sold the blasted thing.

---

### Post by MaindotC on 2008-05-24
Btw I'm assuming you're familiar with all of my terms and that you're a well-rounded network administrator so please ask me if you have any questions as to what I'm talking aboot.

---

### Post by MaindotC on 2008-05-24
Hey spencer - can you ping the DC by IP and by name?  If you can ping by name then there's no way it could be a DNS issue.

---

### Post by trspencer on 2008-05-25
The DC name is added to my /etc/hosts file, but like the other values in that file I can't ping them. I _think_ the ping is being halted by xVM, as I can't ping anything within Vista. 

I can, however, connect to the DC via RDS in Vista, both by name and by number, so I know I can connect to it. 

Does xVM turn pings off by default?

---

### Post by MaindotC on 2008-05-25
I'm not familiar with xVM - I use virtualbox.  However, you should be able to configure your Vista VM for straight connectivity to the physical machine's NIC, NAT, or no connectivity.  Are you able to access other internet resources with Vista like browsing or FTP?

Btw, you are the administrator of the domain with the domain administrator password, right?

---

### Post by trspencer on 2008-05-25
That is correct. Within Vista I can browse to both internal and external sites (www and ftp). Right now it's configured to use the hosts NIC (using NAT). 

My account does have admin rights in the domain.

And thanks again for pursuing this, I appreciate the help.

BTW, got my answer about pinging (excerpt from Sun Virtualbox help file):

ICMP protocol is very limited:
Some frequently used network debugging tools (e.g. ping) rely on sending/receiving messages based on the ICMP protocol. The ICMP protocol cannot be used directly by normal applications such as VirtualBox, as it would, at least on Linux hosts, require root permissions (more precisely CAP_NET_RAW). Since this is not desirable, no attempt has been made to support ICMP to addresses other than 10.0.2.2 and 10.0.2.15. If you try to ping any other IP address you will not get any response.

---

### Post by MaindotC on 2008-05-25
I just want to be very specific - you are a domain administrator - like in the "Domain Administrators" group in AD it has your login credentials, right?  Just want to make sure we're clear on that.  If you've joined other clients to the domain before then it's not even a question.

I'm not sure about that NAT'ing issue.  I don't think NetBIOS will work because once it leaves the software NAT it has no way to get back.  I'm going to bed - I hope someone else can advise you in the meantime.

---

### Post by trspencer on 2008-05-25
That is correct...I am in the domain admins group.

The more I look at it the more I'm convinced the NAT setup in Virtualbox is the problem. I _think_I need to set up a host interface to get around the protocols that NAT blocks, assuming that can be set up correctly (my first attempt last night didn't work right), I would think I'd still need to get Samba in place as well. Was hoping to avoid Samba, as it has been very unstable on my box. 

At any rate, am going to try the host interface route and see where that leads me.

---

### Post by MaindotC on 2008-05-25
Can you try using a physical client and not a virtual one?

---

### Post by trspencer on 2008-05-26
That's a last resort...hopefully I don't have to do that. I'm making progress setting up a host interface, taking NAT out of the equation. I _think_ once that's in place then domain authentication should be possible.

---

### Post by alemic48 on 2008-05-26
delete

---

### Post by MaindotC on 2008-05-27
Alemic what an informative and helpful post!  Yemen ???  I'm getting my 4GB tomorrow so I should be able to run some more VM's and troubelshoot this myself.  If I try any of my VM's I get a lockup so I think it's definitely a ram issue.

---

### Post by alemic48 on 2008-05-27
> **strAlan said:**
> Alemic what an informative and helpful post!  Yemen ???  I'm getting my 4GB tomorrow so I should be able to run some more VM's and troubelshoot this myself.  If I try any of my VM's I get a lockup so I think it's definitely a ram issue.

i love you alan. ur my hero

:guitar:

---

### Post by MaindotC on 2008-05-27
Dude this 4GB upgrade is sweet!  I had some trouble w/ VM's but now I've got OpenSolaris, Solaris 10, XP, and Vista Ultimate running - 1 GB of memory for each :)

---

### Post by alemic48 on 2008-05-27
> **strAlan said:**
> Dude this 4GB upgrade is sweet!  I had some trouble w/ VM's but now I've got OpenSolaris, Solaris 10, XP, and Vista Ultimate running - 1 GB of memory for each :)

wow thats sick. i think im gonna get this for 45 after GC.

[http://www.buy.com/prod/ocz-4gb-2-x-2gb-sodimm-ddr2-667mhz-laptop-memory/q/loc/101/204887399.html](http://www.buy.com/prod/ocz-4gb-2-x-2gb-sodimm-ddr2-667mhz-laptop-memory/q/loc/101/204887399.html)

---

### Post by MaindotC on 2008-05-27
Cool - I got $10 off my first order from GC.

---

### Post by MaindotC on 2008-05-29
Spencer what's the status on this issue?

---

### Post by trspencer on 2008-05-30
Sorry...busy week at work, haven't had an opportunity to pursue next steps. 

Through a couple of sources I've been able to confirm that NAT is the root cause of my problems, that I need to get a properly configured host interface running in order for the domain request to be successfully passed from the guest to the DC. 

Hoping to find the time this weekend to try this: [http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/]("http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/"). Will follow up with results asap. 

Thanks again for following up...Tim

---

### Post by theZoid on 2008-05-31
Check the Zenwalk wiki for VirtualBox setup as I if I remember they go into what you want to do, i.e. set up an interface suitable for lan connectivity by the client OS.  It's late now, but worth checking.  If I wrong, I tried :D

---

