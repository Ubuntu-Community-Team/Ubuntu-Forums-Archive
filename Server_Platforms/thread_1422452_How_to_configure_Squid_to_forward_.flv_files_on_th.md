---
title: "How to configure Squid to forward .flv files on the fly?"
date: 2010-03-05
forum: Server Platforms
---

### Post by sikander3786 on 2010-03-05
Hello community!

I am using Squid Proxy Server alongwith Dansguardian, dhcp3 and ClamAV on my local network. Everything is working fine except for .flv files like [www.youtube.com](www.youtube.com). The problem is that Squid wants to download the whole .flv file first to its cache and then serve it to the client.

It has an advantage that the whole video loads at once on the client's browser but that is not what our users want.

What they want is that these files load on the fly as they do on a normal internet connection. How do I configure squid to serve .flv files on the fly to the client PCs?

Regards.

Sikander.

---

### Post by Barriehie on 2010-03-05
Try the always_direct directive.  The docs and a few examples are [here](http://www.squid-cache.org/Doc/config/always_direct/).

HTH,
Barrie

---

### Post by sikander3786 on 2010-03-06
> **Barriehie said:**
> Try the always_direct directive.  The docs and a few examples are [here](http://www.squid-cache.org/Doc/config/always_direct/).

HTH,
Barrie

Thanks for the reply.

I have looked at your link and have google "always_direct directive" but couldn't get it working. Actually I am new at squid. Can you kindly give some examples about streaming all the .flv files or will I have to add all the web addresses manually as the page you linked states?

Regards.

---

### Post by Barriehie on 2010-03-06
> **sikander3786 said:**
> Thanks for the reply.

I have looked at your link and have google "always_direct directive" but couldn't get it working. Actually I am new at squid. Can you kindly give some examples about streaming all the .flv files or will I have to add all the web addresses manually as the page you linked states?

Regards.

Don't know what problem you're having.  It worked on this end when I man an acl with [www.youtube.com](www.youtube.com) in it and then:
```

acl **acl_name** dstdomain "**path/acl_name**"
always_direct allow **acl_name**

```

---

### Post by sikander3786 on 2010-03-08
> **Barriehie said:**
> Don't know what problem you're having.  It worked on this end when I man an acl with [www.youtube.com](www.youtube.com) in it and then:
```

acl **acl_name** dstdomain "**path/acl_name**"
always_direct allow **acl_name**

```

I've added the following line to squid.conf but it didn't work.

```

acl youtube dstdomain www.youtube.com
always_direct allow youtube

```

What do you think is going bad?

---

### Post by Barriehie on 2010-03-08
What does your log file say???

---

### Post by sikander3786 on 2010-03-08
> **Barriehie said:**
> What does your log file say???

It states

1268071910.250 204870 127.0.0.1 TCP_MISS/200 5693601 GET [http://v13.lscache4.c.youtube.com/videoplayback?](http://v13.lscache4.c.youtube.com/videoplayback?) - DIRECT/74.125.101.29 video/x-flv

Is this what you were asking for?

---

### Post by Barriehie on 2010-03-08
> **sikander3786 said:**
> I've added the following line to squid.conf but it didn't work.

```

acl youtube dstdomain www.youtube.com
always_direct allow youtube

```What do you think is going bad?

Where you have [www.youtube.com]("http://www.youtube.com") has to be enclosed in quotes and a full path, i.e. my acl's are in ~/squid so I've got:
```

acl blacklist-domains dstdomain "/home/barrie/squid/domains"

```For the sake of readability I would change the acl name to my-always-direct or something indicative of what you're doing; might make it easier a year from now when you choose to change something!

---

### Post by sikander3786 on 2010-03-09
Thanks a lot buddy. That worked like a charm.

Now I can add all the website addresses in /home/malik/squid/domains file and they will follow always_direct rule.

Thank you.

---

### Post by Barriehie on 2010-03-09
Glad you got it working!

---

