---
title: "CPAN creates new perl directory, hoses installation"
date: 2014-07-20
forum: Server Platforms
---

### Post by guymerritt on 2014-07-20
First, I'm not actually using Ubuntu Server edition - but I thought that this might best place to post this question.  Over the last couple of days I installed a server on Ubuntu 12.04 (amd64 desktop edition) and compiled most of the packages (Apache, Openssl, PHP 5.3.x, MySQL, Qmail, etc.).  Everything works fine, but, the spamassassin package from the Debian repos is typically missing a lot of perl mods which are essential to spamassassin actually working properly.  So, in an earlier test, I used CPAN to grab some perl mods.   I've done this on Ubuntu 10.10 and it worked fine.  However, on 12.04 using CPAN caused a new directory to be created under the user's home directory (eg. /home/guy/perl5), and, it totally hosed the installation.  It seems as if the perl mods are not being appended to the stock installation of perl in the same way that they are on Uubuntu 10.10 (and, in other distros).   As I've said, using CPAN broke the perl installation - I could no longer boot to a desktop, etc. - I had to reformat and start over.  I did a bit of reading and I wondered if using the "sudo" command would have helped.  Anyway, I'm a dummy - about a C+ Linux guy....and I wondered why CPAN (which works on Centos, earlier versions of Ubuntu, etc.) behaved in this way.   Any tips would be appreciated......thanks.

---

### Post by TheFu on 2014-07-20
Mixing OS perl and end-user perl is to be avoided.  So you have 2 choices.

a) stick with Ubuntu packages and resolved dependencies using APT methods (try aptitude); look for the needed perl packages in the ubuntu repos - they do exist. DO NOT USE CPAN!  I cannot imagine CPAN breaking anything on a server.

b) completely remove all OS perl dependencies from the spamassassin and use 100% user-maintained perl install via something like **perlbrew**.  This is what perl developers do and it is a best practice. Then you can use CPAN-minus with  the newer perl you'll install using perlbrew.  

**Do not mix os perl stuff with non-OS perl stuff.**  The Ubuntu team expects us to use the perl packages they provide.

I think you'll be happier with method "a" above, unless you want to become a hardcore Perl developer. Every company I know that is heavy into perl is hiring, based on the YAPC:NA conference job opportunities announced last month. There must have been 80 companies there - all looking for perl people.

10.10 is a long time ago. Things have changed with Ubuntu and Perl significantly since that time.  Modern Perl has requirements that any perl before 5.14 just can't support.  Between 5.8, 5.10, 5.12, 5.14 and now 5.20 - there are HUGE changes to Perl.

---

### Post by SeijiSensei on 2014-07-21
Actually, I don't use CPAN on CentOS either.  I use the pre-built packages from Dag Wieers ([http://rpmforge.net](http://rpmforge.net)).  

Most of the packages for Ubuntu seem to be here: [http://packages.ubuntu.com/trusty/perl/](http://packages.ubuntu.com/trusty/perl/)

---

### Post by guymerritt on 2014-08-15
> I cannot imagine CPAN breaking anything on a server.  Hmm - well, prior to my experience with Ubuntu 12.04 I couldn't imagine it, either.   As I said, though, it creates a folder in the user's home folder (root, in my case) called "perl5" - and nothing works, afterwards.  I've never seen this happen on other systems (the creation of this folder in the user's home directory).    It's entirely possible that I'm doing something wrong, somehow....  At any rate, I've found that I can install perl mods using the Software Manager, or, using aptitude and everything is fine.  I just sort of wondered why CPAN didn't work.  Again, it could be that I've done something to the system (though I cannot imagine what it would be) that is causing the problem with CPAN.  And I'd tried it about 5 times - the minute I install perl mods with CPAN I can no longer boot to the Unity desktop....  It's a mystery but, hey, aptitude works fine.....  OH: and you can trust the warnings on the Ubuntu pages that say, to paraphrase, "Hey, don't just download these things and install them...." - that doesnt work either.   Before trying the Software Manager and aptitude I tried just doing web searches for the perl mods and downloading them.  Again, that hoses the system.

---

### Post by TheFu on 2014-08-15
So I'm a PM (Perl Monk/Monger) and attended the YAPC:NA conference this year.  There are many, many, many changes coming. Much of the best things in Perl6 are being back-ported to Perl5.  They have a goal of NOT breaking backwards compatibility, but ... there are things in 5.20+ that WILL BREAK existing Perl code.  There are warnings, but most people don't see those on running servers - it always worked before, right?  PAY ATTENTION to the deprecation warnings.  The policy, as I understand it, is for any change that breaks compatibility to be a warning for 6 months. IF you are like me and only use TLS releases ... er ... well, screwed comes to mind.  Of course, I am NOT a core developer of Perl, so this is just my interpretation.  Best to read the **perldoc perlpolicy** (or [this]("http://perldoc.perl.org/perlpolicy.html")) for the exact wording.

So - if you are running perl stuff that is part of the OS, please, please, please only use the OS perl packages.
Otherwise, setup perlbrew and take ownership of your development, test, production environments.  5.20 has some fantastic capabilities that Perl has needed since the beginning.  Soon, moose will be core, so there won't be the slow startup time for our **modern perl** programs.  I've been using Mo - Moo, and Mouse and Moose were too heavy for me. ;)

There is a way to freeze specific module levels for every application using perlbrew. I haven't gotten to the point where I want a completely separate development setup for every perl app I write - but I do keep 4 different perl versions loaded for testing of some apps.5.12 / 14 / 18 / 20 - 5.20 feels good.

Oh - and be certain your programs:
```
use strict;
use warnings ;
```

---

### Post by guymerritt on 2014-08-15
> So I'm a PM (Perl Monk/Monger) and attended the YAPC:NA conference this year.  Interesting stuff, there...  Clearly, like the majority of people on Earth, you're a lot smarter than me!   Yes, I've learned my lesson: only use the perl mods provided by the builder of the OS.  It's a bit curious to me, though, that CPAN has always worked in this past.....  I guess I found it odd that I hadn't read anything about this kind of problem (which I replicated over and OVER - ACK!) and CPAN has always been a particulary easy way to update/append a perl installation.  It was defintately the kiss of death for me on Ubuntu 12.04.

---

### Post by TheFu on 2014-08-16
I doubt I'm any smarter.  Just been around a long time and have an interest in perl.  I'm an idiot in many, many, many, many other topics - like how my yard is full of crabgrass because the broadleaf killer I used last month wiped out all the non-crabgrass. That's just 1 example of thousands of dumb things I've done. ;)  Oh - and the dumb things I've done or seen happen on computers .... well - [http://blog.jdpfu.com/2010/07/27/top-9-ooops-moments](http://blog.jdpfu.com/2010/07/27/top-9-ooops-moments) . Enjoy.

---

### Post by guymerritt on 2014-08-16
> Oh - and the dumb things I've done or seen happen on computers ....  God bless you for sharing those notes.... I only read the first four, but, ACK!!!!  I loved the script which - whoops - inadvertently included wiping out anything that was hanging around under "/".  Man - that had to a moment......HA HA.   Good to know that even smart guys can throw the wrong switch now and then.......funny stuff (because, MAN, can I relate to those moments....).  Bear in mind, I'm 62 years-old and when I was 49 I asked the IT guy at the music store where I worked if I could run my own web server from my house.  He said, "Yeah - but I'd use Linux....".  My response was, "Okay - what in the hell is Linux....?".   He replied, "Basically, it's a free version of Unix." I replied, "Great - what's Unix.....?".   So I'm a really late bloomer.  I think the only thing that got me this far was that I used Redhat 7.3, briefly, and then got stuck on Slackware (for a long time).   With Slackware you were forced to learn the inner workings of Linux, to a reasonable degree, or you were (pretty much) shafted in a lot of ways.....  Anyway - haha - thanks again for sharing.  And good luck with that damned yard.

I had to come back and add this, after reading some more of your page: I lived right across the street from the Johnson Space Center for four years (I mean, virtually across the street).  We were probably neighbors.  Man - that's a really fun page......

---

