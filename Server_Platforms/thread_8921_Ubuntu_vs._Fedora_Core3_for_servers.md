---
title: "Ubuntu vs. Fedora Core3 for servers?"
date: 2004-12-22
forum: Server Platforms
---

### Post by BillDrew on 2004-12-22
I have an old IBM 300GL that currently has Fedora Core 3 installed on it.  I would like to use Ubuntu on it but want to experiement with various webserver based services for libraries.  Can Ubuntu do this and where is the best palce to get the Apache for this?  I am a newbie to Linux.

---

### Post by mr_ed on 2004-12-22
The best place to get Apache from is the Ubuntu repository.

Open up Synaptic and do a search for apache.  It's there.  Do you want apache 1 or 2?  If you want version 1, you'll have to enable the Universe repository, but that's not recommended, since stuff in Universe doesn't get security updates.  So... use 2.

If you prefer to do it from a terminal:
sudo apt-get update
enter your user password
sudo apt-get install apache2

There are also plugins for databases and PHP, Perl, Python, etc.

sudo apt-get install libapache2-mod-auth-mysql
will install the mySQL plugin.  ;)

Easy as pie.  :)

The default webpage is located at /var/www, I believe.

---

### Post by BillDrew on 2004-12-22
Many thanks.  that is all I needed to know to get me to use Ubuntu.  I am installing it now on my test machine.  I have found the Ubuntu community much friendlier to newbies like me than the Fedora Core community. 8-) 

Bill Drew
Systems Librarians
[Morrisville State College Library](http://library.morrisville.edu) 
[EMAIL=drewwe@morrisville.edu]drewwe@morrisville.edu[/EMAIL] 
  :D

---

### Post by acidmax on 2004-12-27
One more thing: **cgi-bin** is located at the unusual **/usr/lib/cgi-bin**, not in **/var/www/cgi-bin** as it should be.

---

### Post by Ninja Cow on 2005-01-02
[QUOTE=BillDrew]I have an old IBM 300GL that currently has Fedora Core 3 installed on it.  I would like to use Ubuntu on it but want to experiement with various webserver based services for libraries.  Can Ubuntu do this and where is the best palce to get the Apache for this?  I am a newbie to Linux.[/QUOTE]
 Ubuntu all the way. One of my machines went wacko on me recently so I had to start over. Now, on this box I've tried several distros for a server: Red Hat, Mandrake, Fedora, and then Slack.  Let me put it this way: My Ubuntu machine is twice as fast as my (previous) Slack box.

Setup took less than 30 minutes for everything I need.

---

### Post by britishtrident on 2005-01-04
[QUOTE=Ninja Cow]Ubuntu all the way. One of my machines went wacko on me recently so I had to start over. Now, on this box I've tried several distros for a server: Red Hat, Mandrake, Fedora, and then Slack.  Let me put it this way: My Ubuntu machine is twice as fast as my (previous) Slack box.

Setup took less than 30 minutes for everything I need.[/QUOTE]
 I found Fedora Core 1 & 2  to be nice looking  and because it has  highly tweaked kernel it is the fastest of the big brand commercial distros but it is also  full of really serious bugs  --- after all FC is only intended as a testing distro for future Red Hat releases. 
For stability a Debian based distro is required and although it is very early days the future of Debian is clearly spelled unbuntu.
Ubuntu and other Debian based distros are slimmer and  faster than the big brand name Linux distros but more importantly the handling of .deb software package installation by apt makes updating, removing and installing sdoftware almost fool proof  unless an incompatible repository is added to the sources list.

Short of a custom Gentou installation (a nice pastime if you have at least a couple of weeks to spare) the fastest distro is Yoper but although a very quick and easy install is too cutting edge for general use it is also the product of just one very talented guys very hard work.       
I use Yoper on one of my destop PCs and love it but apart from an IPCop firewall all my other nix PCs are unbuntu.

---

