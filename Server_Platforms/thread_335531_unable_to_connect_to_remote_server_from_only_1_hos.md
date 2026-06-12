---
title: "unable to connect to remote server from only 1 host"
date: 2007-01-10
forum: Server Platforms
---

### Post by PetePete on 2007-01-10
ok this has got me quite stumpted...

Ive got a ubuntu server (running in a remote location) and can't seem to connect to it (ssh or anything) from my home connection. for example if i run ssh or telnet xyz 22 it just times out.

but the strange thing is if i run it from work, or via VPN with works ip, or ssh to another server and connect from that it works fine.

I've tried connecting to it from my vmware windows PC and that has the same issue, so i dont think its to do with my PC..

The server isn't running a firewall (its behind a router with port fowarding) so its not a case of that dropping the packets .... (i was using fail2ban, but stopped this and checked the logs and it didn't mention anything about my home IP)

any ideas?!!!

---

### Post by Brazen on 2007-01-10
This server is at work, and you are at home, right?  I would assume the network at work has a firewall, so is port 22 from the firewall forwarded to the Ubuntu server?  Are you establishing a vpn connection from your home to your work network?  Is this server supposed to be accessible from the internet?

---

### Post by PetePete on 2007-01-10
no no no! the server is mine, just at another location (my other house..) 
i was simply using my works VPN to test if i could connect to my server (which i can)
just when i'm at home i can't.... unless i connect through VPN at work, then connect to server, or ssh into another box first.

and i know there isn't any fancy firewall on the server as i set it up!

---

### Post by PetePete on 2007-01-10
for example.
me ---- work via vpn----server = ok
me --- ssh some other linux box --- server = ok
me --- server = host not found ????

i've also tried pinging myself from the server (when logged in through a 'proxy') and it results in 100% loss ?????!
although doing a nmap ping sweep on the subnets does show other hosts on the subnet up, just not my PC  :(

it was working a few days ago

---

### Post by Brazen on 2007-01-10
So is this server open to the internet?  No router even?

Is your setup like this?
Home1:
computer ----router ---modem ---- internet

Home2:
server ------ modem ----- internet

---

### Post by PetePete on 2007-01-10
the server (home2) is behind a router..

home1(where i am now) 
computer -- router--modem--internet

home2
server -- adsl belkin modem/router --- internet


even more strange, just logged into the server (from proxy) and tried pinging myself (home1) and also resulted in 100% loss ????? but other IPs on the (ISPs) subnet  were ok.

I think somewhere along the line theres a firewall which is banning all outgoing and incoming traffic to one of my IP addresses, either home1 or home2..... But i def havn't set that up, would an ISP do this? Not even like i've used it much.

I've also rebooted home1's router and modem... will make a call later and try and get home2's router reset, but i can't see that being the issue.

---

### Post by PetePete on 2007-01-10
ok heres some logs from traceroute... (dunno if this is a good idea posting this, but f' it !)

[edit]
removed traceroute logs as they were the same for tracerouting IPs which i can access in teh same subnets...

---

### Post by Brazen on 2007-01-10
hmmm, well usually home routers will not respond to ping requests on the outside interface.  Do you have remote administration set up on home2's Belkin router?

If so, you could try and see if you can connect to that (this would be disabled by default).  If you CAN connect to the router, then it would be a clue as to where your problem lies.

Also, you ISP may have decided to block port 22.  I don't think it's common for ISP's to block port 22 (Cox doesn't) but they do block certain ports incoming to home connections.  Such as, port 80 is probably blocked for sure, maybe even 8080 (your router might use 8080 for the remote admin, just change that to 8081).

---

### Post by PetePete on 2007-01-10
well i purposly set up home2s router to block wan pings, but home1 is set to respond and does from other hosts, just not from home2..

Its not a case of the port being blocked, as im using a non default port and it DID work a few days ago.

unfortunatly i dont have remote admin on home2's router. 

think the next step is to get home2's router reset, which will change the IP address (DHCP adsl) and go from there, only prob is no one's answering the fecking phone!

cheers for the help

---

### Post by PetePete on 2007-01-10
Finally managed to get through to somone and instructed them to restart the router at home2.

everything appears to be working fine ..... for now :D

bit weird though how a belkin router could deny 1 single host.

---

### Post by Brazen on 2007-01-10
wow, yeah, I'm pretty surprised that fixed it.  good deal.

---

