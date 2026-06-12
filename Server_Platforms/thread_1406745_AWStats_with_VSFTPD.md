---
title: "AWStats with VSFTPD"
date: 2010-02-14
forum: Server Platforms
---

### Post by ack.inc on 2010-02-14
Hi! I'm trying to set awstats up to read VSFTPD's logs. I've done every step mentioned here : [http://awstats.sourceforge.net/docs/...s_faq.html#FTP]("http://awstats.sourceforge.net/docs/awstats_faq.html#FTP"), except for the last statement that reads "Now you can use AWStats as usual (run the update process and read statistics)."

I'm flabbergasted...How do I "run the update process"?

I don't have any directories that read "wwwroot" or "cgi-bin" nor can I find a "awstats.pl" script anywhere...

Please help!

---

### Post by FuturePilot on 2010-02-14
wwwroot usually just refers to the root directory of the webserver. Ubuntu uses /var/www by default. cgi-bin is an alias to /usr/lib/cgi-bin. To access awstats you will want to put
```
http://example.com/cgi-bin/awstats.pl
```
in your browser.
Of course replacing example.com with your domain.

---

### Post by ack.inc on 2010-02-15
First off, thanks for the quick reply! I've checked my /usr/lib/cgi-bin directory, and (to my surprise) found awstats.pl there.

But trying to navigate to [ftp://localhost/cgi-bin/awstats.pl](ftp://localhost/cgi-bin/awstats.pl) returns a "550 failed to change directory" error.

---

### Post by FuturePilot on 2010-02-15
> **ack.inc said:**
> First off, thanks for the quick reply! I've checked my /usr/lib/cgi-bin directory, and (to my surprise) found awstats.pl there.

But trying to navigate to [ftp://localhost/cgi-bin/awstats.pl](ftp://localhost/cgi-bin/awstats.pl) returns a "550 failed to change directory" error.

You cannot view awstats via FTP. Try http:// instead of ftp://

---

### Post by ack.inc on 2010-02-16
Yikes, I should've known. Thanks for your assistance so far!

Just one teeny problem left... the configuration, etc. is all done, but trying to navigate to:

[U][http://localhost/awstats/awstats.pl?config=ftp](http://localhost/awstats/awstats.pl?config=ftp)
[/U]
results in:

[COLOR=#880000] Error: SiteDomain parameter not defined in your config/domain file. You must edit it for using this version of AWStats. [/COLOR]

And I'm out of ideas...

---

### Post by MikeFlint on 2011-06-14
Are you still having this problem?  

I've been playing with awstats recently and this error means that awstats.pl can't find the SiteDomain parameter in your config file. 

But in my experience it's not that it can't find it, it's usually that it can't open the .conf file ... so check the user you are running awstats under has read access to the .conf file you are specifying - in your case /etc/awstats/awstats.ftp.conf

---

