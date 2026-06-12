---
title: "creating a wiki"
date: 2008-09-04
forum: The Cafe
---

### Post by nerdman978 on 2008-09-04
My friends and I are creating a wiki for our school classes where we and several other students will post our notes, what the night's homework was, etc. for a gigantic collaborative effort to pass some of the hardest available classes at our high school (no we will not be cheating when doing this..just a heads up). 

I do know how to host a blog in windows...its pretty simple with XAMPP and dyndns updater. Since we are too cheap to spend a cent on this project (only our time) we want to host it directly off my friend's backup computer that was replaced recently by a new computer he built. He has already registered a hostname with dyndns (lyceumwiki.doesntexist.org...hehe) which is free, and set up dyndns' updater, which constantly tells dyndns what his public IP address is (and he set up a static IP on his LAN network). 

After that though, we seem a bit stuck. Is there a format already out there for creating a wiki (and if so, where?). Also, could XAMPP be used for this? (on windows of course, he doesn't want to install linux on the backup computer because his little brother occasionally plays video games on it..) Please also note we don't want to sign up for even a free online wiki service.


thanks in advance for any help you can provide

---

### Post by LaRoza on 2008-09-04
There are several wiki packages you could use, I suggest using a free online host like wikidot or various mediawiki sites.

---

### Post by Old_Grey_Wolf on 2008-09-04
You might find a message board useful for this project. Since you are familiar with XAMPP you could install XAMPP and a message board like phpbb.

---

### Post by az on 2008-09-04
> **nerdman978 said:**
> 
After that though, we seem a bit stuck. Is there a format already out there for creating a wiki (and if so, where?). Also, could XAMPP be used for this? (on windows of course, he doesn't want to install linux on the backup computer because his little brother occasionally plays video games on it..)



I would recommend a linux box instead of Windows.  And yes, a LAMP stack is the way to go.

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

Creating a wiki is as easy as installing it on top of your LAMP stack.

You could use an old pentium II and still get awesome results for what you are trying to build.

Here is a bunch of web applications that run on LAMP (They mostly all install the same way):
[https://help.ubuntu.com/community/Servers#Web%20Applications](https://help.ubuntu.com/community/Servers#Web%20Applications)

---

### Post by bp1509 on 2008-09-04
d

---

### Post by the yawner on 2008-09-04
> **bp1509 said:**
> [dokuwiki]("http://www.dokuwiki.org/dokuwiki").

seriously.  Get a host and just upload docuwiki to the public root of it and that's it for the most part.

It's saves everything in static text files.  No mysql required at all.  It's quick to install, it's fast to load and it's just as easy to use as mediawiki and it's got tons of plugins which as easy to install.  So screw installing the entire stack.  Just have the OS and your web server of choice. 

If it's something one of you host out of home, i'd also go for a slimmer web server (like lighthttpd).

My recommendation too. Although I actually had one setup here at work running in an Ubuntu server with template set to [Monobook]("http://tatewake.com/wiki/projects:monobook_for_dokuwiki") to emulate Mediawiki/Wikipedia's looks. It should work with XAMPP as well.

---

