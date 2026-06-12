---
title: "web server migration .. want to test by changing /etc/hosts ... not working"
date: 2010-11-12
forum: Server Platforms
---

### Post by NathanScrivener on 2010-11-12
Hi, I'm not 100% sure if this is the right category to post in, but figure it's close enough ? 

I am moving some websites from a shared host to a newly configured Xen based VPS with Ubuntu 10.04. A steep learning curve but I am getting there!

I have a couple of sites installed on the new server and want to test them out, from what I understand I should be able to edit /etc/hosts on my desktop computer (running Ubuntu 10.04) which should automatically redirect my browser to the new server. But it doesn't seem to work.

This is what I appended to the /etc/hosts file:

12.34.56.78       [www.xxxx.com](www.xxxx.com)

I thought that this should send any requests for [www.xxxx.com](www.xxxx.com) to 12.34.56.78? 

Some googling indicated that the browsers I am using may be using DNS caching, ignoring the hosts file. I've tried clearing the cache with Chromium 7.0.517.44 (64615) and Firefox 3.6.12, and even installed a plugin in Firefox to block DNS caching. 

No luck.

Any help would be much appreciated. 

Thanks

---

### Post by wongo888 on 2010-11-12
Try pinging the new host. Changes to the hosts file happen instantly.

```
$ ping www.xxxx.com
```

If you see your IP there, then maybe your apps are caching the old info. Perhaps a reboot is in order?

---

### Post by NathanScrivener on 2010-11-12
tried that ... ping displays the desired ip, have rebooted too.

---

### Post by wongo888 on 2010-11-12
My guess is that your browser is doing a DNS search before checking your hosts file. 

You might want to do the following checks for completeness:

```
$ cat /etc/nsswitch.conf | grep "hosts"
hosts:          files dns
```


```
$ cat /etc/host.conf | grep "hosts"
order hosts,bind
```

If both of those are similar then you should check for others having this problem on Chrome and FF support forums. I'm out of ideas.

---

### Post by Ryan Dwyer on 2010-11-13
What makes you think your hosts file change isn't working? If all is good you won't notice any change at all when you browse to the host.

---

### Post by NathanScrivener on 2010-11-13
> **wongo888 said:**
> My guess is that your browser is doing a DNS search before checking your hosts file. 

You might want to do the following checks for completeness:

```
$ cat /etc/nsswitch.conf | grep "hosts"
hosts:          files dns
```


```
$ cat /etc/host.conf | grep "hosts"
order hosts,bind
```

If both of those are similar then you should check for others having this problem on Chrome and FF support forums. I'm out of ideas.


The first, /etc/nsswitch.conf displays the following:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

The second, /etc/host.conf displays the following:

order hosts,bind

> What makes you think your hosts file change isn't working? If all is good you won't notice any change at all when you browse to the host

I guess there are any number of ways to determine this, in my case I have moved the website files to a different folder, which should create a 404 error if you attempt to browse to the site with a /etc/hosts redirection to the new server.

If anybody else has any ideas I would be grateful to hear them. Thanks.

---

### Post by wongo888 on 2010-11-13
I did a test on one of my Ubuntu servers by installing elinks and I managed to redirect [www.google.com](www.google.com) in the following manner:

Add to /etc/hosts:

```
192.168.0.10 www.google.com

```

That's my Mac laptop running Apache2 at that IP. On the Ubuntu server try to open Google in elinks:

```
$ elinks www.google.com
```

Reveals the expected page served by my Mac and not Google.

Granted that elinks is not Chrome, but it is a web browser. There is a support thread here with a diagnostics procedure:

[http://www.google.com/support/forum/p/Chrome/thread?tid=292fbe1492ac3e1a&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=292fbe1492ac3e1a&hl=en)

Apparently, some people are running into issues when using Google Web Accelerator. I don't have any machines running Ubuntu desktop to try this out on Chrome/FF.

---

### Post by NathanScrivener on 2010-11-13
thanks for that ... elinks is a nifty little program!

I thought to try a couple of tests, to see if I could narrow this problem down a bit.

As I have apache2 running on my local machine, I set up a hosts entry for a domain name to redirect to the local IP. This works, no problem, which is consistent with your test.

Then I tried another external IP address and another domain, and I run into the same problem as before.

So - 1. Hosts entries relating to the local network OK
2. Hosts entries relating to the internet - seem to be ignored or are failing for some reason.

---

### Post by wongo888 on 2010-11-13
I tried redirecting [www.google.com](www.google.com) to one of my CentOS boxes in Edmonton, AB, Canada. I added the follwing to my /etc/hosts:

```
199.96.28.240 www.google.com
```

Once again the browser worked as expected.

---

### Post by NathanScrivener on 2010-11-13
This is doing my head in! 

I tried your entry, and successfully redirected to your CentOS box.

Here's my actual server IP and website name:

My server IP is: 173.255.216.228
The FQDN is [www.divineanswers.com](www.divineanswers.com)

/etc/hosts has:
173.255.216.228 [www.divineanswers.com](www.divineanswers.com) divineanswers.com

If I type in the IP address, I get an index listing. (I have removed all files except placeholder file for the time being so it is obvious whether it is working or not). 

If I type in the FQDN, I get the working website, which means it has got to be still going to the old host. 
:confused::confused::confused:

---

### Post by wongo888 on 2010-11-13
That's very strange for sure. I put the following in my /etc/hosts file:

```
173.255.216.228 www.divineanswers.com divineanswers.com

```

I started up elinks again and it displayed your webroot as you said it would (pic attached).

For a lark, I also changed the hosts file on my Mac and it also works in both latest mac Chrome and FF3.6. I'm not sure of the diff in the dns host resolver in Chrome across platforms though. Chrome DNS internals shows the right IP.

If you're sure that you're not going through a proxy and not viewing a cached page, then I'm at a loss too.

---

### Post by NathanScrivener on 2010-11-13
> If you're sure that you're not going through a proxy and not viewing a cached page, then I'm at a loss too.

Well I'm not sure ... a quick google reveals my ISP has introduced a transparent proxy. Could this be related?

[EDIT] [http://www.geekzone.co.nz/forums.asp?forumid=39&topicid=66599](http://www.geekzone.co.nz/forums.asp?forumid=39&topicid=66599) ... I don't think I'm the only one having this problem.

---

### Post by wongo888 on 2010-11-13
It may be related. Since you are a paying customer, you might want to call customer support.

---

### Post by NathanScrivener on 2010-11-13
Yep, Telecom NZ (Xtra) have confirmed this as an issue. In order to solve, they are placing us on a static IP so that we can be added to their proxy bypass list. 

Thank you very much again for your help.

---

