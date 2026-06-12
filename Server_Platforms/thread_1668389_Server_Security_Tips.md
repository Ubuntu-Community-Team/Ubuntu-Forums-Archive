---
title: "Server Security Tips"
date: 2011-01-16
forum: Server Platforms
---

### Post by ryanstubbs on 2011-01-16
Hey. I just thought I'd post this here because I figured that I'm more likely to get a decent useful answer here as opposed to anywhere else.

I've finally got my own server and I'm migrating from a CentOS one that I didn't manage myself. I've got Ubuntu 10.10 installed and I plan to install Apache, PHP, etc. on there later but I was wondering if anyone has any tips or software I can install to best secure it when I've finished? I consider myself to be quite knowledgable on the process of maintaining it but I'm a complete newbie when it comes to securing the thing.

Any help is greatly appreciated so thanks a lot in advance to anyone that can help.

---

### Post by spynappels on 2011-01-16
Hi Ryan,

Bodhi.zazen's stickies in the Security forum are a great place to start, they explain the main downfalls and the best way to avoid them.

The different packages have different ways to secure them best, but the default ways to secure a server is to not run any unecessary services and make sure your passwords are a mixture of lower and upper cases and include some numbers. Use key authentication for SSH and disable password logins for SSH. That is a good start.

---

### Post by spynappels on 2011-01-16
Double post.

---

### Post by koenn on 2011-01-16
First thing you have to learn about security, is that it's _never_ about "tips" or memorizing a list of software to install. 
A lot of Windows users think their computer is secure if it has up to date antivirus software. They're wrong. A lot of linux users think their system is secure because they run firefox wih no-script, and "it's behind a router anyway". That's just as silly. 

I repeat : it's not about software.
In that respect, the stickies in the security forum are misleading, because they focus quite hard on software ("I have snort and tripwire and apparmor, so my system is secure. And it sits behind a router, anyway")

Also, there's no such thing as "securing *a* server". What you have is 1 specific server in 1 very specific situation; that situation exposes the server to specific risks, and "security" is what you do to reduce those risks while still letting the server "serve". 

So what you want is to figure out what the risks are for your specific server, and come up with a plan to deal with them. Then you start looking for tools to deal with them, i.e. some of those "security" packages. Because you've thought about it, you'll also know which ones you need and how to configure them, instead of just installing them all with their default config. 
You may find that, in most cases, there's no 1 size fits all solution for your requirements, you'll need to take several measures that complement each other. Sometimes, you're requirements will contradict each other, and and you need compromises. That's where that saying comes from that security is like an onion : it has layers (and it stinks). 


So, what you need to think about is :
what services does this server need to serve up ?
to whom ? -> how do i tell the good guys from the bad ? 
how do I keep the good guys from doing bad things ? 

Once you succeed in getting a pretty clear, concrete picture about this, implementing a solution is usually easy, and you'll have an answer to your questions about "tips" ~> "how do i do this ?" and "software" ~> "what software do i need to accomplish this ?".

---

