---
title: "The best wiki is ... ?"
date: 2008-01-17
forum: The Cafe
---

### Post by tjk on 2008-01-17
Okay, I need this "community's" advice.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]  I've spent many many hours researching and trying out different wikis.  The biggest frustration that I have is that they are nearly impossible to install.:confused:  The wikis that are self-contained (or desktop or standalone) wikis are usually very basic.  And the few web wikis that I got running are far to complex for me -- and even worse I don't know enough about security to guarantee that the wiki is totally private.  In summary, I'd like a wiki that is easy to install, secure/private, has a HTML (and WYSIWYG) editor, and has multiple ways of linking and viewing information.

So now I hope you'll take a minute to respond:[INDENT][IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] What wiki(s) do you use (or have you used) and why do you use it?
[/INDENT][INDENT][IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] And most of all, was it easy to install -- or  better still, would it be easy for an amateur to install?[/INDENT]

---

### Post by DoktorSeven on 2008-01-17
The only wiki software I used for any period of time was MediaWiki, which is what Wikipedia uses.  It was pretty easy to install, though advanced configuration had me directly editing source files.  Still, their documentation is very thorough on what to do.  Definitely not so simple that you can just drop it in and go unless you need just a very basic wiki, but nothing horribly complex, either.

I have tried many others, but they are just far too simplistic or feature-limited compared to Mediawiki.

---

### Post by Polygon on 2008-01-18
mediawiki also looks the best in my opinion.

---

### Post by Washer on 2008-01-18
Mediawiki here too. Is it easy to install.. not for an *amateur* amateur, but you're a server admin so yeah totally. I think on ubuntu (desktop gutsy) all I had to do was install apache & mediawiki & they took care of dependencies. Then move some files around...? Can't remember it was some time ago. The hardest part was importing some old database I had lying around. Never tried securing it.

---

### Post by ablaze on 2008-01-18
I'm using pmwiki a lot. Having played arounf with many different wiki engines, I always end up using pmwiki -> [www.pmwiki.org](www.pmwiki.org)

It's easy to set up, flexible, and has a huge amount of so called recipes to expand functionality.

---

### Post by bonzodog on 2008-01-18
Over at the udsf, we have just switched from mediawiki to dokuwiki.
I personally think Dokuwiki is much better than mediawiki, and much faster, as it does not require a database backend like mediawiki does.
It also seems to be more secure than mediawiki, and easier to protect against spam attacks.

---

### Post by nickburns on 2008-01-18
Media Wiki +1

If you want the easy install, with no headache I use twiki at work.  It is in the repos:

sudo apt-get install twiki, then find it at [http://yourhost/twiki](http://yourhost/twiki)

---

### Post by MCrittenden on 2008-01-18
TiddlyWiki doesn't have a WYSIWYG editor, and you're limited to plain or formatted text (no pictures, etc.), but it's a self-contained HTML file that you can take anywhere on a flash drive, is easy to use, quite powerful (especially via plugins), very customizable, blah blah blah. I love it. 

[http://www.tiddlywiki.com/](http://www.tiddlywiki.com/)

If you think you can live without a WYSIWYG editor, check it out. Otherwise, I'd also vote for MediaWiki.

---

### Post by popch on 2008-01-18
As usual, there is no 'best' wiki. There's at most a 'best suited for your particular needs'.

I sense a difficulty in your requirements. You want a web application (wiki, in that case) which is secure and which does not require any kind of expertise to put up.

That's not going to work. You either know what you do, or you get an insecure solution, product notwithstanding.

---

### Post by tjk on 2008-01-19
> **bonzodog said:**
> Over at the udsf, we have just switched from mediawiki to dokuwiki.
I personally think Dokuwiki is much better than mediawiki, and much faster, as it does not require a database backend like mediawiki does.
It also seems to be more secure than mediawiki, and easier to protect against spam attacks.

I looked at what some people said about MediaWiki and I found that it was too cumbersome for me.   As you say, I've read in many places that it is a slow wiki, but mostly it didn't have quite what I was looking for. (See comparison of MediaWiki to WikkaWiki at: [http://wikkawiki.org/MediaWikiComparison](http://wikkawiki.org/MediaWikiComparison))

Dokuwiki, however, was one of my top five picks (I especially liked how developed and informative the DokuWiki website was) -- right now I've settled for WikkaWiki, it was easy to install and it is simple, but flexible (w/plugins) -- but I'm still looking...

---

### Post by tjk on 2008-01-19
> **popch said:**
> As usual, there is no 'best' wiki. There's at most a 'best suited for your particular needs'.

I sense a difficulty in your requirements. You want a web application (wiki, in that case) which is secure and which does not require any kind of expertise to put up.

That's not going to work. You either know what you do, or you get an insecure solution, product notwithstanding.

I agree with you that, in fact, there is no "best" server...  but I still like the idea of someone telling me what *they* liked "best". [COLOR=SandyBrown](I reserve the right to disagree, though.)[/COLOR]

As far as the security thing, well one has to start somewhere -- my philosophy is: [COLOR=DarkOrchid]**do something or nothing will get done**[/COLOR].  I have learned a lot about network security since installing my wiki and I have the sense that I will never know it all. :)

---

### Post by tickingaway on 2008-02-21
MCrittenden mentioned Tiddlywiki.  There's a similar project called "Wiki on a Stick" that you can find here [http://swik.net/stickwiki](http://swik.net/stickwiki) .

I too would opt for Mediawiki, if I were able to use it from a USB drive.  Has anyone gotten such a setup to work?

---

