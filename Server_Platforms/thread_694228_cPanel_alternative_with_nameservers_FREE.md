---
title: "cPanel alternative with nameservers? FREE?"
date: 2008-02-11
forum: Server Platforms
---

### Post by bscharff on 2008-02-11
Hiya,
I'm currently working to open my server to the public and I'm about to install Ubuntu onto my server computer.

I already have a domain, but without nameservers.
I **really** don't want to use a public forwarding one. (i.e. ZoneEdit)

I'm considering Webmin, but does it come with nameservers?

Like, so I can tell my domain registrar my nameservers I make and... You know... like free hosting without actually transferring your domain over to them.

If it matters, I registered my domain with NameCheap.

---

### Post by faulkes on 2008-02-11
If you wish to run your own nameservers, the pre-requisite for that is having a static IP address for your server.  The caveat being you will in almost all cases be unable to provide your own reverse DNS entries (PTR records), all other records AFAIK are fair game (A, CNAME, TXT, etc)

If you have a static IP address from a provider, the provider must be willing to provide you the reverse DNS (PTR record).  While not critical, if you intend to send/receive mail on this server from the internet, many sites will refuse to accept your mail unless a valid  matching PTR record exists.

I don't use webmin, AFAIK, it is an admin tool for various services, which would likely include BIND (DNS).

Faulkes

---

### Post by bscharff on 2008-02-13
so, does webmin have nameservers and/ or an equivalent?  could it function as a nameserver?  if not, what could?

---

### Post by faulkes on 2008-02-13
> **bscharff said:**
> so, does webmin have nameservers and/ or an equivalent?  could it function as a nameserver?  if not, what could?

Webmin itself is a front-end to services (like apache, postfix, bind).  A quick google search turns up that it can be used as a front end to BIND aka DNS server aka nameserver.

It cannot by itself function as a nameserver, you would need to install the bind package.

Faulkes

---

### Post by bscharff on 2008-02-14
So basically do this:
Install Ubuntu
Install Webmin
Install Webmin BIND "addin" (a link to it would be awesome!)
Upload website
Open for viewing?

Sorry, I'm (somewhat) new to this :P

I'm used to using XAMPP with a free DNS service but since I know that I can run my own nameservers I'd rather do that.

---

### Post by faulkes on 2008-02-14
> **bscharff said:**
> So basically do this:
Install Ubuntu
**Install BIND package <- this is new, if you didn't install bind during the ubuntu install**
Install Webmin
Install Webmin BIND "addin" (a link to it would be awesome!)
Upload website
Open for viewing?


You need only go to the webmin site page and you should be able to find the
addin for BIND.

Note, that after installing BIND, you still need to configure the zone files for it, that is an entirely different excersize although there is a wealth of documentation available for it.

> 
Sorry, I'm (somewhat) new to this :P


Don't be sorry for being new, we were all new at one point and I certainly asked my fair share of questions (and still do).

Faulkes

---

### Post by bscharff on 2008-02-15
So I should use Ubuntu Server Edition?
I just figured that it would auto-install apache and all that and then it would conflict with Webmin...

---

### Post by faulkes on 2008-02-15
> **bscharff said:**
> So I should use Ubuntu Server Edition?
I just figured that it would auto-install apache and all that and then it would conflict with Webmin...

The Server Edition will do what you want, switching to the desktop version wouldn't provide any additional benefit other than X, which wouldn't solve these problems.  In my post below I did make a mistake because you will be using Webmin to configure BIND which should make it easier for you than manually creating zone files.

The Server Edition is meant for exactly that purpose, to act as a server, to a certain extent, that adds some additional learning overhead.  The community is here to help you with questions as you move along.

Faulkes

---

### Post by bscharff on 2008-02-15
I'll be starting the setup process on my server in about 30 minutes.

Is there any tutorial that would completely walk me through the Webmin + Ubuntu Server Edition setup? (I'll look)

---

### Post by bscharff on 2008-02-16
OK, sadly, I couldn't find any tutorial.

I installed it correctly on Kubuntu Desktop Edition (My Ubuntu Server Edition CD crapped out on me :( ) but it didn't install any servers (apache, etc.). I told the web administration panel to download apache but it reported some weird error (I can't remember it). After that, I told the Adept Update Manager to install it's 238 updates. While installing those updates, it crashed and wouldn't boot correctly (Kstartupmanager had an error in it's config file). I looked on aptitude (using sudo of course) in recovery mode to see if I could re-download it, but it found no such package. Luckily, I had a Ubuntu Desktop Edition CD in my desk, so I popped it in and installed it. I let it download updates (526 MB worth) and restarted it. I installed the kubuntu-desktop package because I love KDE so much :).

How fun, right?
Right now, it's downloading update 155/1132. (Because the CD was Ubuntu 6.9 or something like that...)

I've decided to use it as a desktop computer until I can get it working correctly.

---

