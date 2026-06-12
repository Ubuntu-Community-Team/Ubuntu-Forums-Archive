---
title: "Samba Authentication."
date: 2004-12-23
forum: Server Platforms
---

### Post by tvlad on 2004-12-23
I'm on a lan consisting of 16 or so computers, connected with switches, with one computer with linux installed acting as a server for only 5 of those 16 computers.

The external ip is on the server. The server is used as both a firewall for external, AND internal computers who don't pay for the net, by blocking their mac addresses and ip, and is also used for NAT for those 5 paying computers.

The trouble is that if someone sets the same IP and MAC address as mine or another of those computers who have net access, even if the paying computer is on, he WON"T get an ip conflict message, meaning that anyone who knows about this can steal to their heart's content.

One way to solve the problem would be through manageable switches, though it's not feasible because we don't have any. Another way would be to use Samba for authentication, an authentication based on a software key on those computers who have net access, the question being is HOW can i implement it, perhaps you could help me with some answers, thanks.

---

### Post by socrazy143 on 2004-12-24
Are you talking about setting up a domain?

Samba can do that by using MySQL as the backend and is quite simple to do.  Go to [http://www.tldp.org](http://www.tldp.org) (Linux Document Project) they have a nice how-to for Samba.

---

### Post by tvlad on 2004-12-24
What i meant is that seting up a domain seems to be just a bit complicated. I once redirected all trafic through squid and made user's authenticate before being allowed access to the net.

Can i do the authentication part with certificates (software keys), given by me, instead of username and password ? because the username and password won't be effective in my situation, if i've authenticated and someone who steals my mac and ip, to samba it will be me, and he won't be asked to authenticate.

---

