---
title: "Default Package Blues - How to reconfigure with MY options?"
date: 2005-11-16
forum: Repositories &amp; Backports
---

### Post by joe_rocket on 2005-11-16
Hi,

Ubuntu is pretty awesome, but for my needs in the past I have always installed Apache-PHP-MySQL with FreeTDS and mcrypt from scratch.  Ubuntu has almost everything I need as a package, except that I still need both mysql and mysqli.  I have no problem doing everything from scratch, but since Ubuntu has almost all of it, would it be easier to reconfigure the existing PHP5 package?

I don't know anything about source packages.  What are the steps to reconfigure?  Do I still do configure, then make, then make install?  Do I stop in the middle before install and do some command to turn my config into a installable package?  Are the default configure options listed in some input file for packages or are those always entered on the cammand line?

And one last strange thing...  Using phpinfo() on my other Linux boxes shows the configure options.  But running phpinfo() with the Ubuntu install doesn't show what the configure options were.  I'd like to know that, before modifyign anything.  Is there a dpkg command that shows the configure options for a package?


Thanks in advance for any help!

---

### Post by rkelly on 2005-11-18
[quote=joe_rocket]
And one last strange thing... Using phpinfo() on my other Linux boxes shows the configure options. But running phpinfo() with the Ubuntu install doesn't show what the configure options were. I'd like to know that, before modifyign anything. Is there a dpkg command that shows the configure options for a package?[/quote] 
Weird that it doesn't show the compile time options. Maybe it is disabled for security reasons.
Try to get the info from the commandline:
# php -i | less
You will get a number of screens full of info...
 
(if less is not available use more)

---

### Post by joe_rocket on 2005-11-18
From the comman line, php -i doesn't give me the configuration command options, either.

I gave up trying to use mysqli at this point.  I also just added the apache-ssl module, and now apache doesn't know what a php file is.  (gives me a save file as pop up).  So, I go to look at the httpd.conf and ssl.conf.  The httpd.conf is just a few lines about being there for backwards compat and everything is in apahe2.conf.  I tried adding an AddType line for the php, and it doesn't work.

I think I am going to quit using Ubuntu.  It's great as an end-user system.  I like the ease to updating the system, but getting something other than what the default packages provide is a total pain.  I think everything is over-packaged and separated far beyond what the logic of the Linux File System Standard originally meant to do.

At this point, it's become so difficult to change anything beyond default, I'd rather go back to installing programs from scratch into /usr/local or wherever they default.  

Is there a simple way to feed the configure options into a source package and build it.  I tried to do PHP5 source package that way.  It doesn't work like the PHP5 instructions from php.net which I've used many times in the past.  It says something about apxs is not done the same anymore.  WTF?  I don't see the logic in so drastically changing the installation of the software.  Changing locations and directories is fine, but it seems to go way beyond that.

Can anyone clue me in on the logic here?

---

