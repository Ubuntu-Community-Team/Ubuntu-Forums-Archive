---
title: "How secure can a website REALLY be?"
date: 2011-05-25
forum: Security
---

### Post by garfonzo on 2011-05-25
I want to set up a website that hosts very confidential business information. The info needs to be accessed by multiple people in different geographical regions. The entire website would require the high security (ie: there are no little sections that are publicly viewable). 

While the site will be run with Ubuntu server, I will be hosting it in Amazon's EC2 cloud.

So, if I use the HTTPS protocol with an SSL certificate, am I pretty well reaching the most secure possible situation? Are there any concerns with using the EC2 solution?

Obviously there are a LOT of variables involved with maintaining website security, but I want to know if HTTPS is the current best bet (in addition to all the "best practices" of securing a site) or if there is a more robust way of securing content.

Thanks!

---

### Post by wojox on 2011-05-25
My bank uses https, so yeah. If I can move money around and what have you. :P

---

### Post by garfonzo on 2011-05-25
> **wojox said:**
> My bank uses https, so yeah. If I can move money around and what have you. :P

Thanks for the quick reply. That was what I was thinking too. However, I wonder if they have something else going on in the background in addition to HTTPS that really secures the site.

---

### Post by Thewhistlingwind on 2011-05-26
While I don't know anything about specifics, I know that server security is an field unto itself, and depending on just how confidential were talking, it may not be possible to "effectively" secure it with your time and resources.

As far I know however, HTTPS is a secure protocol.

 EDIT: Example of a bank using https ([https://www.chase.com/](https://www.chase.com/))
However, as that's not my bank, that may be a phish for all I know.
EDIT2: Also, I would say that no, thats not the most secure solution, theres more to it then that.

---

### Post by wojox on 2011-05-26
There is a lot of good information in the sticky [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by SeijiSensei on 2011-05-26
I'd be more concerned about application security rather than transport security.  SSL ("https") is a perfectly robust solution.  What can be more problematic is whether users can manipulate the web application to reveal information about other users.  Then we're talking about how cookies are created, used and expired, whether you're using effective password hashes, whether your application checks to insure that SQL-injection attacks can't be run against it, and so forth.

---

### Post by tgm4883 on 2011-05-26
Worth noting that once you get this all setup and secured, that security is a journey, not a destination.

---

### Post by wojox on 2011-05-26
> **tgm4883 said:**
> Worth noting that once you get this all setup and secured, that security is a journey, not a destination.

True, a never ending journey. :P

---

### Post by anomie on 2011-05-26
[QUOTE=garfonzo]So, if I use the HTTPS protocol with an SSL certificate, am I pretty well reaching the most secure possible situation?[/quote]

Of course not. There is an illuminating text on this topic that I highly recommend to any Apache http server administrator: 

*Apache Security*, by Ivan Ristic

If you are serious about understanding and deploying Apache with security in mind, read the book. (It's relatively inexpensive to buy, and should be available in many local libraries. Disclosure: I do not know the author, and I do not get paid to suggest his book.) 

[QUOTE=garfonzo]Are there any concerns with using the EC2 solution?[/quote]

Yes. Storing unencrypted, sensitive information on a co-located host (the cloud is co-located to the nth degree) should be a major concern. 

[QUOTE=garfonzo]I want to know if HTTPS is the current best bet...[/QUOTE]

TLS and x509, in this context, solve a limited set of problems: encryption over the wire, and (in theory) authentication. That's it.

---

### Post by garfonzo on 2011-05-27
> **anomie said:**
> Of course not. There is an illuminating text on this topic that I highly recommend to any Apache http server administrator: 

*Apache Security*, by Ivan Ristic

If you are serious about understanding and deploying Apache with security in mind, read the book. (It's relatively inexpensive to buy, and should be available in many local libraries. Disclosure: I do not know the author, and I do not get paid to suggest his book.) 



Yes. Storing unencrypted, sensitive information on a co-located host (the cloud is co-located to the nth degree) should be a major concern. 



TLS and x509, in this context, solve a limited set of problems: encryption over the wire, and (in theory) authentication. That's it.

I'll have to go find that book as I will be deploying Apache with security in mind. As far as Amazon's EC2, you're saying that they may not be a great place to host a web-app with sensitive data? My understanding is that the EC2 machine instance you use (and the storage service Amazone provides) can all be locked down and encrypted. Isn't securing an EC2 machine instance similar to having my own server in my office and securing it down? I'm not following how/why the EC2 is an insecure platform.

---

### Post by anomie on 2011-05-27
Cloud storage potentially spans across many different backend servers, none of which are physically secured by you. Unless your data is encrypted by a key the end user (somehow) safely provides, there is always going to be a chance that your data could be accessed in a way you might not expect. 

I'm not a cloud expert, and I don't have any credible cloud storage security resources to point you to. Just be aware that it's a very different animal than your standalone business server that is sitting in an (access controlled) data center.

---

### Post by Het@l99 on 2011-06-15
HTTPS is the most secure protocol and its a security certificate for your website. Also people can trust on the website having this certification.

---

### Post by tapi0n on 2011-06-15
> **Het@l99 said:**
> HTTPS is the most secure protocol and its a security certificate for your website. Also people can trust on the website having this certification.

If you (as user) want to trust a website presenting a certificate you have to look at the root of that certificate. If a known instance (which handles certificate signing) signed a certificate you can be pretty sure it's safe.

But you can just as easily create a self-signed certificate which doesn't guarantee anything iirc.

---

### Post by BkkBonanza on 2011-06-15
EC2 is not known specifically to be insecure but consider that you are placing data on a machine in a data center far away and that you have no physical control over who may or may not see the contents or what they may do. It simply depends on the level of security you need. There is some point where data may be so valuable/dangerous that you wouldn't want to risk those unknowns.

SSL is secure but it is more secure if you use your own (self-signed) certificates created by your own CA. Then you are not taking the risk associated with some third party controlling the root certificate to your security. This assumes you have the ability to properly protect your own root certificate. If you can't prevent someone from breaking in and stealing that then it isn't such a good idea.

Likewise, the security of EC2 is in comparison to how well you can secure a server on your own premises, or the premises of any third party data center. I'd think that Amazon has as good or better security as any data center but unless you've done homework on these issues how can you know?

You can always take things further than SSL. You can maintain encrypted volumes (on EC2 or wherever) and require users access your server via an SSH proxy that then grants them access to an internal SSL web site (this is easy but more steps for users). You can require multiple levels of authentication in this process. Preventing public users from even seeing the web site or knowing it exists helps offset (important) issues regarding web page programming where mistakes are often made (even with SSL being used).

---

