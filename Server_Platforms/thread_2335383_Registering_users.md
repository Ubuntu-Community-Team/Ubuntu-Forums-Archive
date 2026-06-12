---
title: "Registering users"
date: 2016-08-28
forum: Server Platforms
---

### Post by karolho121 on 2016-08-28
Hello,
Can someone help me with registering users on my website? 
I have made the page for it, i just don't really know how to code it so it
adds the user. I don't know how this works, can someone tell me how to do it?

---

### Post by TheFu on 2016-08-28
Uh .... what language?  There are **OWASP** [best practices]("https://www.owasp.org/index.php/SCG_WS_Apache") that would be worth reviewing too.  [http://resources.infosecinstitute.com/authentication-hacking-pt1/](http://resources.infosecinstitute.com/authentication-hacking-pt1/) might be helpful. Look at this from a cracker's perspective, so you can protect the site from known issues.

Sadly, if you coded it and don't know how it works, we won't be much help.  There are lots of beginning web-app programming books which will take you step-by-step through setting up a simple website, displaying pages, connecting a DB, and user management.  These are necessarily toy applications, to keep the complexity low.  They also teach TDD, version control, a little design and some VPS stuff.  I've worked through a few on Perl and Ruby a few years ago.  

New Ruby has been released since then, so that book isn't specifically good anymore. Don't know of the author released - yet another edition -  he had been doing a new book every year to keep up with the new ruby and new rails releases.  My guess is that the only people making money doing Ruby/Rails are the people selling updated books (huge changes in 1 of those every year). Constant major update issue with that language.

OTOH, Perl isn't a popular language for all the new kids, so new books on it aren't written.  There are some amazing web frameworks for Perl and since Perl basically invented TDD, every package used from the CPAN repo is extremely well-tested across thousands of platforms.

So ... which language are you coding in?

---

### Post by SeijiSensei on 2016-08-28
If this is a hobby project, start with "[basic authentication]("https://wiki.apache.org/httpd/PasswordBasicAuth")" as supported by Apache. If this is a professional effort, hire someone who knows about this stuff.

---

