---
title: "Installing Bugzilla package on 11.04"
date: 2011-09-25
forum: Server Platforms
---

### Post by areeda on 2011-09-25
I'm having a few issues trying to install Bugzilla.  Hopefully someone who's done it successfully can help.  My experience with BZ is as a user, this is my first server install so please excuse the stupid questions.

First of all the package install BZ 3.6.3.0-2 while the current version at bugzilla.org is 4.0.2.  While I prefer package installs, is is worth getting V4?

Next, I'm having permission problems and it's not clear how to resolve them.

It seems like the package scatters BZ files in:

[LIST]
[*]/etc/bugzilla3
[*]/usr/share/bugzilla3
[*]ls /usr/share/perl5/Bugzilla/
[/LIST]
Perhaps other places but this is all I've found so far.  After install everything is owned by root:root with permissions 755.  This causes problems with checksetup.pl especially while trying to secure things with .htaccess.  Shouldn't at least some of the directories be in the www-data group and group writable. 

I haven't found a good Ubutuntu how to install past Ubuntu 9.  Is that because y'all found something much better?

Thanks
Joe

---

### Post by areeda on 2011-09-26
Well, I decided to install v4.0.2 from the bugzilla.org site.

It is up and running.  I followed their instructions and had to load a bunch of perl modules (for full functionality) and a good number of packages.

If this is a common issue, I think I can now do a wiki page on installing from the download.

Joe

---

