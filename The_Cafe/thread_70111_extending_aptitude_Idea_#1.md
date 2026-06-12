---
title: "extending aptitude: Idea #1"
date: 2005-09-28
forum: The Cafe
---

### Post by brentoboy on 2005-09-28
One feature missing from aptitude (for obvious reasons) is support for commercial apps.  Which, when you consider the roots of aptitude makes sense. It comes to us from Debian / gnu Linux - the home of the free - as in freedom.  The concept of a "commercial app" is anti-gnu.

But, aptitude needs to progress beyond its roots - in order to meet the needs of the community.  Companies (like vmware for instance) need to be able to offer a repository for their proprietary stuff.

Here is how it would work.  In your sources list (or in your settings area of synaptic) you would fill in a url and stuff just like you do for free repositories - then, you would provide an extra "key" that uniquely identifies you to them - like the install key that vmware offers to let you download their stuff.

All apt needs to do is "login" with this key to the proprietary repository, and then vmware and related offerings are available in your package list.  you can then apt-get install vmware and you don't have to bash your brains out to get "special" software.

They can do whatever they want on their end to drop misused keys and stuff, so it isn't like they are giving their stuff to the world.  They can also keep people up to date the same way the rest of Ubuntu is updated.  It would check for updates and tell you when there is a new version you could download and apply.

Any comments? Am I going somewhere good with this? Is this a terrible idea?

---

### Post by 23meg on 2005-09-29
if the key were to work an infinite number of times, it could be distributed, which would mean piracy. if it were to be dropped at a single use, or a limited number of uses, apt would have to be modified to allow this, and that wouldn't be very welcome in the Debian world. plus limiting the number of downloads goes against the convenience of being able to reinstall from repositories whenever your installation gets borked.

---

### Post by brentoboy on 2005-09-29
At the software company where I work, we offer download subscriptions to our website. People have to login to download stuff.  we have "warning" signals when it looks like there is gross abuse of the system.  We allow for a pretty decent amount of downloading though without any questions.

There is a recognizable differnece between 1 active user who likes to reinstall our stuff a lot, and a community who got the key.  It is easy for a website to revoke keys - they own the web server.

---

### Post by 23meg on 2005-09-29
maybe a separate apt-like (apt-forked?) framework optimized for commercial distribution can be developed and users would only have to install it if they're intending to work with proprietary software from vendors. apt repositories should be isolated from commercial distribution in my opinion.

but even then it would be a whole burden trying to get vendors to settle on this one standard..

---

### Post by brentoboy on 2005-09-29
[QUOTE=23meg] apt repositories should be isolated from commercial distribution in my opinion.[/QUOTE]

I agree wholeheartedly.
the public free repositories shouldnt have to know about or deal with the private commercial offerings of indiviual companies.  But the people who purchase VmWare should be able to add  

deb [http://www.vmware.com](http://www.vmware.com) hoarty restricted {key=1234-xyz7-12345}

to their sources list, and vmware should show up as a package in synaptic.

---

### Post by az on 2005-09-29
[QUOTE=brentoboy]One feature missing from aptitude (for obvious reasons) is support for commercial apps.  Which, when you consider the roots of aptitude makes sense. It comes to us from Debian / gnu Linux - the home of the free - as in freedom.  The concept of a "commercial app" is anti-gnu.
But, aptitude needs to progress beyond its roots - in order to meet the needs of the community.  Companies (like vmware for instance) need to be able to offer a repository for their proprietary stuff.
Here is how it would work.  In your sources list (or in your settings area of synaptic) you would fill in a url and stuff just like you do for free repositories - then, you would provide an extra "key" that uniquely identifies you to them - like the install key that vmware offers to let you download their stuff.
All apt needs to do is "login" with this key to the proprietary repository, and then vmware and related offerings are available in your package list.  you can then apt-get install vmware and you don't have to bash your brains out to get "special" software.
They can do whatever they want on their end to drop misused keys and stuff, so it isn't like they are giving their stuff to the world.  They can also keep people up to date the same way the rest of Ubuntu is updated.  It would check for updates and tell you when there is a new version you could download and apply.
Any comments? Am I going somewhere good with this? Is this a terrible idea?[/QUOTE]


Providing means for proprietary software to be installed by apt is already there.  All they have to do is create the repositories.  Just like fetching wine from winehq instaed of the Ubuntu repositoryes.

As for adding key for a particular package in apt, well, that is a step backwards.  The individual application should take care of that, not apt.

And progressing beyond it's roots is bollocks.  Free software is more advanced than proprietary software.  The point is that you do not need proprietary software anymore.  It is a limited and limiting developmental framework.

---

### Post by brentoboy on 2005-09-29
[QUOTE=azz]The point is that you do not need proprietary software anymore.  It is a limited and limiting developmental framework.[/QUOTE]

The *intent* is that I dont *need* proprietart software anymore. The truth is that VmWare is the best pc emulator (right now) and the open source nv driver just isnt the proprietary one.  ... and on, and on.

Open source is great for applications that are so universal that they have a community, but there will always be one or 2 programs worth buying.  They should be just as easy to install (once you buy them)

No need to step outside of the built in installation mechanizm just to use a piece of software that was written by a company who wants to charge for it. - so long as you have connection to their repository.  And it is only fair that they can protect thier repositories from people they dont want to give access to.

OpenOffice.org is better than msoffice becuase it was first compatible, you beet out the other guy by accepting them first, and then doing better.  Not by pushing them away just becuase they are different - that is the microsoft way.

like it or not, proprietary software exists, and some of it is worth paying for (until a community replaces it)

---

