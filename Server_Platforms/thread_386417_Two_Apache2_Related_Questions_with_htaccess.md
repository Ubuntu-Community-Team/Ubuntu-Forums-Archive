---
title: "Two Apache2 Related Questions with htaccess"
date: 2007-03-17
forum: Server Platforms
---

### Post by mikestefff on 2007-03-17
Hey..just got two quick questions here..very easy i am sure..

1) my website has three trap directories for spam bots to fall into and die. there is a single index.php in each directory but i am having a problem. i see bots are accessing the directory but looking for a different file other than index.php. so how can i use htaccess. or something else, to force traffic located ONLY in certain directories to go to a certain dir/file? i am not to good with mod_rewrite or whatever it takes..

2) i know it is smart to move rules in .htaccess to httpd.conf for apache. but how exactly does this work for apache2. which file should you transfer everything to? does anything have to change?

THANKS

---

### Post by MJN on 2007-03-17
> **mikestefff said:**
> 1) my website has three trap directories for spam bots to fall into and die.

That sounds rather a hopeful expectation? Can you elaborate? Presumably the file(s) in this directory produce lists of pseudo-random e-mail addresses generated on the fly that then get scraped? (e.g. [http://www.newtonnet.co.uk/people/default.php](http://www.newtonnet.co.uk/people/default.php)) Whilst this has the potential to be effective at polluting spammers lists don't for one moment think their bots are somehow going to 'die' in an endless loop - their connection to you will be one of many so chopping off this one connection is not really going to have any effect on its 'life'.

With regards to your question why are the spambots asking for files other than index.php? Are they not following a link into this directory? Specifically, how do they know the existance of this directory?

> 2) i know it is smart to move rules in .htaccess to httpd.conf for apache. but how exactly does this work for apache2. which file should you transfer everything to? does anything have to change?Put the access rules in the relevent <Directory></Directory> section of the appropriate <Virtualhost> container in the site at /etc/apache2/sites-available/default (or wherever your site config is, probably there though).

Mathew

---

### Post by tturrisi on 2007-03-17
> i see bots are accessing the directory but looking for a different file other than index.php
...and how exactly do you know this to be true?  Server logs?  If so, it may be futile to try to stop the robots.  The dirs-files they are seeking may be hard coded into the robot itself, it may be looking for default or common named dirs & files.  And you state "spam bots".  By that do you mean email harvesters? (a spam bot = an email address havesting robot)  If it's just search engine robots you can counter most of them using a robots.txt file.
[http://www.robotstxt.org/](http://www.robotstxt.org/)

---

### Post by mikestefff on 2007-03-17
I figured it out..

ErrorDocument 404 <address of trap file>

My traps do not give fake email addresses. They ban the IP that hits the dir/file for 45 minutes. After viewing logs I saw many requests to pages that didnt exist such as phpmyadmin/settings.php , or even gibberish requests that didn't exist. Just very strange behavior. These bots apparently were not following links and just common directory names I assume. There are links to the traps as well. So a combination of both should help.

---

### Post by MJN on 2007-03-17
> **mikestefff said:**
> There are links to the traps as well.

What happens to genuine surfers that might click on the link?

I trust you've got a robots.txt file that stops search engines from falling into the trap too?

Mathew

---

### Post by mikestefff on 2007-03-17
yes of course I have robots.txt preventing access to the pages

the links are invisible to humans

---

### Post by pjbgravely on 2007-03-18
Normally spam-bots are defined as computers that are part of a bot-net that spews forth most of the spam out there. Strange that it all comes from one brand of OS.

What you are seeing are bots from script-kiddies looking for insecure web apps (phpmyadmin is a web app for administering mysql) and the exploit of the month. You can't stop these hits and the IP addresses keep changing. 

You can add an index file that redirects to your traps in places you don't want acessed, but there might be better ways to lock these down.

Paul

---

### Post by mikestefff on 2007-03-18
the first links on the top of all of my pages points to trap directories..bots can see them..humans cant..

what else can I do?

my hope is either: they see the dir's in robots.txt saying disallow so they want to go there, its the first links so they follow them, or the dir's are named after common places for bots to go, so they get caught..

---

### Post by mikestefff on 2007-03-18
lol by the way I did have another problem when i first posted...anyone check that out?

thanks

---

### Post by pjbgravely on 2007-03-18
> **mikestefff said:**
> lol by the way I did have another problem when i first posted...anyone check that out?

thanks

That depends, if you installed apache2 from source then httpd.conf is where everything goes. 

If you installed the official Ubuntu apache, then things are quite different. Some things can go into /etc/apache2/apache2.conf but to really understand how things are different you should read the readme. (see attachment)

---

### Post by MJN on 2007-03-18
> **mikestefff said:**
> lol by the way I did have another problem when i first posted...anyone check that out?

thanks

I already answered that one - see second post above!

Mathew

---

### Post by mikestefff on 2007-03-18
Haha oh I totally missed it...

Will that work with mod_rewrite ? Being inside the <Directory> ?

---

### Post by MJN on 2007-03-18
Everything inside <Directory> basically applies to that directory tree only - I should've clarified this before. Hence, anything you want on a per-directory basis (e.g. password-protect a particular directory) would therefore belong in there.

Mod_rewrite rules are quite happy inside <Directory> containers, although just be aware of the caveat above.

Mathew

---

### Post by mikestefff on 2007-03-18
works perfect..thank you very much

---

### Post by MJN on 2007-03-19
That's great - thanks for getting back!

Mathew

---

