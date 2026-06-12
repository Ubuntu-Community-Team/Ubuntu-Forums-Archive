---
title: "Best Wiki software?"
date: 2007-06-22
forum: The Cafe
---

### Post by RAV TUX on 2007-06-22
I have been researching Wiki's...

Currently using TikiWiki, but both MediaWiki(used by Wikipedia) and MoinMoin Wiki(used by  Debian, Ubuntu, & Fedora) look awesome...

For those who admin , use, or host Wiki's which do you find to be the best (according to you) and why?

---

### Post by phrostbyte on 2007-06-22
I like MediaWiki cause it's what Wikipedia uses (and I familar with their wikicode) :)

---

### Post by az on 2007-06-22
What exactly do you need?  On a site I manage which uses Drupal. I though about tacking on a wiki using different software, but realised that I could just create another content type in Drupal and make it world-writable as well as use revisions.  Although there is no wiki markup (who needs that anyway) I got the benefits of community contribution using the tools I already had.

---

### Post by SoulinEther on 2007-06-22
MediaWiki... it's the most familiar, in my opinion, and easy to set up. Plus, it runs with a MySQL database and PHP, so you don't have to hunt down a server with Python support.

---

### Post by RAV TUX on 2007-06-23
> **az said:**
> What exactly do you need?  On a site I manage which uses Drupal. I though about tacking on a wiki using different software, but realised that I could just create another content type in Drupal and make it world-writable as well as use revisions.  Although there is no wiki markup (who needs that anyway) I got the benefits of community contribution using the tools I already had.

Actually after testing several Wiki's out I have decided to try out Drupal for now. I use Drupal for several other sites. I may see how it goes for a while...I am trying to decide if I should use mediawiki....

---

### Post by luca.b on 2007-06-23
Choice of wiki depends much on what you want to do. Mediawiki is overkill for small realities: personally (but it's an one-man wiki) I use DokuWiki to handle my laboratory notes.

---

### Post by bobbocanfly on 2007-06-23
I would recommend MediaWiki. It is stable enough to be used on one of the busiest websites on earth and whats more its very very easy to install. Only downside is that for the newest versions you must have PHP5 installled on your server

---

### Post by az on 2007-06-23
> **bobbocanfly said:**
> Only downside is that for the newest versions you must have PHP5 installled on your server

You would run a site under PHP4?  I wouldn't accept that - it's too insecure.

---

### Post by bobbocanfly on 2007-06-23
> **az said:**
> You would run a site under PHP4?  I wouldn't accept that - it's too insecure.

I know, i use PHP5 for everything but not every host out there will upgrade to PHP5 (ones that use cPanel for example).

---

### Post by dzoner on 2007-06-23
> **phrostbyte said:**
> I like MediaWiki cause it's what Wikipedia uses (and I familar with their wikicode) :)

same here :)

---

### Post by az on 2007-06-23
> **bobbocanfly said:**
> I know, i use PHP5 for everything but not every host out there will upgrade to PHP5 (ones that use cPanel for example).

My hosting provider uses PHP5 and cPanel...

---

### Post by afljafa on 2007-06-23
Problem with many wikis is that they are either too complicated to use or administer. I like wakowiki - it`s lite and easy to setup. 

I use it for a small mythtv wiki I have set up. [http://mythtv.goldtel.com.au](http://mythtv.goldtel.com.au)

---

### Post by RAV TUX on 2007-06-23
> **az said:**
> My hosting provider uses PHP5 and cPanel...

I emailed my host with a request to upgrade to PHP5, I'll see what happens.

> **afljafa said:**
> Problem with many wikis is that they are either too complicated to use or administer. I like wakowiki - it`s lite and easy to setup. 

I use it for a small mythtv wiki I have set up. [http://mythtv.goldtel.com.au](http://mythtv.goldtel.com.au)

Nice, compact, easy wiki site you have there.

---

### Post by jonjonz on 2007-07-17
I use Mediawiki, but be forwarned the last Ubuntu build was 1.4.14 and the current general release is 1.10+ something.  

It looks like no one is bothering to maintain a Ubuntu build since 1.4.14.

Most new plugins for Mediawiki require 1.5 or better.

---

### Post by az on 2007-07-17
> **jonjonz said:**
> I use Mediawiki, but be forwarned the last Ubuntu build was 1.4.14 and the current general release is 1.10+ something.  

It looks like no one is bothering to maintain a Ubuntu build since 1.4.14.

Most new plugins for Mediawiki require 1.5 or better.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=mediawiki](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=mediawiki)
Feisty has version 1.7 and Gutsy 1.9.  If no one is bothering to maintain it, that's your opportunity to jump in and do it.  Can we count on you?

But anyway, your server is supposed to be stable.  I don't recommend you install web applications using the package manager anyway.  Your server infrastructure should remain solid and you are free to upgrade your web applications seperately.

As well, you may need to install multiple instances of a web application and you just can't do that with the package manager.

---

