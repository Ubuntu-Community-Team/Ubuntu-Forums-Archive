---
title: "Basic Squid Config File"
date: 2013-10-04
forum: Server Platforms
---

### Post by andrew_king2 on 2013-10-04
What is the best practice for the squid config file. Do you run the sample config file with 3000+ lines of documentation or do you create a much tighter config with just the lines that you require?

I've been running with the full config + documentation and I am tried to scrolling and searching to find the lines I need to edit. The full config loads fast and having the documentation is great but seems unnecessary for day to day operation. Opinions??

-Andrew

---

### Post by SeijiSensei on 2013-10-04
To strip the comments use this command:

```
sudo grep -v '^#' squid.conf | grep -v '^$' > squid-stripped.conf
```

That removes any line beginning with a hash mark, then deletes all empty lines and stores the result in squid-stripped.conf.  I find it infinitely easier to manage a file with the just the directives.  

The tilde represents the beginning of the line, and the dollar sign the end.  The regular expression '^$' thus matches any empty lines.

One other useful tip if you use lots of ACLs is to put them in separate files.  Here's an example:

```

acl banned_domains dst "/etc/squid/ACL/banned_domains.conf"
http_access deny banned_domains

```

The banned_domains.conf file has a list of names like "facebook.com".  I created a directory "ACL" to keep all those files in one place.

---

### Post by Korabza on 2013-10-06
Hello there,
I have configured transparent squid on ubuntu 12.04 enterprise server and it works well when I manually configure proxy on my web browsers. But it users can browse internet without squid configration. My question is: -
[LIST=1]
[*]How can I configure squid so that clients cannot use Internet with out squid configuration 
[*]How can I configure squid so that browsers can automatcally make use of Internet without manual confuguration of squid on each and every browser. 
[/LIST]
I am using cisco 2901 router as gateway to the Internet.

---

### Post by Lars Noodén on 2013-10-06
> **Korabza said:**
> Hello there,
I have configured transparent squid on ubuntu 12.04 enterprise server and it works well when I manually configure proxy on my web browsers. But it users can browse internet without squid configration. My question is: -
[LIST=1]
[*]How can I configure squid so that clients cannot use Internet with out squid configuration 
[*]How can I configure squid so that browsers can automatcally make use of Internet without manual confuguration of squid on each and every browser. 
[/LIST]
I am using cisco 2901 router as gateway to the Internet.

It's probably better to start a new thread since your question is new and not from the original poster. 

That said, you describe two mutually exclusive scenarios.  For the first one, you must have a router or gateway in between the clients and the Internet, using the packet filter and blocking all traffic except to Squid.  The second one, it used to be called a transparent proxy, but now it is called an intercepting proxy.  When you search for material, keep that difference in mind as old material might not be valid.  Again, you have to have a router or gateway in between the clients and the internet, but instead of blocking traffic, it intercepts everything destined for port 80 and routes it to Squid.  IIRC the [http_port](http://www.squid-cache.org/Doc/config/http_port/) needs to be changed and ACLs set accordingly.

As to how you get all that onto a Cisco 2901, that's another question.  There are some [configiration examples](http://wiki.squid-cache.org/ConfigExamples) at the Squid site for other Cisco models, maybe they work.  Actually, thinking about it, Squid does not have to be on the router or gateway itself.

---

