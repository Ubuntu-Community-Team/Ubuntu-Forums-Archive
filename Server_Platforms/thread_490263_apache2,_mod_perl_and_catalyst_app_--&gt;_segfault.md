---
title: "apache2, mod_perl and catalyst app --&gt; segfault"
date: 2007-07-02
forum: Server Platforms
---

### Post by stiV on 2007-07-02
hello!

i tried googling for my problem, but i couldn't find much - i hope someone can help me or give a tip where i could find help ... this is being tested on ubuntu edgy server

status:
i have a big catalyst web application (perl), which has been developed using the development server that comes with catalyst, everything works just fine there. now i wanted to test my app with apache2 and mod_perl, which didn't work so well - i can't start apache2 with my app.

i'm getting a backtrace - i GUESS it could be a problem with mod_perl, but this is just a guess. Here is what i get when i start apache2 - this is printed to the console, not the error logfile. The catalyst applications starts just fine - i can see the debug output in the apache error log file, but then everything crashes ...

see start.txt for backtrace

what i tried so far is:
getting myself a fresh system, installing apache2 and libapache2-mod-perl2, then installing all needed cpan modules via cpan (see attached perlmodules list) and
gett myself a fresh system. install apache2 and libapache2-mod-perl2 and installing all available cpan modules from the ubuntu repository and only the ones i needed in higher versions (just 1) or that aren't in the repository via cpan.

nothing helped...


anyone any idea? i've invested so much time in this and i'm getting to the point were i don't know what to do or try...

thanks in advance!

---

### Post by stiV on 2007-07-02
i just got a hint in the irc channel from catalyst and it solved my problem really fast and easy ...

i just needed to install "apache2-mpm-prefork" instead of mpm-worker (which is standard), and everything works fine.

hopefully this post will help some people with the same problem :-)

---

