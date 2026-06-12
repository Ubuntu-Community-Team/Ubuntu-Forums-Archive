---
title: "Wiki/CMS with Access Control Recommendations"
date: 2009-08-21
forum: Server Platforms
---

### Post by msbarker on 2009-08-21
Hi Everyone,

I am a wiki noob and after reading up on wikis I am still a bit fuzzy on the best option.  I want to set up a wiki or cms on my workstation to manage projects with collaborators (here and abroad).  Ideally, I want a password protected wiki that will show users only the links to the wiki pages they can edit.  It is important that users do not see links to the other projects.  I have looked at moinmoin, pmwiki, and drupal, but I am still uncertain if any of these provide the desired function.  Any good recommendations?  Bonus points for easy install on Ubuntu!

Thanks in advance,
Mike

---

### Post by volkswagner on 2009-08-21
[Twiki]("http://www.twiki.org/") is in the repo's.

```
sudo apt-cache search twiki
libwww-mechanize-twiki-perl - Provides a programatic interface to TWiki's REST interface
twiki - A Web Based Collaboration Platform
twiki-ldapcontrib - LDAP services for TWiki
```

[Foswiki]("http://foswiki.org/About/WebHome") is a fork of Twiki.  There are some really cool things which can be done with [access control]("http://foswiki.org/System/AccessControl") and [authentication]("http://foswiki.org/System/UserAuthentication").

For the most part anything in Twiki works on Foswiki.  I just believe the dev's at Foswiki want to keep the "community FOSS" going ([long explaination]("http://foswiki.org/About/WhyThisFork?redirectedfrom=Home.WhyThisFork")).

---

### Post by ugm6hr on 2009-08-22
Coincidence....

I have just started experimenting with twiki: [http://ubuntuforums.org/showthread.php?t=1244508](http://ubuntuforums.org/showthread.php?t=1244508)

Thanks for the pointer to foswiki - I will give it a try.

I have found the documentation elating to TWiki forms and templates impossible to understand.  Hopefully foswiki will prove more wiki-noob friendly.

However, my initial experimentation has demonstarted that user access settings are very simple with twiki.

---

### Post by msbarker on 2009-08-24
Thanks for the suggestions!  It looks like foswiki probably has a brighter future and good forum support.  I'll give it a try.

---

### Post by ugm6hr on 2009-08-24
> **msbarker said:**
> Thanks for the suggestions!  It looks like foswiki probably has a brighter future and good forum support.

Definitely.  I got a response from one of the main developers within 2 hours following a question relating to html forms.

I also felt obliged to contribute my own experience for documentation.  Don't you love community driven software?

---

