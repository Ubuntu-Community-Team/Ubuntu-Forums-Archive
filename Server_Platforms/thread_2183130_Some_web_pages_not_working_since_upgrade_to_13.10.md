---
title: "Some web pages not working since upgrade to 13.10"
date: 2013-10-23
forum: Server Platforms
---

### Post by Chris of Arabia on 2013-10-23
I upgraded a day or so back but am now seeing some odd behaviour, in that some web pages and apps work, but others don't anymore and are reporting 'page not found'

The ones that work are:

[LIST]
[*]App - phpmyadmin
[*]App - webmin
[*]Page - phpinfo
[/LIST]

The ones that don't work are:

[LIST]
[*]App - Mantis
[*]Page - default "It works!"
[/LIST]

From what I can see, nothing about the missing ones has been deleted, but Apache doesn't appear to be able to find them, so my guess is that perhaps a config/redirect file has been overwritten, I just need to nail down which one. Can anyone give me a quick pointer as to where to look first?

---

### Post by cariboo on 2013-10-24
Have you checked /var/log/apache2/error.log to see if there is an indication of the problem?

---

### Post by nobodyfamous on 2013-10-24
it may be related to the upgrade to apache2.4

from ispConfig> [COLOR=#282828][FONT=Lato]Ubuntu 13.10 has been released recently. This new Ubuntu versions uses apache 2.4 by default which causes various problems. The apache configuration Syntax has been changed from apache 2.2 to 2.4, so websites that were created for apache 2.2 will fail on the new version.[/FONT][/COLOR]

---

### Post by Chris of Arabia on 2013-10-24
> **cariboo907 said:**
> Have you checked /var/log/apache2/error.log to see if there is an indication of the problem?

There's nothing in the error log that indicates anything amiss, and all I can see in the Apache Access Log are a series of 404 errors, which tell me no more than the browser response give me.

> **nobodyfamous said:**
> it may be related to the upgrade to apache2.4

from ispConfig

That's where I'm headed next...

I forgot to mention, the phpinfo page is what I'm being presented with instead of the "It works!" page.

---

### Post by Chris of Arabia on 2013-11-16
My apologies for resurrecting this, however, since my last post, I've got precisely nowhere with this and things are much as they were, though admittedly I've not had much time to put into it.

My main www directory is sitting in:

[LIST]
[*]/var/www/ - which contains
[LIST]
[*]index.php (holds the phpinfo request) 
[/LIST]
   
[/LIST]

The Mantis installation is located in the default location the distro installed it to:

[LIST]
[*]/usr/share/mantis/ 
[/LIST]

Though I can also find related files in:

[LIST]
[*]/etc/mantis/
[LIST]
[*]apache.conf 
[*]config_inc.php 
[*]config_local.php 
[*]custom_constraints_inc.php 
[*]custom_functions_inc.php 
[*]custom_relationships_inc.php 
[*]custom_strings_inc.php 
[*]htaccess.dat 
[/LIST]
   
[/LIST]

As far as the default 'It works!' page goes, well, I can find dozens of them, but the one I suspect is the correct one is located at:

[LIST]
[*]/usr/share/apache2/default-site/index.html 
[/LIST]

The thing that seems odd to me, is that it's not just an application that apache seems to know nothing of (in this case Mantis), but also that index.html file. That's the most basic indication that apache is working, yet seemingly, apache knows nothing of it - it's never been moved, never edited, or changed in any way. Which brings me to the comments by nobodyfamous - how would the[FONT=verdana] "[COLOR=#282828]apache configuration Syntax has been changed from apache 2.2 to 2.4" apply here? Would apache syntax apply to how it goes about locating a basic html file? To be honest, most of what I've read on the subject just leaves me scratching my head.

Would anyone care to give me a bit of a clue on how apache routinely finds the applications installed within it's realm? It's finding other apps (webmin, phpmyadmin), so why not these?

Oh, and here's the phpinfo file, or at least the top of it, maybe that offers some clues.

[ATTACH=CONFIG]247876[/ATTACH][/COLOR][/FONT]

---

### Post by Chris of Arabia on 2013-11-16
> **Chris of Arabia said:**
>      
As far as the default 'It works!' page goes, well, I can find dozens of them, but the one I suspect is the correct one is located at:

[LIST]
[*]/usr/share/apache2/default-site/index.html 
[/LIST]



I just tried renaming this one to something else, just to check whether index.php files had been prioritised in the /var/www/ folder, but no such luck - I just get the directory listing, it doesn't try and scoot off elsewhere to find what it's looking for.

---

