---
title: "Add .co.uk domain to server"
date: 2010-04-10
forum: Server Platforms
---

### Post by elliotbeken on 2010-04-10
Hi all,

i have got a ubuntu server running apache mysql etc running well

all i now want to do is add a .co.uk name and not have to use ****.dyndns.org

i can add virtual hosts as i have 5 *****.dyndns.org addresses added but when i try to add my .co.uk name to it i fail


do i need to point my address to my home server ???
(my isp uses dynamic ip addresses)

thanks all

---

### Post by dudumomo on 2010-04-10
Basically, you need to modify all your virtualhosts and to redirect your domain name to your IP.
Also, you might need to add your domain name to your /etc/hosts file.

---

### Post by elliotbeken on 2010-04-10
so is it possable to have my .co.uk and my elliotbeken.dyndns.org running at the same time ??

and i am stuck on how it will work if i point my domain to my home server as the IP address changes 

thanks

---

### Post by Skidbladnir on 2010-04-10
It's impossible to do that; But normally, most ISPs give IPs for about 6 months.  Mine does.

---

### Post by dudumomo on 2010-04-11
> **elliotbeken said:**
> so is it possable to have my .co.uk and my elliotbeken.dyndns.org running at the same time ??
Yes, configure your virtualhost for your .co.uk, by example, and simply create a web redirection of your elliotbeken.dyndns.org to your .co.uk

> **elliotbeken said:**
> and i am stuck on how it will work if i point my domain to my home server as the IP address changes 
This is the tricky part, every day your IP change, so every day, you have to update your DNS records.
2 solutions:
- Best one, have a static IP. It is often an option to get with your ISP.
- Alternative, let a software automatically update your IP to your registrar.

---

### Post by Vegan on 2010-04-11
I run my web server like an ISP with user directories, in the Apache files I have it configured to automatically recognize a new user. Now for domains, it agnostic, I dimply have a config file with the domains for each user account in a block.

The idea is that I can manage domains easily from a program.

I posted my config files in my forum, if you need the examples that I implement on a live server.

---

### Post by uberlinuxnerd on 2010-04-14
In the virtual host set the dyndns.org domain name and then CNAME you co.uk domain to your dyndns.org domains.

This is exactly how 'Cloud' providers do it. E.g. Amazon's EC2 with elastic IP.

---

