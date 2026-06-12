---
title: "What do you want in a Content Management System?"
date: 2007-01-27
forum: The Cafe
---

### Post by v8YKxgHe on 2007-01-27
Hey,

This time last year I began coding a open-source PHP content management system that complies with W3C standards, is easy yet powerful to use and offers a lot of flexibility. Progress has been slow since I'm the only one coding it and I have college work which gets in the way, but I'm hoping to release it May/June this year (version 105 or 106).

I'm currently in the process of pretty much re-coding it all to improve security, speed, Search Engine Friendly URLS and to make it even more customizable, so I am wondering - what features, or what would you like to see in a CMS if you were going to use?

If anyone would like to help code I would highly appreciate it as coding an entire CMS by my self is taking some time!

Regards,

---

### Post by v8YKxgHe on 2007-01-31
No one wants anything from a CMS? Cool, less work for me. =) Come on, there has to be something you want!

---

### Post by Brunellus on 2007-01-31
expand the acronym.  I know you devs are acronymphomaniacs, but seriously.

---

### Post by v8YKxgHe on 2007-01-31
CMS = Content Management System, I said it in the first sentence:

> coding a open-source PHP content management system

Other major CMS's are Mambo, Drupal, Jaws etc; they allow you to quickly and easily create and mange content.

---

### Post by Brunellus on 2007-01-31
> **AlexC_ said:**
> CMS = Content Management System, I said it in the first sentence:



Other major CMS's are Mambo, Drupal, Jaws etc; they allow you to quickly and easily create and mange content.
thread title changed to reflect nature of question.  

I'd like a pony.

---

### Post by v8YKxgHe on 2007-01-31
Ok thanks! sorry for the confusion.

Well if you really want a pony, then I suppose I could put one in! :lolflag:

---

### Post by Wartooth on 2007-01-31
This is something I'd love to answer at great length as it is an issue I'm currently facing with a couple of my websites, but my brain power (what little there is) is being directed to something else at the moment.  

I know that I need a nice, brainless CMS that would allow me to make quick and easy updates, add trusted members to the list of folks who could also contribute content, and MOST OF ALL would have a way of proving that the templates chosen would render correctly in various browsers.   

I had happily fought with a couple of templates in Joomla, thought everything was fantastic, then had my husband open it up in IE and was gutted to see the mess IE made of it.  I lost all motivation at that point and have only half-heartedly attempted to go back at it. 

A simple way of altering the CSS/templates would be lovely, too.  I have a book and other resources to go through with CSS stuff, but I just haven't had the time to learn much beyond making a very basic and blah CSS, and it's not enough for me to dive into a template and alter it and have the slightest clue as to what I'm really changing, beyond something like colors. 

I could probably rant at length if given the chance. :)

---

### Post by raublekick on 2007-01-31
i would like to see something like wordpress, but a little more powerful. something like joomla, but a lot less powerful :)

the problem with joomla is that it is just waaaay too complicated. there is so much by default that might not be needed. wordpress is the opposite (and what i currently use), it basically just has the framework to set up a good blog, and if you put in the work (like i did), you can run a full website on it. 

something that each needs is better theme support. perhaps something like a basic theme framework first (set up a header, a footer, side columns, a main column, etc...). after the user sets up the basic setup, they can add little bits into each part. so you could have the basic framework for a header, and then have basic html/php for little parts like a poll or a category list, and those can just be placed into the parent parts.

---

### Post by Brunellus on 2007-01-31
threaded comments.  please.  Why is it that, say, drupal and wordpress have this aversion to actual threaded comments?  Is the blogosphere just too cool for threading?  

guess I'm gonna go back to usenet.

---

### Post by raublekick on 2007-01-31
hmm so it looks like there are at least two people wanting a better method for theming. i have some ideas so maybe we can do some collaboration. i have a site of my own that i can test thigns on, and i have been wanting to get my php skills sharpened.

---

### Post by v8YKxgHe on 2007-01-31
theming is actually something I've focussed on, so if I've done it right and it's easy then that box is ticked! If you look at a Mambo or Joomla template for example they are full of PHP code and other horrible yuck. The CMS I'm coding, TangoCMS, has a very easy way of theming 

All it is is 1 main html file which is entirely HTML, no PHP in it at all. You then add what are called "sectors" into the template file which are simply {S1} for Sector 1 or {S2} for Sector 2. These "sectors" pretty much define where content can go, then users/admins can then attach different content (like a poll, news, text etc) to different sectors. So I could attach the Poll module and an image to {S2} then maybe the Menu module into {S3}.

All of this is easily configurable and the user is not really exposed to the word "sectors" but instead a more human readable version, such as S2 could be located on the top bar, so it's human readable name would be "Top Bar" or what ever the author of the theme decided. So it's more like attaching the menu module to the Top Bar. 

raublekick, if you wanna help me out with ideas/code then just add me to msn and we'll talk =)

edit: Users/admins don't have to add the sector tags ( {S1} ) into the html file, this is done by the author of the theme to define where content should and can go, of course you can easily edit the html file to add more places for content - but there should really be no need.

---

### Post by Brunellus on 2007-01-31
man.  no threading and no ponies?

*grump*

---

### Post by Minyaliel on 2007-01-31
Something a la e107, only without the need to modify databases for hand if you screw up something (anything)... oh, and easily themeable for someone too lazy to learn anything other than html and css...

---

### Post by v8YKxgHe on 2007-01-31
> **Brunellus said:**
> man.  no threading and no ponies?

*grump*

Hehe, sorry - didn't see your other reply. Yeah I could easily implement a system-wide comments system that will allow users (with correct permissions) to comment on any page, you will of course be able to limit what pages the comment's system should show up on and you'll be able to configure it entirely, so you will be able to have threaded comments.

What sort of Pony would you like? One with pink spots?

---

### Post by v8YKxgHe on 2007-01-31
> **Minyaliel said:**
> and easily themeable for someone too lazy to learn anything other than html and css...

All you'll need to have knowledge in to make themes for it will be HTML and CSS.

---

### Post by Brunellus on 2007-01-31
threaded comments > * + pony

I am satisfied.

---

### Post by raublekick on 2007-01-31
> **AlexC_ said:**
> theming is actually something I've actually focussed on, so if I've done it right and it's easy then that box is ticked! If you look at a Mambo or Joomla template for example they are full of PHP code and other horrible yuck. The CMS I'm coding, TangoCMS, has a very easy way of theming 

All it is is 1 main html file which is entirely HTML, no PHP in it at all. You then add what are called "sectors" into the template file which are simply {S1} for Sector 1 or {S2} for Sector 2. These "sectors" pretty much define where content can go, then users/admins can then attach different content (like a poll, news, text etc) to different sectors. So I could attach the Poll module and an image to {S2} then maybe the Menu module into {S3}.

All of this is easily configurable and the user is not really exposed to the word "sectors" but instead a more human readable version, such as S2 could be located on the top bar, so it's human readable name would be "Top Bar" or what ever the author of the theme decided. So it's more like attaching the menu module to the Top Bar. 

raublekick, if you wanna help me out with ideas/code then just add me to msn and we'll talk =)

edit: Users/admins don't have to add the sector tags ( {S1} ) into the html file, this is done by the author of the theme to define where content should and can go, of course you can easily edit the html file to add more places for content - but there should really be no need.

wow, that is actually pretty much what has been flowing through my head, predefined places where little canned snipits can be placed!

i would be glad to take a look at what you have and come up with some ideas and code. got any other ways to contact you besides MSN? hit me up with a PM.

---

### Post by Brunellus on 2007-01-31
> got any other ways to contact you besides MSN? hit me up with a PM.

jabber.

---

### Post by oxman on 2007-02-07
Well this is a little late but I'll give some input anyway. 

I'm currently in the process of deciding HOW to integrate my current website into a CMS application. As I've been doing my homework I noticed that what I hope to do will not be easy.
First, I developed an extensive, multifaceted website using CSS and html 4.01 strict. The site is huge and has several image galleries along with a lot of text content. Then I added a blog along with a store front and search engine. After all that I decided I wanted to integrate the entire thing using some form of CMS. 
Well, its not going real well and I may have to do without one. I don't want to start from scratch.
So, I would say that any CMS that would be easy to integrate an already set up site would conquer the world (my world at least).

---

### Post by v8YKxgHe on 2007-02-08
> **oxman said:**
> Well this is a little late but I'll give some input anyway. 

I'm currently in the process of deciding HOW to integrate my current website into a CMS application. As I've been doing my homework I noticed that what I hope to do will not be easy.
First, I developed an extensive, multifaceted website using CSS and html 4.01 strict. The site is huge and has several image galleries along with a lot of text content. Then I added a blog along with a store front and search engine. After all that I decided I wanted to integrate the entire thing using some form of CMS. 
Well, its not going real well and I may have to do without one. I don't want to start from scratch.
So, I would say that any CMS that would be easy to integrate an already set up site would conquer the world (my world at least).

Not late at all =)

That is a good idea and I'll look into it, but no promises. Thinking about it., it may be very easy to do...hum

I'm currently re-coding the cms and building a proper OOP framework for it, I spent all day on Google and ##php reading and getting my head around design patterns like the Factory, Singleton and Observer - so confusing! But, with me using these design patterns it will mean my CMS will be PHP5 only. This is something I didn't originally want to do, but a few people in ##php said it would be best to code it for php5.

What are you're thoughts on going PHP5 only? If my CMS is good enough maybe it will drag people out from php4 and finally get them using PHP5! :) :)

---

### Post by OffHand on 2007-02-08
> **Brunellus said:**
> I'd like a pony.


:lolflag:

---

### Post by oxman on 2007-02-08
> **AlexC_ said:**
> 

What are you're thoughts on going PHP5 only? If my CMS is good enough maybe it will drag people out from php4 and finally get them using PHP5! :) :)
I think PHP 5 and 4 are on most computers systems that use PHP to deal with the backwards compatibility issues at this time. 
Your effort has the capability of becoming very popular in the community. Better to start out on the right foot. I'd go directly to the php coding community and get their input. The most likely scenario is that there are security flaws in php 4 and inherent weaknesses that inspired the development of php 5. Make it easy on yourself and your future. The main thing to do is make a working model. If it takes off you will find much help.
If you develop the system to be object oriented and modular others will be able to add to it and tweak it. Slap a little code in the CSS or html of a site and bingo you CMS is up and running :)
So what is the name of this CMS of yours? You did name it right? Can't start without a name can you?
Good fortune. I'll be tracking it closely.

---

### Post by v8YKxgHe on 2007-02-08
removed

---

### Post by oxman on 2007-02-08
Perhaps you should put it up on source forge. Will  it  be GPL?

---

### Post by v8YKxgHe on 2007-02-08
> **oxman said:**
> Perhaps you should put it up on source forge. Will  it  be GPL?

Yeah once I get some more code done of this new framework and have a few working modules, I will put it up on source forge. Yep, every bit of it will be under GNU/GPL 2 license.

---

### Post by bomanizer on 2007-03-01
Last fall I dug into Joomla, relating to a school project, so I got a nice intro to the world of CMS stuff. Agreed, joomla is big and sometimes very clumsy, but combined with a more powerful template management it would rock. What I'm talking about is: Somehow make the layout elements more freely and easily movable and re-sizable. Cheers!

---

