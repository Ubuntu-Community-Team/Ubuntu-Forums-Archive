---
title: "Splitting headache"
date: 2008-11-13
forum: Server Platforms
---

### Post by gravitus on 2008-11-13
I recently installed the server edition. I simply want to serve an html website, have openssh, webadmin, run torrentflux, and use some samba shares. I have all of these things running right now. I used domain name from no-ip.org and got everything working to a tee. I did some port forwarding on my linksys router with dd-wrt and only forwarded 80 and 22 to my server for connection. I have the router firewall turned on. I did port scanning and it only showed 80 and 22 open. I have the server(ibex), my desktop(windows), my wifes laptop(windows), and another laptop running ubuntu desktop version(hardy). Everything hooks to my linksys router(dd-wrt) with dhcp enabled. The internal ip's are 192.168.1.1 for the router then 192.168.1.100/110 for the server and workstations. 

I started reading a thread here about security and downloaded tiger and ran the html report. After running it, the report says I have basically failed everything in terms of security, there are unknown files on the machine, all of the defaults that I am using are a bad thing and my machine will basically be a bot before I finish writing this post. It also said my md5 checksums did not match. I installed denyhosts for some simple security and ended up locking myself out of ssh while the auth.log shows ip's in china brute forcing my machine for ports(37000+) that are not even open on my router presently.

I like linux and really want to go forward with it but how damn hard does setting this thing up have to be. Anyone have any ideas on how I can lock this thing down while making sure that I can access the services that I want? I think I am fairly competent but this has me worried. I will provide logs if neccesary but at this point, I think I want to re-install the whole thing and start fresh. Appreciate any help that is given concerning this.

---

### Post by iponeverything on 2008-11-13
> started reading a thread here about security and downloaded tiger and ran the html report. After running it, the report says I have basically failed everything in terms of security, there are unknown files on the machine, all of the defaults that I am using are a bad thing and my machine will basically be a bot before I finish writing this post. It also said my md5 checksums did not match. I installed denyhosts for some simple security and ended up locking myself out of ssh while the auth.log shows ip's in china brute forcing my machine for ports(37000+) that are not even open on my router presently.

check your md5's with:
```
debsums -c

```
what's changed?

the port scan at 37000+ and your only listening on 80 and 22?  Bots are always scanning that range looking for zombies-- it is really nothing nothing worry about. 

It is quite easy to lock it down. though being behind nat -- don't know what the point would be.

---

### Post by Philio on 2008-11-13
Why do you have port 22 open? You should probably close that one off as I doubt you need it and it's going to invite people to try and hack in. You only need port 80 open for non-SSL web pages. If you want to serve HTTPS then open 443 as well.

There is no way someone could be connecting on other ports unless you have your router setup wrong (with IP in DMZ or something) or someone has got into your server over the open SSH port.

Not sure what iponeverything is on about, there is no mention of OSX in OP!!!

---

### Post by iponeverything on 2008-11-13
your right. reading too many posts at once. don't know where I got the OSx thing from..

BTW -- port 22 is ssh.

---

### Post by oneloveamaru on 2008-11-13
Tiger is a security auditing program that is in the repositories of Debian and Ubuntu.

Send me the exact report and I'll go through it with you. I have tiger on a couple of my really important production servers.

---

### Post by gravitus on 2008-11-13
Thanks for the response folks. I will send you the report when I get back to the house later tonight oneloveamaru. I was unsure of everything so I simply unplugged the ethernet cable from my router and disabled the port forwarding for now then went to work. 
 Could I send you my auth.log as well? That is what initially got me worried when I saw the brute force attempts and some other info that wasn't adding up.

I know I have a ton of learning to do with this server and guess I am looking for the piece of mind that I am not doing something stupid as I try and learn the ins and outs. I want to lock it down until I am comfortable with opening things up. I just don't know whats open right now...

---

### Post by hictio on 2008-11-13
Is this Tiger thing like a Root Kit Hunter aimed specifically for Ubuntu Server?

---

### Post by oneloveamaru on 2008-11-13
> **hictio said:**
> Is this Tiger thing like a Root Kit Hunter aimed specifically for Ubuntu Server?


It is a security audit program ONLY. If you have a Rootkit installed on your server, your security has already been compromised.

There are lots of programs to run and detect root kits. Google can give you a ton.

---

### Post by hictio on 2008-11-13
> **oneloveamaru said:**
> It is a security audit program ONLY. If you have a Rootkit installed on your server, your security has already been compromised.

There are lots of programs to run and detect root kits. Google can give you a ton.

I guess I wasn't clear enough, no root kit, thank you very much :)
I wanted to know if Tiger is a port (a version, a customized release) of [Root Kit Hunter](http://www.rootkit.nl/projects/rootkit_hunter.html) for Ubuntu Servers.

---

### Post by Philio on 2008-11-13
> **hictio said:**
> I guess I wasn't clear enough, no root kit, thank you very much :)
I wanted to know if Tiger is a port (a version, a customized release) of [Root Kit Hunter](http://www.rootkit.nl/projects/rootkit_hunter.html) for Ubuntu Servers.

[http://www.nongnu.org/tiger/](http://www.nongnu.org/tiger/)

---

### Post by cariboo on 2008-11-13
For more info on security scanners go here:

[http://www.linux4biz.net/articles/articlescanner.htm](http://www.linux4biz.net/articles/articlescanner.htm)

Jim

---

### Post by oneloveamaru on 2008-11-13
They are seperate programs but I believe they can work hand in hand. Tiger has lots and lots of options you can configure. Like what to ignore...

---

