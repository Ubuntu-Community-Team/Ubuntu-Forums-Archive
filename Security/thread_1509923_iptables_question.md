---
title: "iptables question"
date: 2010-06-14
forum: Security
---

### Post by mituw16 on 2010-06-14
hey all, i have a question about the function of the iptables prerouting redirect.

so i already know how to write a line in an iptables script to redirect a said pc on my LAN to any destination ip address I want.

```


#iptables -t nat -A PREROUTING -s 192.168.1.2 -j DNAT --to-destination <ip here>


```

but I was curious if anyone knew a way to replace the destination ip with an HTTP address like [www.google.com](www.google.com) or something?

---

### Post by yeleek on 2010-06-15
You could replace with a hostname, but http is a protocol so not sure why you'd want www?  or do you just want to fwd it to a named destination.  In which case try hostnames...

---

### Post by yeleek on 2010-06-15
oh and you may need something like this

[http://diginc.us/2010/05/using-iptables-with-dynamic-ip-hostnames-like-dyndns-org/](http://diginc.us/2010/05/using-iptables-with-dynamic-ip-hostnames-like-dyndns-org/)

Pay attention to 
Whenever IPTables has a hostname in a rule it looks up the hostname’s IP address and uses that instead of the actual hostname – so it’s stuck with the IP until the next time IPTables is flushed/restarted.

---

### Post by mituw16 on 2010-06-15
thanks for you reply, I'm still not sure what you mean though. I use hostnames for a lot of my rules for different comps on my LAN, but how would I put in a hostname for [www.google.com?](www.google.com?)

Like lets say for example my laptop's ip address is 192.168.1.2, how would I redirect all web traffic from my laptop to [www.google.com?](www.google.com?) (I already know how to do if i put the DNAT to google's IP address, but many website's ip addresses are virtual host on a machine, and therefore the ip is usless for this purpose.)

---

### Post by yeleek on 2010-06-15
Am confused.  IPtables supports fqdn's, and thats all google.com is, a fqdn (hostname)

Google however is likely to have a huge number of ips, so the issue i mentioned earlier appears 

'Whenever IPTables has a hostname in a rule it looks up the hostname&#8217;s IP address and uses that instead of the actual hostname &#8211; so it&#8217;s stuck with the IP until the next time IPTables is flushed/restarted.'

Look at this, this addresses the virtualhost ip issue

[http://www.linuxquestions.org/questions/linux-networking-3/iptables-fqdn-342378/](http://www.linuxquestions.org/questions/linux-networking-3/iptables-fqdn-342378/)

---

