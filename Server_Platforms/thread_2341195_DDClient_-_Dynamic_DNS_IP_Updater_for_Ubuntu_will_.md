---
title: "DDClient - Dynamic DNS IP Updater for Ubuntu will this work on Ubuntu Server?"
date: 2016-10-25
forum: Server Platforms
---

### Post by Lukasz Tarkowski on 2016-10-25
DDClient - Dynamic DNS IP Updater for Ubuntu,  will this work on Ubuntu Server? I have a text version of Ubuntu Server.  I am just trying to make it easier for myself

---

### Post by cariboo on 2016-10-26
You'll probably get better and quicker help here.

---

### Post by darkod on 2016-10-26
Can something like this help you?
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

You need to check the dynamic dns provider if they have recommendation of software/package to use. Start there... Then look for config instructions for that specific software. Usually there will be plenty on the internet.

---

### Post by Lukasz Tarkowski on 2016-10-26
Thanks guys this will help a great deal I read the Instructions as well.  I will work on this Thursday when I get back.  I have been having trouble with Ubuntu Server I will solve it :)

---

### Post by Lukasz Tarkowski on 2016-10-27
Hi Guys does this work and can you see my Apache It works page?
Here is the link.  So is it working?
[http://lukestechsite.dynu.com/]("http://lukestechsite.dynu.com/")

---

### Post by Lukasz Tarkowski on 2016-10-28
Hey Guys so is the link above working?

---

### Post by bearlake on 2016-10-28
sorry, seeing this.

Firefox can&#8217;t establish a connection to the server at lukestechsite.dynu.com.

---

### Post by Lukasz Tarkowski on 2016-10-28
hmm how can I fix this?

---

### Post by darkod on 2016-10-28
Hmm, that doesn't even return a public IP:
```
darko@nuc6:~$ dig luketechsite.dynu.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> luketechsite.dynu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31386
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;luketechsite.dynu.com.		IN	A


;; AUTHORITY SECTION:
dynu.com.		89	IN	SOA	ns1.dynu.com. administrator.dynu.com. 366031070 900 600 86400 90


;; Query time: 48 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Fri Oct 28 19:31:48 CEST 2016
;; MSG SIZE  rcvd: 104
```

It seems that the dynamic client is not working at all.

Also, on the router in front of the server, did you forward port 80 and allowed it in the firewall (if necessary)? You know you need to do that, right?

But in this case it looks more like the dynamic client not working so there is no A record linked to your URL.

---

### Post by Lukasz Tarkowski on 2016-10-28
How do I port forward port 80?  I am using a powerline linksys

---

### Post by darkod on 2016-10-28
You can probably find more precise info on google with the model number. I don't know where exactly it would be. Look around... And don't forget to check out the A record issue.

Always test first either with dig or nslookup. That should return the public IP of the router.

---

### Post by Lukasz Tarkowski on 2016-10-28
So the problem is I can see my Apache it works page but the world can't

---

### Post by darkod on 2016-10-28
You can see it from where? If you can see it only from your local network, it doesn't count. Like you say, all the world needs to see it, it needs to be available from the internet.

---

### Post by Lukasz Tarkowski on 2016-10-28
How do I make the world see it?

---

### Post by darkod on 2016-10-28
1. Check the dynamic dns client setup. Something is wrong because the result is a private IP. The nslookup result has to be your router public IP.
```
darko@nuc6:~$ nslookup lukestechsite.dynu.com
Server:        8.8.8.8
Address:    8.8.8.8#53


Non-authoritative answer:
Name:    lukestechsite.dynu.com
Address: 192.168.0.26
```
192.168.0.26 is a private IP that no one can find over the internet. The output has to be a public one.

2. Forward tco port 80 on your router to your server private IP.

That should be enough.

---

### Post by Lukasz Tarkowski on 2016-10-28
So yes you are right it is on private ip how do I set my network to public, sometimes it asks me to set network to private or public. Its somewhere i  Network Connections,  In Control Panel.  I don'yt know how to set private to 80 port

---

### Post by Lukasz Tarkowski on 2016-10-28
I set my ip to public  didn't work,  so I need to set private to 80 I don't know how

---

### Post by dudumomo on 2016-10-29
Hi Lukasz,

I'm not familiar with your powerline linksys, but you need to go to its admin panel and create a forwarding rule. (Port 80, to your local IP 192.168.x.xxx)

Then, you need to make sure DDClient is well configured to provide the right IP to your registrar.
You should be able to check directly in your registrar, see if the IP associated with your domain name, match your real public IP that you can get here: [http://www.my-ip-address.net/](http://www.my-ip-address.net/)
If it doesn't match, you will need to update your ddclient conf. May be this other tutorial could help: [http://freedif.org/host-a-server-on-a-dynamic-ip-with-an-ovh-and-similar-domain-name/](http://freedif.org/host-a-server-on-a-dynamic-ip-with-an-ovh-and-similar-domain-name/)

Good luck !

---

