---
title: "MediaWiki install-setup problem"
date: 2005-11-30
forum: Server Platforms
---

### Post by tarpon_bill on 2005-11-30
Hello,

Using Ubuntu 5.10 -- I have installed apache, php, mySQL, phpMyAdmin, wordpress, all from the synaptic package manager. All setup properly and now work fine :-).

Then I did an synaptic install of mediawiki -- But, when I try to setup MediaWiki, problems. Biggest is there is no config directory in /usr/share/mediawiki, hence no index.php setup file. The browser just faults, file not found, when clicking the link on the mediawiki start page. BTW, the mediawiki start page appears, so at least there is hope.

So -- where is the config/index.php setup file? or is there another way to setup mediawiki on Ubuntu?

I donwloaded the latest mediawiki tarball from the mediawiki site, uncompressed and all the files appear to be in the tarball as directed, including the config directory with the proper index.php file inside.

I don't know much about debian/ubuntu, mostly RH experience, but I am learning. Ubuntu is a nice polished distro and am planning to switch my server to it as soon as I figure it all out.

I searched, no joy, if there is a HowTo, a link would be appreciated.

I am going to tackle proftpd next, so if there is a HowTo a link would help since so far I can't find one yet.

---

### Post by marks_linux on 2005-11-30
mine was in /var/www/mediawiki(version)

I renamed the folder to just mediawiki to make things cleaner.

worth a look!

Mark

---

### Post by tarpon_bill on 2005-11-30
Did you do a tarball install or use synaptic?

I used Synaptic install, it put the files in /usr/share/mediawiki with a link to there in /var/www/. The mediawiki init page shows in the browser, so the install appears correct, it's just the config directory is missing. Bad synaptic package is what I suspect ...

---

### Post by marks_linux on 2005-12-01
Got mine using aptitude/apt.

---

### Post by tarpon_bill on 2005-12-10
Sounds like I found a broken package in the repository ...

The one from the MediaWiki site works so I am going to stick with that one for now.

---

### Post by seb_renaud on 2006-12-20
I am trying to install MediaWiki on dapper using synaptic, I seem to be missing a repository:

> 
mediawiki:
 Depends: mediawiki1.7  but it is not installable
 Depends: mediawiki1.7-math  but it is not installable


Can anyone point me in the right direction? I would preffer using synaptic / apt if possible, but I can handle another installation method if necessary.

---

### Post by b3ckm4n on 2008-02-27
I got the same issue, but I'm using Ubuntu 7.10 and MediaWorks 1.10. I got both, MySQL Server 5 and the newest version of MediaWorks, packages from the Synaptic Package Manager, and installed all the dependencies etc, and then restarted. 

I started up Firefox and checked [http://myinternalIP/](http://myinternalIP/) and saw that Apache was working. So I went to [http://myinternalIP/mediawiki/index.php](http://myinternalIP/mediawiki/index.php) and got a 404.

This is my first time using both Ubuntu and any version of a wiki, so I'm not really sure where to go from here. Any help would be greatly appreciated.

Thanks a lot

EDIT:
Ok, so I checked localhost/mediawiki1.10 (the folder name under /usr/share/mediawiki1.10) and it still doesn't resolve. The config folder is inside that folder, so I'm still not really sure what's going on.

EDIT 2:
Ok, so I changed the default DocumentRoot to /usr/share/mediawiki1.10/ instead of /var/www/, and I think I got it to work.

---

