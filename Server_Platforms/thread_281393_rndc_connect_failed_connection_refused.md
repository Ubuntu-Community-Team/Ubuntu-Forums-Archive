---
title: "rndc: connect failed: connection refused"
date: 2006-10-21
forum: Server Platforms
---

### Post by fouressence on 2006-10-21
Hi,

I have a vps server running Ubuntu 6.06, and I'm trying to set up bind9 on it.  I've run into the problem of, when I type either "rndc start" or "/etc/init.d/bind9 restart" I get the error "rndc: connect failed: connection refused"

I used rndc-confgen to generate rndc.conf, and I copied that appropriate lines from it into named.com.  Here's my rndc.conf:

key "rndc-key" {
    algorithm hmac-md5;
    secret [hidden];
};

options {
    default-key "rndc-key";
    default-server 127.0.0.1;
    default-port 953;
};


And here's the part of my named.conf that I got from rndc-confgen:


key "rndc-key" {
    algorithm hmac-md5;
    secret [hidden];
};

controls {
    inet * port 953 allow { any; } keys { "rndc-key"; };
};


Both rndc.conf and named.conf are located in /etc/bind/


I've done quite a bit of searching on this problem, but haven't been able to find a solution that works.  Any ideas?

Thanks!
-=Derek

---

### Post by twistedtwig on 2006-10-21
this may not be the answer but i have been getting this as well.  what i found was that it was when i had other errors in my files.  i used named -g -p 53 which showed some of them.  i also looked though the var/log/daemon.log to see what other errors there were.  it seemed to be that i had a miss type of some sort and when i fixed it and restarted bind the error went away.  that or a permissions error.

hope this helps

Twiggy

---

### Post by unless on 2006-10-28
I had the same problem on a Debian server this week. As you probably noticed when Googling, there are a lot of different things that could cause this problem.

The first thing to check is whether or not named is listening on the port that rndc uses to talk to it: tcp 953

```
netstat -paln | grep 953
```

should return a line showing named is listening.

The problem on my DNS server was just that: Nothing was listening on port 953. In /var/log/daemon, I was seeing:

```
named[7030]: couldn't add command channel 127.0.0.1#953: file not found
```

What worked for me was to copy the *key "rndc-key" {...}* clause from rndc.conf and paste it into a file called */etc/bind/rndc.key*, rather than placing it directly in named.conf. 

rndc.key is read by named, and rndc.conf is read by rndc.

HTH.

---

### Post by Ubimad on 2007-05-20
One stupid ";" was missing in my named.conf that made me last time reinstall BIND new. This time thanks nano /var/log/daemon.log I found it.
Strange it worked for months without that *;*

May 20 11:25:47 server01 named[3464]: starting BIND 9.3.2 -u bind -t /var/lib/named
May 20 11:25:47 server01 named[3464]: found 1 CPU, using 1 worker thread
May 20 11:25:47 server01 named[3464]: loading configuration from '/etc/bind/named.conf'
May 20 11:25:47 server01 named[3464]: /etc/bind/named.conf:15: missing ';' before '}'
May 20 11:25:47 server01 named[3464]: loading configuration: failure
May 20 11:25:47 server01 named[3464]: exiting (due to fatal error)

---

### Post by mpadams on 2007-05-30
Another thing to watch out for is if you're using views: you'll have to go make sure all your zones are in views (including the default zones in resolv.conf) if you use them even once. I have my view for my default zones setup in a "default" zone with the "match-clients {any;};" parameter.

---

### Post by zaazu48 on 2007-08-31
Hello Fouressence,

how are u?

I was having the same problem, but I was able to fix mine. as I parsed this command

"named -g -p 53" and it spilled these errors on screen

sudo named -g -p 53
31-Aug-2007 11:41:02.309 starting BIND 9.3.2 -g -p 53
31-Aug-2007 11:41:02.314 found 1 CPU, using 1 worker thread
31-Aug-2007 11:41:02.328 loading configuration from '/etc/bind/named.conf'
31-Aug-2007 11:41:02.332 /etc/bind/named.conf.options:18: unknown option '192.168.0.1'
31-Aug-2007 11:41:02.337 loading configuration: failure
31-Aug-2007 11:41:02.339 exiting (due to fatal error)

and from the above, I think the problem is with my forwarder option. try removing it and see.

---

### Post by amitbiswas on 2007-09-18
Hi there,
Check whether you have uncomment the 
forwarders {
                192.168.0.1;
 };
Hope this fix your prob. Cheers. amit

---

### Post by phpcitizen on 2008-06-24
Mostly it is a typo.

Mine was an extra space in the end of the file:

> /var/lib/named/etc/bind/named.conf.options

---

