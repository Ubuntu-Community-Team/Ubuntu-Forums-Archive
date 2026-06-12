---
title: "mod_perl and local  version of perl"
date: 2012-03-22
forum: Server Platforms
---

### Post by RogerThompson on 2012-03-22
[FONT="Courier New"]
Environment:
  Ubuntu: 11.10 (32 bit)
  Apache: 2.2.20 (Ubuntu)
mod_perl: 2.0.5
    perl: 5.12.4

apache and mod_perl were installed using apt-get.

perl 5.12.4 is the system perl residing at /usr/lib which I do not want to mess with.  I have my own version of perl residing at /home/thompson/local/perls/perl-5.14.2/bin.  I maintain this using perlbrew.

How can I have my local version be the one that mod_perl uses?
Do I need to build mod_perl from source?
[/FONT]

---

### Post by mbuell on 2012-05-01
Since you did not get ANY answer - I suggest you go to CPAN, and start looking there. Maybe look at perlbrew. 

I do NOT know any of this stuff - I am just trying to answer a similar question - so what I found may not help you - but I thought I would give it a pitch, since you didn't get any other answers. 

If you found something yourself, it might help me to know what you found.

---

