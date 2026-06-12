---
title: "Reliable, repeatable way to get abuse email for a given IP"
date: 2012-01-16
forum: Server Platforms
---

### Post by jobsonandrew on 2012-01-16
Hi All,
I have a home server that gets SSH dictionary attacked several times a day.

I've implemented Fail2Ban which works great, and emails me the output of whois for the given offender.

Ideally I'd like to capture an attacking IP and automatically email the owning provider's abuse address, with details. The problem is that the output from whois is totally non-standard.

Does anyone know of any way to get the abuse email for a given IP without writing an unreliable parser for every possible whois format?

Cheers

---

### Post by Habitual on 2012-01-16
I usually whois the IP and get the Abuse@ identifier.
but I haven't ever tried automating such a tedious task.

---

### Post by jobsonandrew on 2012-01-16
Hmm, yeah you could grep the output of whois for 'abuse@'

Looking back at a few whois reports that would work maybe half the time, if not more, which could be useful...

It would be good if anyone knew of a whois webservice where you could query for specific information..?

---

### Post by SeijiSensei on 2012-01-16
You do realize that the probability anyone will respond to these notices approaches zero?  I only ever notify legitimate domain holders when I get spams that spoof their domains in the From address.  I've even given up on this practice because such notices largely fall on deaf ears.

Often the person from whose IP these attacks originate has no idea what's going on.  They've been "pwned" and a proxy set up on their machine through which the attacks are directed.

---

### Post by hackertarget on 2012-01-16
By far the majority of ssh brute force attacks are performed by automated bots / scripts on compromised servers. As mentioned you will be lucky to get a response from most IP block owners regarding these.

A good option that will improve your security and stop your logs filling up with failed logins, is to move the ssh port to a different port other than port 22.

---

### Post by CharlesA on 2012-01-16
> **hackertarget said:**
> 
A good option that will improve your security and stop your logs filling up with failed logins, is to move the ssh port to a different port other than port 22.

That would help reduce "log spam," but it doesn't do much for security because if someone wanted to get in, they'd just do a port scan to see if any exploitable services are running.

My logs look fairly clean but I have a rule that drops traffic from an ip address if it makes 3 connection attempts in a minute. Helps cut down on the clutter for me.

---

### Post by hackertarget on 2012-01-16
> That would help reduce "log spam," but it doesn't do much for security because if someone wanted to get in, they'd just do a port scan to see if any exploitable services are running

You are correct in that security by obscurity is no solution; I was referring to the fact that if you have bots hitting you all day long your security will be improved by moving the port.

Of course you still need strong passwords / key based authentication and system monitoring in place.

By moving the ssh port to a different port number, you will cut down automated attacks by 99%. Then if you do get alerted on failed logins (with ossec or some other monitoring script) you will be more conscious that perhaps this is an attacker trying to break into my system rather than a script that is scanning half the Internet. :)

---

### Post by CharlesA on 2012-01-16
> **hackertarget said:**
> You are correct in that security by obscurity is no solution; I was referring to the fact that if you have bots hitting you all day long your security will be improved by moving the port.

Of course you still need strong passwords / key based authentication and system monitoring in place.

By moving the ssh port to a different port number, you will cut down automated attacks by 99%. Then if you do get alerted on failed logins (with ossec or some other monitoring script) you will be more conscious that perhaps this is an attacker trying to break into my system rather than a script that is scanning half the Internet. :)

Indeed. Still helps to know what to look for. ;-)

---

### Post by jobsonandrew on 2012-01-17
> By moving the ssh port to a different port number, you will cut down automated attacks by 99%.
Yeah I've seen that moving the port pretty much stops attacks.

However, I'm usually connecting from places that only allow port 22 outbound :-/ so changing the port makes it pretty much unreachable most of the time (and that's nothing to do with my local NAT/network configuration)

Indeed strong passwords and accounts with no remote logins are essential, but responding to endless failed logins is work I'd rather not have the machine do.

I've noticed Fail2Ban includes 'complain.conf' which appears do do something I've thought about writing.. So seeing as it's already been written I might read up/turn it on and see if I get any responses (though I agree that's unlikely).

Back to the original question, though, does anyone know of a more 'parseable' (that is now a word) version of whois?

Thanks

---

### Post by hackertarget on 2012-01-17
> Back to the original question, though, does anyone know of a more 'parseable' (that is now a word) version of whois?

I have been meaning to take a look at pywhois and if it works out I may add it to the [ip tools]("http://hackertarget.com/ip-tools/") page @hackertarget

Looks like it can parse the email addresses quite easily.

[http://code.google.com/p/pywhois](http://code.google.com/p/pywhois)

Correction - looks like it can only parse domains not IP's.

---

