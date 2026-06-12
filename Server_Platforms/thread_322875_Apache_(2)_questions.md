---
title: "Apache (2) questions"
date: 2006-12-21
forum: Server Platforms
---

### Post by rogier.de.groot on 2006-12-21
Alright, I've got a few questions for y'all...

1) At work I'm behind a firewall that doesn't let through anything but HTTP. Very annoying if you want to modify something on your server - like when trying to figure out why http/webdav subversion won't work. Is there some sort of server-side thing I could include in my website, something like PuTTY, but server side. I've already tried applets, but they won't work, since they still connect from your client machine.
2) Is there some way to do file sharing via http/apache2 ? Something samba-over-http-ish? Could I share the same directory via it & regular samba without the two biting each other?
3) I've got mod-python installed but I'm wondering which of the huge list of python libraries are useful - there's a whole bunch of them - all I want is basically the same as the php extensions I have; mysql+sqlite+sqlite3 support, some graphics manipulation (GD), some crypto (mhash, mcrypt), random handy stuff (e.g. client session, tcp/ip sockets, smtp, etc). Basically anything handy for standard boring simple webapps.

EDIT: btw, I'm running Ubuntu Edgy (6.10) server.

Any and all help appreciated, TIA,
Rogier

---

### Post by kidders on 2006-12-21
Hi there,

I don't know a huge amount about Python, but I might be able to help with the other questions ...

The problem with running multiple services over HTTP is that only one server can be listening on a given port at any one time. Assuming you're serving websites from your Ubuntu box, that'll be Apache, so your only option for filesharing is probably WebDAV. If you're interested in tweaking your server remotely, Webmin is probably your best bet.

Depending on how important security is to you, running WebDAV and Webmin on your server *might* be unacceptable risks. You could try port scanning yourself to make certain that nothing but port 80 is open. If there is even one port available that you're not already using, I would run an SSH server on it, and tunnel remote admin and filesharing services over it. Much safer :-)

---

### Post by rogier.de.groot on 2006-12-21
Thanks for the reply. I had already considered WebDAV but I am largely unfamiliar with it (I know the http+svn solution uses it, but nothing beyond that). One of the reasons I wanted something PuTTY-ish over http is that actually have multiple servers I might want to manage with ssh, not all of them in my own LAN. So I just wanted to be able to make one connection to my home server, and ssh to other ones from there.
To clarify, my current work environment blocks all outbound traffic except that going to port 80 (http) and 443 (https). It *might* allow some other protocols for specific hosts, but mine isn't one of them.
I want my server to do the following:
1) run a few simple webapps (my own php/python creations).
2) run subversion over http for version control of all my prive & work stuff (already running).
3) mysql + management (phpmyadmin) or maybe pymyadmin if such a thing exists (phpmyadmin already working).
4) filesharing (to read & write to /var/www so I can upload new webstuff from anywhere).
5) manage mine & other servers with ssh without the damn firewall @work getting in my way.

any suggestions on any of the above are welcome.

---

### Post by kidders on 2006-12-21
Hmm... so you're looking for a way to access your home PC from work? In this country, most companies consider that theft ... you should probably check out your local situation before trying that.

In the absence of a third party (ie a HTTP proxy that would let you tunnel the SSH protocol through it), the only way for you to get SSH access to your home PC would be to run the server on port 80 or 443. This would obviously prevent you from running a web server on those ports. As you mentioned, once you're into your own computer, you can do what you like though :-)

Incidentally, if you poke around, you might find port 53 could be open also ... that wouldn't be unexpected.

---

### Post by speedman on 2006-12-21
> **rogier.de.groot said:**
> 4) filesharing (to read & write to /var/www so I can upload new webstuff from anywhere).

There are lots of web based apps for sharing files, but this is one of my favourites:

[http://pfn.sourceforge.net/](http://pfn.sourceforge.net/)

> 5) manage mine & other servers with ssh without the damn firewall @work getting in my way.

As per the other suggestions you could bind ssh to another port.

For example, if you only bind apache2 to port 80 (only have Listen 80 in /etc/apache2/ports.conf) you could then edit /etc/ssh/sshd_config and change Port 22 to Port 443, which would allow you to ssh to the box like this:

ssh -p443 user@host

The downside would be losing https for apache, but you would accomplish your goals albeit it with less than desirable security.


SM

---

### Post by chrisfay on 2006-12-21
> Hmm... so you're looking for a way to access your home PC from work? In this country, most companies consider that theft

I'm curious about your logic regarding that statement. I've never encountered a company that not only denied me access to my system at home, but also considered it 'illegal'. 

....and theft?:-k

---

### Post by kidders on 2006-12-21
Yeah, most companies I've worked for object to use of network resources they own for purposes that are not business-related. Occasionally, we hear about cases where employees are prosecuted under theft legislation. I figured I should mention it, just in case you could get in any trouble.

In fact (without wanting to name names), the last company I worked for fired a colleague of mine for doing exactly what is described in this thread. He ran an SSH server at home on port 80, and tunelled a connection to it through their WWW proxy with puTTY. The company called it "installing personal software without approval", "circumventing network access restrictions" and "theft of company resources" ... and escorted him out of the building!

Of course, if the company you work for is a little more ... well ... reasonable, things should work nicely for you. The only suggestion I have is to try to avoid proxying SSH, if possible. Web proxies tend not to like to keep connections alive for extended periods, so you might find your SSH terminal dies every so often. That's why I suggested checking out port 53, which is ordinarily used for DNS.

---

### Post by chrisfay on 2006-12-21
> Yeah, most companies I've worked for object to use of network resources they own for purposes that are not business-related. 

Interesting....I suppose I've been fortunate and somehow escaped such limitations. I can totally understand how bypassing a firewalled company network to gain access to your system could cause issues and hence also see the relevance to this thread. 

Thanks...

---

