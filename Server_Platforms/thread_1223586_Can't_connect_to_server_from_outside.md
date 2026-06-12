---
title: "Can't connect to server from outside"
date: 2009-07-26
forum: Server Platforms
---

### Post by HarveyDX on 2009-07-26
Hi all,

I recently began playing around with Linux and servers. What I have is an old Dell Optiplex running Ubuntu Server 9.04. On my Vista laptop I can easly connect to the server using Putty for SSH and WinSCP for FTP using the local ipaddress. But when I try it out with my external ipaddress it won't connect. 

I have the following setup: 
a LiveBox modem (an another students room. I do have access to it though)
a Sweex router (also in the other students room and also access to it)
a Sitecom WL 341 router in my room.

Now i have forwarded ports 20 and 21 in both routers and the modem and when I checked both off them in canyouseeme both appear to be open. 

Now I read somewhere that since I'm on the same network or something it won't work when using the external ipaddress, but I find that to be a little fishy.

So what can I do to make it work? 

Thx in advance

---

### Post by volkswagner on 2009-07-26
What type of router are you using?

Check the security settings on your router for NAT.  On my Linksys I have "Filter Internet NAT Redirection" disabled.

---

### Post by Iowan on 2009-07-26
> **HarveyDX said:**
> Now I read somewhere that since I'm on the same network or something it won't work when using the external ipaddress, but I find that to be a little fishy.
What addresses are in use? (on each router?)

---

### Post by HarveyDX on 2009-07-26
Thx for replying guys,

@ volkswagner: I checked both routers and couldn't find anything like filter Nat redirection. Maybe you could tell me where to look?

@Iowan: Don't know exactly what you mean, but here goes:
On the modem i forwarded port ranges 20 & 21 to 192.168.1.20 <- checked that one on the sweex router.
On the sweex router i forwarded port ranges 20 & 21 via internal port 21 to 192.168.2.22 <- checked that on the sitecom router 
On the sitecom router i forewarded port 20 & 21 as two separated entry's to 192.168.0.101 <-static ipaddress of the server as in both entry's the local and public port is 20 resp. 21

---

### Post by cariboo on 2009-07-26
Just to state the obvious, put the default port ssh listens on is 22.

---

### Post by volkswagner on 2009-07-26
Hmn port 22.  :o

If it is not the obvious, check /var/log/auth.log.

You may have hosts.allow and hosts.deny setup.  You may need to add the ip to /etc/hosts.allow.

---

### Post by bartos on 2009-07-26
Default ssh port is 22. 
20 and 21 are for ftp. You should set your ssh port to a much higher range (mine is in the 8000's) and set up your router accordingly by forwarding that port.
Check here for file ```
etc/ssh/sshd_config
```. And edit the line Port 22


access it from a terminal by ```
ssh -p 8000 user@192.168.1.102
```.

---

### Post by HarveyDX on 2009-07-26
@cariboo907 & bartos 
I know that port 22 is for ssh and 20 and 21 for ftp. What I am trying to do is connect to the ftp using my external ipaddress. That's why I forwarded port 20 and 21. 
And also the PC I am using to connect with is a Vista computer running Putty for SSH and WinSCP fot FTP

@volkswagner I checked that using the man and googeling some, but I don't know how the entry should look like. (both of them are empty for now)

---

### Post by H4F on 2009-07-26
Check you ISP . as they might block ports below 1024 for security reasons.
I had similar problem, my ISP opened ports for me on my request.

---

### Post by HarveyDX on 2009-07-26
using canyouseeme it said that both port 20 and 21 are open...

---

### Post by bartos on 2009-07-26
HarveyDX

My mistake. Read your post too quick.

---

### Post by alienatom on 2009-07-26
> **H4F said:**
> Check you ISP . as they might block ports below 1024 for security reasons.
I had similar problem, my ISP opened ports for me on my request.

That's always a good idea to think about. Try other ports other than the standards. Not to mention the fact that using alternative ports also helps with security anyway.

---

