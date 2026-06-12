---
title: "Public DNS Server"
date: 2011-06-21
forum: The Cafe
---

### Post by piine on 2011-06-21
Hi, I am building my website from scratch, using a Linode VPS and I have finally gotten my DNS working. I will be launching a small web hosting site in the near future and will be using my personal DNS server for both internal usage between my servers, as well, to serve out publicly. I am curious, where do I post my public dns so that I can get people using it publicly???

Edit: bodhi.zazen - link removed

---

### Post by jerenept on 2011-06-21
> **piine said:**
> Hi, I am building my website from scratch, using a Linode VPS and I have finally gotten my DNS working. I will be launching a small web hosting site in the near future and will be using my personal DNS server for both internal usage between my servers, as well, to serve out publicly. I am curious, where do I post my public dns so that I can get people using it publicly???

Here will do just fine. Also; why?

---

### Post by stmiller on 2011-06-22
Who are you? :)  Not that we assume anything evil or wrong, but by running a DNS server, you could easily hijack / alter our DNS lookups and make a fake phishing scam page ([www.mybank.com](www.mybank.com), etc).

I'm not saying this is the case of course, but there is a lot of trust in choosing a DNS server.

Cheers,

---

### Post by alphacrucis2 on 2011-06-23
> **piine said:**
> Hi, I am building my website from scratch, using a Linode VPS and I have finally gotten my DNS working. I will be launching a small web hosting site in the near future and will be using my personal DNS server for both internal usage between my servers, as well, to serve out publicly. I am curious, where do I post my public dns so that I can get people using it publicly???

If you have a registered domain name, your registrar should allow you to specify whatever DNS servers you like as being authorative for that domain. Of course they have to be working DNS servers otherwise your domain will be dead. Most home/small business domains will generally have the domain authority set to the DNS servers of their domain registrar but there shouldn't be anything stopping you specifying your own DNS servers. You are normally required to provide at least two DNS servers in case one fails.

[QUOTE="Wiki"]When domain names are registered with a domain name registrar their installation at the domain registry of a top level domain requires the assignment of a primary name server and at least one secondary name server. The requirement of multiple name servers aims to make the domain still functional even if one name server becomes inaccessible or inoperable.[12] The designation of a primary name server is solely determined by the priority given to the domain name registrar. For this purpose generally only the fully qualified domain name of the name server is required, unless the servers are contained in the registered domain, in which case the corresponding IP address is needed as well.[/QUOTE]

According to a whois lookup at network solutions. The domain betteryourweb.net currently has the following authoritive DNS servers:

      NS1.LINODE.COM 
      NS2.LINODE.COM 
      NS3.LINODE.COM 
      NS4.LINODE.COM 
      NS5.LINODE.COM

---

### Post by piine on 2011-06-23
This is more or less a project for me... building a web hosting control panel...

---

### Post by haqking on 2011-06-23
> **piine said:**
> Hi, I am building my website from scratch, using a Linode VPS and I have finally gotten my DNS working. I will be launching a small web hosting site in the near future and will be using my personal DNS server for both internal usage between my servers, as well, to serve out publicly. I am curious, where do I post my public dns so that I can get people using it publicly???[]("http://dns.betteryourweb.net")

i cant see too many people taking up your offer of a untrusted DNS server ;-)

it screams HIJACK and SCAM ;-)

No offence meant by the way ;-)

---

### Post by piine on 2011-06-23
I would like a little direction on the subject if anyone can help. I am a web developer and I have hosting plans with a few hosting companies. I have turned a couple VPS into share web server to host a few of my sites, I do some specialty programs for a few companies which require VPS... Well, I have these other VPS setup so well with the share servers that I started making scripts to automate task and a very slim control panel... Well, I am giving a shot at building a hosting service, small scale of course, however, I, first of all, want to offer a service I created (free service), and secondly, this will be the best way for me to get everything rock solid.

I'm asking for a little help... If you see me doing something wrong, please help guide me to the proper path...

---

### Post by piine on 2011-06-23
Also, I am not looking for it to get too big too fast... I will also have my own DNS servers for my hosting... 

If you test it and tell me what I need do to make it better, please do... I plan to at the very least, plan to have a forum up on the site within the next couple of days... This is more or less a side project... Not a big rush... I will be putting the control panel on sourceforge.net in the near future...

Please help or point me to help, thanx...

---

### Post by Dangertux on 2011-06-23
> **haqking said:**
> i cant see too many people taking up your offer of a untrusted DNS server ;-)

it screams HIJACK and SCAM ;-)

No offence meant by the way ;-)

I'm with you on this one...

Honestly, for a project of this nature. You are going to have to work very hard to build your reputation. I would question anyone who said oh hey I just changed my DNS to some random guy's private DNS server. Like haqking said, no offence but...Yeah , it just looks bad.

---

### Post by alphacrucis2 on 2011-06-23
> **piine said:**
> Also, I am not looking for it to get too big too fast... I will also have my own DNS servers for my hosting... 

If you test it and tell me what I need do to make it better, please do... I plan to at the very least, plan to have a forum up on the site within the next couple of days... This is more or less a side project... Not a big rush... I will be putting the control panel on sourceforge.net in the near future...

Please help or point me to help, thanx...

As I said if you are the domain owner you should be able to make your own DNS servers authorative for any domain that belongs to you. With the registrar I deal with they give their users a web portal that allows us to login and set the DNS servers and other things for the domains that we own. Doing that links the DNS servers into the normal internet domain system but the specified DNS servers will only be responsible for the domains that you have authority over. As others have said, no one is going to change their DNS settings to point directly at your servers as you could then feign authority for domains that are not yours.

---

### Post by piine on 2011-06-24
I was thinking more on the lines of OpenDNS, Verisign, or Google DNS... What I am testing is the recursive caching DNS... I am not worried about authoritative DNS right... That is a completely different issue... 

I know those are all big companies, been out there a while, blah, blah, blah... Not try to have a million users over night... Just would like a few people to use it a nameserver on their computer...

And again, criticisms, but no help... I own a small company, so I have little to rep... I am working on that, but until then, I am just looking for help, not a bashing, so pls, if what ur going to post is not helpful, pls, don't post... 

If I am wasting my time, pls tell me so I can move on... Not meaning to be an ***, however, I need help, not a lecture, talking to or bashing...

---

### Post by piine on 2011-06-24
If by chance you think it's fraudulent, how about you setup a Virtual Machine and test it... All this server does is foward googles dns 8.8.8.8 and 8.8.4.4 and resolves from the root servers. They have many diagnostic tools in which to help you verify the validity of my servers. ex. dig and nslookup...

---

### Post by Dangertux on 2011-06-24
I think you took me the wrong way.

The criticism I gave you was legitimate, asking someone to switch their DNS is a serious issue. You have to consider all sides of the coin when asking if this is worth your while. Not just from a technical aspect. 

From an educational aspect, I think it's a great idea, learning new things and setting up new things is always beneficial. From a business standpoint you have two major issues.

1 -- Most people don't think much about their DNS service at all, in fact most don't even know what DNS is, they go on blindly thinking that their browser magically knows where to find google.

2 -- If they DO know what DNS is, they also understand what you're offering, or can at least research it. When it comes to that point, you don't have the name Google, as your company's name, regardless of if you're just caching their records or not. Thus, you don't have the required reputation to back up the claim that you're more secure than the standard ISP or competing public DNS. You have to answer the who are you question. Why would I switch to your DNS? Is it more secure? You tell me it is. How do I know?

The perspective I gave you in an earlier post was shared to get you to look at some points of view that I'm not sure you've thought all the way through. It's not a slam, personal attack , or any type of bashing.

You also have some technical issues with what you're doing as well.Linode, your host only allows a certain number of file descriptors(1024), if you get into heavy traffic you're going to have some issues there ; especially if you're hosting a website a public DNS server, a mail server and whatever else you decide to run. 

Bottom line, for learning, I think what you're doing is great. Do I think you've thought the entire project all the way through to its finality? Nope, not really. You have issues with the presentation, and the technical means for delivering this service. As far as will I test your service, no I won't. Why? If you want to put something out to the community, and ask people to test it; you shouldn't turn around and complain that they are bashing you when they have perfectly legitimate concerns.

---

### Post by bodhi.zazen on 2011-06-24
Thread closed.

If you wist to run a private DNS server for your LAN, more power to you, I personally do.

But running a public DNS service is a security risk, as has been mentioned in this thread.

As a waring to all, use only trusted DNS servers, otherwise your traffic could easily re-directed to malicious sites, leave you vulnerable to man-in-the-middle attacks, etc.

If needed there are several "public DNS servers" - google, opendns 

[http://www.opendns.com/](http://www.opendns.com/)

I will edit the above  discussion and remove the ip listed here.

---

