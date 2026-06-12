---
title: "Easiest Wiki to Install on Ubuntu Server?"
date: 2006-12-11
forum: Server Platforms
---

### Post by ryharv on 2006-12-11
Hi,

I'm running a simple apache server on Ubuntu.  It's working fine for serving up html and other files just like I want it to.

I'd love to install a wiki that I can edit from anywhere, via a broswer.  I've tried to install Instiki (based on ruby on rails) and Twiki.  No luck with either of them.  I wouldn't say Ubuntu is foreign to me, but I'm also not a super-user.  

Has anyone installed a wiki (any wiki) easily on ubuntu, with minimal configuration?  What's the easiest one?

Thanks for your help.

---

### Post by elst on 2006-12-11
Ubuntu has packages for MoinMoin, which is an excellent product. It's actually the software that the Ubuntu Wiki uses.

---

### Post by hagen00 on 2006-12-12
We use wikimedia, which is the one that wikipedia uses. Installs very easily and is super cool.

---

### Post by technodigifreak on 2006-12-12
> **ryharv said:**
> Has anyone installed a wiki (any wiki) easily on ubuntu, with minimal configuration?  What's the easiest one?

TiddlyWiki [http://www.tiddlywiki.com/](http://www.tiddlywiki.com/)

It's a single html file, you only need to drop it into a web accessible folder and change the permissions to read/write.  Full howto is on the webpage, but it's nice because you don't even need a webserver to run it locally, just a web browser.

---

### Post by EmmEff on 2006-12-12
> We use wikimedia, which is the one that wikipedia uses. Installs very easily and is super cool.

It's actually called [MediaWiki](http://www.mediawiki.org) :)

---

### Post by technodigifreak on 2006-12-12
> **EmmEff said:**
> It's actually called [MediaWiki](http://www.mediawiki.org) :)

yeah, MediaWiki kicks!  Too bad it's a heavy install.

---

### Post by EmmEff on 2006-12-13
I guess for any heavily used wiki, it's probably best to be backed by a database.

---

### Post by technodigifreak on 2006-12-13
Well they did ask for the easiest...........

TiddlyWiki is just copy and paste....no configuration what-so-ever.  :D

---

### Post by engla on 2006-12-13
Ikiwiki is a pretty new but unixy wiki -- it uses svn for storage, markdown for syntax and can be either read-only (only local updates, for example via ssh) or remote with full cgi.

---

### Post by pmasiar on 2006-12-13
> **ryharv said:**
> I'd love to install a wiki ... but I'm also not a super-user.  

Yes, you are! You *are* sudoer on your box, it means you  are superuser! :-)

Easiest wiki to use is: get own free wiki at pbwiki.com. No installation required - cannot be easier than that! :-)
You can keep it private and/or share password with couple of people. 

If you want to install it on your own box, synaptic will install you MoinMoin. But you need to learn how to administer it etc.

To make your life as unexperienced superuser :-) easier, let me suggest you mc - midnight commander (older between us may remember norton commander). Synaptic will install it. You can run it in terminal, look around file system, do stuff in a way which is very visual but it is not GUI and you can run it remotely over ssh. Try it, and your sudoer's life will change forever! :-)


> **technodigifreak said:**
> TiddlyWiki [http://www.tiddlywiki.com/](http://www.tiddlywiki.com/)

It's a single html file, you only need to drop it into a web accessible folder and change the permissions to read/write. 

So for edit, browser will dowload the page. How I would write? Upload the page?

> **EmmEff said:**
> I guess for any heavily used wiki, it's probably best to be backed by a database.

Not obvious to me. Quite the opposite: text-based wiki, (page versions in svn) can grab the latest page (in internal wiki format) as text file, and render it into HTML. No database overhead. Simple text diff. How do you store versions of the same page in database? Full page text?

Because you have like 10-100 reads for every edit, it makes sense to optimize for reading pages. IMHO, YMMV.

---

### Post by az on 2006-12-13
I thought there was a documentation page on how to install mediawiki.  It is really straightforward.

You can follow this:
[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)
but substitute mediawiki.

A lot of LAMP web applications are installed the same.

---

### Post by rcmc2020 on 2006-12-13
I agree that MediaWiki is great. If you start with a working LAMP server, it takes about 3 minutes to install and configure a working copy of MediaWiki. You have to know a little PHP to start customizing it but you'll really have to dig around for up-to-date documentation. It's worth it though because it's a very solid and flexible package.

---

