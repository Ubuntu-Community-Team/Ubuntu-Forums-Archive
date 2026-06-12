---
title: "Content management"
date: 2004-12-16
forum: Server Platforms
---

### Post by az on 2004-12-16
What would your choice be for a simple CMS.  

I am looking for something with a small learning curve that can handle simple database functions (conference registrations, address changes...)

So far, I am looking at Drupal.  It's appeal is that it is free software and that there seem to be the modules that I would need.  I will try to install it to see how hard it is to configure.  

Any suggestions would be appreciated.

I am curious why this forum runs on non-free software (vBulletin) when free alternatives exist.  I am not complaining; it's just an observation.  What are the advantages in this case?

---

### Post by dataw0lf on 2004-12-16
It depends on what language/database you're looking for.  Perl? Python? PHP? MySQL? PostgreSQL?  I've never used an out of the box CMS, to be honest.  However, [www.hotscripts.com](www.hotscripts.com) has thousands of CMS scripts.  
dataw0lf

---

### Post by az on 2004-12-16
I am not much of a programmer myself and I would not be maintaining this site for long.  I am looking for a set-and-forget application.  

I guess you can say that I will sacrifice powerful options for ease of use.  Those who would be maintaining the site in the future would have next to zero computer experience.

Web-based configuration is appealing here.

---

### Post by burlap on 2004-12-16
Look at [http://cmsmatrix.org](http://cmsmatrix.org) - there you can compare different cms to find one with all the features you need. 

I am a complete newbie in terms of site building, however I have managed to make something of TikiWiki (CVS version has multilingual features, crucial for the site I am designing), but it seems to be quite difficult at first sight, so you have to be, well, brave to use it (if people who will later maintain your site use linux everyday - they can manage). 

But my experiences are in general quite negative - mambo was really disappointing, typo3 had too many unclear options. Haven't tried drupal though. I have an impression that all the cms even if they seem easy, they are difficult to set up properly (especially when you start adding some real content) and they will be quite difficult to maintain. Just like Linux distro (notwithstanding Ubuntu - I thought it was relatively painless (for me it was) until my brother has started installing it, it's day 5 now).

---

### Post by jdodson on 2004-12-16
[QUOTE=azz]What would your choice be for a simple CMS.  

I am looking for something with a small learning curve that can handle simple database functions (conference registrations, address changes...)[/QUOTE]

i have used mambo before, and it is progressing very nicely. [www.mamboserver.com](www.mamboserver.com)

you could also checkout phpnuke, one of the original free CMS : [http://phpnuke.org/](http://phpnuke.org/)

[QUOTE=azz]So far, I am looking at Drupal.  It's appeal is that it is free software and that there seem to be the modules that I would need.  I will try to install it to see how hard it is to configure.[/QUOTE]

this one looks GREAT!  i think i am going to give it a try.  


[QUOTE=azz]I am curious why this forum runs on non-free software (vBulletin) when free alternatives exist.  I am not complaining; it's just an observation.  What are the advantages in this case?[/QUOTE]

i talked to ubuntu-geek about this personally and i was told that it was changed over because vBullitin had features that phpBB did not.  so the system was switched because this one was better in the long run i guess.  i really like vbulliten, it is pretty slick, the only cavat is that you have to pay for it though.....

---

### Post by eric_andresen on 2004-12-17
I would stringly recommend phpNuke. 

[http://www.phpnuke.org/](http://www.phpnuke.org/)

There is a huge community around it, and lots of support available.

Heck, if I can get it running anyone can do it!

---

### Post by az on 2004-12-21
Thanks for the suggestion but phpnuke is not GLPed and it does not seem as friendly to non-computer people.

Drupal seems nice but I am having a few issues.  I can't seem to access it properly from a remote machine (on my lan)  When I access it from localhost it runs well (on a pentium one - SSllooww)  From the other machine, I get the text from the main page, but no icons, nor do any links work.  I get "connection refused from localhost."

I think this must be a problem with the mysql user and database - I probably have it named wrong...

On another note, how does plone stack up?  What about just plain zope?
They seem to have lot of the features that I need...  Does anyone have any experience with either of them?

---

### Post by az on 2004-12-22
Burlap -  Thanks for the cmsmatrix link.  Top notch!  What version of mambo did you use that was dissapointing?


To answer my own question regarding Plone/Zope, I found this comparison with Drupal:
-quote-
I think I am qualified to answer this.
achilles - December 1, 2004 - 14:10
I'm one of the core developers on Plone, and also a user of Drupal. I don't find my loyalties divided, as I find both systems suitable for very different purposes.

I'm going to assume most people reading this site are familiar with Drupal already, so I won't cover the feature set or intended audience, except to say that Drupal works pretty well for smallish community sites that require minimal expenditure of effort in setup, and a defined set of core features.

Plone, on the other hand, whilst being reasonably suited to that task, is a bit of a different beast. Its development has arisen out of the Zope application server (in itself a gargantuan project), and the Zope Content Management Framework, neither of which actually really gives you a website.

Plone is the user layer on top of Zope and the CMF that offers an incredible amount of functionality out-of-the-box that you just won't find anywhere else. Features like: end-to-end i18n; localisation; placeless content; pluggable, configurable workflow; messaging; granular security (in way more depth than Drupal); and so on.

Now, there are 2 main differences that you're going to look at when choosing Drupal or Plone. The first is the scale of the undertaking. Zope/Plone is fantastic for large-scale projects, as you can do amazing things with it in a very short period of time. I regularly take on very large scale projects and use Plone for them. Drupal doesn't meet my needs in that space, yet. Zope and Plone as a combination provide an almost unparalleled development platform, and, even traditionally as a PHP programmer myself, I will happily assert that Python is the more appropriate choice of programming language to meet these goals.

The second thing that you're going to need to look at is usability. Now, I'm a hardcore developer. I tend to think through problems in terms of code issues. However, when it comes to actually *using* Plone on a daily basis for my own personal website, it drives me nuts. I find Drupal's configuration, layout, content editing, and style to be far more comfortable than Plone's. I'm really not a fan of Plone's default skin, but that's as a matter of personal preference. Technically, and from an accessibility viewpoint, Plone and Drupal are on a pretty even footing.

Just as a quick guideline, I reimplemented my personal website last night in Drupal as part of a familiarisation exercise for another project that I'm getting involved in. Now, bearing in mind I've been building websites commercially for about 9 years, this took me about 2 hours, from no prior knowledge of Drupal, but Ihaven't done any there reworking yet. The last time I did it in Plone took me about 8 hours, including a full skin rework, but I'm confident I could build a full Plone site for my personal needs in about 3 - 4 hours now.
-quote-

---

### Post by geek404 on 2005-01-02
I would suggest Mambo.  Especially if you are going to turn it over to end users.  I run a personal Mambo site and have about 10 co-workers who now run it after my suggestion to use it for their websites.  We have even selected mambo to use for our new training site for our customers since we can turn over content creation to our trainers without them needing to learn HTML.  Overall I have been extremly happy with Mambo after trying out serveral different CMS's.

---

### Post by HiddenWolf on 2005-01-06
Damn. I'll be trying some of these things.

I'm now coding my first database-driven website in php, and I do it for sport, but this is good stuff. :-)
I'll go and look to see what idea's I can steal. :-)

---

### Post by dataw0lf on 2005-01-06
Now, we can start in on the grand MySQL vs Postgres argument....
;)
dataw0lf

---

### Post by HiddenWolf on 2005-01-06
Damn. I'll be trying some of these things.

I'm now coding my first database-driven website in php, and I do it for sport, but this is good stuff. :-)
I'll go and look to see what idea's I can steal. :-)

---

### Post by az on 2005-01-06
Well, actually...  I was just going to ask about postgreql vs Mysql.

Drupal is excellent.  I use the 4.5.0 version and a number of additionnal modules.  I started with Mysql since certain modules were built only for mysql.  I will not be using any of these modules after all and I will be trying out postgresql.  Would anyone share their experience with the differences between these two database servers?

Using Drupal, I have zero interaction with them. What I would find interesting is to know things about their performance.

---

### Post by Dustin Wyatt on 2005-01-07
Here's one I've been considering using:

[http://www.geeklog.net/](http://www.geeklog.net/)

---

### Post by meneer on 2005-01-08
I'm using [e107](http://www.e107.org) on another system. Lots of [plugins](http://www.e107coders.org) and personalisation options.

---

### Post by machiner on 2005-01-08
mambo 4.5-1.09

And you can set it up so the search engines absolutely adore your site.

---

### Post by jakeslife on 2005-01-08
I do the mambo as well (4.5.1)

---

### Post by garret on 2005-01-08
Give SocialMPN a try [http://socialmpn.com](http://socialmpn.com), one of the big up and comers in this space.

---

### Post by cpinto on 2005-01-08
[QUOTE=azz]Well, actually...  I was just going to ask about postgreql vs Mysql.

Drupal is excellent.  I use the 4.5.0 version and a number of additionnal modules.  I started with Mysql since certain modules were built only for mysql.  I will not be using any of these modules after all and I will be trying out postgresql.  Would anyone share their experience with the differences between these two database servers?
[/QUOTE]

What I can say is that PostgreSQL is far more advanced than MySQL: you've got triggers (I understand that mysql already suports this but it's been in postgres like, for ever!), stored procedures, transactions, multiple stored procedure languages (you can do stored procedures in perl, python, java, tcl). 

If I have to go with one, usually I choose postgres. Personally I only use MySQL for relatively small stuff (my personal blog, postfix database that doesn't have a lot of hits - yep, that right, postfix).

I also feel that the postgres shell is a bit more advanced. The only thing that turns me off is the authentication configs for postgres (editing psql_hba.conf file) but once you get a hold on it you'll be fine. MySQL's authentication is quite straight forward.

At the end of the day, it all depends on what you want from it.

---

### Post by josel on 2005-01-08
Well, postgres and mysql have different target audiances. You really dont need ACID compliance with a CMS system, speed is more important so i would recommend mysql :-)

---

### Post by az on 2005-01-08
Thank you all for the wonderful suggestions.  Drupal has been satisfying my needs for a few weeks now and so I think I will stick with that.  Mambo was a contender.  It had a just slightly easier installation with its installation interface, but it left me feeling a bit short.

Also, I read from the Mambo installation manual 
([http://mamboforge.net/cgi-bin/cvsweb.cgi/*checkout*/mambo/4.5_manuals/english/install/MamboInstallation.pdf?rev=1.2&content-type=application/pdf](http://mamboforge.net/cgi-bin/cvsweb.cgi/*checkout*/mambo/4.5_manuals/english/install/MamboInstallation.pdf?rev=1.2&content-type=application/pdf))
that the WYSIWYG editor only seems to work on internet exporer?  Is this so?  The HTML WYSIWYG editor that I use in Drupal works just fine in Firefox.

Also, forums are in the Drupal base install.  I had a hard time finding documentation for installing modules (like the forums) in Mambo.  I did, however, give up quickly.



"speed is more important so i would recommend mysql"

Does anyone dissagree with that?

---

### Post by steffen on 2005-01-09
[QUOTE=azz]Thank you all for the wonderful suggestions.  Drupal has been satisfying my needs for a few weeks now and so I think I will stick with that.  Mambo was a contender.  It had a just slightly easier installation with its installation interface, but it left me feeling a bit short.

Also, forums are in the Drupal base install.  I had a hard time finding documentation for installing modules (like the forums) in Mambo.  I did, however, give up quickly.
[/QUOTE]

Any other differences between Mambo and Drupal? I have looked at the general UI for Mambo, and it looks extremely slick.

I want a CMS where I can have a centralized login for different users, managing different domains, and which is easy to set up for a new domain and a new user. Also, making and inserting templates should not be too complicated.

The lower-level users should be able to add new content, pages, links, headlings, pictures, and preferably directories and buttons.

Any suggestion on Drupal v. Plone v. Mambo on this?

> Also, I read from the Mambo installation manual  ([http://mamboforge.net/cgi-bin/cvsweb.cgi/*checkout*/mambo/4.5_manuals/english/install/MamboInstallation.pdf?rev=1.2&content-type=application/pdf](http://mamboforge.net/cgi-bin/cvsweb.cgi/*checkout*/mambo/4.5_manuals/english/install/MamboInstallation.pdf?rev=1.2&content-type=application/pdf)) that the WYSIWYG editor only seems to work on internet exporer?  Is this so?  The HTML WYSIWYG editor that I use in Drupal works just fine in Firefox. 

A WYSIWYG editor is also really important, preferably one that works with Firefox, and preferably also on Apple Macs. It should be pretty easy to change the default editor in Mambo, shouldn't it? Anyone know whether FCKEditor works on Mac OS X?

...ahh, and a good, active developer forum is really important as well  :) I tend to make buggy contribs :-?

---

### Post by shimon on 2005-01-09
YUCK who the hell recomended puke
its hackable in 2 seconds it doesn't work...

i highly recommend dragonflycms.com GPL'd works AND use hardly any of the server power....

think of phpnuke aka puke as winbloze

e107 as red hat

and dragonflycms as ubuntu

---

### Post by garret on 2005-01-09
Agreed. PHPNuke has a history that can't be ignored, and it's for lack of security. If you value your content or web presence at all, I would stay clear of PHPNuke.

Garret

---

### Post by machiner on 2005-01-09
The WYSIWYG editor in Mambo makes crappy code - I don't see why people would use it -= and there are actually 3 or 4 you could install, I know one worked in Fire(bird) in windows -- some time ago.

THere is actuall a component for Mambo that you can install to CLEAN UP the crappy code that its editor makes.

But then again, when I made html sites I used notepad.

good luck with your CMS

---

### Post by shimon on 2005-01-10
if you want a wysiwyg editor try nvu

---

### Post by steffen on 2005-01-12
Does anyone have experience with EZ ([www.ez.no](www.ez.no))?

From what I can see on [www.cmsmatrix.org](www.cmsmatrix.org), it seems to have a lot of functions. Apparently you're charged extra for a WYSIWYG editor, but I guess that simply downloading FCKEdit from Sourceforge.net and putting it into the PHP should be an easy job.

---

### Post by steffen on 2005-01-13
[QUOTE=azz]Also, I read from the Mambo installation manual 
([http://mamboforge.net/cgi-bin/cvsweb.cgi/*checkout*/mambo/4.5_manuals/english/install/MamboInstallation.pdf?rev=1.2&content-type=application/pdf](http://mamboforge.net/cgi-bin/cvsweb.cgi/*checkout*/mambo/4.5_manuals/english/install/MamboInstallation.pdf?rev=1.2&content-type=application/pdf))
that the WYSIWYG editor only seems to work on internet exporer?  Is this so?  The HTML WYSIWYG editor that I use in Drupal works just fine in Firefox.
[/QUOTE]

I just tested Mambo's WYSIWYG editor in Firefox (the default Firefox for Warty, whch is 0.9) and it works just fine! It's doesn't have too many features though - can't add pictures and tables with it, etc. which I would expect.

The Drupal demo on [www.opensourcecms.com](www.opensourcecms.com) doesn't include a WYSIWYG editor at all, it seems.

Mambo also has nicer looking menus. Don't know how extensive these demos are, but I hope they give a nice overview of the possibilities.

---

### Post by az on 2005-01-13
"I just tested Mambo's WYSIWYG editor in Firefox (the default Firefox for Warty, whch is 0.9) and it works just fine! It's doesn't have too many features though - can't add pictures and tables with it, etc. which I would expect."

The drupal default htmlarea plugin includes tables and images.  It works really well.


"The Drupal demo on [www.opensourcecms.com](www.opensourcecms.com) doesn't include a WYSIWYG editor at all, it seems."

No, it is a module you have to add on.  It took me about thirty seconds to find it, download it and install it.
How easy is it to find and install modules (or the equivalent in mambo) in Mambo?  I could not navigate the documentation site very easily.  It seemed that the modules were a bunch of undocumented files.  Like I said earlier, I gave up quickly, though.


"Mambo also has nicer looking menus. Don't know how extensive these demos are, but I hope they give a nice overview of the possibilities"

It seems to me that every Mambo-made page I see has just about the same theme.  I find it unfriendly.  The Drupal Pushbutton theme (standard install) is big and friendly with nice menus.

I am running this on a 200 MHz machine and I am impressed at the response time.  Most pages take about two seconds from click to rendered.  I was not expecting that.


Drupal is not an all-in-one solution, and it can be a bitch to figure out.  But overall, I seem to be satisfied.

---

### Post by steffen on 2005-01-13
Thanks for for info azz!

Would you say that the Drupal demo on opensourcecms.com is not representative for what Drupal could easily become if adding a few modules?

The only thing I really need for a CMS is ability to customize the templates down to the very bottom, and then give access for the owner of the site to take care of content, pictures, menus, what to go on the front page, etc. That is why menus and WYSIWYG is so important.

Would you say that Drupal would be the best alternative then?

Initially I was thinking about setting up a Plone server, but if Drupal should do the work, I'll probably be happy with that.

---

### Post by steffen on 2005-01-13
I know, I'm asking too many questions... But I really want to get this right the first time.

I have about 20+ websites that are going to start using this system. Currently they send all updates for their website to me, but I want them to be able to log in themselves to edit content easily.

All the websites have totally different layout and design, and some require password protected directories. But other than that, only simple functions like calendar, adding documents (uploading PDFs), etc. are necessary.

Would you still recommend Drupal, considering these sites should all have different templates, and that I have 20+ of them hosted on one server?

...or should I go for Plone?

---

### Post by az on 2005-01-13
"Would you say that the Drupal demo on opensourcecms.com is not representative for what Drupal could easily become if adding a few modules?"

It is what it is.  That is an out-of-the box drupal install with nothing added and nothing configured.

"Would you say that Drupal would be the best alternative then?"

You are asking me?  I was the first to ask the question!

"Initially I was thinking about setting up a Plone server, but if Drupal should do the work, I'll probably be happy with that"

If you are comfortable with plone, use plone.  I do not think that I could handle plone.  I am sure that the ones who will be tending to the site on which I am working will not be able to handle plone.  It depends on your needs.  Plone seems to be quite powerful.  I refer you to my post a few weeks ago  on this thread regarding plone versus Drupal.  I quote the author of Plone.  Read it.  That is pretty much what you are asking.

---

### Post by andlinux21 on 2005-06-17
Machiner how do you set up your mambo site so the search engines just love it????

---

### Post by Beernut on 2005-06-18
You might want to check out [http://xoops.org](http://xoops.org) Xoops is a fantastic CMS.  I used to use MyPHPnuke but that project seemed to be dead in the water.  XOOPS has a very active and helpful community and has good security.  My site [http://NEGeocaching.com](http://NEGeocaching.com) uses it.

---

### Post by Yoda_Oz on 2005-11-28
does anyone here use joomla?

ive set up a basic joomla install in 5 mins, not even.

joomla is the next generation of mambo. apparently the mambo developers got shitty with the mambo execs so they started their own cms. so everything that works in mambo works in joomla too.

the worst thing about joomla is lack of documentation. it took me hours to work out how to install modules and components, as well as new pages and menu items! but ive just started to get the hang of it now and its becoming really really easy and user friendly... and quite powerful.

i havent set up any website as yet. im only doing this on a free web server for the time being to have a play around with the joomla install. you can have a look at what i have at the moment...
[http://www.cbrooker.gwgaming.net](http://www.cbrooker.gwgaming.net)

I even have a blog there about installing breezy onto my laptop. i havent finished the blog yet but im getting there... time is something i dont have much of at the moment!

i maintain 2 sites at the moment which dont use cms:
1. [http://www.divingnsw.org.au](http://www.divingnsw.org.au)
2. [http://www.huda.org.au](http://www.huda.org.au)

anyway, looking at my sites. do you think drupal might be better than joomla to incorporate these diving websites?

by the sounds of it, it seems like drupal is much more user friendly to start of with but a little less hands on and therefore less powerful tham joomla. am i right?

---

### Post by az on 2005-11-28
Joomla is a wonderful example of when to fork.

You can create a documentation wiki page about setting up joomla in ubuntu on the wiki.ubuntu.com wiki.  That would be helpful.  I think the big reason why people do not use it is because of the lack of documentation.

---

### Post by Yoda_Oz on 2005-11-28
> 
Joomla is a wonderful example of when to fork.


i dont understand that statement...

anyway. yeah i might do that wiki thing. that will be my first ever wiki though. its not a hard deal to set up joomla.

i just registered my domain name and i have signed up for website hosting. i did my domain name registration with [http://www.godaddy.com](http://www.godaddy.com) and my web hosting with [http://www.streamline.net](http://www.streamline.net).

pretty soon ill have a decent working joomla site up and running. ill document all my actions!

---

### Post by Alex132112 on 2007-05-15
> **dataw0lf said:**
> It depends on what language/database you're looking for.  Perl? Python? PHP? MySQL? PostgreSQL?  I've never used an out of the box CMS, to be honest.  However, [www.hotscripts.com](www.hotscripts.com) has thousands of CMS scripts.  
dataw0lf


[Mortgages pollution Equity Loans memory Equity Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

