---
title: "problems resolving hosts"
date: 2007-12-27
forum: Server Platforms
---

### Post by gquant on 2007-12-27
Hello,

(apologies of this the wrong forum) 
I have suddenly a very odd problem with a LAMP server running Gutsy.
Without warning it just stopped resolving named hosts.  There has been no change in any configuration (that I know of), and the DNS servers used by the server are the same that I use on my desktop machine and I have seen so problems there.

Does anyone have any idea about how to proceed?
many thanks in advance :confused:
(oh I should add, I am quite new to ubuntu server)

---

### Post by bmathis on 2007-12-28
I've seen this happen when someone installs Postfix which also installs resolvconf. To fix this use nano to edit **/etc/resolvonf/resolv.conf.d/base** and add the following, save, and exit the file
```

search localhost
nameserver xxx.xxx.xxx.xxx (whatever your router ip address is)
nameserver xxx.xxx.xxx.xxx (a secondary DNS server - optional)
```

Use the following command to update resolv.conf```
sudo resolvconf -u
```

Now restart the networking process and everything should be golden!
```
sudo /etc/init.d/networking restart
```

---

### Post by HermanAB on 2007-12-28
Hmm, in my experience, resolvconf is pure evil and I always kill it whenever I see it.  To my mind, it causes problems and doesn't doesn't do anything useful.

Just my tuppence worth.

Herman

---

### Post by GigaVolt on 2007-12-28
See hear:

dancho@thoth:~ > cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 thoth thoth.gigavolt-bg.net

87.120.40.168   test.dancho [www.test.dancho](www.test.dancho) bulengco.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by GigaVolt on 2007-12-28
btw What is DNS caching?
[http://www.lowcostnames.co.uk/faq/faqc11q115.html](http://www.lowcostnames.co.uk/faq/faqc11q115.html)

---

