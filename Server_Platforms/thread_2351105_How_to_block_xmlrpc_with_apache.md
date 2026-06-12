---
title: "How to block xmlrpc with apache"
date: 2017-01-31
forum: Server Platforms
---

### Post by fernandoch on 2017-01-31
Hello,

I have ubuntu 12.04 and running apache for my wordpress sites.

I have consistent xmlrpc attacks.

I tried blocking the IPs with ufw, but it does not seem to work.

What is the best way to block the attacks?

Thanks

---

### Post by Habitual on 2017-01-31
fail2ban. 

If you don't have an "app" that dialogs with your site, you could rename or remove the xmlrpc.php file,
or try the addon wordfence.

---

### Post by fernandoch on 2017-01-31
fail2ban? Do you have any instructions?

I believe wordpress' updates need that file.

I tried blocking with wordfence and as if nothing, the attack continued.

---

### Post by Habitual on 2017-01-31
> **fernandoch said:**
> I believe wordpress' updates need that file.It does not.
You believe wrongly.

```
sudo apt-get install fail2ban
```
installs it.

Instructions are in /etc/fail2ban/jail.conf after the install.
I have a "few" instructions, but I'll leave you to it, since everyone's learning style is different.

[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)
[http://www.fail2ban.org/wiki](http://www.fail2ban.org/wiki)
[http://www.scottbrownconsulting.com/2014/09/countering-wordpress-xml-rpc-attacks-with-fail2ban/](http://www.scottbrownconsulting.com/2014/09/countering-wordpress-xml-rpc-attacks-with-fail2ban/)
and [https://ubuntuforums.org/showthread.php?t=2305198&p=13401254#post13401254](https://ubuntuforums.org/showthread.php?t=2305198&p=13401254#post13401254)
has some pointers for you, from me.

Also [https://www.digitalocean.com/community/tutorials/how-to-protect-an-apache-server-with-fail2ban-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-protect-an-apache-server-with-fail2ban-on-ubuntu-14-04) 
is what got me started on fail2ban.

Good Luck.

---

### Post by fernandoch on 2017-01-31
Jetpack uses xmlrpc.

Would that work?

/etc/fail2ban/filter.d/xmlrpc.conf (new file)

[Definition]
failregex = ^<HOST> .*POST .*xmlrpc\.php.*
ignoreregex =
/etc/fail2ban/jail.local (appended to the existing file)

[xmlrpc]
enabled = true
filter = xmlrpc
action = iptables[name=xmlrpc, port=http, protocol=tcp]
logpath = /var/log/apache2/access.log
bantime = 600000
maxretry = 2
findtime = 6000

And I have my apache logs in different files according to the domains, so I guess I would have to modify that.

---

### Post by Habitual on 2017-01-31
> **fernandoch said:**
> Jetpack uses xmlrpc.

Would that work?

/etc/fail2ban/filter.d/xmlrpc.conf (new file)

```
[Definition]
failregex = ^<HOST> .*POST .*xmlrpc\.php.*
ignoreregex =
```
/etc/fail2ban/jail.local (appended to the existing file)

```
[xmlrpc]
enabled = true
filter = xmlrpc
action = iptables[name=xmlrpc, port=http, protocol=tcp]
logpath = /var/log/apache2/access.log
bantime = 600000
maxretry = 2
findtime = 6000
```

And I have my apache logs in different files according to the domains, so I guess I would have to modify that.
1. ) [Adjusting the General Settings within Fail2ban]("https://www.digitalocean.com/community/tutorials/how-to-protect-an-apache-server-with-fail2ban-on-ubuntu-14-04") tells you what you should be editing, not "appending".

I recommend defaults which are thoroughly documented.
```

[DEFAULT]
ignoreip = <Your_IP> 
....
bantime  = -1 
findtime = 600 
```
and it's python, so** do not mix spaces and tabs**. 
Line everything up on the right-side of any " = " assignments.

Test your xmlrpc.conf using
```
fail2ban-regex /var/log/apache2/access.log /etc/fail2ban/filter.d/xmlrpc.conf
``` and view the summary report.

---

### Post by TheFu on 2017-02-01
BTW, you know that **support for 12.04 ends in a few months**.  You should be planning a migration THIS month and performing that migration in MARCH at the latest.

I would block this using my reverse proxy, nginx.  Matching patterns is trivial.
```
   if ($request_uri ~* (phpmyadmin) ) { return 403; }
   if ($request_uri ~* (setup.php) ) { return 403; }
   if ($request_uri ~* (login.php) ) { return 403; }
   if ($request_uri ~* (index.php) ) { return 403; }

```
I block sql injection attempts, file injections, and many other common exploits too.  Also block people trying to use my servers as remote image servers (they like my image and link directly to it).  Also block sites trying to put my site into a frame with their banners/ads - like some of the bookmarking sites.

---

### Post by fernandoch on 2017-02-02
Thanks to both.

I forgot the support ends in a few months, so busy that I might not be able to do it on time.

TheFu, I am using apache, not nginx.

---

### Post by TheFu on 2017-02-02
> **fernandoch said:**
> Thanks to both.

I forgot the support ends in a few months, so busy that I might not be able to do it on time.

TheFu, I am using apache, not nginx.

Yep, knew you were on apache - haven't used it much here in years.  Apache can do what you want, I'm certain. I don't know how. Just wanted to show an alternative.

Moving to the next LTS really needs to be your priority. I'd let upper management know ASAP, so they can help with your priorities.  No running supported software can violate professional liability insurance. I know it violated ours.

I have 1 box still on 12.04 too. Think I tried to move it to 14.04 a few years ago and failed.  Maybe one of my guys handled it in the background. ;)  Checking ..     ```
"description": "Ubuntu 12.04.5 LTS",
```
2 words.  Oh crap.  The machine running the older release .... my nginx reverse proxy box!  Oh crap.

I'm glad I checked, but this sucks. It isn't the nginx stuff that concerns me. There's another process on that machine that has to be public or it is useless.
Seems I'm in the same boat as you. ;(

---

### Post by fernandoch on 2017-02-03
I am upper management and lower management :) I manage most of the things in my company, this is why I have no time :(

Should start outsourcing really soon :)

---

### Post by TheFu on 2017-02-03
> **fernandoch said:**
> I am upper management and lower management :) I manage most of the things in my company, this is why I have no time :(

Should start outsourcing really soon :)

I would still check with the real boss (my wife) if I needed more time on the systems which impacted family time. ;)
Be careful with outsourcing important stuff.  Don't forget that "the cloud" is ....
> 
The cloud is someone else’s hard drive attached to someone else’s server in someone else’s data center at the end of an Internet pipe controlled by someone else. If that works for you – and it might! – great. But do be aware of what you are doing. -some guy on /.

---

