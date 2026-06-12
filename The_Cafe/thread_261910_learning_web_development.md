---
title: "learning web development"
date: 2006-09-20
forum: The Cafe
---

### Post by maniacmusician on 2006-09-20
Hello everyone,

I need some help. I'm looking for a crash course in website design...using a WYSIWYG type of editor such as screem or quanta plus. (quanta looks pretty promising...but the "handbook" that was included with it was missing all the tutorials and help pages). I have some basic html experience from years ago.

I know I can just google around and whatnot, but I know that a lot of you are quite proficient at website design so I thought you could point me in the right direction. Also, since i'll be using linux to design these websites (I don't have windows anymore, so its not even an option), I thought you would know the right resources to go to.

any suggestions?

thanks a lot.

---

### Post by DoctorMO on 2006-09-20
[http://www.w3schools.com/](http://www.w3schools.com/) has always been my one shop stop. but I tend to code html in kate/gedit because it makes me feel like a man! ;-)

Getting all the elements in div tags so you can apply css sheets is the biggest boon, yes with most html editors (WYSIWYG) you end up loosing this advance. so what you gain in speed to produce you loose in maintence and lexability later on.

did you try Nvu?

---

### Post by maniacmusician on 2006-09-20
I did, but the point is that having never used any kind of text editor besides notepad in windows (and i made some really crappy websites with that), I don't know how to use html editors. 

the reason i like quanta is that it supports CVS, which will be useful later on. Thanks, i'll check out the link

---

### Post by mustang on 2006-09-20
As someone who was in the same boat at the beginning of this summer as you are right now, perhaps I can help you at.

First, you need to decide if you *really* want to learn HTML (that is, code by stratch) or get by with WYSIWYG editors. I found a hybrid approach to be the best: I had NVU do all the grunt work and then I copy and pasted into gEdit and tweaked as needed. 

One of the great things about web design is that there are **tons** of resources out there--moreso I would argue, then for programming. Literally every specific web design question is a google search away. From web developer blogs to web dev forums, it's all there.

In terms of specific software recommendations, I can only advise you from own experiences: a combination of NVU & gEdit. I've heard good things about BlueFish and Screem---never used them though.

If you're going to need php or mysql, I highly recommend setting up [XAMPP]("http://www.ubuntuforums.org/showthread.php?t=223410") on your computer or server. The installation will take minutes and it's really easy to turn on/off with the script provided. If you opt not to develop locally and still need php & mysql, try awardspace.com. It's pretty slow and updating code is a nightmare (no SSH so you have to use their web page editor = more time spent clicking/loading around than actual coding) but free is free. (Personally, I am developing locally and come launch time, I'll probably jump in on the netfirms $10/yr deal. Already snagged a domain name from godaddy for ~$7/yr).

Here are some of my favorite webdev resources:

forums---good place to search if you couldn't find the answer to your question on google

[http://www.webmasterworld.com/home.htm](http://www.webmasterworld.com/home.htm)
[http://www.sitepoint.com/forums/](http://www.sitepoint.com/forums/)

PHP:

[http://www.tizag.com/](http://www.tizag.com/)
[http://www.php.net/manual/en/](http://www.php.net/manual/en/)

CSS:
[http://www.w3schools.com/css/default.asp](http://www.w3schools.com/css/default.asp)

HTML:
[http://www.w3schools.com/html/default.asp](http://www.w3schools.com/html/default.asp)
[http://www.htmlhelp.com/](http://www.htmlhelp.com/)
htmlgoodies.com (basic)

Hope it helps! Happy web deving!

edit: oh by the way, accomodating all browsers is a headache--especially with parts of CSS. My advice: code for opera, tweak for firefox and IE.

---

### Post by maniacmusician on 2006-09-20
wow! thanks for all those links! lol that will keep me busy for weeks.

---

### Post by szf on 2006-09-20
The beautiful thing about the web is that sharing is a given... with rare exceptions [except for wholesale site-lifting] no one seems to mind. I am inspired by [what I find to be] great [web designers]("http://www.456bereastreet.com/") and follow their advice. Then I follow the links to their peers, and so on, and so on...

---

### Post by maniacmusician on 2006-09-20
heh i don't think I know quite enough to take that approach yet, but thanks for the link

---

### Post by GuitarHero on 2006-09-20
Stay away from WYSIWYG editors if possible.  They create sloppy, non compliant code usually.  Gedit works wonderful for html, and html if very easy to learn.

---

### Post by Bloodfen Razormaw on 2006-09-20
You should definitely stick with Quanta.  It lets you work with WYSIWYG or the code itself equally well, and you can watch the web site appear as you code it.  It helps immensely having the web view updated in real time in a split pane view.  No switching back and forth between programs or tabs to test it.  It also acts as a complete IDE for scripting, and has fantastic project management.  The only other HTML editor in the same league as Quanta is Dreamweaver, which of course is commercial, proprietary, and not available for Linux. Nvu is the next step down, not nearly as advanced as Quanta, and much heavier and slower.  Nvu is to Quanta what Frontpage is to Dreamweaver.  Once you get below Nvu everything left is just a glorified notepad.exe, in which case you might as well use a real text editor.

As for learning, I prefer to just use w3.org.  The code is easy to learn.  It is good design that is hard.  For that you just have to find designs you like and figure out what you like about them.

---

### Post by maniacmusician on 2006-09-20
thanks for your suggestions. i'm aware that WYSIWYG editors are sometimes an annoying hassle, but like Bloodfen said, Quanta lets you edit with WYSIWYG or directly to the code. I'd appreciate some specific information that can help me with quanta, but all the general links were awesome too! they'll keep me busy for a long time

---

### Post by majesticturkey on 2006-09-21
Quanta is nice because you can do a little WYSIWYG to start off, and fix things up in code. I learned HTML bass-ackwards though, by first learning PHP via a phpBB site, then getting into HTML. If you're as stubborn as I am, and as driven, I highly recommend you just jump straight in and start screwing around with a cheat sheet nearby of tags and attributes. Much like learning a language, the easiest way is just immersing yourself.

But if you decide to use Quanta, I highly recommend you review all code you create, and try to slim it down.

---

### Post by maniacmusician on 2006-09-21
are there any resources on actually using WYSIWYG editors (specifically quanta?) 


thanks majesticturkey, i'll definitely glance over the html. that's what I like about quanta, you can actually do that, and edit it easily.

---

### Post by Bloodfen Razormaw on 2006-09-21
The only resources I can think of for specifically using Quanta is the Quanta handbook, which should be fairly good.  If it isn't installed, you can read it at docs.kde.org.  In general, though, the basics of Quanta should be easy to pick up.  Just think of the WYSIWYG display as a word processor and build your page.  WYSIWYG is a good way to start, since you can't create malformed or non-standards-compliant code.  Turn on the HTML code view to so you can see the HTML code being generated while you make the page, to help you learn HTML.

I actually like Quanta for the opposite reason as you, majesticturkey: being able to write code by hand first and then edit it in WYSIWYG mode without having my code mangled.  It's nice to be able to make your web site and then edit the text in the web display itself (being able to use multiple spaces without &nbsp; is nice!), and not have the web site's code completely rewritten.  I haven't seen that in any other free editor, or even most commercial products *coughFrontpagecough*.

---

### Post by kburnik on 2008-10-30
I've found a site where a Web expert talks about web technologies and mechanisms,
[http://www.invision-web.net]("http://www.invision-web.net")
I've signed up to the site as 53rd member, the tutorials starts when there are 200 members..

The guy says it's free... So i tought why not give it a shot...

---

