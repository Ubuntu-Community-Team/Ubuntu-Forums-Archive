---
title: "How can I install a circumventor?"
date: 2009-04-15
forum: Server Platforms
---

### Post by c3lica on 2009-04-15
I am running Ubuntu Server 8.10 and would like to know how to install a circumventor. I already have apache2 up and running. 

How should I go about doing this?

---

### Post by ikonia on 2009-04-15
what's a circumventor ?

---

### Post by spynappels on 2009-04-15
It is a type of proxy server which allows you to circumvent certain content filters at work or in school etc.

---

### Post by ikonia on 2009-04-15
oh, maybe not best to give out that advice then, as if someone is blocking something - bypassing it will be against their policy

---

### Post by HighCommander540 on 2009-04-15
> **ikonia said:**
> oh, maybe not best to give out that advice then, as if someone is blocking something - bypassing it will be against their policy

Lol, yeah but that has nothing to do with this guy's server. In reality is actually not even that complicated or hard to do. Its also not called a circumventor it is called a proxy and their intended use is not to go where ever you want. Its actually for security and encryption.

If you would like to use on in the fashion you are talking about, we hold no responsibility for what happens in the wake.

Here are a few that you could use depending upon what you have installed on your server:

[http://www.proxybuilder.com/]("http://www.proxybuilder.com/")

^That is actually both HTTP types of a proxy in one. It also makes the code for you.^

---

### Post by BkkBonanza on 2009-04-15
It sounds like the OP wants to run his apache behind some filtered or firewalled service. Hard to tell as very little info provided. We need more info about what's wanted to provide suitable directions.

---

### Post by c3lica on 2009-04-15
The goal is to be able to check gmail at work. I can check it on my phone but it takes a lot longer so this will save me time and in turn save the company I work for money :p.

---

### Post by BkkBonanza on 2009-04-15
Do you know what ports are open at your work place? Can you get out to web sites? http (80), https (443) or any other ports? Do you have access to a server outside your work that can act as a relay point?

I think gmail uses port 995 for secure email if I recall.

---

### Post by c3lica on 2009-04-15
> **HighCommander540 said:**
> Lol, yeah but that has nothing to do with this guy's server. In reality is actually not even that complicated or hard to do. Its also not called a circumventor it is called a proxy and their intended use is not to go where ever you want. Its actually for security and encryption.

If you would like to use on in the fashion you are talking about, we hold no responsibility for what happens in the wake.

Here are a few that you could use depending upon what you have installed on your server:

[http://www.proxybuilder.com/]("http://www.proxybuilder.com/")

^That is actually both HTTP types of a proxy in one. It also makes the code for you.^


This worked great. Thanks. I had one installed on windows a long time ago and it was a lot more work. This is nice and easy and can be modified real easy.

---

### Post by BkkBonanza on 2009-04-15
I don't understand why you would use ProxyBuilder. It looks to me like you use that to make a script to run on a web site that behaves like a proxy. Is that right? If so why go to all that trouble when ssh has a built in prefectly functional secure proxy and doesn't require anything extra - and certainly not a whole web server just waiting to do proxying. I'm not being facetious - I just want to know when it would make sense to do all that extra setup.

---

### Post by Thirtysixway on 2009-04-16
One way you could do it is ssh into your server from work, and then tunnel your http traffic over that.  It would bypass an existing proxy.

---

### Post by c3lica on 2009-04-17
I planned on allowing others to use it who have limited computer knowledge. being able to go to a bookmark and from there just type a website like google.com or something is simple. Just about anyone can do it. If I looked into using ssh only I would be able to use it or I would have to teach the others how to use it. 

I am just trying to keep it as simple as possible for the user of it.

---

### Post by dwasifar on 2009-04-22
> **BkkBonaza said:**
> I don't understand why you would use ProxyBuilder. It looks to me like you use that to make a script to run on a web site that behaves like a proxy. Is that right? If so why go to all that trouble when ssh has a built in prefectly functional secure proxy and doesn't require anything extra - and certainly not a whole web server just waiting to do proxying. I'm not being facetious - I just want to know when it would make sense to do all that extra setup.

This kind of thing is intended to be a user-friendly no-geekery proxy that can be used to get around content filtering or blocking.  Say you're at work and you want to check facebook, and your employer has it blocked; you connect to your own webserver instead, which (presumably) is not blocked, and proxy out to facebook, avoiding the block.  

One of the better-known implementations of this is the Circumventor project at peacefire.org, hence the title of this thread.  Over there they have a downloadable turnkey installer that sets up a Windows system to be this kind of proxy using Apache and OpenSSL, if memory serves.  Personally I don't like peacefire's approach; by default, if you install their setup, your system becomes part of a network of such open proxies, and though it's possible to change it, I don't think most people do.  I wouldn't want to run a completely open proxy this way; you never know who'd use your connection to do things like download kiddie porn or instructions for constructing IEDs.

---

