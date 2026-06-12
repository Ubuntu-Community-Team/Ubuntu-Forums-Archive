---
title: "Perl CGI not working on new install"
date: 2008-01-17
forum: Server Platforms
---

### Post by trevorj on 2008-01-17
I am completely stumped. I did a new install of 7.10. No mods whatsoever. I immediately then used synaptic to do an apache2 install. No mods whatsoever. I then write test.pl and put it in /usr/lib/cgi-bin (the apache 'default' site location for CGI scripts. The contents of test.pl is:

#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hello, World!\n"

I set test.pl permissions to 777. I goto /usr/lib/cgi-bin and run the script (i.e. ./test.pl[ENTER]). Runs fine. 
I cp test.pl test. I run it (i.e. ./test[ENTER]). Runs fine. 
I browse (using default firefox) to: [http://localhost/cgi-bin/test.pl](http://localhost/cgi-bin/test.pl)

AND I GET PROMPTED TO DOWNLOAD THE FILE! WHAT IS GOING ON! I'm using a new install without mods. New apache2 without mods (see site-available/default for settings). And, it doesn't work. WHY?

FIGURED IT OUT! Its working fine....it was the script!. (It really had to be but I couldn't see it.)

---

### Post by twistedtwig on 2008-01-18
The way I got it to work was to have a link in the www folder to cgibin so the CGI scripts are in usr/bin or where ever it is but the link then includes them in the web site.

There was a thread about it I used in the howto..It was for AWSTATS and that explained how to do it.

do a search of the forums and you should find your answer.

---

