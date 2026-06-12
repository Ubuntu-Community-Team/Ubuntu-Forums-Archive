---
title: "Ubuntu Server + Webmin...need some help with a few basic things..."
date: 2013-04-29
forum: Server Platforms
---

### Post by icebox83 on 2013-04-29
Brand new to Linux administration and so far have accomplished (with full understanding) the following:

 - Installed Ubuntu Server in a virtual appliance utilizing bridged networking
 - Installed Webmin
 - Forwarded appropriate ports on router for SSH & HTTP
 - SSH via Terminal on Mac
 - Installed phpMyAdmin

I need help figuring out (and understanding) the following, be it with or without the use of Webmin:

 - Securing my server if necessary. I won't be hosting anything major, just a dozen or so WordPress sites that see a couple hundred hits a month.
 - Figuring out how users work. For example, do I use root? Do I use the user I created when installing Server?
 - How exactly do I set up Virtual Hosts? I've found different sets of directions online...
 - Where do I or should I located web resources? E.g. user01/public_hml, www/site01, etc.? Separate user folders vs. all sites under www?
 - How can I set up permissions so that I can modify appropriate files via sFTP?

I think that just about covers it for now. Thanks in advance!

---

### Post by CharlesA on 2013-04-29
Read the basic security link in my signature.

1. Lock down SSH and depending on what web server you are using, look into locking it down too.
2. Why Webmin? Are you allowing it access to the outside world?
4. Is phpmyadmin accessible from outside the local network?

As far as users work, I create one main user and then either su to root or use sudo depending on how the machine is configured. If you installed Ubuntu, you can just use the user created during installation and run commands as root via sudo.

Since you mentioned virtualhosts, I assume you are going to be using Apache and not Nginx. Did you read the [server guide]("https://help.ubuntu.com/12.04/serverguide/index.html")? 

Where you serve your web sites from is up to you. I usually either stick to putting them in /var/www/somesite.com or /webroot/somesite.com

---

### Post by icebox83 on 2013-04-29
> **CharlesA said:**
> Read the basic security link in my signature.

1. Lock down SSH and depending on what web server you are using, look into locking it down too.
2. Why Webmin? Are you allowing it access to the outside world?
4. Is phpmyadmin accessible from outside the local network?

As far as users work, I create one main user and then either su to root or use sudo depending on how the machine is configured. If you installed Ubuntu, you can just use the user created during installation and run commands as root via sudo.

Since you mentioned virtualhosts, I assume you are going to be using Apache and not Nginx. Did you read the [server guide]("https://help.ubuntu.com/12.04/serverguide/index.html")? 

Where you serve your web sites from is up to you. I usually either stick to putting them in /var/www/somesite.com or /webroot/somesite.com

Thanks! I just read through the guide a couple times.

1. What specifically do you mean when you say lock down SSH and Apache?
2. I like Webmin because currently - two days into Linux administration - I'm getting lost amongst some of the command line stuff. As of right now access is local only.
3. phpMyAdmin is local only at present.

Thanks for the Server Guide link. Going through that next. Any additional notable guides, tips, tricks, etc. appreciated.

---

### Post by CharlesA on 2013-04-29
Look at the SSH page here: [https://help.ubuntu.com/12.04/serverguide/openssh-server.html](https://help.ubuntu.com/12.04/serverguide/openssh-server.html)
Also, check out the Advanced OpenSSH page that is linked at the bottom of the above page.

I'm not really sure what you need to do to lock down apache as I don't use it, but this page might help.
[http://www.thegeekstuff.com/2011/03/apache-hardening/](http://www.thegeekstuff.com/2011/03/apache-hardening/)

---

### Post by |{urse on 2013-04-29
2 really non-technical but really important tips.

The biggest tip would be: Go ahead and set up vhosts, even if you are only hosting one site currently, it will save you future headaches.

Also: Backup your configs, you never know when you will need them.

---

