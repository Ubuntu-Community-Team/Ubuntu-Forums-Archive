---
title: "Dealing with hack attempts"
date: 2009-10-02
forum: Security
---

### Post by noway2 on 2009-10-02
As I run a personal email server, I expect to get attempts to hack into it.  This morning, I received an OSSEC notification of such an attempt.  Out of curiosity, more than anything, I inspected the mail and auth logs and I saw something that caught my attention.

The "attack" consisted of attempting to open multiple (total 9) simultaneous connections to Postfix, and then a few seconds later attempting use a plain text login (disabled) on each of them.  Each attempt was denied, but the attempt appeared to have a little more sophistication behind it than normal script kiddies.

The part that really caught my attention was that the IP address (203.85.114.102) came back as resolved to an unknown.  I then attempted to do an nslookup and dig on this IP address and continued to get unknowns.  I then proceeded to try and worm my way down the chain starting with one of the root servers and finally worked down to a name server on the 203.85.114.x network that appears to be located in Hong Kong (the domain ends in .hk), where the name servers having authority claimed that it was an unkown IP address.  Undoubtedly the IP was spoofed.

In response, I added this IP address to the permanent blacklist in IPTables, but I am wondering if there is a more appropriate response that I could take?  My query is more academic than one of paranoia, but I am curious how best to handle these conditions.

---

### Post by cdenley on 2009-10-02
That IP is probably not spoofed.
```

cdenley@ubuntu:~$ host hr.sae.com.hk
hr.sae.com.hk has address 203.85.114.102

```
[http://hr.sae.com.hk/](http://hr.sae.com.hk/)

I think they are running an outdated release of Fedora Core, with apache and ssh servers. They were probably compromised, and their server is now being used to attack other servers. This type of thing will happen often.

---

### Post by noway2 on 2009-10-04
I was going to ask how you figured out who the address belonged to because I tried several name servers and got nada.  Then it occurred to me to simple try the web page: [http://203.85.114.102](http://203.85.114.102) - which came up with the answer.

I think you are correct, it was a hijacked system that someone was using.  As they managed to hijack that system, it also explains the apparent intelligence behind the attempt.

---

### Post by cariboo on 2009-10-04
I got the same result as cdenley, using whois and the ip address. I personally use whois in a terminal, but if you go to System-->Administration-->Network Tools-->Whois, you get the same functionality.

---

### Post by cdenley on 2009-10-04
> **noway2 said:**
> 
As they managed to hijack that system, it also explains the apparent intelligence behind the attempt.

Not necessarily. For all we know, their SSH server could have root login enabled with a weak password like "root" or "secret".

---

### Post by Lars Noodén on 2009-10-05
> **cdenley said:**
> Not necessarily. For all we know, their SSH server could have root login enabled with a weak password like "root" or "secret".

Or they were running a web server with php.  ;)


As to what to do, use [whois](http://manpages.ubuntu.com/manpages/jaunty/en/man1/whois.1.html), or the GUI equivalent, to look at the offending IP number and find out the ISP hosting that machine and the e-mail of the contact person for that ISP.

Make a form letter where you can fill in the date, time, IP number and offending activity.  Save it as a template.  Then fire it off when you identify attacks.  

Be sure that your computer is using NTP, or OpenNTP to synchronize the clocks with the right time (if you don't have a timer card or GPS built in)

---

### Post by noway2 on 2009-10-05
Making up a form letter that you can fill in is a good idea.  Of course this assumes that it is worth it to you to take the time out to do this.  Chances are the only real benefit would be in your own satisfaction, but you never know.  Personally, I think the energy would be better spent on making sure your own server was as secure as possible.

---

### Post by Lars Noodén on 2009-10-05
> **noway2 said:**
> Making up a form letter that you can fill in is a good idea.  Of course this assumes that it is worth it to you to take the time out to do this.  Chances are the only real benefit would be in your own satisfaction, but you never know.  Personally, I think the energy would be better spent on making sure your own server was as secure as possible.

The two activities are not mutually exclusive.  

A problem can only be solved at the source.

---

### Post by thewanderer on 2009-10-05
Unless you discover evidence that the attempt hack was of a targeted nature I would not be too concerned.

The amount of noise that an Internet server receives is astounding.

In fact most operators would not have even noticed the noise. Good thing you are running [OSSEC]("http://www.ossec.net"). It really is an excellent defensive tool.

---

### Post by fela on 2009-10-05
Lucky my server is behind two hardware firewalls and one or two DHCP servers :)

My policy on security is not to look into it unless I get hacked :)

---

### Post by noway2 on 2009-10-06
In regards to this particular instance, I am going to operate under the semi-informed assumption that Postfix can handle it: the attempt to create some form of overflow by opening several simultaneous connections.

However, this also provided some motivation to finally disable password authentication for (remote) SSH.  I have been using key authentication for quite a while and it has worked fine.  Now, at least that portion of the server should be a lot more secure.

I guess it can't be reiterated enough: unless it is necessary to do so, don't open the port or service to the world.

---

### Post by Lars Noodén on 2009-10-06
Just to throw three ideas for postfix into the discussion:

1) Postfix probably was compiled to be tcpd-aware.

If you do not need to allow incoming traffic to postfix from everybody, then you might look at setting up something in [/etc/hosts.deny](http://linux.die.net/man/5/hosts.deny) or [/etc/hosts.allow](http://linux.die.net/man/5/hosts.allow) for [tcpd](http://linux.die.net/man/8/tcpd).  It is one way of whitelisting.  

Or if you allow the world to send to postfix, then you could use hosts.allow to check up on the sending host.  


2) You can use iptables to limit the rate of new connections.  One guess is below.  Like tcpd above, it can be adjusted to reflect your actual network setup.

```

iptables -I INPUT -p tcp --dport 25 -i eth0 -m state \
  --state NEW -m recent --set
iptables -I INPUT -p tcp --dport 25 -i eth0 -m state \
  --state NEW -m recent --update --seconds 360 --hitcount 10 -j DROP
iptables -I INPUT -p tcp --dport 25 -i eth0 -m state \
  --state NEW -m recent --update --seconds 60 --hitcount 2 -j REJECT

```


3) Greylisting currently usually is enough to deter most spammers:
[http://www.postfix.org/SMTPD_POLICY_README.html#greylist](http://www.postfix.org/SMTPD_POLICY_README.html#greylist)

---

