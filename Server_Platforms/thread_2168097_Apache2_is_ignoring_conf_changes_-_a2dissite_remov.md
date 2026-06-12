---
title: "Apache2 is ignoring conf changes - a2dissite removes symlink from sites-enabled"
date: 2013-08-16
forum: Server Platforms
---

### Post by Rebajas on 2013-08-16
Hiya,

Got bit of a weird one today, hoping someone might have hit this issue before.

I'm running a bunch of sites on a Ubuntu Server 10.04 LTS. I use [FONT=Courier New]**[COLOR="#d05630"]a2ensite[/COLOR]**[/FONT] &  [FONT=Courier New]**[COLOR="#d05630"]a2dissite[/COLOR]**[/FONT] to add and remove respective confs from the site-enabled folder and that seems to be working fine; when I do [FONT=Courier New]**[COLOR="#d05630"]ls-l[/COLOR]**[/FONT] I can see the symlinks have been added or removed.

Once this has been done though the site are visible even after I have run [FONT=Courier New]**[COLOR="#d05630"]service apache2 stop/start/restart/reload[/COLOR]**[/FONT]

So basically it seems my conf settings are being cached or something - I haven't seen this behaviour before, and my way of changing the configuration hasn't changed.

Any ideas?

Thanks,


Tony.

---

### Post by Rebajas on 2013-08-16
If no-one has any idea on cause then maybe an alternative way to reload the conf files?

Any short term workaround appreciated at this stage.

Thanks.

---

### Post by koenn on 2013-08-18
you're not literally running 'service apache2 stop/start/restart/reload', are you ? You're doing something sensible like 'service apache2 restart', right ? 

apache reads its config from files in certain directories. If sites don't go offline after  they've been removed from sites-enabled, maybe ypur apache is also reading sites-available ?
maybe you want to search the config files to see what directories apache looks in.

or temporarily remove a site from 'sites-available' and see if it goes offline. if that works, you have your workaround

---

### Post by Rebajas on 2013-08-19
> **koenn said:**
> you're not literally running 'service apache2 stop/start/restart/reload', are you ? You're doing something sensible like 'service apache2 restart', right ?

Right, I ain't that stooopid ;)

> **koenn said:**
> apache reads its config from files in certain directories. If sites don't go offline after  they've been removed from sites-enabled, maybe ypur apache is also reading sites-available ?

They don't go offline after being removed from sites-enabled using [FONT=Courier New]**a2dissite**[/FONT]. But neither do they pick up changes to the confs made in sites-available - it's like they are either cached or simply not being re-read.

> **koenn said:**
> maybe you want to search the config files to see what directories apache looks in.

My conf files are in one place as far as I know, and always have. My method of updating the sites has never changed either.

> **koenn said:**
> or temporarily remove a site from 'sites-available' and see if it goes offline. if that works, you have your workaround

I'm actually trying to change the configuration of a site, the fact sites aren't going offline is like a side effect of the fact my conf files aren't being reloaded.

Thanks for your thoughts on this matter - I'm trying to get someone to do physical reboot for me. Hopefully that will help, but I'd still like t know why this has happened...


Tony.

---

### Post by SeijiSensei on 2013-08-19
When you remove a site, do you also remove its DNS entry?  Disabling a virtual host doesn't stop the server from accepting requests for the site; Apache will simply deliver the contents of the default configuration, usually the "It Works!" page.  Is that what is happening, or are you getting the site-specific content for the disabled site?   If so, did you clear your browser's cache before testing the disabled site?

---

### Post by koenn on 2013-08-19
> [QUOTE]Originally Posted by koenn
maybe you want to search the config files to see what directories apache looks in.
My conf files are in one place as far as I know, and always have. My method of updating the sites has never changed either.[/QUOTE]

what I meant is : 
apache reads 'sites-enabled'  (or other directories) if it's been told to do so, eg in /etc/apache2/apache2.conf : ```

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

```

If you or someone else made modifications to apache2.conf, maybe those are causing  sites-enabled to not being read anymore, or similar "my config changes have no effect' issues. That's why I suggested you have a look at it. A bit of a long shot, yes. but who knows ?
Browser cache is also falls in the category "obvious but worth checking", imo

---

### Post by Rebajas on 2013-08-19
> **SeijiSensei said:**
> When you remove a site, do you also remove its DNS entry? Disabling a virtual host doesn't stop the server from accepting requests for the site; Apache will simply deliver the contents of the default configuration, usually the "It Works!" page.  Is that what is happening, or are you getting the site-specific content for the disabled site?  

I only removed the site to see whether the config change was picked up - so while I appreciate the comment that's not really the problem.

**The problem is that if I make a change to a conf; such as changing the DocumentRoot, that change isn't being picked up.**

I've never had this problem before and my process for conf changes hasn't changed - as I said in the last reply, I'm hoping a reboot will fix things but would like to know if anyone else has seen this behaviour in case it doesn't fix it :\

> **SeijiSensei said:**
> If so, did you clear your browser's cache before testing the disabled site?
> **koenn said:**
> Browser cache is also falls in the category "obvious but worth checking", imo

Yup, forever clearing caches :)

---

### Post by Rebajas on 2013-08-19
> **koenn said:**
> what I meant is : 
apache reads 'sites-enabled'  (or other directories) if it's been told to do so, eg in /etc/apache2/apache2.conf : ```

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

```

Just had a look and there are no additional directories being included. There was nothing surprising in conf.d either.

> **koenn said:**
> If you or someone else made modifications to apache2.conf, maybe those are causing sites-enabled to not being read anymore, or similar "my config changes have no effect' issues. That's why I suggested you have a look at it. A bit of a long shot, yes. but who knows ?

I'm happy to try long shots at this stage :) but I can't see anything out of place in the configuration - and I'm the only admin for this particular box...


Cheers.

---

### Post by SeijiSensei on 2013-08-19
Anything of interest in /var/log/apache2/error.log, or the error logs for the virtual sites if you keep them separate?

Do these problems occur regardless of which site's configuration is changed?

I've run Apache servers for nearly fifteen years, and I can't think of a time I've had the problem you report.

You can try simulating a connection on the server itself like this:

```

$ telnet ip.of.the.server 80
[server replies]
GET / HTTP/1.1
Host: www.example.com


```

That should display the page associated with [www.example.com](www.example.com).  Note that you must hit Enter twice after the "Host" line.  If you run this from the server's command prompt, you'll be able to rule out problems in transport like proxies and caching.

---

### Post by Rebajas on 2013-08-19
> **SeijiSensei said:**
> Anything of interest in /var/log/apache2/error.log, or the error logs for the virtual sites if you keep them separate?

Apache2 logs are almost empty - I'll try to remember to paste them up here later though.

> **SeijiSensei said:**
> Do these problems occur regardless of which site's configuration is changed?

Changed a couple of DocumentRoots earlier in the week and neither site is looking in the new location. As I said in my opening post, a2ensite & a2dissite are working in that they remove the symlink but the config still behaves as if they are there! :|

> **SeijiSensei said:**
> I've run Apache servers for nearly fifteen years, and I can't think of a time I've had the problem you report.

I can't boast that sort of experience but I've been running LAMP on Ubuntu since 2005 and have never seen anything like this either. Hoping it's a glitch that will clear when the machine is rebooted; really, really hoping!

> **SeijiSensei said:**
> You can try simulating a connection on the server itself like this:

```

$ telnet ip.of.the.server 80
[server replies]
GET / HTTP/1.1
Host: www.example.com


```

Not sure if I did something wrong but using telnet to connect resulted in:

```
Escape character is '^]'.
```

Running the following:

```
GET / HTTP/1.1
Host: www.secretsauce.co.uk
```

Returns a Bad Request. The site though is accessible via a browser.

Can't try it on the server as I don't have telnet installed.

---

### Post by Rebajas on 2013-08-19
Quick question - if there is an error in a new config, does Apache2 use the last know good config or does it fall over on restart?

Wondering if I've done something when changing the Document Root... even though I've checked both those changes like 20 times!

---

### Post by Rebajas on 2013-08-20
Thanks for all your help guys.

I found the issue - in desperation I went through all my confs and found a file with duplicate settings for one of the sites I'd changed the other day. Goodness knows where it came from but I'm glad it's found!

All is now well, though I may just go through the rest and make sure they are all okay...

---

