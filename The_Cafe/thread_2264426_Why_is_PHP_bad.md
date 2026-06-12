---
title: "Why is PHP bad"
date: 2015-02-07
forum: The Cafe
---

### Post by bashiergui on 2015-02-07
No one can match this guy's passionate hate for PHP. I have to admire the level of OCD required to exhaustively and thoroughly document that hatred. ;)[URL="http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/"]
http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/[/URL]> I can&#8217;t even say what&#8217;s wrong with PHP, because&#8212; okay. Imagine you have uh, a toolbox. A set of tools. Looks okay, standard stuff in there.

You pull out a screwdriver, and you see it&#8217;s one of those weird tri-headed things. Okay, well, that&#8217;s not very useful to you, but you guess it comes in handy sometimes.

You pull out the hammer, but to your dismay, it has the claw part on both sides. Still serviceable though, I mean, you can hit nails with the middle of the head holding it sideways.
You pull out the pliers, but they don&#8217;t have those serrated surfaces; it&#8217;s flat and smooth. That&#8217;s less useful, but it still turns bolts well enough, so whatever.

And on you go. Everything in the box is kind of weird and quirky, but maybe not enough to make it completely worthless. And there&#8217;s no clear problem with the set as a whole; it still has all the tools.

Now imagine you meet millions of carpenters using this toolbox who tell you &#8220;well hey what&#8217;s the problem with these tools? They&#8217;re all I&#8217;ve ever used and they work fine!&#8221; And the carpenters show you the houses they&#8217;ve built, where every room is a pentagon and the roof is upside-down. And you knock on the front door and it just collapses inwards and they all yell at you for breaking their door.

That&#8217;s what&#8217;s wrong with PHP.

---

### Post by Lars Noodén on 2015-02-07
Unfortunately he is spot on with the assessment.

---

### Post by SeijiSensei on 2015-02-07
Like many things, that's a matter of opinion.

Some people complain that the syntax of functions is inconsistent.  I'll agree with that.  Others argue that PHP is innately insecure.  I don't think that is the case.  Most vulnerable applications fail to do even simple validity checks like examining input strings before acting on them (SQL injection attacks being a prime example). PHP3 and earlier had some security holes like automatically creating globals from variables passed in a GET or POST.  Those types of vulnerabilities no longer exist in current versions of the language.  Writing a web application in perl that doesn't validate inputs is going to be just as vulnerable as one written in PHP.

PHP is an easy language to learn so there are lots of PHP applications on the web.  Many of them are written by people who have little experience and don't think about the security implications of the code they write.  

I've written thousands of lines of PHP code over the years. I've never had a site compromised including one for a mid-sized healthcare provider. That application processed "patient health information" and needed to comply with [HIPAA]("http://www.hhs.gov/ocr/privacy/hipaa/administrative/securityrule/").  While I suspect my earliest efforts had vulnerabilities, after nearly twenty years of experience I've learned to think first about security.

If the complaint is the jack-of-all-trades nature of PHP, I find that a feature, not a bug. Having simple functions to interact with the enormous diversity of *nix server software is incredibly valuable.  Need strong encryption?  Use the mcrypt functions.  Need to talk to a PostgreSQL database?  Use the pg() functions.  Need to open a socket?  Sure. That type of functionality isn't unique to PHP on the *nix platform either.  Any other high-level language like Python, Ruby, or perl can do all that, too. 

Many widely-used applications are written in PHP, like this very vBulletin forum.  These applications get pounded every single day, but they rarely have security breaches. The Ubuntuforums breach arose from a disused account with administrative privileges.  It had nothing to do with PHP.  WordPress has to fix a security hole from time to time, but that's because it needs to write into directories like wp-content.  The applications I write never need to write into publicly visible directories.

Are there reasons to think that ASP or .NET or Ruby on Rails or whatever applications are inherently more secure than ones written in PHP?  I'd be willing to rethink my opinion if someone can point me in the right direction.

---

### Post by Erik1984 on 2015-02-07
This was a funny bit:
> Functions for parsing bbcode, a very specific kind of markup used by a handful of particular forum packages.
(from [http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/#standard-library](http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/#standard-library))

I might agree that it is weird that bbcode parsing is part of the standard libraries but there are quite some users of those 'particular forum packages' :P

---

### Post by MartyBuntu on 2015-02-07
Hilarious read...

---

### Post by Dragonbite on 2015-02-08
I like using PHP.   Maybe it is because I started off doing ASP (Classic, pre-.NET) and and PHP is similar in being all scripting and no compiling.

Maybe I like it because I find that the syntax in PHP is similar to JavaScript that my brain doesn't have the "shift gears" far to go from one language to the other.  Or maybe because it's simple enough that it is fun to program with.

Recently when we upgraded the web server and the PHP, the only "hiccup" I had was that functions could no longer take referenced variable.  It took me a few minutes to change the functions but it wasn't too bad at all.  

So, I just enjoy playing/programming in PHP.  It may not mean I am a "real programmer" but hey, it still makes me money! ;)

---

### Post by sffvba[e0rt on 2015-02-11
[IMG]http://www.commitstrip.com/wp-content/uploads/2015/01/Strip-PHP-doute650-Webenglsih.jpg[/IMG]

---

### Post by Dragonbite on 2015-02-11
Love that comic!

---

### Post by PartisanEntity on 2015-02-18
PHP is my favorite web development language. It was very easy to grasp, and easy to develop projects using it.

The point is, there is nothing out there that doesn't have weaknesses and deficiencies. This fact renders hatred of such a nature irrelevant.

---

### Post by Sasha_Aderolop on 2015-02-22
PHP is the best web development language for me. 
1 - PHP has several problems with language design, core implementations, etc (many of these are legacy-related). It's also easy to get started with, which leads to a community with a large percentage of newbies making silly mistakes.
2 - (a lot of) programmers are elitists, bandwagon-lovers, or just trying to fit in; PHP is an easy target for the things I mentioned in the first point.

---

### Post by jacobpratt909 on 2015-02-22
I find it great how people are responding about how "fabulous" PHP is when you pointed out the phrase >  Now imagine you meet millions of carpenters using this toolbox who tell  you &#8220;well hey what&#8217;s the problem with these tools? They&#8217;re all I&#8217;ve ever  used and they work fine!&#8221; And the carpenters show you the houses  they&#8217;ve built, where every room is a pentagon and the roof is  upside-down. And you knock on the front door and it just collapses  inwards and they all yell at you for breaking their door. 
It just makes me laugh harder xD

-Wyz

---

### Post by aysiu on 2015-02-22
Speaking as someone for whom programming doesn't come naturally, I love PHP. I'm probably one of those "newbies" making mistakes all the time, but I'm really trying my best to do things efficiently and, when interfacing with MySQL to use prepared statements and validate input before shoving it into the database. I'm trying to learn Python now on CodeAcademy, and that's fine... but PHP just makes more sense to me, for some reason. A simple example is being able to plop a bunch of variables inline with text without having to put in *%s* placeholders.

---

### Post by Dragonbite on 2015-02-23
I prefer PHP over ASP.NET.

Annoyingly, the best PHP IDE I have used is strangely from Micorosft; WebMatrix 3.

---

### Post by nilla78ro on 2015-03-05
It is not bad at all, I'm java programmer but i'm using php for my personal web sites. I don't have too much time for my personal projects and on php is enough to change / upload the file to have the change up and running.
In my opinion the php looks ugly beacuse we don't have any good IDE like other languages (I'm using Netbeans).
So, php is not bad at all.

---

### Post by Dragonbite on 2015-03-05
> **nilla78ro said:**
> It is not bad at all, I'm java programmer but i'm using php for my personal web sites. I don't have too much time for my personal projects and on php is enough to change / upload the file to have the change up and running.
In my opinion the php looks ugly beacuse we don't have any good IDE like other languages (I'm using Netbeans).
So, php is not bad at all.

Netbeans has a PHP plug-in, but not sure how much better that is than gEdit with the file listing on the side.

But I agree, Linux needs a good (preferably non-Java based) open source PHP editor.  Maybe even one that integrates a web server back-end for debugging (without having to run a web server all of the time or go through manually installing/scripting and running the server components).

---

### Post by Bimasena_Putra on 2015-03-09
For me PHP is easy to use, it's my favorite

---

### Post by Sasha_Aderolop on 2015-03-17
1. Bad recursion
2. Many PHP-modules are not thread safe
3. PHP is crippled for commercial reasons
4. No namespaces
5. Non-standard date format characters
6. Confusing licenses
7. Inconsequent function naming convention
8. Magic quotes hell
9. Framework seldom used

---

### Post by SeijiSensei on 2015-03-17
> **Sasha_Aderolop said:**
> 
1. Bad recursion.
PHP applications rarely need recursion at all.

> 2. Many PHP-modules are not thread safe
Which ones? There are dozens.  Does this include the most common modules for things like MySQL, PostgreSQL, mcrypt, IMAP, etc.?  Or does it apply mostly to less-common and less well-supported modules?

> 3. PHP is crippled for commercial reasons
Evidence?  What does "crippled" mean?  Are you talking about the relationship with Zend? How has that "crippled" PHP?

> 4. No namespaces
And the consequences of that are?

> 5. Non-standard date format characters
True, but you get used to it, or you just bookmark the documentation page for date() as I did.

> 6. Confusing licenses
Examples?  The main codebase uses a [BSD-style license]("http://php.net/license/"). Some modules may have different licenses if they interface with commercial products, I suppose.  I don't see anyone objecting to distributing PHP on open-source platforms.  If the licenses were more restrictive, Debian wouldn't support it.

> 7. Inconsequent function naming convention
I find the naming less important than the inconsistencies in argument order.

> 8. Magic quotes hell
Who uses magic quotes? I gave up on that long ago and wrote a class of functions to handle transactions with the database.  The functions add quotes when needed.  Magic quotes was always a kludge that anyone with much PHP experience knows to avoid.

> 9. Framework seldom used
I don't know what this means.

---

