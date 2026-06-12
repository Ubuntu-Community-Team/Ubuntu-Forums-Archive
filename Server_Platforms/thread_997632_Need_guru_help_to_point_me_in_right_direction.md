---
title: "Need guru help to point me in right direction"
date: 2008-11-30
forum: Server Platforms
---

### Post by headhunter23 on 2008-11-30
Hello, new to forum.  Used to have red hat servers and internet servers hosting 6 years ago.  Burned out, getting back into it, seems I'm bloody rusty.

I have a ubuntu server already setup on my own private network(two other home computers) behind a basic linksys router.  Has all the basic internet server stuff installed plus samba(I'm sure this is a security risk, I would like to keep it running as I enjoy the file server aspect for home computers, if you think this is a really bad idea.  Please post, or post on how to make it secure)

The server is the dmz for the network.  I've been trying to setup a dns server for multiple domains](*,).  Unfortunately I can't get it to work.  I've been digging and reading up on this, I've read a lot of suggestions to not go with a private dns server.  

Question at this point is, should I?  Shouldn't I.  Also if you've seen a succesful install off of rogers network behind a basic router, please post.

Thanks in advance for info and suggestions!;-)

---

### Post by bab1 on 2008-11-30
> Has all the basic internet server stuff installed plus samba(I'm sure this is a security risk,

For many years now Samba has been considered a LAN technology only.  I don't believe ISP's will allow traffic on these ports:
```

netbios-ns	137/tcp		# NETBIOS Name Service
netbios-ns	137/udp
netbios-dgm	138/tcp		# NETBIOS Datagram Service
netbios-dgm	138/udp
netbios-ssn	139/tcp		# NETBIOS session service
netbios-ssn	139/udp
microsoft-ds    445/tcp         # Microsoft Naked CIFS

```
In a nutshell -- run samba behind a FW and only to serve you LAN needs.

> I've read a lot of suggestions to not go with a private dns server. 
No reason you can't run a DNS server for the LAN side.  On a small network it probably isn't needed.  Have a look at DNSmasq.  It's a lightweight DNS server that can be integrated with dhcp.

---

### Post by headhunter23 on 2008-11-30
Mmm... don't need dns for lan, need it for internet so people can see my domains.

Have run through both "the perfect server" and another ubuntu how to.  Still no luck, before I pursue further, just need question bellow answered first.

Anyways as an internet dns host, behind firewall but dmz host, on rogers network, would hosting dns server for internet be a good idea or should I go else where?

Ivan.

---

### Post by bab1 on 2008-11-30
As usual, it depends.  If you are an ISP or a HP or Google sized entity you want to run your own DNS serves.  If you need to make changes you just make them.  If you are a small domain that has gotten a name from someone like GoDaddy then you can have them host your DNS services.  If you ed to make changes you have to ask them to change it for you.

Most of my work has been with universities and we have change all the time.  Sub-domains come and go.  We have no thought of out sourcing.  On the other hand I have consulted for small companies and the hosted DNS worked well.

Then there is the *[COLOR="Green"]I want to do it because I can[/COLOR]* situation.  It all boils down to what you are trying to accomplish.

---

### Post by headhunter23 on 2008-12-02
I have 6 currently, some domains are from godaddy.  Some unfortunately are at networksolutions still, was never able to switch them over.  Networksolutions wasn't too helpful on that end.:(

have you seen a "how to" or a thread I might have missed in my searchs, specifically setting up dns for home based servers on rogers?  :confused:

---

### Post by bab1 on 2008-12-02
By Rodgers, I assume that you mean the ISP Rodgers.  No I have not seen (but I don't look) for anything specifically for either Rodgers or small local based DNS systems.

---

### Post by headhunter23 on 2008-12-02
bugger.  thanks anyways will continue digging.

---

### Post by bab1 on 2008-12-02
Let me think about this a little longer.  I want to get part of this straight in my mind though.  You have 6 domains (FQDN).  Do they point to a webserver hosting virual hosts?  Do you have a static IP address(s) from Rodgers? What did you mean by this:> Some unfortunately are at networksolutions still, was never able to switch them over. 
What did you need to switch over?

---

