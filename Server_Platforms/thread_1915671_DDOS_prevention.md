---
title: "DDOS prevention"
date: 2012-01-26
forum: Server Platforms
---

### Post by DanHorniblow on 2012-01-26
Hi, I have recently setup a VPS server which I will be using for web hosting.

I have a freind who is very knowledgeable in IT security and he was ablle to bring my VPS down temporarily.

How would i protect against this? Would a simple software firewall do?


Many Thanks

---

### Post by lisati on 2012-01-26
One option might be [fail2ban]("https://help.ubuntu.com/community/Fail2ban"), which monitors system logs and works with the firewall to block misbehaving clients.

---

### Post by DanHorniblow on 2012-01-26
Hi, I setup fail2ban on the server earlier. How do I know if its working?

---

### Post by Dangertux on 2012-01-26
There are many types of denial of service attacks, fail2ban will not help with most of them. That being said, to givey you a more complete answer we'd really need to know what was done to "bring down your VPS".

I would suspect a resource starvation attack of some kind, as most cheap VPS'es do not provide balloon access to resources beyond a very small amount. Like I said, you would need to know more about what was done. However a basic set of things you can look into are as follows.

- iptables rate limiting (search it there have been at least a dozen threads on it in the past 3 months on this forum)

- mod-evasive , mod-security and mod-qos (if you're using Apache)

- fail2ban can help in some cases (but this is redundant with rate limiting)

- Proper kernel tuning (google it)

- Mandatory access controls to limit the amount of resources a given process can utilize (this can also be done in your kernel)

- Working with your VPS provider in the case of a denial of service condition (whether malicious or getting slashdotted) is often the most productive as they can give you access to a VERY large amount of resources, and more bandwidth then you will need to ride out the attack.

Hope this helps.

---

### Post by Vegan on 2012-01-26
DDoS is impossible to stop, all you can do is wait for the attack to come to an end

---

### Post by Dangertux on 2012-01-26
> **Vegan said:**
> DDoS is impossible to stop, all you can do is wait for the attack to come to an end

Umm...Not really. But okay, besides unless his friend controls a rather large botnet I find it unlikely the VPS was actually DDOS'ed more like just regular ole DOS'ed.

---

### Post by DanHorniblow on 2012-01-31
Hi, Sorry for the late reply.

My freind was making lots and lots of http requests and then not responsing to them. I think it was something like that anyway.

I was confused how one laptop with a internet connection of about 5 or 6 meg could bring down my VPS which has a 100 meg connection.

I am looking into what you sugested Dangertux :)

Thanks

---

### Post by poolet on 2012-02-01
:) One of my Professors told me "If someone wants full security in his/her network, just tell him/her to un-plug the cable from the pc or server whatever"  Doesn't matter how far is.... Try Fail2ban.. it's a good idea. Or you can forwarding any attact with your router (I don't want to promote products here ) search in google....  :)

Good Luck...!

---

### Post by DanHorniblow on 2012-02-01
Hi, Thanks for all the support people. This is what I have done.

I have setup fail2ban to allow a maximum of 6 failed attempts for ssh, ftp, smtp, imap and pop3

I have also installed the shorewall firewall which has allowed me to block pings and alot of other things that where being allowed through.

I will be soon implementing the apache mods that Dangertux spoke about (mod-evasive , mod-security and mod-qos).

Thanks for all the help.

---

### Post by Dry Lips on 2012-02-01
I'm not sure if you guys have heard about cloudflare, but they boast about being able 
to prevent/limit DDOS attacks...

---

### Post by Dangertux on 2012-02-01
> **DanHorniblow said:**
> Hi, Sorry for the late reply.

My freind was making lots and lots of http requests and then not responsing to them. I think it was something like that anyway.

I was confused how one laptop with a internet connection of about 5 or 6 meg could bring down my VPS which has a 100 meg connection.

I am looking into what you sugested Dangertux :)

Thanks

That attack seems similar to LOIC (lame) or Slowloris (equally lame) mod_qos deals with both nicely, as will mod-security.

Hope this helps.

---

### Post by DanHorniblow on 2012-02-02
Hi, I have now setup mod_evasive and mod_security, I wrote a post about them and how I implemented them [here]("http://danhorniblow.co.uk/protecting-against-ddos-attacks-with-apache-mod_evasive-mod_security/").

Althought what other benefits would mod_qos give me, it seems that mod_evasive and mod_security are doing evrything needed?

---

### Post by DanHorniblow on 2012-02-02
I now have a new problem tho.

When I installed and configured shorewall I configured it with these rules:

```
DROP	net	fw	icmp
DROP	net	fw	tcp	pop3
DROP	net	fw	tcp	https
DROP	net	fw	tcp	mysql
DROP	net	fw	tcp	ftp
ACCEPT	net	fw	tcp	dns
ACCEPT	net	fw	tcp	imap
ACCEPT	net	fw	tcp	smtp
ACCEPT	net	fw	tcp	www
ACCEPT	net	fw	tcp	ispconfig
ACCEPT	net     fw      tcp     webmin
ACCEPT  net     fw      tcp     ssh

```

These rules are working perfectly apart from the dns one.

When domain names are pointed to my VPS with the use of the name server option from the registrar that it is hosted. My VPS will not translate the domain name unless the firewall is open.

What other ports / protocols to do I need to allow through for DNS to work properly?

Many thanks Dan

---

### Post by Dangertux on 2012-02-02
You need to open port 53 UDP as well, 53 TCP is only for zone transfers and large requests.


Hope this helps.

---

