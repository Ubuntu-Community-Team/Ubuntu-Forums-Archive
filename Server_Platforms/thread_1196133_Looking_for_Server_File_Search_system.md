---
title: "Looking for Server File Search system"
date: 2009-06-24
forum: Server Platforms
---

### Post by TwiceOver on 2009-06-24
So I've had it with Microsoft Server Search...  Google appliances are way too spendy for small business and the Google Desktop Search hacks don't seem to work any more :(.

Looking for something that will index Samba shares on my server and then allow some sort of web interface for my users to search and open the files.

I haven't come across anything free yet, wondering if anyone here would have an idea to use?

---

### Post by R.Bucky on 2009-06-24
I indexed and had a web based search system configured with Beagle across Samba shares. You can use the Beagle front end or Peagle. Also, be aware that either of these configurations will require that you modify Firefox for access to local links. 

Also, try Apache Lucene. There are a few of them on the net. However, Beagle works well.

---

### Post by TwiceOver on 2009-06-24
> **R.Bucky said:**
> I indexed and had a web based search system configured with Beagle across Samba shares. You can use the Beagle front end or Peagle. Also, be aware that either of these configurations will require that you modify Firefox for access to local links. 

Also, try Apache Lucene. There are a few of them on the net. However, Beagle works well.

Thanks for the info.  Lucene looks like the way to go, but is way over my head at this point.  I'll have to read and understand it better.

Beagle works GREAT!  The Beagle Web Interface only works with FF, we use IE here :(.  I tried the "Peagle" web front end but it is so out of date that it no longer works.

---

### Post by R.Bucky on 2009-06-24
Also, try [http://trac.xapian.org/wiki/Omega]("http://trac.xapian.org/wiki/Omega")
or
[http://www.flax.co.uk]("http://www.flax.co.uk")
and finally
[http://www.mnogosearch.org/]("http://www.mnogosearch.org/")

---

### Post by TwiceOver on 2009-06-25
Well I got Lucene-Solr running.  Seems way overkill and hard to actually administrate.  Was fun getting there, but I dont' think this is the right solution for what I want to do.

I guess I'm still looking.  Thanks for the second list.  They all seem to be pay except Omega... Which is my next stop.

If MS would get off their high horse and allow MSSE to search by file name I wouldn't be in this mess.  Seriously, this day in age Who "TF" would write a search engine that doesn't search by file name...

---

### Post by Francewhoa on 2009-06-28
Solr. 

Websites using Solr: [http://drupal.org/node/447564](http://drupal.org/node/447564)

How-to handbook for absolute beginners at [http://drupal.org/node/504558](http://drupal.org/node/504558)

---

### Post by TwiceOver on 2009-06-28
> **Onopoc said:**
> Solr. 

Websites using Solr: [http://drupal.org/node/447564](http://drupal.org/node/447564)

How-to handbook for absolute beginners at [http://drupal.org/node/504558](http://drupal.org/node/504558)

Yeah I have it installed on a test system but I guess I just don't get it.  All I can see is that it will take XML files for search listings, but I don't get how I tell it to just go to town indexing file directories.  Also the default search is a little complicated for the average user.

---

