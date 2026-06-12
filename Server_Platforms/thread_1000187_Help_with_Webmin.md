---
title: "Help with Webmin"
date: 2008-12-02
forum: Server Platforms
---

### Post by roundhay on 2008-12-02
I have installed Webmin on my server and so far have been very impressed.

I have changed the default port

I can access over my lan using [https://servername:portnumber](https://servername:portnumber) but I can't access using my host name [https://my.hostname.org:portnumber](https://my.hostname.org:portnumber)

Any idea what I need to add or update to get this to work?

There seem to be a large number of module available for download does anyone have any recommendations for useful modules?

---

### Post by Dr Small on 2008-12-02
Did you open the port on your router/firewall?

---

### Post by roundhay on 2008-12-02
I had forwarded the port but just check again (just in case) and noticed that I had not enabled it!](*,)]

---

### Post by hictio on 2008-12-02
> **roundhay said:**
> I have installed Webmin on my server and so far have been very impressed.

I have changed the default port

I can access over my lan using [https://servername:portnumber](https://servername:portnumber) but I can't access using my host name [https://my.hostname.org:portnumber](https://my.hostname.org:portnumber)

Any idea what I need to add or update to get this to work?

There seem to be a large number of module available for download does anyone have any recommendations for useful modules?

I have seeing that before on many Redhatish installs.
Do you have the necessary Perl libraries installed?
Type this at the prompt:

```

perl -e 'use Net::SSLeay'

```

If it doesn't return anything, its installed, if it spills an error, *similar* to this one:

```

Can't locate Net/SSLeay.pm in @INC (@INC contains: /System/Library/Perl/5.8.6/darwin-thread-multi-2level /System/Library/Perl/5.8.6 /Library/Perl/5.8.6/darwin-thread-multi-2level /Library/Perl/5.8.6 /Library/Perl /Network/Library/Perl/5.8.6/darwin-thread-multi-2level /Network/Library/Perl/5.8.6 /Network/Library/Perl /System/Library/Perl/Extras/5.8.6/darwin-thread-multi-2level /System/Library/Perl/Extras/5.8.6 /Library/Perl/5.8.1 .) at -e line 1.
BEGIN failed--compilation aborted at -e line 1.

```

You'll need to install that library at least (you'll also need the OpenSSL one.

Regarding modules, I like this one: [WebminStats](http://webminstats.sourceforge.net/), it needs RRD Tools.

---

### Post by trentscott4 on 2008-12-03
As far as useful modules go, I use the proftpd module (it's preinstalled and can be found either by searching in Webmin or under 'Unused Modules'.  If you run a proftpd ftp server, it allows for easy setup and maintenance of users and permissions so you don't have to muck around with messy .conf files.

Also, if you plan on offering any type of web hosting, the Virtualmin and Usermin packages may be useful.  Other than that, for my purpses at least, Webmin is great out of the box!  I run it locally (haven't opened the port on my router), just so I don't have security vulnerabilities to my server.

Good luck!

Trent

---

