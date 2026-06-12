---
title: "[SOLVED] PTR Record"
date: 2007-11-13
forum: Server Platforms
---

### Post by kmac on 2007-11-13
i think the problem with my webserver is that it is associating my virtual hosts with the wrong ip.

long story -- shortened:

originally i thought my ip address was static, so i configured my account on everydns to a static ip, we'll call it 
```

my.old.ip.add

```

Then i found out it was dynamic, so i reconfigured everydns to match it as such. doing a lookup of the ip on mydomain.com through another website service, it returned my current dynamic ip.

however, starting apache, i get the infamous: 
```


apache2: apr_sockaddr_info_get() failed for myhostname
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

after seeing this, i run nslookup and get:
```

nslookup mydomain.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   mydomain.com
Address: my.old.ip.addr

```

1) is the error and this response associated?

2) if so, can i edit the PTR record?

3) ...ok i just ran nslookup again and now it shows my current dynamic ip, but i still get the error message when restarting apache... 

any help would be grand


--Kyle

---

### Post by MJN on 2007-11-14
The PTR record belongs to whoever owns your IP (likely your ISP), however it's not what's needed in this case so it by the by.
 
The Apache 'error' (more of a warning) is because it tried to lookup the IP address of whatever is in your /etc/hostname and failed - it does this to determine who 'it' is as this is necessary for various aspects of web server operation.
 
The solution is to add your hostname to the 127.0.0.1 line in /etc/hosts - next time it does a lookup it will succeed and it will know 'it' is 127.0.0.1.
 
Furthermore, it is worthwhile adding a **ServerName <website name>** (and, optionally, **ServerAlias <aliases such as without the www prefix)**) to the <Virtualhost> container that contains your site config to identify unambiguously what your site is (this is critical should you start hosting multiple virtual sites on the same machine).
 
If you need anything explaining further just shout.
 
Mathew

---

### Post by kmac on 2007-11-14
well i am running multiple virtual hosts and my /etc/hosts file reads:

```

127.0.0.1 localhost domain1.com domain2.com domain3.com
127.0.1.1 my.HOSTNAME

```

and my virtual host (all are alike w/ different domain names and docroots)

```

NameVirtualHost *
<Virtual Host *>
  ServerName domain.com
  ServerAlias domain.com *.domain.com
  
----snip------


```

i don't get it cus everything is by the book word for word... some even copied and pasted from apache docs (obviously modified to my preferences.)

I think there's something else...

--Kyle

---

### Post by MJN on 2007-11-14
Obfuscating your domain names makes it a right pain in the proverbial to diagnose the fault as the problem could quite easily be a typo or omission of a data item in a location.
 
Is there a reason you're keeping it secret? If not, post the real data and we can take it from there.
 
Fo example, you say the error mentioned 'myhostname' yet your hosts file only contains 'my.hostname'. And you have a ServerName of 'domain.com' yet no 'domain.com' in your hosts file. Are these mistakes reflections of your true config or copy-and-paste mishaps? I trust you understand my reluctance to chase potential red herrings...
 
Mathew
 
P.S. I take it you have enabled the virtual sites (and hence their config is being parsed)?

---

### Post by kmac on 2007-11-14
I'm not at home now, so i can't actually copy and paste from my server. but i will do when i get home tonight. and yes, the sites are definately enabled...

thanks, i'll probably be posting again tonight btwn 9 and 10pm eastern time.

Thanks for your help, and before i post i'll dblcheck for typos, errors, etc.

--Kyle

---

### Post by kmac on 2007-11-14
i spoke with a professor at a nearby college and he told me the that the errror doesn't mean much. i explained to him that my sites were accessible from the server itself and by nobody else (not even within my own network!). He told me to double check firewalls and my port forwarding on my router.

sure 'nuff... there was a typo in my port forwarding on my router... sending requests to 192.168.1.8 instead of ....1.6.

4 days.... 4 days of trying to figure this out and it was indeed a typo. i'm going to finally go to bed on time tonight.

thanks to all who helped, even my unnamed alaskan friend

--Kyle

---

