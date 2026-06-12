---
title: "Linux server Vs, Windows Server"
date: 2007-03-28
forum: Server Platforms
---

### Post by Nxion on 2007-03-28
Hi all,

I want to know form you point a view would Ubuntu be a good choice for a file/mail server over a Windows server ? Or should I separate the servers. Meaning should i have one for Active Directory and File sharing and the other for mail server ?

Any advice would be very helpful in my decision.

Thanks :)

---

### Post by Brazen on 2007-03-28
I would suggest having one Samba file server and one postfix email server, running on Ubuntu Dapper.  You'll probably also want an OpenLDAP server for authentication.

---

### Post by pppetter on 2007-03-28
It's really hard for "us" to answer that question. It all comes down to you anyway. But we could give you some advise on the way. 

Personally I would answer your question with another question. What is it for? Your home or  a small office? What OS does the clients run? And so on....

---

### Post by Nxion on 2007-03-28
It is for a Small office

All the clients are Windows XP Pro and maybe 1 or 2 Vista machines.

The office uses Comcast internet with a small Linksys router/switch which goes to a 16 port switch. This switch/router serves as a DHCP server to dole out addresses,

---

### Post by Brazen on 2007-03-28
I would get 1 hardware server and put VMWare Server on it, so you can create the 3 servers I mentioned in virtual machines.

---

### Post by Nxion on 2007-03-28
Hmm that is a good idea Brazen. I always forget about VMware :)

---

### Post by rickyjones on 2007-03-28
I'm a fan of "one server, one application." Yes, this is usually more expensive but it can definitely save a lot of aggravation down the road. For a small office setup I would probably go with two physical servers: one would be dedicated active directory; the other could be a dedicated VMWare machine hosting several linux servers each with their own task.

I'm not sure if that is the perfect way, but it definitely seems like a feasible option. Personally, if you are running a production network that needs optimal uptime and performance then you will want to separate your applications and servers as much as possible. That way the failure of one piece of hardware will not bring your network to its knees.

-Richard

---

