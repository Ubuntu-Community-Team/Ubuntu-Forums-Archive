---
title: "subversion server problem"
date: 2010-10-11
forum: Server Platforms
---

### Post by blwizard on 2010-10-11
Hello guys, I followed the guide strictly from here: [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion) to set up a subversion server using apache. However, since my server is behind a uni proxy and only ports above 9000 are usable from outside, so I made some changes to apache settings to allow the use of port 9008.

Here is the contents a couple of files that I think are worth putting out.

/etc/apache2/ports.conf
```

NameVirtualHost *:80
Listen 80
NameVirtualHost *:9008
Listen 9008

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

And the first line of /etc/apache2/sites-enabled/000-default is:
```

<VirtualHost *:80 *:9008>

```

When I run svn checkout it shows me this message:
```

svn: OPTIONS of 'http://lisa.cs.mu.oz.au:9008/svn/thesis': 200 OK (http://lisa.cs.mu.oz.au:9008)
```

So what is actually going on?

---

### Post by Zanthir on 2010-10-11
> So what is actually going on?

That's kind of a vague question.

It looks like you're just listening to port 9008 for your subversion service.

I'm not sure I understand the question though. Is your subversion server running? The title says there is a problem. I don't feel like you described the problem. One thing you can do (I just learned this "magic code" today) is look at the output of this. ```
netstat -an | grep "LISTEN "
```It shows your open ports on your server (grep gets the lines that tell your server to listen, gives those to netstat via a pipe, and netstat displays the data about hose).

You can see if you are successfully listening on port 9008, or if the error is getting subversion to open that port.

Good luck, and with more information about your problem, you should be able to get even better support.

---

### Post by blwizard on 2010-10-11
Thanks Zanthir, my apache server is listening to port 9008:

```

$ netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:9008            0.0.0.0:*               LISTEN 
...
...

```

And this shows svnserve is running:
```

$ ps aux | grep svnserv
root      4213  0.0  0.0  11420   936 ?        Ss   16:40   0:00 svnserve -d

```

I don't know what other information would be help me get better help.

---

### Post by HermanAB on 2010-10-11
Howdy,

You can also debug network issues with good old telnet:

$ telnet serveripaddress 9008

You should get the SVN banner.

---

