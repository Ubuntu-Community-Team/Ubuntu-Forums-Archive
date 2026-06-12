---
title: "Which firewall shoud I use ?"
date: 2009-04-08
forum: Server Platforms
---

### Post by forcevision on 2009-04-08
Hello !

I have just started up my web,ftp and mailserver with ubuntu 8.04 as os. This server is standing behinde a router with firewall. Shall I install a software firewall on my server to or is it enough with the firewall on my router ?

If I shoud install software firewall on my server which one shall I install ?

Thanx!!

/Force

---

### Post by iponeverything on 2009-04-08
Since its behind a router with a firewall there is really no need to have firewall rules on server itself. 

The linux firewalling is done via a kernel packet filtering mechanism  called iptables. There are a number of front-ends available for iptables, but in my opinion they make the machine less secure by over complicating the rules. Building the rules rules by hand is a good way to know you actually understand what your filtering and why.

---

### Post by anderswestrup on 2009-04-08
For servers without a need for complicated firewall rules i use "ufw" which is included in the default ubuntu install (stands for uncomplicated firewall i think)

When I need more complex stuff I use shorewall.

One good thing with ufw is that it supports ipv4 and ipv6 without having to duplicate rules.

---

### Post by forcevision on 2009-04-08
Okey so I dont need any firewall then. :)

---

### Post by wkulecz on 2009-04-08
> **forcevision said:**
> Okey so I dont need any firewall then. :)

As long as remote admin (from outside the internal subnet) is disabled on your router, and your router is not one of the ones allegedly cracked, you should be fine.

If you are a belt and suspenders kind of guy, no real harm in doing both unless you are a very high volume server.

--wally

---

### Post by BkkBonanza on 2009-04-08
Use netstat -lnptu to view what ports are open and listening. Any services listening on ports you don't *require* should be disabled on servers.

Also use Shields Up or similar ( [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) ) to scan your router for anything open. After that whether you want a second firewall depends on how likely you think the first one could be compromised. If you have hands on control or depend on someone you don't know to secure it. You aren't severely at risk with Linux because in general ports are all closed unless needed.

Reading up a bit more on server hardening and security in general is a good thing to help understand the most likely vulnerabilities.

---

### Post by hictio on 2009-04-08
No matter what firewall might be between the internet (or whatever) and my servers, I always use an internal firewall, it helps a bit to relax you know.
On Linux servers, that firewall is iptables, which, on Ubuntu, you can control thru the "ufw" program.

[Howto: Use, setup, and Take advantage of the New Ubuntu Uncomplicated Firewall UFW](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)
[Setting up firewall in Ubuntu](http://imyousuf-tech.blogs.smartitengineering.com/2008/05/setting-up-firewall-in-ubuntu.html)
[ufw disable ping / icmp](http://ubuntuforums.org/archive/index.php/t-773485.html)

---

### Post by forcevision on 2009-04-08
How do I see if can remote admin on my router from the outside ?

---

### Post by smeerbartje on 2009-04-08
> **forcevision said:**
> How do I see if can remote admin on my router from the outside ?

If port 22 (default) is forwarded from your router (external) address to your server's internal address, then you can remotely log-on.

---

### Post by Sylslay on 2009-04-08
Yours choice: 
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by forcevision on 2009-04-09
But then I use ssh the port 22 must be open on the router to my server or ?

---

### Post by hictio on 2009-04-09
> **forcevision said:**
> But then I use ssh the port 22 must be open on the router to my server or ?

You can do that, or you can open, say port '2222' on the router, and make the router forward that to the port 22 of the IP address that the Linux box is using inside your LAN.
Really handy if your ISP blocks traffic on ports bellow 1024.

---

### Post by forcevision on 2009-04-10
Okej how do I do that in the router ?

---

### Post by bigbearomaha on 2009-04-10
there are several firewall apps that manipulate iptables.

firestarter is one known for ease of use.

Webmin has a default firewall admin tool that is nice.

firewall any and every single server in your network
not only for incoming traffic but to control what comes out of a server.

even if you think you are protected by a firewall from gateway, there are still local security concerns to consider, depending on the environment.  users who have access, etc..

it's all relative.


Big Bear

---

### Post by forcevision on 2009-04-13
Okej so firestarter shoud I activate then?

When I activate firestarter witch port do I need to open same as in the router ?

---

### Post by hyper_ch on 2009-04-13
in most cases you don't need a firewall. If you run a (public) server you want it to be accessible. So there's not a point about having a firewall.

---

### Post by hictio on 2009-04-13
> **hyper_ch said:**
> in most cases you don't need a firewall. If you run a (public) server you want it to be accessible. So there's not a point about having a firewall.


I don't agree with the above.
Imagine the situation where, for instance, you have a mail server, or a web server running on a Linux box; if those are public, you'll have to have those services available over the network, **but only to those services**, you can have SSH (more than likely you'll do) or Webmin on the same box, and made those services only available for specific IP addressees or networks.
One of the easiest and fastest ways of doing that, is using an internal firewall.

---

### Post by hyper_ch on 2009-04-13
> **hictio said:**
> I don't agree with the above.
Dito :)

If yo are to stricly on what you allow on a remote server you can block yourself out. Bind SSH server to only one IP and then you need to change it and forget to do so on the server - have fun.

The easiest way is (a) know what you have installed (b) what settings you have applied (c) use strong passwords

---

### Post by bigbearomaha on 2009-04-13
you use firewalls to control not only what comes into a server, but what comes out of a server as well.

if you have said 'public' server and someone accesses that in an improper manner, they can use that access to communicate to other machines that server has access too.

This is preventable with a simple local firewall.

if you are wanting to forward ssh to that server, for example, you would make ONLY port 22 accessible and then you will likely want to use a tool like fail2ban to prevent multiple login attempts.

any way you go, have fun, learn lots

---

### Post by hyper_ch on 2009-04-14
> **bigbearomaha said:**
> you use firewalls to control not only what comes into a server, but what comes out of a server as well.

if you have said 'public' server and someone accesses that in an improper manner, they can use that access to communicate to other machines that server has access too.

Can you provide an example?

---

### Post by forcevision on 2009-04-15
So if I whant to control what is going out of the server the best tool is a firewall ?

I run a webserver and a mail server and a ftp server on the same ip number. And I have heared what hackers love to use ubuntu servers to fishing and spread virus with. So Its sound Like a firewall is a good thing to have on the server. But I dont understand the difference between the routers firewall and the server software firewall ?

---

### Post by hictio on 2009-04-15
> **forcevision said:**
> So if I whant to control what is going out of the server the best tool is a firewall ?

I run a webserver and a mail server and a ftp server on the same ip number. And I have heared what hackers love to use ubuntu servers to fishing and spread virus with. So Its sound Like a firewall is a good thing to have on the server. But I dont understand the difference between the routers firewall and the server software firewall ?

If you want to control that **on** the same server, yes, it is the best bet.
If you want to control that for the whole LAN, then a router firewall/ gateway is the solution.

IMHO, you get the best of both worlds if you can somehow combine both solutions.

---

