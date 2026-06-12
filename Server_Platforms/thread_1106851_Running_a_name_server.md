---
title: "Running a name server"
date: 2009-03-26
forum: Server Platforms
---

### Post by blazemore on 2009-03-26
I'd like to run a low-load web server from my university dorm room.
Everything needs to run from one Ubuntu server (Possibly with different virtual machines to isolate each "server")

I've found lots of information on HTTP, mail anf file servers, but the main problem is a nameserver.

Basically I need to know how to run a server where I put my own nameservers into GoDaddy (or another registrar).

---

### Post by windependence on 2009-03-26
You don't need a server for that. You can go into your domain control panel and just set up your A records, cnames, and MX records and you're done. I guess some time ago someone decided that you had to run your own DNS to host web sites and now everyone here thinks you do. You don't. In fact, it's more trouble than it's worth.

-Tim

---

### Post by BkkBonanza on 2009-03-26
I don't where that idea ever started from either. It's a lot easier and more reliable to have your names served off your registrar or a third party. 

If you want to do it to learn how then good enough but it's not needed or even the best option. I know that my registrar provides a really good control panel for free and I don't recall it ever being down.

Now, for learning there are many options. The classic heavyweight is Bind. But running that on a vps is a terrible waste of precious resources. I have installed and used tinydns (aka djbdns) several times and it is so much smaller and lighter. There are other ones out there too. If you want to put in tinydns then check out the step by step tutorial at djbdnsrocks.org. Same guy who did qmailrocks. 

I wrote some patches for tinydns to support geo routing based on country of user. That's the only reason I use my own nameserver now.

---

### Post by windependence on 2009-03-26
I only have ONE set up for all my commercial clients. This one I had to set up because local mail was not being routed properly so I had to do a split DNS set up. Other than that, all my clients are set up with externel or third party DNS. I have enough trouble keeping redundant power and servers, let alone full blown DNS. ;)

-Tim

---

### Post by daboroe on 2009-03-26
> **blazemore said:**
> I'd like to run a low-load web server from my university dorm room.
Everything needs to run from one Ubuntu server (Possibly with different virtual machines to isolate each "server")

I've found lots of information on HTTP, mail anf file servers, but the main problem is a nameserver.

Basically I need to know how to run a server where I put my own nameservers into GoDaddy (or another registrar).

blazemore, please be very very careful. A lot of universities and college's such as mine forbid doing this. If they detect this you will be violating their AUP and you will suffer at the wrath of them. I have not done it myself but I have been told of stories that have happened here. SO, just please be careful. I would hate for you to have all this set up and you get busted for it.

Why don't you just have it at your house? That is what I am planning on doing actually.

Thanks

Mike

---

### Post by blazemore on 2009-03-26
So hang on, I'm a bit new to all this.
If I register a domain name, [www.example.com](www.example.com)
And my HTTP server has a web-facing ip 1.2.3.4
How do I set it up so people type in [www.example.com](www.example.com) go to the server?

---

### Post by BkkBonanza on 2009-03-26
Go to your name registrar's control panel and add a dns record. Only takes a few seconds and then minutes-hours to udpate worldwide.

You need an A record that points example.com to 1.2.3.4
And add a CNAME record for www to point to root A record above.

There are lots of variants of course but this is most basic. You can add other subdomains too eg. mail.example.com

Once you get into their control panel it should be pretty self evident.
Their DNS servers will take care of you fine (unless you have a crumby registrar).
If you wanted to run your own nameservers then you would still go to their control panel but you would make the settings that tell them where your nameservers are instead. And then they would update the worldwide records to say that now you handle your own DNS (not them anymore).

Most domain regsitrars today also have support for dynamic dns. If your server is on a connection that uses dynamic ips then this option allows the name records to get updated automatically whenever the ip changes too. Handy for home servers.

If you are running a server on a dynamic ip then it's practically impossible to run your own nameservers - how can users query the names when the nameserver ip keeps changing too.

---

### Post by blazemore on 2009-03-27
Ok Thanks for all your help, especially Bkk.
Is there a guide on the internet to help me set up a multi-user web server (/home/usr/public_html I believe?)

---

### Post by BkkBonanza on 2009-03-27
I don't know of a specific tutorial but the apache docs are always a good place to start... if that's unclear then at least it may give you keywords for google to locate a tutorial.

[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

---

