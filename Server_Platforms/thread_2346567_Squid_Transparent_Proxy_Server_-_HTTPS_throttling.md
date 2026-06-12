---
title: "Squid Transparent Proxy Server - HTTPS throttling"
date: 2016-12-16
forum: Server Platforms
---

### Post by kasdasd on 2016-12-16
Hello Guys,

my goal is to throttle every kind of traffic based on a IP-Address. This is already working if I configure my Squid Server as an non-transparent proxy - means the user has to setup the proxy server in his browser.
Everything is getting throttled as we wanted.

The Problem is this is just a test environment, we cannot tell 3000 random people to please setup a proxy server. So this is the reason it needs to be transparent.

Now I realized i cannot simply use routing-table to forward 443 (HTTPS) traffic to Port 3128 (Squid-Server). 
For HTTP traffic this is no problem - using this command:
iptables -t nat -A PREROUTING -i ens192 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128 

Same thing is obviously not working for HTTPS.
So i cannot tell the user to use Proxy, nor i can tell him to please install a certificate. What are my options?

Thank you very much!

---

### Post by SeijiSensei on 2016-12-16
> **kasdasd said:**
> So i cannot tell the user to use Proxy, nor i can tell him to please install a certificate. What are my options?
Buy a valid certificate and use it on the proxy with SSLBump enabled.

You cannot proxy HTTPS traffic since that will appear to the browser like a "man-in-the-middle" attack.  The "SSLBump" code that was added to Squid gets around this problem by using its own certificate to endorse the remote site.  You can use a self-signed certificate in the proxy, but your customers will be told not to trust the site.  If you use a valid certificate from a known provider, it will probably work transparently.

I've done a little testing with self-signed certificates, and they do work if you ignore the browser's complaint.  At the client where I manage a Squid proxy we've talked about implementing HTTPS proxying, but they're not ready to take that step yet.

---

### Post by kasdasd on 2016-12-19
Thanks for your answer!

I'd rather not have to implement HTTPS proxying as well, but I guess i have no choice. 
We want to throttle every kind of traffic from every single user to a specific bandwidth... which we cannot do without redirecting everything though squid. 
Thanks for the hint with the public certificates.

By the way - what happens to all the other kinds of traffic? Talking about FTP or SSH. 
Will those remain unlimited in bandwidth anyways because Squid cannot handle them?

You may know about a better solution without having to invest in other hardware / software?

---

### Post by SeijiSensei on 2016-12-19
Have you read this: [http://lartc.org/lartc.html#LARTC.QDISC](http://lartc.org/lartc.html#LARTC.QDISC)

I've never had the need to do any of this myself, so beyond this you'll have to rely on others here.

---

### Post by kasdasd on 2016-12-21
Thanks for the information!
Can you please help me once more? 
What kind of Certificate do i need? Do i need two certificates - one host-certifcate for the client-side and one wildcard one for the internet side?
Or can i handle everything with just one certificate? 

Also looks like i'm having trouble setting HTTPS up for Squid ... thank you so much.

---

### Post by SeijiSensei on 2016-12-21
I believe you only need one that endorses the machine running Squid.

Have you read the [documentation]("http://wiki.squid-cache.org/Features/SslPeekAndSplice") for "Peek-and-Splice" and SSLBump?  I just followed that when I was testing.

Give it a try first with a self-signed certificate and see if you can get a client browser to connect.  You'll get the security warning, of course, but see what happens if you accept the bogus certificate.

---

### Post by kasdasd on 2016-12-22
Yeah I have that documentation on my to-do list.
I'm sure it will work if I add my self-signed certificate to my browser. 

My only concern is that I don't think it's possible to do what I want even with a bought, trusted certificate WITHOUT having to touch the client.
I guess since my intention is to throttle all kind of traffic by IP, i'll try something with iptables / tc commands and dont have to worry about certificates- but I don't know yet if it will fit my requirements. 

Anyways ... thank you very much for your help. I'll keep you posted.

---

### Post by SeijiSensei on 2016-12-22
I find throttling to make little sense in most cases.  TCP/IP generally uses bandwidth pretty efficiently.  Are you an ISP providing connections to clients?  If so, I'm sure there is professional equipment that can do what you want without having to learn about arcane features in Linux.

I never understood why FTP sites had bandwidth limits.  If my connection to a server is five times larger than yours, then I'll be done downloading five times sooner.

---

### Post by kasdasd on 2017-01-11
The problem I had was that there is very little bandwidth and very many users sharing this bandwidth - this is the reason we need to throttle some of them for a fair use policy. 
You know there are always people that uses much more traffic then others do. Top 2% of users used like 40% of bandwidth... this is what i want to change.

No professional equipment needed - I got this working on a standard linux server working with QDISCs and iptables. I can now limit every single IP in both, download and upload, on the exact value I like to whatever kind of traffic they use.
On a second server squid is running and caching everything on port 80...

Thanks for your help!

---

