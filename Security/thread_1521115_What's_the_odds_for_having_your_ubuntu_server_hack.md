---
title: "What's the odds for having your ubuntu server hacked?"
date: 2010-06-30
forum: Security
---

### Post by TheAlien on 2010-06-30
I'm about to have a web server at home for the first time. I've always missed having full control and not having to contact my hosting company when I need to do some specific changes - and some changes they won't do for you at all.

I've chosen the non-GUI Ubuntu Server with LAMP, and nothing more is installed really except for a couple of command line tools from the repository. The LAMP software has been locked down as good as I can by following some guides on the net and using common sense. Like Apache 2 don't have access to the file system except for the www folder, and setting the headers to Prod. MySQL has skip-networking and I've commented out the listen string to localhost. PHP has a truckload of functions that I've disabled in the php.ini, also by following some guides on the net, among some other security enhancing php.ini editing.

The only thing the server will serve is a well known PHP forum and some html docs, and that's all. Nothing advanced or complicated stuff, and I'm definitely not programming PHP myself or letting anyone do it for me.

But I do want to sleep well at night knowing that my server is always on and sitting on the edge of my home network! And can I do that? I've heard that you don't need to be worried about getting your Linux server box hacked, but you should be worried about anyone getting root access to it. But is it really that simple? Ubuntu is shipped without root account and you must have the sudo password, right? What's the odds for anyone to get full access to my system?

An issue: I've heard that Apache never must run as root. When I do a **ps -ef**, I see that there are several www-data processes running apache, but there's one root process running apache too. Is this normal and is it safe?

An issue: I've heard that PHP can fail pretty easily. But isn't PHP running under apache 2 and limited by the www-data filesystem access?

An issue: MySQL is running as a MySQL user, and I guess that's an unprivileged user right?


If you have the time to just consult me with my concerns and questions, I would be very grateful! :)

---

### Post by yeleek on 2010-06-30
> **TheAlien said:**
> I've heard that you don't need to be worried about getting your Linux server box hacked, but you should be worried about anyone getting root access to it. But is it really that simple? 

[https://blogs.apache.org/infra/entry/apache_org_04_09_2010](https://blogs.apache.org/infra/entry/apache_org_04_09_2010)

"Our JIRA instance was hosted on brutus.apache.org, a machine running Ubuntu Linux 8.04 LTS."

Makes for a thought provoking read...

and finally - don't put it in your home network, at least get a proper dmz and stick it in there :)

---

### Post by conundrumx on 2010-06-30
If you leave SSH configuration at default, and have strong user passwords (or better yet, don't expose SSH to the internet) the chances are very low.  Stay up to date with patches and you'll be fine.

Ubuntu **does** have a root account, all Linux distros do.  It ships without a password, and you should absolutely change that.  It sounds like the most likely thing to get compromised is your website, not the server itself.

---

### Post by movieman on 2010-06-30
> **conundrumx said:**
> Ubuntu **does** have a root account, all Linux distros do.  It ships without a password, and you should absolutely change that.

No, it ships with root logins disabled... shipping with no root password would be mad.

As far as I'm aware the three most common routes for hacking linux servers are:

1. VNC
2. SSH
3. PHP

VNC should only even listen to localhost (use ssh to forward it to a remote machine if required), SSH should use public keys rather than passwords, and PHP bugs seem to be the most common method of breaking into a web server.

Ideally you should install an apparmor profile for whatever web server you're running, but since it can try to access pretty much anything on the system that's not easy to configure.

---

### Post by unspawn on 2010-06-30
> **yeleek said:**
> "Our JIRA instance was hosted on brutus.apache.org, a machine running Ubuntu Linux 8.04 LTS."

Makes for a thought provoking read...
Errors nonetheless but mostly human errors if I read that correctly.

---

### Post by Rubi1200 on 2010-06-30
I think you should definitely read this:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

The most common hacks are via ssh and vnc and countless tales of woe abound.

I can't remember now where I read it, but the root account is protected with, I believe, a hashed password.

---

### Post by unspawn on 2010-06-30
> **movieman said:**
> VNC should only even listen to localhost
In the OP he said "*I've chosen the non-GUI Ubuntu Server with LAMP*" so while the VNC advice in general is good, it doesn't really apply here, does it?


> **movieman said:**
> PHP bugs seem to be the most common method of breaking into a web server.
I agree. Web stack compromises make up a large part of R/L incidents I read about. Unfortunately the OP only says "a well known PHP forum" but checking [http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=phpbb](http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=phpbb) or say [http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=smf](http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=smf) or just [http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=forum](http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=forum) shows forum software is no exception.

---

### Post by unspawn on 2010-06-30
> **TheAlien said:**
> I've chosen the non-GUI Ubuntu Server with LAMP
As long as it's a maintained, supported release that's OK.


> **TheAlien said:**
> nothing more is installed really except for a couple of command line tools from the repository. The LAMP software has been locked down as good as I can 
- You probably do already but do make backups.
- Automate as much updating as possible and ensure you install security updates as they are released.
- Never run outdated, stale, unsupported, no loner maintained SW.
- Regularly auditing the machine gives you the opportunity to adjust controls and anticipate attacks.
- And *do test* locally and from a location outside of your LAN to ensure all is OK and stays OK. 


> **TheAlien said:**
> The only thing the server will serve is a well known PHP forum
Which one?


> **TheAlien said:**
> I've heard that you don't need to be worried about getting your Linux server box hacked
I've head Androids dream of Sheep ;-p Fuzzy human expressions like "worrying", "guessing" and "thinking" do not apply. Try to see security as binary: either it is secure or it isn't. Flip a switch, test the result. Really, it's *that* simple.


> **TheAlien said:**
> What's the odds for anyone to get full access to my system?
IMHO a question like that is best answered with the test reports at hand. Since you don't list your hardening measures in detail anything else can only be speculation.

---

### Post by movieman on 2010-06-30
> **unspawn said:**
> In the OP he said "*I've chosen the non-GUI Ubuntu Server with LAMP*" so while the VNC advice in general is good, it doesn't really apply here, does it?

I was speaking in general terms, and plenty of people use VNC to run a GUI on a headless server.

---

### Post by cdenley on 2010-06-30
> **Rubi1200 said:**
> 
I can't remember now where I read it, but the root account is protected with, I believe, a hashed password.

User accounts are protected with hashed passwords. The root user, by default, has "!" set as their "hashed password". Of course, this isn't a hashed password at all, which makes password authentication as root impossible.

---

### Post by Rubi1200 on 2010-06-30
> **cdenley said:**
> User accounts are protected with hashed passwords. The root user, by default, has "!" set as their "hashed password". Of course, this isn't a hashed password at all, which makes password authentication as root impossible.

Thanks for the clarification cdenley. I probably misread the first time :oops:

---

### Post by conundrumx on 2010-06-30
> **movieman said:**
> No, it ships with root logins disabled... shipping with no root password would be mad.

Kinda.

SUM works.

`sudo su -l` works.

root has no password by default, so `su` won't work, but "disabled" is an exaggeration.

---

### Post by movieman on 2010-06-30
> **conundrumx said:**
> root has no password by default, so `su` won't work, but "disabled" is an exaggeration.

You can't log in as root. You can't su to root.

Obviously you can become root when you have to using sudo, because you wouldn't be able to perform any maintnance tasks otherwise. But root logins are disabled, as I said.

---

### Post by TheAlien on 2010-07-03
> **yeleek said:**
> [https://blogs.apache.org/infra/entry/apache_org_04_09_2010](https://blogs.apache.org/infra/entry/apache_org_04_09_2010)

"Our JIRA instance was hosted on brutus.apache.org, a machine running Ubuntu Linux 8.04 LTS."

Makes for a thought provoking read...

and finally - don't put it in your home network, at least get a proper dmz and stick it in there :)

> [COLOR=Red]The same password should not have been used for a JIRA account as was  used for sudo access on the host machine.[/COLOR]PWNED! LOL!

Luckilly I'm not that stupid.

---

### Post by TheAlien on 2010-07-03
> **conundrumx said:**
> If you leave SSH configuration at default, and have strong user passwords (or better yet, don't expose SSH to the internet) the chances are very low.  Stay up to date with patches and you'll be fine.

Ubuntu **does** have a root account, all Linux distros do.  It ships without a password, and you should absolutely change that.  It sounds like the most likely thing to get compromised is your website, not the server itself.

I don't think I'll ever need SSH. :)

---

### Post by HermanAB on 2010-07-04
```
I was speaking in general terms, and plenty of people use VNC to run a GUI on a headless server.
```

Not for very long though...

Once they get hacked, they wizen up and switch to SSH.

---

