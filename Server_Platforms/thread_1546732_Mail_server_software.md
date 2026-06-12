---
title: "Mail server software"
date: 2010-08-05
forum: Server Platforms
---

### Post by M!K3_$ on 2010-08-05
Hello,

I want to know your opinion on the best, free (as in $0.00) mail server software.

Please include a good tutorial and an explanation of your opinion

---

### Post by kevin11951 on 2010-08-06
> **M!K3_$ said:**
> Hello,

I want to know your opinion on the best, free (as in $0.00) mail server software.

Please include a good tutorial and an explanation of your opinion

There are two big name ones:

Citadel: Small, and runs on a server running other software.  Simple to setup, just add the repo and install citadel-suite (do not use the ubuntu packages, or the simple install script)

Zimbra:  A monster thats needs its own private server.

I suggest you use Citadel.  Info here: [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

Install from here:  [http://www.citadel.org/doku.php/installation:debian](http://www.citadel.org/doku.php/installation:debian)

```
deb [http://ubuntu.citadel.org/ubuntu/](http://ubuntu.citadel.org/ubuntu/) **hardy** main
```

Note: Only works with hardy, and I recommend hardy for a server either way.  With that said, if you want lucid, then install from the ubuntu packages, and ignore this repos thing.

sudo apt-get install citadel-suite

Let me know if you have trouble

---

### Post by HermanAB on 2010-08-06
I second Citadel.  There are some guides on my web site, but all you need to do is run the Easy Install script and you will have a working system in about 20 minutes.  Citadel is the easiest mail server ever and it is totally configurable, once you get tired of the defaults.

---

### Post by kevin11951 on 2010-08-06
> **HermanAB said:**
> I second Citadel.  There are some guides on my web site, but all you need to do is run the Easy Install script and you will have a working system in about 20 minutes.  Citadel is the easiest mail server ever and it is totally configurable, once you get tired of the defaults.

I personally advise against the "Easy Install" scripts, because they cause files on the system to become out of sync with the package manager.  The repo is just as easy, you get automatic updates, and the package manager is in charge.

---

### Post by kevin11951 on 2010-08-06
Oh, I FORGOT!

Do you have a domain name?  If not, you can't have an email server...  If you do:

Post the output of:
```
hostname -f
```

---

### Post by M!K3_$ on 2010-08-06
Wow, thanks guys. I'll be sure to try Citadel. The croud seems split between easy-install or not.

and yes, i do have a domain name.

---

### Post by kevin11951 on 2010-08-06
> **M!K3_$ said:**
> Wow, thanks guys. I'll be sure to try Citadel. The croud seems split between easy-install or not.

and yes, i do have a domain name.

I am begging you, do not do easy install... It will end in crying kittens and puppies.  Also, make sure that your FQDN is google.com and not mail.google.com, or your email addresses will be [email]name@mail.google.com[/email].

(note, replace google.com with your domain)

---

### Post by HermanAB on 2010-08-07
Actually, the best way to run a complex server is on a separate Virtual Machine.  This way, you can easily make a backup of the whole thing (just stop it and make a tar ball) and when you update Ubuntu, you don't trash your mail server.  I never update my mail servers.  I install them, secure them and then leave them running for 4 or 5 years.

Citadel has a download of a pre-installed VMware image for download.  So instead of installing Citadel, you can simply install VMware Player, download the VM and run it.

---

### Post by kevin11951 on 2010-08-07
> **HermanAB said:**
> Actually, the best way to run a complex server is on a separate Virtual Machine.  This way, you can easily make a backup of the whole thing (just stop it and make a tar ball) and when you update Ubuntu, you don't trash your mail server.  I never update my mail servers.  I install them, secure them and then leave them running for 4 or 5 years.

Citadel has a download of a pre-installed VMware image for download.  So instead of installing Citadel, you can simply install VMware Player, download the VM and run it.

I personally would not recommend that to someone who has never run an email server before...  Then you are combining the complications of both email servers and VMs in one project...

---

### Post by HermanAB on 2010-08-07
I have used the Citadel VM.  It is installed right, on a minimalist system, with Spam Assassin and ClamAV, all ready to go.  So this would be good for a beginner Mail Administrator.

---

### Post by Blues- on 2010-08-07
Postfix ! no question about it.
Great MTA, great install guide @ flurdy's site ..
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by HermanAB on 2010-08-08
Postfix is only a half assed partial solution.  To be able to use Postfix, you also need Apache, Roundcube, Dovecot, Spam Assassin and ClamAV, some way to hook Spam Assassin to Postfix and some way to virtualize the users so that everybody are not system users.  

Building a mail system from all these Lego blocks is a great learning experience, but I have given up with Postfix several years ago.  Zimbra, Citadel and Kolab have surpassed Postfix and left it in the dust, where it belongs.

---

