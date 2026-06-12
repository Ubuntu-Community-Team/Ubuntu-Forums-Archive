---
title: "A new threat?"
date: 2012-11-11
forum: Security
---

### Post by jsvidyad on 2012-11-11
Hello,

   It's possible for someone who hacks into a router to change the DNS server ip addresses for that router and thus redirect users(connected to that router) who are accessing the internet to malicious websites in order to steal information from the users and do other unpleasant things. 

    I was under the impression that to protect against this, all I have to do is specify trusted DNS server ip addresses in my laptop itself and thus all DNS requests from my computer would ignore and bypass the DNS servers specified in the router(by the hacker) and all DNS server requests from my computer would go to the trusted DNS servers I specified in my laptop. This is supposed to protect me from being mis-directed to the malicious sites and from other traps set up by the hacker. But, after reading this website: [http://hackercodex.com/guide/how-to-stop-isp-dns-server-hijacking/](http://hackercodex.com/guide/how-to-stop-isp-dns-server-hijacking/) I am not too sure anymore. Can you read this webpage and give me some feedback regarding this?

---

### Post by Moose on 2012-11-11
Makes you worry some of the things hackers can do..

---

### Post by Hungry Man on 2012-11-11
If your router is performing DNS resolution I guess. But your local system is going to be performing it.

What they can do is intercept the DNS request via MITM (instead of just changing a router setting, which wouldn't do anything unless your system couldn't resolve the DNS AFAIK)because DNS isn't encrypted.

It's the same way that when you visit a website over HTTP an attacker can put information into the page you view or they attacker can see that information.

To solve this you can use DNSCrypt by OpenDNS. It encrypts DNS, although I'm not sure about the specifics.

---

### Post by drmrgd on 2012-11-11
Boy, you're really concerned about hackers and your router aren't you?  As others have said, just reset the router and the password and let it go.  

As Hungry Man says, I'm not sure a hacker that has changed the DNS settings on the router could do too much with the system.  Further I'm not sure how the page you linked is related.  In that case, the way I read it, the ISP was re-routing traffic where they wanted it.  That was pretty independent of the users router, until the reconfigured it.

---

### Post by Hungry Man on 2012-11-11
In the case of ISPs redirecting traffic etc there is very little we can do. In various other governments less friendly to privacy we've seen SSL handshakes broken so that users are forced to use HTTP versions of websites or users are prevented from using TOR etc.

Everything you do goes through your ISP at some point - your DNS, all traffic. So while you can have name resolution take place at your router the router just acts as an RX server - it still has to fetch from the ISP or through the ISP.

---

### Post by jsvidyad on 2012-11-15
So, what you guys are saying is that the best I can do is just set the DNS server ip addresses in my computer itself and hope for the best?

---

### Post by jsvidyad on 2012-11-15
> **drmrgd said:**
> Boy, you're really concerned about hackers and your router aren't you?  As others have said, just reset the router and the password and let it go.  

As Hungry Man says, I'm not sure a hacker that has changed the DNS settings on the router could do too much with the system.  Further I'm not sure how the page you linked is related.  In that case, the way I read it, the ISP was re-routing traffic where they wanted it.  That was pretty independent of the users router, until the reconfigured it.

Hi!!

  I just came across that website when I was looking up DNS servers. 

Can a attacker do the same re-routing of dns traffic or can only the ISP do that?

---

### Post by jsvidyad on 2012-11-15
Any suggestions for how to set up dnscrypt in kubuntu 10.04 and ubuntu 12.04?

---

### Post by jsvidyad on 2012-11-16
Can someone please help me here?

---

### Post by cariboo on 2012-11-16
Have you found this [thread]("http://askubuntu.com/questions/105366/how-to-check-if-dns-is-encrypted") yet?

In many cases, the Ubuntu wiki is a great resource when you need to set something, or just need help to solve a problem.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by Hungry Man on 2012-11-16
> **jsvidyad said:**
> Any suggestions for how to set up dnscrypt in kubuntu 10.04 and ubuntu 12.04?

[https://insanitybit.wordpress.com/2012/07/23/setting-up-dnscrypt-by-opendns-on-an-ubuntu-12-04-system-8/](https://insanitybit.wordpress.com/2012/07/23/setting-up-dnscrypt-by-opendns-on-an-ubuntu-12-04-system-8/)

I wrote that a while back. It may still be relevant if they haven't changed anything.

---

### Post by jsvidyad on 2012-11-23
From what I've seen so far, there seems to be issues in getting DNScrypt to work with ubuntu. Do you think it is actually necessary to adopt DNScrypt at all. Will it be enough if I specify trusted DNS servers on my computer itself instead of relying on my router or my ISP to specify the DNS servers? If I specify DNS servers on my computer, can an attacker still redirect my DNS traffic/requests to a malicious DNS server other than the DNS servers specified on my computer? Aren't the DNS server IP addresses specified in the packets sent out by my computer? So, how can such a re-direction take place? 

   The website I gave in my initial post talks about the ISP re-directing traffic even with a different DNS server(other than the ISP provided DNS servers) specified on the router. Can an attacker do the same with the DNS servers specified on the computer itself?

---

### Post by a2j on 2012-11-23
[DNS Poisoning]("http://en.wikipedia.org/wiki/DNS_spoofing"), and you don't have to hack any routers

---

### Post by jsvidyad on 2012-11-24
That's interesting. But, you still haven't answered the question I asked in the post above yours.

---

### Post by mike acker on 2012-11-24
over time i have reflected on  DNS spoofing as well as the Man in the Middle attack.  Both of these are designed to re-direct your computer to a Bad Place

IMHO these attacks are facilitated by our incomplete handling of the keys used in x.509 certificates: we really do not take the trouble to validate even the high level CA that we trust to sign certificates for all the various web sites that are out there

here's my view of this issue:
[IMG]http://napfn.com/https_validation_diagram.png[/IMG]

To really understand this you will need to understand the Trust Model that is used with Public Key Encryption:

the "gist" of it is simple: nothing is trusted until I have performed Due Diligence and validated whatever key(s) I need to trust.

For starters I would need to find the "fingerprint" for (e.g.) VeriSign's key.    Then I would check their x.509 certificate and when I had veriifed their fingerprint I would sign therir certificate and set the Trust level to approve them to sign for other certificates.

Having done this, if a hacker tries to  present a web page that appears to be validated by VeriSign -- by just making it look good -- that page will appear with an UNTRUSTED signature .... and the detection requirement for security is effected.

Sadly all of the above is "too much to trouble the customer with" at least in the view of the marketing people

of course the Governor of South Carolina may now be a bit more interested in this sort of thing...

in all fairness I should note that your x.509 certificates are delivered to your system by your browser OEM.  They should be OK.

---

### Post by OpSecShellshock on 2012-11-24
> **jsvidyad said:**
> The website I gave in my initial post talks about the ISP re-directing traffic even with a different DNS server(other than the ISP provided DNS servers) specified on the router. Can an attacker do the same with the DNS servers specified on the computer itself?

These are basically 2 different things if the ISPs are doing what I suspect. In the case of ISP redirections, even if you use alternative DNS, you are still sending requests and receiving responses over the ISP's infrastructure, so if the traffic is in the clear and you request a domain that doesn't exist, the ISP can intercept the NXDOMAIN response and serve the page with the ads on it anyway. That, I believe, is why something like DNSCrypt has been proposed as a solution. In this case the ISP is not changing the user's DNS server settings, they're just running a MiTM on the network traffic.

If someone can get sufficient access to change DNS settings locally on your computer, they can also do anything else they want to with it, at least there on the local system. They probably won't be intercepting and manipulating network traffic, though.

So the difference is, the ISP can do it because they own the network infrastructure, but the attacker only owns your computer itself.

---

### Post by jsvidyad on 2012-11-24
Hello, can someone please reply to the question I asked in my earlier post. I am giving that post below for your reference:

> From what I've seen so far, there seems to be issues in getting DNScrypt to work with ubuntu. Do you think it is actually necessary to adopt DNScrypt at all. Will it be enough if I specify trusted DNS servers on my computer itself instead of relying on my router or my ISP to specify the DNS servers? If I specify DNS servers on my computer, can an attacker still redirect my DNS traffic/requests to a malicious DNS server other than the DNS servers specified on my computer? Aren't the DNS server IP addresses specified in the packets sent out by my computer? So, how can such a re-direction take place?

The website I gave in my initial post talks about the ISP re-directing traffic even with a different DNS server(other than the ISP provided DNS servers) specified on the router. Can an attacker do the same when the DNS servers are specified on the computer itself? 

---

### Post by maglinu on 2012-11-24
> **jsvidyad said:**
> From what I've seen so far, there seems to be issues in getting DNScrypt to work with ubuntu. Do you think it is actually necessary to adopt DNScrypt at all. Will it be enough if I specify trusted DNS servers on my computer itself instead of relying on my router or my ISP to specify the DNS servers? If I specify DNS servers on my computer, can an attacker still redirect my DNS traffic/requests to a malicious DNS server other than the DNS servers specified on my computer? Aren't the DNS server IP addresses specified in the packets sent out by my computer? So, how can such a re-direction take place? 

   The website I gave in my initial post talks about the ISP re-directing traffic even with a different DNS server(other than the ISP provided DNS servers) specified on the router. Can an attacker do the same with the DNS servers specified on the computer itself?
I found no difficulty setting up DNScrypt in ubuntu 12.04 (and if I can do it anyone can).

I followed this:
[http://www.webupd8.org/2012/02/encrypt-dns-traffic-in-linux-with.html](http://www.webupd8.org/2012/02/encrypt-dns-traffic-in-linux-with.html)
It seems to work (ie it connects to OpenDNS, I wouldn't have a clue if it actually encrypts)

---

### Post by jsvidyad on 2012-11-24
> **OpSecShellshock said:**
> These are basically 2 different things if the ISPs are doing what I suspect. In the case of ISP redirections, even if you use alternative DNS, you are still sending requests and receiving responses over the ISP's infrastructure, so if the traffic is in the clear and you request a domain that doesn't exist, the ISP can intercept the NXDOMAIN response and serve the page with the ads on it anyway. That, I believe, is why something like DNSCrypt has been proposed as a solution. In this case the ISP is not changing the user's DNS server settings, they're just running a MiTM on the network traffic.

If someone can get sufficient access to change DNS settings locally on your computer, they can also do anything else they want to with it, at least there on the local system. They probably won't be intercepting and manipulating network traffic, though.

So the difference is, the ISP can do it because they own the network infrastructure, but the attacker only owns your computer itself.


Hello, I guess my post wasn't too clear. What I wanted to ask was can an attacker do the kind of re-direction the ISP does in that article even in the case when I specify trusted DNS servers in my computer itself. I was not asking what happens if an attacker can change DNS servers on my computer. Sorry! My bad.

---

### Post by The Cog on 2012-11-24
> **jsvidyad said:**
> From what I've seen so far, there seems to be issues in getting DNScrypt to work with ubuntu. Do you think it is actually necessary to adopt DNScrypt at all. That is your decision. Depends how paranoid you feel. At some point, you have to ask yourself if you really trust the OpenDNS servers (or their information sources).> Will it be enough if I specify trusted DNS servers on my computer itself instead of relying on my router or my ISP to specify the DNS servers? If I specify DNS servers on my computer, can an attacker still redirect my DNS traffic/requests to a malicious DNS server other than the DNS servers specified on my computer? 
No and yes. No, specifying the IP address of a trusted server is not enopugh. Yes, and attacker can still redirect your DNS requests, or (more likely) just impersonate the DNS server you asked for. In my opinion that is "wire fraud" and is a  criminal offence in many countries, but ISPs seem to get away with it anyway.> Aren't the DNS server IP addresses specified in the packets sent out by my computer? So, how can such a re-direction take place? The ISP's equipment is forwarding your packets/messages. They are perfectly able to read your packets and substitude different contents whenever they want to. This could include redirecting or falsifying DNS queries or even connections to servers. This kind of message tampering is what encryption is trying to prevent.> 
   The website I gave in my initial post talks about the ISP re-directing traffic even with a different DNS server(other than the ISP provided DNS servers) specified on the router. Can an attacker do the same with the DNS servers specified on the computer itself?Yes. If the attacker controls any equipment along the path between your PC and some other computer you wish to talk to, he can simply monitor the connection, or fully impersonate whatever server you think you are talking to. Several ISPs simply modify the "DNS name not found" message (called NXDOMAIN) from DNS servers to send you to their own servers which then serve you pay-per-click adverts instead.

---

### Post by tubbygweilo on 2012-11-24
Have you ever consider using the [Google Public DNS]("https://developers.google.com/speed/public-dns/")? They have a [Security page]("https://developers.google.com/speed/public-dns/docs/security") and [Privacy page]("https://developers.google.com/speed/public-dns/privacy"). 

Must confess I use Gmail, Google Search Enginge, Google Public DNS and Chromium browser.

---

### Post by mike acker on 2012-11-24
> **The Cog said:**
> {snip}
If the attacker controls any equipment along the path between your PC and some other computer you wish to talk to, he can simply monitor the connection, or fully impersonate whatever server you think you are talking to. Several ISPs simply modify the "DNS name not found" message (called NXDOMAIN) from DNS servers to send you to their own servers which then serve you pay-per-click adverts instead.

this is where it is critical to understand the authenticity and integrity checking capability of Public Key Encryption.

 Where Public Key Cryptology is used properly the attacker cannot impersonate a legimate sender -- or modify the legitimate sender's traffic -- without discovery.

"User properly" is a tall order though, and x.509 as implemented today skips over the most important part of this requirement, that being that each of us needs to authenticate the keys we choose to trust.

authentication problems are a huge part of the trouble we have in electronic security today and sadly too many good people havn't had a chance to understand the capability that PGP, GnuPG, or Public Key Encryption can provide.

There is a support wire/mail list for Thunderbird/Enigmail available for anyone interested . I was delighted to find GnuPG included by default with my Ubuntu system.  For Thunderbird, to get started you just click on Tools ~ get add-ons ~ get and install Enigmail.  then generate your keypair.  my public key is on the server.

---

### Post by tubbygweilo on 2012-11-24
The [Enigmail handbook]("http://www.enigmail.net/documentation/handbook.php") & other assorted information held on [project site]("http://www.enigmail.net/home/index.php") are a good place to start. Much harder is convincing those who you email to adopt Enigmail!

---

### Post by OpSecShellshock on 2012-11-24
> **jsvidyad said:**
> Hello, I guess my post wasn't too clear. What I wanted to ask was can an attacker do the kind of re-direction the ISP does in that article even in the case when I specify trusted DNS servers in my computer itself. I was not asking what happens if an attacker can change DNS servers on my computer. Sorry! My bad.

Technically yes, practically no. In order to do specifically and exactly what the ISP is doing in the article, an attacker would have to compromise the ISP itself (or the DNS servers that you have selected).

---

### Post by mike acker on 2012-11-25
> "Security is a function of the resources your adversary is willing to commit," said Julian Sanchez, an attorney with the Cato Institute in Washington, D.C.


DNS Poisoning was quite the issue a few years back but the issue faded out when the DNS Server Operators added an authentication requirement for updates... imagine that

IMHO (as usual ) the computer industry -- from the advent of the microprocessor ( c.1980) until around 2004 took a pretty slip-shod approach to security

hacking started as a prank with stuff like the "Pakistani Brain", "Your Computer is Stoned, Man, get some good weed " , to "Falling Letters" &c

but it has graduated to Zeus and the new & Improved Black Hole Exploit Kit and other kits that produce as much as 1 new virus sample per second, 24/7.

the industry has been slow to respond but I think they are "getting it": letting a computer run any program that is thrown at it is a recipie for trouble.

as a result we are seeing the development of approved libraries.  even Google/Android seems to have headed in this direction in the last month or so

with virus cropping up at 1 a second or better searching for known virus is not a solution. we have to move to the approved library model.   this is discussed in the anti-virus sticky notes we have on our forum.

Fundamentally we have 3 main type of software:

[LIST=1]
[*]your Operating System
[*]your installed applications
[*]transient software: java script, flash objects, .net, Visualbasic, php, xss, sql injections, iFrames etc.  These are "scripting" components of web pages, word documents, excel sheets and such
[/LIST]
The first 2 types can easily be controlled by simply authenticating updates.  



The 3d class is more difficult.  the first thing to do is to 'sandbox' the program you use for interpreting the web pages and other documents that are sent to you


i have AppArmor applied to my Firefox browser for this reason now. Hopefully we will see more discussion of this fine product.


The key we are looking for is to insure that some sort of transient script is not able to surreptitiously add a 'plug in' to your interpreter (Firefox, Word, etc ) .

---

### Post by jsvidyad on 2012-11-30
> **The Cog said:**
> That is your decision. Depends how paranoid you feel. At some point, you have to ask yourself if you really trust the OpenDNS servers (or their information sources).
No and yes. No, specifying the IP address of a trusted server is not enopugh. Yes, and attacker can still redirect your DNS requests, or (more likely) just impersonate the DNS server you asked for. In my opinion that is "wire fraud" and is a  criminal offence in many countries, but ISPs seem to get away with it anyway.The ISP's equipment is forwarding your packets/messages. They are perfectly able to read your packets and substitude different contents whenever they want to. This could include redirecting or falsifying DNS queries or even connections to servers. This kind of message tampering is what encryption is trying to prevent.Yes. If the attacker controls any equipment along the path between your PC and some other computer you wish to talk to, he can simply monitor the connection, or fully impersonate whatever server you think you are talking to. Several ISPs simply modify the "DNS name not found" message (called NXDOMAIN) from DNS servers to send you to their own servers which then serve you pay-per-click adverts instead.


Hello, so the gist of your post is that just setting trusted DNS servers on my computer is not good enough and I should use some kind of encryption such as the one provided by DNSCrypt. Is that right? If yes, do I have some option other than DNSCrypt? Hopefully something that is straight forward to set up and for which packages are available in the ubuntu repositories?

---

### Post by jsvidyad on 2012-12-01
Can someone please help me here?

---

### Post by OpSecShellshock on 2012-12-01
There wouldn't be anything in the repositories, but there are packages created by OpenDNS developers apparently. Check out [this post]("http://blog.opendns.com/2012/02/16/tales-from-the-dnscrypt-linux-rising/") for links and instructions. As far as I know, DNSCrypt is the only thing like it that is available and easy to use.

Do keep in mind that the only problem this really solves is that of your ISP returning a landing page of their choosing instead of an error page that the standards actually dictate (and apparently OpenDNS also redirects to landing pages if you just use their servers without setting up an account and make a request for a domain that doesn't exist). The article linked in the original post was about that, and not about attackers. If there are indeed problems with DNSCrypt working in Ubuntu then it's likely not worth it.

If you're worried about an attacker and not your ISP, I wouldn't. Since you have locally specified DNS servers by IP address on your computer itself, an attacker would have to have compromised either your ISP, the ISP used by OpenDNS for their servers, the backbone provider between the two, or the actual DNS server that you're connecting to. All of those things are very unlikely, but they are also completely out of your control. If those systems were under the control of an attacker, you wouldn't be able to do anything about it and you also probably wouldn't have any way to know it was even happening.

---

### Post by maglinu on 2012-12-01
I don't really want to add to the paranoia, but I'm not sure how much you could trust DNScrypt when it's needed anyway.

The default behaviour of DNScrypt in Windows is to fail over to unencrypted if encrypted traffic is rejected. In windows the GUI allows you to change this default easily.

I don't know what the default behaviour is in Linux. If it's the same as Windows (which seems logical since it's the same basic application) then presumably all the bad man in the middle trying to spoof your ISP or DNS has to do is reject encrypted traffic and DNScrypt will helpfully provide the information unencrypted?

I guess there will be a DNScrypt config file that allows me to interrogate/edit the Linux defaults, but I haven't spotted it.

---

