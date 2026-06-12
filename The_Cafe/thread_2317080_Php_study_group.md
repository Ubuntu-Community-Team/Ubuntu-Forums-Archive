---
title: "Php study group"
date: 2016-03-13
forum: The Cafe
---

### Post by AstroLlama on 2016-03-13
Is anyone interested in starting a php study group? We could come up with an idea for a project and then build it as a team.

---

### Post by darkeale on 2016-03-13
Hey,

I would be interested in this. What level would you be starting from? I have coding experience in other languages (C, C++, python). I haven't used PHP before but I'd definitely be up for learning!

---

### Post by AstroLlama on 2016-03-13
Hi Darkeale, I would say I'm at an intermediate level (but with some gaps in my knowledge). Got it from building a site for my family's small business. At the start it was very "procedural" code, but as I learn more it gradually becomes more object-oriented. At the moment I'm comfortable creating functions, classes and interfaces; working with cookies, sessions and forms (the basics); and a few other things...

Oooh, Python, that's something I've been wanting to learn for a while, now...

---

### Post by darkeale on 2016-03-13
OK, so I guess I would have a bit of catching up to do, but I'm definitely up for giving it a try! I usually find it a lot easier to learn things when I have a project to work towards. Did you have any projects in mind?

---

### Post by AstroLlama on 2016-03-14
I've never done anything similar, so I was hoping that someone could advise! :)

---

### Post by Dragonbite on 2016-03-14
Sounds interesting and I know some PHP (but plenty of room to grow).  My problem is getting home-time for working on projects but I would be interested.  Should start off with some simpler things to get our feet wet and see what skill level we are talking about, and then gradually get more and more complex.

I wonder if this is better in the cafe, or somewhere in [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310").  An Admin would the best for deciding that.

---

### Post by SeijiSensei on 2016-03-14
I've been building sites in PHP for at least fifteen years now.  I just thought I'd describe how I organize them.

I try to split the programming and content as much as possible.  A typical site has this structure:

```

/path/to/site/include/common
/path/to/site/include/public
/path/to/site/include/public/handlers
/path/to/site/include/public/content
/path/to/site/include/admin
/path/to/site/include/admin/handlers
/path/to/site/include/admin/content

```
The index.php page usually contains only pointers to the top of this directory tree, then invokes the startup files and displays the page:
```

<?php
$includes = "/path/to/site/include/current/";
$common = $includes."common/";
$handlers = $includes."public/handlers/";
$content = $includes."public/content/";

require($common."init.inc");
include($content."index.inc");
?>

```
I usually have a "current" and "dev" directory with the former holding the production code, and the latter containing the most recent development version.  

The "common" directory contains things like class definitions, an "init" file that runs each time the site is accessed, and the code to start a session.  Sessions and session cookies are invaluable if you need to handle logins or track users as they traverse the site.  These are files that need to be accessed by both the publicly-visible site and the privately-visible "admin" site.

I then split off "handlers" which includes most of the program code.  Most of my sites use a hidden "go" field which determines which content to display inside index.inc.  Often that file is as simple as:
```

<?php
include($content.'page_header.inc');
include($mycontent);
include($content.'page_footer.inc');
?>

```
The value of $mycontent is determined based on the value of $go and the result of any form handlers.  For instance, the default value of $mycontent might be "home.inc", but if a form is processed it might be changed to "request_credentials.inc" if the user asks to reset a password.

Forms usually have a "do" field that is sent back in a GET or POST request.  I'll often use "do" as the identifier for buttons, so a "Submit" button might be coded as:
```
<input type='submit' name='do' value='Submit'>
```
Usually there is a master handler with a "switch($go)" structure that selects the relevant code for each page.  Some of the handlers may have a "switch($do)" structure to invoke different code snippets depending on the chosen action.  For instance, if a form is found to be missing required values, I'll display a "review" file that indicates the source of the error.  If the form is complete, the $mycontent variable will point to a confirmation page.

I use PostgreSQL as the backend database for my sites.  When I first began web programming, MySQL was still not fully open-source and could not be redistributed on servers I built for clients.  I chose Postgres for that reason and have never looked back.  I do run MySQL for things like WordPress, but I don't use it for any site I build myself.

Having all the files be stored as "file.inc" means I can write an Apache rule that blocks downloads of any file with that extension thus preserving the code from prying eyes.

---

### Post by branau on 2016-03-15
Hey, I'm a self-taught web developer and I use PHP more than anything else at my work. I'd be happy to help out where I can, and I could probably learn a thing or two from some of the more experienced developers too. Count me in

---

### Post by AstroLlama on 2016-03-18
Arigato, SeijiSensei, for sharing your approach with us, and welcome, Darkeale, Dragonbite and branau.

In what timezone does everyone live? It would be helpful to organize a meeting over IRC or elsewhere to brainstorm. Shouldn't take more than an hour.

At the present I live in Belgium, UTC +1 hour.

---

### Post by Dragonbite on 2016-03-18
Eastern Time (-4 I think).

We recently changed our clocks so I'm even more confused that I was before...

---

### Post by Carpentr on 2016-03-18
Great idea. 

Would love to join, but my spare time is a little slim.

Usually when I start learning a new programming language, and become relatively comfortable, I work on creating a small-scale ERP app for a fictional business. It gives exposure to common things like user authentication, data pulls, reporting, and UI/UX design.

Coming from ASP.NET/C#, I have written very little PHP, but I have heard great things about CakePHP.

Carpentr

---

### Post by darkeale on 2016-03-18
Thanks SeijiSensei, lot's of good information there!

I'm in England so 1 hour behind you in Belgium.

---

### Post by Dragonbite on 2016-03-18
> **Carpentr said:**
> Would love to join, but my spare time is a little slim.

Same here. For that reason, posting and using the forums when people can check in when their time allows, may be a good way to go (but IRC may work for the initial setup).

I am usually on IRC during work (shhhhhh..!!) which is 8 AM - 4 PM here (or (8 AM +4) 12 PM to (4 PM +4) 8 PM UTC).  Or if it helps, I listen to [UbuntuOnAir ]("http://ubuntuonair.com")at 12 NOON (11 AM before clock changes) which according to the calendar runs at 4PM.

> **Carpentr said:**
> 
Usually when I start learning a new programming language, and become relatively comfortable, I work on creating a small-scale ERP app for a fictional business. It gives exposure to common things like user authentication, data pulls, reporting, and UI/UX design.

Coming from ASP.NET/C#, I have written very little PHP, but I have heard great things about CakePHP.

Carpentr

I come from using ASP.NET (VB.Net) at work and have self-taught myself PHP.  We did have a CakePHP site set up but to convert it to a newer version was horrendous and so we decided to rebuilt that site custom-PHP and use bits and pieces from CakePHP for things like calculations.

---

### Post by AstroLlama on 2016-03-19
Ah yes, Connecticut is at UTC -04:00 now... I have family in Wethersfield ("Ye most auncient towne" in CT) ;)

How about **tomorrow, Monday or Tuesday, UTC 22:00?**
That's 23:00 for me, 19:00 for Dragonbite/Seijisensei, and 17:00 for branau (your profile indicates Mexico?)

I'll set up a channel on IRC and post it sometime tomorrow. (I assume everyone knows how to connect to IRC)

---

### Post by Dragonbite on 2016-03-19
Tuesday is the best day for me.

---

### Post by darkeale on 2016-03-20
Tuesday works for me too

---

### Post by Steve R. on 2016-03-20
Having a PHP study group sounds great, as I am just learning. As for an IRC channel, I am clueless. So an internet search on how to utilize it will be in order.
I'm in Morehead City, NC which is on the east coast of the US. Time would be -4 UTC.
Tuesday is acceptable, but there is the usual caveat of it is difficult to commit at times.

---

### Post by Dragonbite on 2016-03-21
I assume it would be on Freenode?

I usually use xchat or [http://webchat.freenode.net/]("http://webchat.freenode.net/") (a web-based IRC interface).

xchat, or most locally installed applications, may be able to keep the text of conversations between session while the web-based one remembers nothing.

---

### Post by Dragonbite on 2016-03-22
Any idea on the Channel name and server?

---

### Post by Dragonbite on 2016-03-22
If the OP doesn't set up a channel, I opened one on freenode called #ubuntu-php-study just in case.  I'll leave it on there but if there is another channel to use just post and let everybody know!

---

### Post by Steve R. on 2016-03-22
> **Dragonbite said:**
> If the OP doesn't set up a channel, I opened one on freenode called #ubuntu-php-study just in case.  I'll leave it on there but if there is another channel to use just post and let everybody know!First, I forgot. Next, it did look like I made a connection; but an hour late, but no one was there. Too be expected.

---

