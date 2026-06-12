---
title: "Dedicated Ubuntu Server - How do I make it a .com?"
date: 2010-10-26
forum: Server Platforms
---

### Post by Nate204 on 2010-10-26
A heads up, This isn't fully ubuntu related. I thought this would be a great place to ask though, due to the fact that I can't be the only one who's had this problem. Ubuntu is my server, but what do I do next?

Here is what I'm trying to do:

I'm hosting my own dedicated server with Ubuntu Server 10.10. I have it set up with a static local IP, and I've configured DynDNS to link up with my router and allow my server to go live to the internet. I have all the appropriate ports unlocked, with the exception of port 80.

This port is blocked by my ISP (Charter) and I can't use it. Due to this, I configured my router to listen on port 81, and direct it to my server.

So, In order to view it, you need to go to the IP XXX.xxx.XXX.xxx:81
Today, I registered ([www.online-self.com](www.online-self.com)) in hopes of getting around my current mask (provided by DynDNS.com (omegame.selfip.com).

So here is my dilemma,
When I go to the host of my domain name , I want to redirect my DNS to my server IP.

I can't seem to do it though? They want a strict IP address, no port extensions. 
How do I get around this so that my domain name and IP address link up?

I'm thinking I may be missing a step, or maybe I needed to register a domain name that simply redirects? I'm starting to get confused on what I should do next. Can I even do this?

Thanks for your support and suggestions,
 - Nate

---

### Post by SeijiSensei on 2010-10-26
> **Nate204 said:**
> How do I get around this so that my domain name and IP address link up?

I'm thinking I may be missing a step, or maybe I needed to register a domain name that simply redirects? I'm starting to get confused on what I should do next. Can I even do this?

Short answer, no.  DNS only maps between hostnames and addresses; there's no way to use it to redirect traffic to a non-standard port.

I assume port 80 is blocked because your ISP has a "no-servers" policy, right?  Your choices are to upgrade to a business-class connection with a fixed IP and no restrictions, lease a virtual server (see [www.linode.com](www.linode.com) for one source), or use a web-hosting service.  My preferred domain registrar, [www.directnic.com](www.directnic.com), offers a decent hosting package for $4/month.  There's free hosting out there as well.

---

### Post by sloggerkhan on 2010-10-26
I think it is possible to find a host/domain registrar that will let you redirect [notUrl://www.xyz.com](notUrl://www.xyz.com) to [notUrl://www.xyz.com:81](notUrl://www.xyz.com:81).

In fact, even with normal dyndns you should be able to set up such a redirect.
See: [http://www.dyndns.com/support/kb/webhops_redirections.html](http://www.dyndns.com/support/kb/webhops_redirections.html)

The 'no-server' isp policy shouldn't be taken too seriously IMO. Have you ever heard of anyone getting kicked off the Internet for connecting to a home VPN or using one of the many remote desktop services to access their computers remotely? Hell AM radio is clogged with ads for that scam 'connect to my pc .com" or whatever it's called. You can probably think of a few hundred more examples of similar situations. When ISPs clearly knowingly allow and abet violations of absurd terms of service it makes the contract rather uneforceable if you've got good legal.

---

### Post by Nate204 on 2010-10-26
Thank you both for your responses,

So, What I'm getting is a big no on what I'm trying to do?

My options are ether keep the DynDNS url I have, or find a web host for a monthly fee? 

Here's another question then, and again, It's unrelated to ubuntu.

If I find some sort of hosting package, will they provide me with an IP to link to my domain name? Will they require me to migrate my domain name over to them?

If you found yourself in my position, paying for a domain name that you can't use yet, what would you do?

p.s. The reason I did this, is because I'll be taking a server class next semester in college. Out of everything i'm learning right now, hosting and servers seems to be the most interesting. I started with Ubuntu for the first time a few months ago, and I can't get over how fun it is to use. oh, and it's FREE!

---

### Post by mainerror on 2010-10-26
Do you have access to your router?

---

### Post by Nate204 on 2010-10-26
Yes, It's sitting right next to me. I own the access to the Cp as well.

---

### Post by SeijiSensei on 2010-10-26
> **sloggerkhan said:**
> The 'no-server' isp policy shouldn't be taken too seriously IMO. Have you ever heard of anyone getting kicked off the Internet for connecting to a home VPN or using one of the many remote desktop services to access their computers remotely? 

From my limited time here, I'd say the moderators frown on suggesting methods to avoid complying with ISPs' terms-of-service.  The fact that the ISP is blocking inbound port 80 is a good indication that they intend to enforce their TOS against at least simple-minded efforts to run things like web servers.

> Hell AM radio is clogged with ads for that scam 'connect to my pc.com" or whatever it's called.

Obviously you have no clue about how gotomypc works.  The desktop PC behind the firewall makes an *outbound connection* to a server run by Citrix and uploads its screen, keyboard and pointer information.  The remote user connects to this server, and the remote desktop is drawn using this information.  Changes by the remote user are stored by the server application and downloaded by the PC client.  That's how it can work though enterprise firewalls.  Rest assured, no one is connecting to his or her PC directly using this (rather clever, I think) technology.

> p.s. The reason I did this, is because I'll be taking a server class next semester in college. Out of everything i'm learning right now, hosting and servers seems to be the most interesting. I started with Ubuntu for the first time a few months ago, and I can't get over how fun it is to use. oh, and it's FREE! 

Well you can learn a lot just by building sites and viewing them from within your local network.  Try writing some simple PHP scripts, then move on to creating content dynamically using a database.  You'd gain experience with setting up a DB server, creating databases, writing SQL queries, etc.  Try writing something like a simple inventory manager for your CDs and DVDs.

---

