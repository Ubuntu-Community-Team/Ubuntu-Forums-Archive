---
title: "Hosting your own Domain?"
date: 2010-07-29
forum: Server Platforms
---

### Post by ipng on 2010-07-29
Hello.

I was wondering if it was possible to host your own domain name, like [www.ipng.co?](www.ipng.co?)
I'm not into buying a domain, while I'm studying and is quite low on money to be honest. It would be great, if my old LAMP server could do the trick ^^ 
The website is for personal use, and is a hobby, more than a need.

Regards.

---

### Post by Bachstelze on 2010-07-29
If you want a domain, you have to register it.  It's really cheap though, just a couple bucks a year.

---

### Post by ctyc on 2010-07-29
To host a domain and its web site you need 3 things.

1) a registered domain name
2) a web server like apache to serve up the web pages
3) a dns entry to point your publicly accessable ip address for your server.

Good Luck

---

### Post by ipng on 2010-07-29
Where can I do that? Can you link a website? :)

Regards.

---

### Post by Bachstelze on 2010-07-29
> **ipng said:**
> Where can I do that? Can you link a website? :)

Do what?

---

### Post by ipng on 2010-07-29
Register a domain?

---

### Post by TheStroj on 2010-07-29
There is a gazillion sites for registering domains. Google it.

Tip: 'Buy domain name'

---

### Post by flatline on 2010-07-29
No offense mate, but if you don't understand the difference between registering a domain name and buying hosting, I'm not entirely sure you're up to pulling this off yourself...

You can register your domain name (ipng.net, ipng.com, whatever) at a site like godaddy.  Then you become the owner of that domain name.

In order for anyone to be able to browse to your site, you need the site itself to be hosted on a machine.  You can do this yourself (this is where the LAMP server would come in), or rent out space from hostgator, dreamhost, etc.

Lastly, as mentioned, you need some way for networks around the world to find your server.  Unless you are specifically paying for it, you most likely do not have a static IP address.  Even if you have a cable/fiber/dsl broadband connection, your IP address periodically changes.  Therefore you would need some other way, like ddclient/dynamicDNS, to have your domain name point to your server.  

Keep in mind also that a lot of internet providers, at least in the US, block incoming traffic on port 80 unless you are a business customer, specifically so you can't host your own website.  If you are on a school's connection, you might not even be able to do this at all, as you wouldn't have control over the router for your server's subnet.

---

### Post by ipng on 2010-08-01
I've already got a Static IP and website with the domain of my external IP address, but I must admit that I need to get my concepts in order.

I thought that, if you could host your own web space (website) then maybe you could host your domain too. Well, I was wrong ;)

---

### Post by Bachstelze on 2010-08-01
> **ipng said:**
> I've already got a Static IP and website with the domain of my external IP address, but I must admit that I need to get my concepts in order.

Yes indeed.  I don't know what "the domain of an IP address" means.

---

### Post by gordintoronto on 2010-08-01
> **ipng said:**
> I've already got a Static IP and website with the domain of my external IP address, but I must admit that I need to get my concepts in order.

I thought that, if you could host your own web space (website) then maybe you could host your domain too. Well, I was wrong ;)

If you have those things done, you just need to tell your router which computer to send requests to, and install Apache.

---

### Post by bcdudley on 2010-08-02
> Bachstelze 	 		**Re: Hosting your own Domain?**
 		 	Quote:
 	 	 		 			 				 					Originally Posted by **ipng** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9666147#post9666147") 				
 				*I've already got a Static IP and  website with the domain of my external IP address, but I must admit that  I need to get my concepts in order.*
 			 		 	 	 
Yes indeed.  I don't know what "the domain of an IP address"  means. 	

I am pretty sure he means he can get to his website from a public location, using his ip address in lieu of a domain name. 

All you need to do if you have that part working is go to a website that sells domain names such as Godaddy or Network Solutions, purchase the domain name and have their dns servers point to your static ip address.

---

### Post by lisati on 2010-08-02
If budget is an issue, there are places where you can register a free domain name, e.g. [noip]("http://no-ip.com") and [dyndns]("http://www.dyndns.com/").

I have a couple of domain names registered there (see my sig): the DNS hosts point my domain name at my public IP address, my router points incoming requests to the machine on which I run apache (website) and postfix (email).

---

### Post by ipng on 2010-08-02
> **Bachstelze said:**
> Yes indeed.  I don't know what "the domain of an IP address" means.

Ease dude.. 
I'm trying to tell you that I'm using my external IP address as my domain.. Well, maby I'm not spelling correct or using the correct terms, but I'm a 15 year old kid and I'm just interested in computers and electronics. Everyone has been a newbie.

---

### Post by ipng on 2010-08-02
> **lisati said:**
> If budget is an issue, there are places where you can register a free domain name, e.g. [noip]("http://no-ip.com") and [dyndns]("http://www.dyndns.com/").

I have a couple of domain names registered there (see my sig): the DNS hosts point my domain name at my public IP address, my router points incoming requests to the machine on which I run apache (website) and postfix (email).

Thanks alot :) It helped me quite alot.

---

### Post by Bachstelze on 2010-08-02
> **ipng said:**
> Ease dude.. 
I'm trying to tell you that I'm using my external IP address as my domain.. Well, maby I'm not spelling correct or using the correct terms, but I'm a 15 year old kid and I'm just interested in computers and electronics. Everyone has been a newbie.

I didn't mean it in a rude way, sorry if that's how it came out. :o

When you're using an IP address, you're not using a domain.  That's the point of a domain: it gives you an easy-to-remember name that you can use to reach a machine over a network without having to remember its IP address.

---

### Post by mcarrara on 2010-08-02
I think the word 'domain' is confusing the issue.

Do you want to host a group of web sites with a custom last three letters such as [www.mysite.grt?](www.mysite.grt?)

You can not make up your own top level domain (TLD)  It is a HUGE deal to get one approved.  I doubt anyone on this forum could get a new tld approved.

There are other uses of the word domain, if you mean one of the other uses, please clarify your question.

---

