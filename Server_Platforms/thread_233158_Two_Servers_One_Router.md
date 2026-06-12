---
title: "Two Servers One Router"
date: 2006-08-09
forum: Server Platforms
---

### Post by stormblue on 2006-08-09
I was wondering the best way to go about putting two servers behind the same router.  I'd like to use two domain names.  The easiest solution I can think of to is set up one server on non-standard ports and leave the other on standard ports.  This would work okay, but I was wondering if there isn't a better solution.  I did some google searches and found a forum post that basically said it was possible with NAT, but didn't go beyond that.

Thanks!

---

### Post by chrisfay on 2006-08-09
If you're just talking about running two websites, why wouldn't you use virtual hosts? Just put both sites in apache2's config files "sites-available" and "sites-enabled/000-default" with each domain's respective root directories in the entries. 

If you're thinking of two FTP servers or something that doesn't support virtual division, then yes you would need to have different ports.

---

### Post by stormblue on 2006-08-09
Thanks for the reply.  One is a network server for my development machine.  This machine will hold mostly websites that I am developing at the time.

The other machine will be a test machine for me to play around with.  I would have no-ip.com dynamic DNS running on them.  


Any other ideas?

---

### Post by chrisfay on 2006-08-09
Then you can do it either way. If you want to keep your development machine seperate, then route some other random port like 8080 to your test box. Change apache2 to listen on port 8080 in ports.conf (again in your test box), then portforward 8080 in your router to the static ip of your test box. 

You would then obviously have to type your WAN IP + 8080 to reach it. 111.111.111.111:8080. Or, if you are using noip like you said, I think they support adding the port to the ip on their end so you wouldn't have to add it yourself every time you type your domain. 

If they don't, use [http://zoneedit.com](http://zoneedit.com). I know they support adding ports to the IP as that's what I used before setting up my own DNS.

---

### Post by stormblue on 2006-08-09
But wouldn't that be bad to add the port on the end, becuase then I can't define FTP, SSH and such ports, correct?  I have these servers at home while I'm away at college.

---

### Post by chrisfay on 2006-08-09
No, if you add 8080 to your noip or zoneedit domain, it would only add 8080 to that domain name request(it doesn't actually force it on your IP). You could still type your WAN IP:22 and bypass your myip setup to get your ssh server on your develpment machine; or whatever port you want. It would just make it easier to reach your test webserver on port 8080 when typing in your domain name.

Example
[www.domain.com](www.domain.com) = 111.111.111.111
[www.domain.com:8080](www.domain.com:8080) ------> web server on test box
111.111.111.111:22  ------> ssh on development machine
111.111.111.111:21  ------> ftp on devolopment machine

It really depends on which servers you run on which box. Then, just portforward the necessary ports to their respective boxes and use your WAN IP instead of either domain to reach your other servers. 

I may be misunderstanding your question here, but it sounds like you want to run a standard web server with your new domain on a test box, while still being able to reach a seperate box for all your existing servers and the other domain.

---

### Post by stormblue on 2006-08-09
Yeah, that's basically it.

Thanks for the clarification.

---

### Post by buchannon on 2008-02-11
Hm... I am curious about the same issue. I understand setting one site to an obscure port and separating them that way, but what if I want to access SSH (port 22) on both machines while I'm away? Would I have to modify SSH (and any other daemon I want to use) to listen on another port than the standard one on one of the computers? 

Let's say I have: 
WAN IP = x.x.x.x
Box1
Box2
[www.Domain1.com](www.Domain1.com)

[www.Domain1.com](www.Domain1.com) ---> x.x.x.x ---> Box1
[www.Domain1.com:8080](www.Domain1.com:8080) --> Box2

I could ssh into Box1 by x.x.x.x:22, but how would I get into Box2 using port 22?

---

### Post by Dr Small on 2008-02-11
> **buchannon said:**
> Hm... I am curious about the same issue. I understand setting one site to an obscure port and separating them that way, but what if I want to access SSH (port 22) on both machines while I'm away? Would I have to modify SSH (and any other daemon I want to use) to listen on another port than the standard one on one of the computers? 

Let's say I have: 
WAN IP = x.x.x.x
Box1
Box2
[www.Domain1.com](www.Domain1.com)

[www.Domain1.com](www.Domain1.com) ---> x.x.x.x ---> Box1
[www.Domain1.com:8080](www.Domain1.com:8080) --> Box2

I could ssh into Box1 by x.x.x.x:22, but how would I get into Box2 using port 22?
You can't.
You would have to edit the sshd_config to listen on a different port.

---

