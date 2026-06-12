---
title: "Help Hosts file users"
date: 2010-05-16
forum: The Cafe
---

### Post by Guest2010 on 2010-05-16
I created an entry in brainstorm.ubuntu.com about wildcards in Hosts file.

[[IMG]http://brainstorm.ubuntu.com/idea/24842/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/24842/)

Please promote it :D

---

### Post by koenn on 2010-05-16
it's a bad idea, so I won't promote it. 

the hosts file is a mechanism for resolving names to addresses. 
Knowingly pitting wrong records in there may be a cute workaround to block access to certain web sites, but it's also misusing the mechanism. 
Asking that this (well established) mechanism be mùodified to better accomodate your workaround is a step too far, imo.

---

### Post by jetsam on 2010-05-16
Yeah, the slippery slope leads all the way to a dns server.  

Install a dns server.  

dnsmasq is great for a home lan.  Tomato firmware comes with it stock, or you can install it internally and wield a network magic wand.  Please search for more info, as this is the cafe.

---

### Post by Guest2010 on 2010-05-16
> **koenn said:**
> it's a bad idea, so I won't promote it. 

the hosts file is a mechanism for resolving names to addresses. 
Knowingly pitting wrong records in there may be a cute workaround to block access to certain web sites, but it's also misusing the mechanism. 
Asking that this (well established) mechanism be mùodified to better accomodate your workaround is a step too far, imo.

But it does a perfect job all you have to do is copy and paste a list ([http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)) and you can add your own sites. 

Nothing to install, setting up and to worry about.

---

### Post by jetsam on 2010-05-16
You're breaking into cars.  I'm offering you a parking garage.

---

### Post by Guest2010 on 2010-05-16
> **jetsam said:**
> You're breaking into cars.  I'm offering you a parking garage.

I don't need to break into my car since i have the keys ;-)

---

### Post by koenn on 2010-05-16
> **Guest2010 said:**
> But it does a perfect job all you have to do is copy and paste a list ([http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)) and you can add your own sites. 

Nothing to install, setting up and to worry about.

So you want to do system and network administration with nothing to install, setting up and worry about ? 
Hm, why doesn't that convince me that your idea is a good one ?

---

### Post by Guest2010 on 2010-05-16
> **koenn said:**
> So you want to do system and network administration with nothing to install, setting up and worry about ? 
Hm, why doesn't that convince me that your idea is a good one ?

Who said that I want to do system and network administration? I am a private user, who cares for his privacy and security. 
I am aware that there are many solutions to accomplish that, I tried most of them. I think the hosts file solution is one of the best and by improving that it would even get better.

---

### Post by jetsam on 2010-05-16
Everything you're looking for is [here]("http://www.youtube.com/watch?v=Y9fNRXUoveg").

---

### Post by Guest2010 on 2010-05-16
> **jetsam said:**
> Everything you're looking for is [here]("http://www.youtube.com/watch?v=Y9fNRXUoveg").

lol, rick roll'd :evil:

---

### Post by koenn on 2010-05-16
> **Guest2010 said:**
> Who said that I want to do system and network administration? I am a private user, who cares for his privacy and security. 
I am aware that there are many solutions to accomplish that, I tried most of them. I think the hosts file solution is one of the best and by improving that it would even get better.

if you're modifying a hosts file, your doing system administration with repercussions on network connectivity. If you're blocking sites, you're doing network administration. Small scale, maybe, but nonetheless. 
I have no problem with that, except for what I said in my first post in this thread.

---

### Post by Guest2010 on 2010-05-16
> **koenn said:**
> if you're modifying a hosts file, your doing system administration with repercussions on network connectivity. If you're blocking sites, you're doing network administration. Small scale, maybe, but nonetheless. 
I have no problem with that, except for what I said in my first post in this thread.

very well then. 

it wouldn't hurt you when they make the hosts file more intelligent.

---

### Post by jetsam on 2010-05-16
What you aren't getting is that internetworking involves more than just you.  You are absolutely free to change your hosts file, and also your resolv.conf file.  

What you can't do succesfully is argue from a position of ignorance.  

When people use words like "dns" and "network administration," and you respond with "no worries," you have lost before you have begun.  All we are asking you to do is educate yourself before you try to fix a system you do not understand.

---

### Post by Sam on 2010-05-17
[http://daniel.hahler.de/easy-dns-wildcard-setup-for-local-domains-using-dnsmasq](http://daniel.hahler.de/easy-dns-wildcard-setup-for-local-domains-using-dnsmasq)

---

### Post by jetsam on 2010-05-17
Lol.  SO easy it's almost cruel.

---

