---
title: "mp3, wav and DVD wont play!"
date: 2005-12-01
forum: The Cafe
---

### Post by poloman2 on 2005-12-01
I get a message saying the plug in is not installed...
what should i do??
how do i install it??

thanxxx

---

### Post by teaker1s on 2005-12-01
look in wilki for restricted formats [here]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29")

---

### Post by Robgould on 2005-12-01
Search forum for "automatix".  It will fix you, but it is illegal to do if you live in USA

---

### Post by Brunellus on 2005-12-01
[QUOTE=Robgould]Search forum for "automatix".  It will fix you, but it is illegal to do if you live in USA[/QUOTE]
Automatix is not, repeat NOT recommended for those who don't know what they're doing.  Some of the steps the script takes will break your system later.

---

### Post by Robgould on 2005-12-01
hmmmm.....worked for me.

---

### Post by Vlammetje on 2005-12-01
automatix also essentially prevents you from learning anything useful about your system.

You need to install the multimedia codecs though.

---

### Post by Robgould on 2005-12-01
what will it break?  To me it just saves time.  Not everyone wants to learn everything either....some people just want to play music.

---

### Post by teaker1s on 2005-12-01
follow the link in my first post and you won't have a problem, and you'll safely see how it all works

---

### Post by Brunellus on 2005-12-01
1) Automatix will prompt you to enable the root password.  For reasons why this is not recommended, see the RootSudo wikipage.

2) More worrying:  automatix uses the --force-yes argument (a total of 35 times!) when installing packages.  This argument ignores dependencies and is a good way to start breaking things on an ubuntu install.  The whole reason your'e in Ubuntu/Debian is to get away from possible package dependency problems...Automatix more or less ensures, by default, that you will encounter them at some point in the lifetime of your installation.

---

### Post by Robgould on 2005-12-01
Well, I did some looking. I believe that Brunellus is correct. I'm still not positive as to what the conerns are....I am still learning myself. Anyway...thanks for the enlightenment. Now I wonder if I need to re-install Ubuntu. I used Automatix. What do you think?
 
Edit
 
I spoke too soon.  Here is the reply from the witer of Automatix himself.
 
[http://www.ubuntuforums.org/showthread.php?t=66563&page=99]("http://www.ubuntuforums.org/showthread.php?t=66563&page=99")
 
As I said earlier...I used Automatix myself.  It worked great.

---

### Post by arnieboy on 2005-12-01
[quote=Brunellus]1) Automatix will prompt you to enable the root password. For reasons why this is not recommended, see the RootSudo wikipage.

2) More worrying: automatix uses the --force-yes argument (a total of 35 times!) when installing packages. This argument ignores dependencies and is a good way to start breaking things on an ubuntu install. The whole reason your'e in Ubuntu/Debian is to get away from possible package dependency problems...Automatix more or less ensures, by default, that you will encounter them at some point in the lifetime of your installation.[/quote] Brunellus:

for your concern number 1, read the following:
[http://ubuntuforums.org/showpost.php?p=518267&postcount=931]("http://ubuntuforums.org/showpost.php?p=518267&postcount=931")

as for concern number 2, --force-yes will NOT, I repeat WILL NOT break anything that automatix installs. If it had even once, atleast someone would have complained in the 1000 odd posts in the automatix thread.. seems like that has not happened yet.

---

### Post by Brunellus on 2005-12-01
[quote=arnieboy]Brunellus:

for your concern number 1, read the following:
[http://ubuntuforums.org/showpost.php?p=518267&postcount=931]("http://ubuntuforums.org/showpost.php?p=518267&postcount=931")
[/quote] 
While enabling a root account does not of itself break anything major, it does break the GUI config tools.

[https://wiki.ubuntu.com/RootSudo:]("https://wiki.ubuntu.com/RootSudo:")
> 
Enabling the root account

Note: This is not recommended! It will break all the GUI admin tools 
 


[quote=arnieboy] as for concern number 2, --force-yes will NOT, I repeat WILL NOT break anything that automatix installs irrespective of what U might have seen in your dreams. If it had even once, atleast someone would have complained in the 1000 odd posts in the automatix thread.. seems like that has not happened yet.[/quote] 
I am very much against the use of any automated script that uses --force-yes on a user who does not know what he's doing.

---

### Post by poofyhairguy on 2005-12-01
[QUOTE=Brunellus]While enabling a root account does not of itself break anything major, it does break the GUI config tools.

[https://wiki.ubuntu.com/RootSudo:](https://wiki.ubuntu.com/RootSudo:)[/QUOTE]

Not true. The GUI tools only break if you uninstall sudo. They will continue to use gksudo, even with a user account. 

> 
I am very much against the use of any automated script that uses --force-yes on a user who does not know what he's doing. 


The whole point of Automatix for those who don't know what any command line command does. If it works, it works. If not, it needs to be fixed.

---

### Post by TeeAhr1 on 2005-12-01
[QUOTE=poloman2]I get a message saying the plug in is not installed...
what should i do??
how do i install it??

thanxxx[/QUOTE]
Try  [XMMS.]("http://www.newsforge.com/article.pl?sid=04/12/02/1710208")  You can find it in the repositories.

---

### Post by arnieboy on 2005-12-02
[QUOTE=Brunellus]While enabling a root account does not of itself break anything major, it does break the GUI config tools.[/quote]
this is one more reason why I hate the wiki so much. they love to spread FUD.

[quote=Brunellus]I am very much against the use of any automated script that uses --force-yes on a user who does not know what he's doing.[/QUOTE]
I dont care what u are against or what u are not. Automatix has gone thru thousands of hours of testing to make sure not a single package which is installed is broken. u can keep ur silly concerns to urself.

---

### Post by az on 2005-12-02
[QUOTE=arnieboy]this is one more reason why I hate the wiki so much. they love to spread FUD.[/QUOTE]

Look who's spreading FUD.

The ubuntu wiki serves the Ubuntu community.  It has helped many thousands of users by providing a way to share documentation and develop Ubuntu.  The development process of this distribution relies on the wiki for developers around the world to collaborate.

There is a clause in the Code of Conduct which says "be respectful."  You are offending one of the core pieces of the Ubuntu community (and a heck of a lot of people you do not even know about) and giving Ubuntu a bad name.

In the spirit of collaboration, if you come accross a wiki page with which you dissagree, fix the page!  Add a comment!

---

### Post by arnieboy on 2005-12-02
[QUOTE=azz]Look who's spreading FUD.

The ubuntu wiki serves the Ubuntu community.  It has helped many thousands of users by providing a way to share documentation and develop Ubuntu.  The development process of this distribution relies on the wiki for developers around the world to collaborate.[/quote]
yes the wiki has been helpful in sharing documentation. However, a group of people on these forums (and that includes me) believe that the wiki is not handled in the manner that it should be and it can be replaced with somthing which is handled and maintained more effectively by a competent and committed group of ubuntuforum members. That is why we are working on trying to make [http://doc.gwos.org](http://doc.gwos.org) a success.

> There is a clause in the Code of Conduct which says "be respectful."  You are offending one of the core pieces of the Ubuntu community (and a heck of a lot of people you do not even know about) and giving Ubuntu a bad name.
I show as much respect to people as they deserve and much more than they give me in general. However it is quite obvious that you wont stop acting like a dethroned-moderator-turned-clown who wont stop at anything in attempting to disgrace my work and the effort that my team has been putting in to making Ubuntu the defacto OS in the whole world. As a senior member of this forum, you should consider quitting this circus show and try setting a better example. If u want to get noticed, try to get more involved in things which are moving ubuntu ahead in the correct direction.

> In the spirit of collaboration, if you come accross a wiki page with which you dissagree, fix the page!  Add a comment!
I dont believe in the wiki.. asd I have mentioned earlier. All my current efforts (and so are my team members) are going into making **doc.gwos.org** the place to go, read, learn and contribute.

---

### Post by endersshadow on 2005-12-02
Okay, I feel the need to back up arnieboy here because the dude's right.

First of all, Automatix is a great program that has helped countless people.  Yes, I know what everything in there does and how to do all of that myself.  Automatix is just quicker.  arnieboy and his team have done a fantastic job and put in countless hours with a script that does everything correctly.  If you run Automatix off a clean install, you'll be fine, and that's what it's meant to do.  It uses force-yes so that it can circumvent asking the user many questions that s/he may not understand, especially if they're a newbie.  If you've been tinkering with your system on your own, I'd recommend not using Automatix, as then it may break dependencies.  However, if you've tweaked your system to the point where Automatix will break it, you probably don't need it in the first place.  Quite frankly, advanced users that have an entirely customized system *aren't* the target market of Automatix.  If you don't like it, don't use it.  For newbies, it's great.


Secondly, one of the great things about Ubuntu is you don't have to be a Linux geek to use it.  Sure, knowing Linux and CLI are very helpful when using Ubuntu, but quite honestly, some people just don't have the time, the ability, or the desire to learn it.  They want an OS that *just works*.  Automatix was made, in part, for these people.

Thirdly, Wiki is unreliable and people tend to editorialize a lot (i.e.-RootSudo).  It's a great concept, but in the end, a core group of writers supplemented by the community in a moderated environment will always provide better material than a free-for-all.  Just the way it is, and that's why the doc.gwos.org project is an amazing endeavor that really needs to be applauded.  While Ubuntu relies heavily on its community, there are others that have just a better understanding of Ubuntu than the rest of us.  To have those people get together and help create full documentation is a great endeavor.  Not only is the information accurate, but it's moderated.

Fourthly, no one has completely answered the original poster's question.  You need to install w32codecs.  Get instructions on how to do that [here]("http://doc.gwos.org/index.php/PLF").

---

### Post by az on 2005-12-02
[QUOTE=arnieboy]However, a group of people on these forums (and that includes me) believe that the wiki is not handled in the manner that it should be .[/QUOTE]

That has absolutely no substance.  You do not know what you are talking about.

The documentation team is very receptive to any help offered.  What would you like them to do different?

[QUOTE=arnieboy]
If u want to get noticed, try to get more involved in things which are moving ubuntu ahead in the correct direction.
[/QUOTE]

You should set the example by releasing your software under the GPL.  You should also go to Community Council meetings be part of the Ubuntu community.

And I do not want to get noticed.  I get a lot of satisfaction from the people who thank me when I answer a question for them.  I said this a long long time ago and it still stands.  I just want ubuntu to be great and for people to not get the wrong impression about it from those who do not know how to behave.

---

### Post by az on 2005-12-02
[QUOTE=endersshadow] It's a great concept, but in the end, a core group of writers supplemented by the community in a moderated environment will always provide better material than a free-for-all.  [/QUOTE]

Ever heard of the doc team?  They do exactly that for the *whole* ubuntu community.


[QUOTE=endersshadow] 
Fourthly, no one has completely answered the original poster's question. [/QUOTE]
See post number two.  As usual, the forums provide an excellent answer promptly.

---

### Post by endersshadow on 2005-12-02
[QUOTE=azz]Ever heard of the doc team?  They do exactly that for the *whole* ubuntu community.[/QUOTE]

It's not nearly moderated enough with the content that goes into it.  With all due respect to the documentation team, the documentation is sometimes misleading, which just has to do with somebody posting it on the wiki out of hearsay without ever testing it.  It's an inherent flaw in the idea of a Wiki.  Así es la vida. Vive con el.

> See post number two.  As usual, the forums provide an excellent answer promptly.

Missed number two, so, in the words of the late, great Kurt Cobain, all apologies.

And yes, the Ubuntu community, on the whole, is absolutely fantastic.

---

### Post by arnieboy on 2005-12-02
[QUOTE=azz]That has absolutely no substance.  You do not know what you are talking about.

The documentation team is very receptive to any help offered.  What would you like them to do different?[/quote]
If u want a detailed explanation of what I meant by that, try not to start off by making ignorant and sweeping statements like "That has absolutely no substance". Contact KingBahamut if you want to know whats going on and why we are doing it. I will not go into the gory details of that out here.

> And I do not want to get noticed.  I get a lot of satisfaction from the people who thank me when I answer a question for them.  I said this a long long time ago and it still stands.  I just want ubuntu to be great and for people to not get the wrong impression about it from those who do not know how to behave.
U get lots of satisfaction by getting thank you's from people whose questions you answer.
I get much more satisfaction by:
1) **Writing tons of Howtos** along with my team for the **customization tips and tricks forums** and also providing quality assurance in the same.
2)** Making and creating automatix **which has converted tens of thousands (and counting) of people to ubuntu because they have confidence in what I do and what I have delivered till date.
3) **Maintaining the doc.gwos.org** with a group of people (who actually contribute much more than I do) in order to make ubuntu more accessible to the *whole* community.
4) also **answering questions** just like u do.
and hey, I havent even started** counting the thanks you's** which have come by as a consequence.

I am not trying to belittle your contribution to the community in any way and I know we have different ideologies in tackling the same challenges. Lets quit this mud-slinging show and inspite of our differences, try and work in our own ways to make ubuntu the best OS that mankind has seen till now.

---

### Post by KiwiNZ on 2005-12-02
Dammit play nice in here folks or I will get out my erazer and padlocks

---

### Post by poofyhairguy on 2005-12-02
[QUOTE=endersshadow]Okay, I feel the need to back up arnieboy here because the dude's right.

First of all, Automatix is a great program that has helped countless people.  Yes, I know what everything in there does and how to do all of that myself.  Automatix is just quicker.  arnieboy and his team have done a fantastic job and put in countless hours with a script that does everything correctly.  If you run Automatix off a clean install, you'll be fine, and that's what it's meant to do.  It uses force-yes so that it can circumvent asking the user many questions that s/he may not understand, especially if they're a newbie.  If you've been tinkering with your system on your own, I'd recommend not using Automatix, as then it may break dependencies.  However, if you've tweaked your system to the point where Automatix will break it, you probably don't need it in the first place.  Quite frankly, advanced users that have an entirely customized system *aren't* the target market of Automatix.  If you don't like it, don't use it.  For newbies, it's great.


Secondly, one of the great things about Ubuntu is you don't have to be a Linux geek to use it.  Sure, knowing Linux and CLI are very helpful when using Ubuntu, but quite honestly, some people just don't have the time, the ability, or the desire to learn it.  They want an OS that *just works*.  Automatix was made, in part, for these people.[/QUOTE]

Perfect.

---

### Post by bwog on 2005-12-02
Can anyone who wants to put the documents in [http://doc.gwos.org/](http://doc.gwos.org/) in the Wiki?

I know Azz only from the consise and helpfull answers he gives in the forum.. He deserves to be treated with respect.

---

### Post by az on 2005-12-02
[QUOTE=arnieboy]If u want a detailed explanation of what I meant by that, try not to start off by making ignorant and sweeping statements like "That has absolutely no substance". Contact KingBahamut if you want to know whats going on and why we are doing it. I will not go into the gory details of that out here.[/QUOTE]

The gory details start at post number 35 of this thread:
[http://ubuntuforums.org/showthread.php?t=81666](http://ubuntuforums.org/showthread.php?t=81666)

That thread speaks for itself.

The timing of this message:
[http://ubuntuforums.org/showthread.php?p=539193#post539193](http://ubuntuforums.org/showthread.php?p=539193#post539193)
leaves me to beleive that it serves no purpose for me to discuss these things.  Consider the topic dropped, on my part.

[QUOTE=arnieboy]
Lets quit this mud-slinging show and inspite of our differences, try and work in our own ways to make ubuntu the best OS that mankind has seen till now.[/QUOTE]

I agree and I accept your apology.

---

### Post by bwog on 2005-12-03
[QUOTE=endersshadow]  If you run Automatix off a clean install, you'll be fine, and that's what it's meant to do.  [/QUOTE]

If that is true, are potential users warned for this?

[QUOTE=endersshadow]  If you've been tinkering with your system on your own, I'd recommend not using Automatix, as then it may break dependencies.  
[/QUOTE]

So, Automatix can break dependencies if it is not apllied to a completely clean install?

---

### Post by arnieboy on 2005-12-03
[QUOTE=bwog]If that is true, are potential users warned for this?



So, Automatix can break dependencies if it is not apllied to a completely clean install?[/QUOTE]
automatix will NEVER break anything.

---

### Post by GreyFox503 on 2005-12-03
[quote=arnieboy]automatix will NEVER break anything.[/quote]

Never say never. :)

You just might have to eat those words later.

BTW:  I still like automatix, I just don't use it.

---

### Post by arnieboy on 2005-12-03
[QUOTE=GreyFox503]Never say never. :)

You just might have to eat those words later.

BTW:  I still like automatix, I just don't use it.[/QUOTE]
No i wont have to. thats the whole point.

---

