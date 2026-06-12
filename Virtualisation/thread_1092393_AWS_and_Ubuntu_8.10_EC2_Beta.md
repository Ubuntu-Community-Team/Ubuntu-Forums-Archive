---
title: "AWS and Ubuntu 8.10 EC2 Beta"
date: 2009-03-10
forum: Virtualisation
---

### Post by jadoti on 2009-03-10
I have a question regarding AWS, Ubuntu 8.10 EC2 Beta, and well, actually it's more just about cloud computing in general.  If any of you have experience hosting on cloud servers, I'd greatly appreciate your input.

I have a service that I'm evaluating utilizing cloud computing for.  It could be setup on a normal LAMP host but I like the scalability of cloud computing, and hence want to go there.

The service is just a set of web services and some web pages, driven by MySQL.  

First question:  How do you handle MySQL when multiple instances can be created?  Do you run a separate server instance in the cloud just to be the database server, so that when the web servers create new instances and scale they all talk to the one mysql server?  Or do you setup your LAMP instance all in one server, and have it scale by adding more resources to the available instance?  I keep reading that they scale by firing up new instances of your server, but that would hose a system dependent on MySQL unless MySQL was off on another server instance, or am I missing something?

Second question: How do IP's work in this setup?  If I have a domain name, I can see it pointing to one instance.  But what happens when the load gets high and they fire up another instance?  What handles the load balancing for this? AWS?  And is it all taken care of automatically? (i.e., new instance fires up, and new requests are automatically directed across all instances)

Thanks for any help, and any pointers to other resources that might help me get my head around how this works...

Mike

EDIT: And apologies if this should have been posted in another forum, this seemed most appropriate.

---

