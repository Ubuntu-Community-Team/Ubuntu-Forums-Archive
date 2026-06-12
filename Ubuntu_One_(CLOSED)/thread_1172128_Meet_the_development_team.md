---
title: "Meet the development team"
date: 2009-05-28
forum: Ubuntu One (CLOSED)
---

### Post by SteveAlexander on 2009-05-28
Hi, I'm Steve Alexander.  I work at Canonical as one of the technical leads for Ubuntu One.  I'm interested in talking about what we're doing with Ubuntu One, and your experiences using around it.

I'm stevea on Launchpad: [https://launchpad.net/~stevea]("https://launchpad.net/%7Estevea")

SteveA on irc (say "hi!" on #ubuntuone on Freenode)

Right now, I'm at UDS in Barcelona.  Find me and say "hi!" if you're here.

I'll ask the others who are working on Ubuntu One to say something in this thread.

-- Steve

---

### Post by joshuablount on 2009-05-28
Hi! I also work for Canonical and am a member of the Ubuntu One team doing front end web work (html, css, javascript), and more general design and visual direction.

I'm jblount on Launchpad ( [https://launchpad.net/~jblount](https://launchpad.net/~jblount) ), Freenode ( #ubuntuone, #django, #bzr ) and I'm stickwithjosh on Twitter & Identi.ca ( [http://twitter.com/stickwithjosh](http://twitter.com/stickwithjosh) [http://identi.ca/stickwithjosh](http://identi.ca/stickwithjosh) )

I'm quite excited about the work we are doing, particularly the thing we'll be doing to make everyone's experience with Ubuntu "out of the box" to be even more awesome (with and without our web service stuff).

---

### Post by fatality_uk on 2009-05-28
Hi guys.

Thanks for the work to date, the service is looking good. I have plans to use the service for both individual use and within our business. I hope to provide feedback as we progress on what we as a business are using UbuntuOne for to help you tune the service

---

### Post by Anzan on 2009-05-28
How many people are on the dev team?

---

### Post by ponkarthik on 2009-05-28
Does this sync just the files or some ubuntu settings as well - like keyring , empathy/pidgin accounts etc...

I know there can be a workaround like how I symlink some preference/conf files in dropbox but it would be great if ubuntuone supports sync of some user conf files out of the box.

Karthik

---

### Post by bapoumba on 2009-05-28
Hello and welcome to the forums :)

---

### Post by stuartlangridge on 2009-05-28
Hey. I'm Stuart Langridge, and I'm part of the Ubuntu One development team too. I spend all my time being excited about the cool stuff we're doing, which makes me sound sad, but there it is :-)

I'm really interested in hearing what people are planning on doing with Ubuntu One, since I do the API side of the project!

I'm sil on [Twitter]("http://twitter.com/sil") and [Identi.ca]("http://identi.ca/sil"), and aquarius on Freenode; [http://www.kryogenix.org/contact](http://www.kryogenix.org/contact) for all the gory details.

sil

---

### Post by Anzan on 2009-05-28
Well then, to answer my own question just in case it's of interest to anyone else:

> There are 38 direct members of the "Ubuntu One hackers" team, and 42 people are members in total, directly and indirectly through other team memberships. 

[https://launchpad.net/~ubuntuone-hackers/+members]("https://launchpad.net/~ubuntuone-hackers/+members")

---

### Post by zekopeko on 2009-05-28
> **ponkarthik said:**
> Does this sync just the files or some ubuntu settings as well - like keyring , empathy/pidgin accounts etc...

I know there can be a workaround like how I symlink some preference/conf files in dropbox but it would be great if ubuntuone supports sync of some user conf files out of the box.

Karthik

this is probably planed. it's a sync service so configuration syncing is only natural.

---

### Post by rafaellaguna on 2009-05-29
Sorry about an inconvenience, but UbuntuOne is getting so much time to answer. I know there're a lot of (friend's) reservations / subscriptions pending. How much time do we have to wait? It's just curiosity.

Thanks in advance.

---

### Post by joshuablount on 2009-05-29
@Anzan: Forgive me for the rough number, but we're just under 25 people right now on the team. The LP team has a few extra members, including sys admins and lots of interested developers from other teams within Canonical :)

@ponkarthik: Right now, the file syncing service that is available just syncs files that you explicity move into a particular folder. We're working on some very interesting things that will provide settings and preferences syncing relatively soon, but it's not quite "fully baked" yet!

@rafaellaguna: Sorry for the long wait to get an invitation! 

[http://ubuntuforums.org/showthread.php?t=1172688](http://ubuntuforums.org/showthread.php?t=1172688) is close to being right about the current waiting list. We've got lots of people interested in trying out Ubuntu One, but right now all the developers are attending the Ubuntu Developers Summit. We've actually been working a bit in the evenings to get the servers ready so that we can let everyone who is currently waiting on an invitation into the system. 

We aren't (yet) committed to a specific time frame beyond "When it's ready", but we hope to get everyone using Ubuntu One as quickly as possible.

Thanks everyone! If you can, feel free to ask any of the developers about themselves, but lets try and keep questions about the service to a more appropriate thread ;)

---

### Post by Junkieman on 2009-05-29
Greets to the Ubuntu One team :) Sounds like an exciting project, glad to have you with us!

---

### Post by Dragonbite on 2009-05-29
UbuntuOne looks really cool, kudos on what you're working on!

I can't wait for an invite, so I can demonstrate it at the computer club (I'm the [_[COLOR="DimGray"]DACS[/COLOR]_]("http://www.dacs.org") Linux SIG Leader, so I can't wait to demonstrate this at one of our meetings.)

---

### Post by Anzan on 2009-05-31
What languages and frameworks do the development team use on this project?

Who does what?

---

### Post by Flimm on 2009-05-31
Thanks for joining us in the forums! I get the impression that most developers hate forums (they seem to prefer mailing lists), so it's especially refreshing to get a thread like this.

---

### Post by gn2 on 2009-05-31
Hello development team.

How's progress coming along with creating an open source server side solution to use with Ubuntu One?

---

### Post by Starbase 9525 on 2009-05-31
I don't know if this is the right place or not but I wanted to say thanks to all of those who work on developing Linux and especially to those who had a hand in 9.04 .   I recently downloaded it and installed it on my laptop. It installed flawlessly and it was a snap to set up the wireless networking, something I have never been able to do before as I don't have much linux experience. Now both of my computers run Linux, not Windows and I am very pleased with that. Thanks again for all the effort.

Starbase 9525

---

### Post by joshuablount on 2009-06-18
> **Anzan said:**
> What languages and frameworks do the development team use on this project?

Who does what?

I can answer a bit of this:

We're using lots, and lots, and lots of python (although Rodney Dawes recently snuck in some C code for the client software :)

Here's a semi complete list of the various projects where using bits or ideas from, sorry for the weird formatting, but it's copied and pasted form a internal wiki page: 

# Django (v 1.0) - [http://djangoproject.com](http://djangoproject.com) (Web framework used for web applications)
# Graphite - [http://graphite.wikidot.com/](http://graphite.wikidot.com/)
# Satchmo - [http://satchmoproject.com](http://satchmoproject.com) (Used only as a reference e-commerce application)
# Storm ORM - [https://storm.canonical.com/](https://storm.canonical.com/)
# OpenID - [http://openid.net/](http://openid.net/)
# OAuth - [http://oauth.net/](http://oauth.net/)
# Bazaar VCS - [http://bazaar-vcs.org](http://bazaar-vcs.org)
# Launchpad - [http://launchpad.net](http://launchpad.net)
# Amazon S3 - [http://aws.amazon.com/s3](http://aws.amazon.com/s3)
# Amazon EC2 - [http://aws.amazon.com/ec2](http://aws.amazon.com/ec2)
# Twisted - [http://twistedmatrix.com/trac/](http://twistedmatrix.com/trac/)
# Google Protocol Buffers - [http://code.google.com/p/protobuf/](http://code.google.com/p/protobuf/)
# HAProxy - [http://haproxy.1wt.eu/](http://haproxy.1wt.eu/)
# mod_proxy_balance - [http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html)
# Ratproxy - [http://code.google.com/p/ratproxy/](http://code.google.com/p/ratproxy/)
# pydoctor - [http://codespeak.net/~mwh/pydoctor/](http://codespeak.net/~mwh/pydoctor/)
# mocker - [http://labix.org/mocker](http://labix.org/mocker)
# testresources - [https://code.edge.launchpad.net/testresources](https://code.edge.launchpad.net/testresources)
# zope

    * transaction
    * zope.component
    * zope.deferredimport
    * zope.deprecation
    * zope.event
    * zope.exceptions
    * zope.i18nmessageid
    * zope.interface
    * zope.proxy
    * zope.proxy
    * zope.schema
    * zope.testbrowser
    * zope.testing 

# PQM
# Postgresql
# graphviz
# YUI 2 and 3
# JSON
# PIL
# python-crypto
# beautifulSoup
# RabbitMQ
# CouchDB
# windmill

---

### Post by Anzan on 2009-06-18
Thank you, joshuablount.

---

