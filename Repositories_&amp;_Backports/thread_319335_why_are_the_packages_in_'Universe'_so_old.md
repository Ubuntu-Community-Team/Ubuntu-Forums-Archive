---
title: "why are the packages in 'Universe' so old?"
date: 2006-12-15
forum: Repositories &amp; Backports
---

### Post by bsmith1051 on 2006-12-15
I am trying to setup a test phpBB server and the version of phpBB in the generic "Ubuntu 6.06 LTS binary Community Maintained Universe" repository is still at 2.0.18.2 whereas the current version on the phpBB web-site is 2.0.21 and is already six months old.  I can understand there being a delay for brand-new versions (like VLC 0.8.6 this week) but why do other packages take so long to get updated?

Since I don't know that much about Linux I was really hoping to rely on the package manager but now it looks like I need to do it all manually.

I also now see that it installed php 4.4.2 (current is 4.4.4 circa 8/06) and Apache 2.0.55 (current is 2.0.59 circa 7/06)

---

### Post by az on 2006-12-15
The newest version is in Edgy.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=phpbb2](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=phpbb2)

The versions in Dapper are frozen.

If you follow this:
[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)
You get it running with apache2, mysql5 and php5

The thing with server packages is that you want long-term support for the infrastructure, but not neccessarily for the web application itself.

You should run a Dapper LAMP server and install the latest upstream source for the web application, IMHO.  It is usually pretty simple to install or upgrade a web application from source.

---

### Post by kerry_s on 2006-12-15
It's because your using dapper which is LTS(long term support) the base packages are locked in already & you will only get security updates & back ports(if you have it on). That way the system can remain as stable as possible. I can see in the feisty test the version is 2.0.21-5, I would usually say you could grab it from feisty repo, but it has dependency's & you would need to update apache as well. Just remember in linux newer is not always better.

---

### Post by bsmith1051 on 2006-12-15
Thanks for clarifying this!

I'm not sure what you guys are recommending:  Should I modify the configuration of my new 6.06 install so that it uses a different/unlocked/newer repository, or should I reinstall with a different version of Ubuntu?

re stable versioning, I thought the version numbers I reported *were* just security updates?  They're certainly not the newest versions.   Also, by manually enabling the Universe repository, I thought I was in-effect bypassing the stable-only versions?

Edgy is v6.10, right?  If I just reinstall the machine using the 6.10 CD, will it then connect to a more up-to-date set of repositories?  

Finally, re setting-up a LAMP server, you're not talking about a particular version of Ubuntu, right?  You're just saying that I need to install Apache MySQL and PHP?  When I use Package Manager (on the existing 6.06 and Universe repository) to select "phpBB2" it prompts me that it needs to install a bunch of other packages including PHP.  So I assumed that was downloading all needed packages.  of course, now I can't seem to find phpBB anywhere on the system -- at least the instructions on the phpBB web-site don't seem to work.

---

### Post by kerry_s on 2006-12-15
I say just chance it, change where it says-> 
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 
to
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 
or
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted 

In your /etc/apt/sources.list, but just to get the updates you want, then just disable it or remove it. Normally i would recommend staying with what you got but i read the change log and there have been a lot of fixes that look important. As always backup your important stuff first just in case you get boned. Good luck.

---

### Post by bsmith1051 on 2006-12-15
> **kerry_s said:**
> change where it says-> 
  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted 
to
  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 
In your /etc/apt/sources.list, but just to get the updates you want, then just disable it or remove it.
wow, now it thinks the whole system is out of date!  Unfortunately, that doesn't seem to have 'found' a newer version of either Apache or phpBB.
____________

EDIT:
I went back and instead changed the one reference to 'dapper universe' to 'edgy universe' -- same result.

I think I'll just reinstall again but with 6.10 "Edgy" this time.

---

