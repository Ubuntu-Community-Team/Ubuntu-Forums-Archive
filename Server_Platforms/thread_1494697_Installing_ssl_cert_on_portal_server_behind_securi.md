---
title: "Installing ssl cert on portal server behind security router"
date: 2010-05-27
forum: Server Platforms
---

### Post by greavette on 2010-05-27
Hello,

I've setup OpenVPN-ALS (formerly known as Adito) on Ubuntu Server 10.04 edition.  I have a security router (Untangle) in front of my internal network.  I have a domain name and an SSL Certificate setup on our security router.  I can access our web interface on our security router with no problems.

I've setup a portforward rule on our router to access this OpenVPN-ALS portal and I can access it, but I get an invalid certificate message.  So I've bought another SSL certificate to install our our Portal, but I'm getting an error message when I enter in our information at the provider where I've bought the certificate. 

Common Name does not contain fully qualified domain name.

I'm not sure what the problem is.  Do I use the hostname I've setup on the portal or do I use the hostname on my security router when I setup the SSL certificate on our portal?

Thanks,

Charles.

---

### Post by cdenley on 2010-05-27
So you're directing your browser to an encrypted page on your portal, but your browser says "Common Name does not contain fully qualified domain name"? Obviously, the hostname you are accessing the page with must match the common name of the SSL certificate, or you will get a scary warning message. It sounds as if your browser is actually complaining that the common name, whether it matches or not, isn't a fully-qualified domain name. For example, "mydomain.com" is fully-qualified, but simply "mydomain" isn't. I don't recall firefox ever having a problem with this. What browser are you using?

---

### Post by greavette on 2010-05-27
Hello cdenly,

Thanks very much for the reply.

Sorry, I need to explain myself better.  I'm not seeing this error message when I connect to our portal through our browser.  Let me explain.

Here are some details (exmaples only):
domain name:  business.biz
untangle router:  gateway.business.biz
Portal hostname: portal

On our Portal I setup the following to create a new Certificate:

    * Host name: portal.business.biz
    * Organisational unit: portal
    * Company: portal
    * City: City
    * State: Province
    * Country: CA


I've bought an SSL certificate from NameCheap.com.  I've downloaded the csr file from my portal server and opened it in Notepad.  I copy and paste everyhing into NameCheap.com to issue  the new certificate.  That is when I receive the message:

Common Name does not contain fully qualified domain name.

So what have I done wrong?  Have I used the wrong hostname when createing a new certificate on our Portal?  Should I have used portal.business.biz or should I have used gateway.business.biz (even though I've already used this to create my certificate on our security router)?

Thanks!

---

### Post by cdenley on 2010-05-27
I assume by "host name" you mean common name. I don't see why it would say "portal.business.biz" is an invalid common name. Perhaps when they check for an FQDN, they assume it uses a .com, .net, or .org suffix, not a .biz.

---

### Post by greavette on 2010-05-27
Yes by hostname I mean common name.  I guess I'll have to ask at NameCheap why they think this is invalid?

If anyone else knows why this isn't working, please let me know.

Thanks!

---

### Post by greavette on 2010-06-01
I spoke to a service rep at NameCheap and they instructed me to use a full name for my hostname like portal.example.biz to get past this error.  I had only been using a hostname like portal which is why I was getting this error.

---

