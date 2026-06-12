---
title: "The Hoary Infrastructure Thread!"
date: 2005-01-19
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-19
In this thread, I'll have ramblings about the new, next-generation backporting infrastructure. Major shortcomings I saw with Warty Backports were:

1.Can only have one backports developer. Any more, then sync would start overwriting and conflicting each others' changes. BOY, wouldn't that be fun?
2.Upload downtime. While uploading and committing changes, the repository would be in an inconsistent state. People would get mysterious Forbidden errors.
3.Circle of Trust / Integrity: There's no method of making sure that packages weren't tampered with. There's no bookkeeping of who MADE the backport.
4.Inefficiency of Backport Announcements: It took way too much effort to write a backports announcement. Sometimes, writing this takes longer than making the actual backport!
5.Inefficiency of promotions architecture. Too much of this process was MANUAL! I would like a user-friendly, automated promotions interface.
6.Lack of statistics. I'd like more detailed reports about backport usage than “200 downloads daily”. When's “off-peak” hours? Which packages are most popular?

The Solution: UBP-NG

This is going to be a PHP+MySQL driven, pseudo-web-based backports tree management protocol, with a versioning system backend. It solves all the problems above.

1.You can have multiple developers. Each one gets a login name via PHP and a CVS/Subversion account. Optionally, restrictive permissions may be imposed through CVS ACL's or Authz (I think). Hopefully, it won't be necessary to do so! Versioning systems are DESIGNED to prevent simultaneous-work conflicts.
2.The main download tree can synchronize with the CVS tree at preset times daily. Optionally, two trees may be available for download, and the download script rotates them for synchronization. In addition, the versioning system and the download tree will most likely be on the SAME SYSTEM, which means almost instant synchronization.
3.CVS/Subversion keeps logs of who's done what. On top of that, a checksum/hash will be made by the PHP script, whenever a backport in the versioning tree is registered with the web frontend. Only registered and checksummed packages will be permitted to download. Unregistered packages will cause a 404 error, packages that fail checksumming will cause a 500/Internal Server Error. Both will alert the backports tree maintainer.
4.Once a backport is registered with the frontend, there will be enough information in the database, so that info pages can be generated on-the-fly. For backport announcements, all a maintainer has to do is provide a link.
5.The Versioning System Tree won't hold the APT directory structure. It'll be generated on-the-fly, by the download script. The MySQL database will hold info about exactly what section (backports, backports-staging, extras, etc etc etc) a given package goes in. The PHP frontend will have a user-friendly interface to designate which sections contain which packages.
6.The download script will keep statistics about downloads.

---

### Post by poofyhairguy on 2005-01-19
[QUOTE=jdong]In this thread, I'll have ramblings about the new, next-generation backporting infrastructure. Major shortcomings I saw with Warty Backports were:

1.Can only have one backports developer. Any more, then sync would start overwriting and conflicting each others' changes. BOY, wouldn't that be fun?
2.Upload downtime. While uploading and committing changes, the repository would be in an inconsistent state. People would get mysterious Forbidden errors.
3.Circle of Trust / Integrity: There's no method of making sure that packages weren't tampered with. There's no bookkeeping of who MADE the backport.
4.Inefficiency of Backport Announcements: It took way too much effort to write a backports announcement. Sometimes, writing this takes longer than making the actual backport!
5.Inefficiency of promotions architecture. Too much of this process was MANUAL! I would like a user-friendly, automated promotions interface.
6.Lack of statistics. I'd like more detailed reports about backport usage than “200 downloads daily”. When's “off-peak” hours? Which packages are most popular?

The Solution: UBP-NG

This is going to be a PHP+MySQL driven, pseudo-web-based backports tree management protocol, with a versioning system backend. It solves all the problems above.

1.You can have multiple developers. Each one gets a login name via PHP and a CVS/Subversion account. Optionally, restrictive permissions may be imposed through CVS ACL's or Authz (I think). Hopefully, it won't be necessary to do so! Versioning systems are DESIGNED to prevent simultaneous-work conflicts.
2.The main download tree can synchronize with the CVS tree at preset times daily. Optionally, two trees may be available for download, and the download script rotates them for synchronization. In addition, the versioning system and the download tree will most likely be on the SAME SYSTEM, which means almost instant synchronization.
3.CVS/Subversion keeps logs of who's done what. On top of that, a checksum/hash will be made by the PHP script, whenever a backport in the versioning tree is registered with the web frontend. Only registered and checksummed packages will be permitted to download. Unregistered packages will cause a 404 error, packages that fail checksumming will cause a 500/Internal Server Error. Both will alert the backports tree maintainer.
4.Once a backport is registered with the frontend, there will be enough information in the database, so that info pages can be generated on-the-fly. For backport announcements, all a maintainer has to do is provide a link.
5.The Versioning System Tree won't hold the APT directory structure. It'll be generated on-the-fly, by the download script. The MySQL database will hold info about exactly what section (backports, backports-staging, extras, etc etc etc) a given package goes in. The PHP frontend will have a user-friendly interface to designate which sections contain which packages.
6.The download script will keep statistics about downloads.[/QUOTE]

kool

I didn't really understand the second list!  :-$

---

### Post by jdong on 2005-01-19
This implementation might lead to a problem:
Sourceforge may not be a suitable host for UBP-NG!

1. CVS is inefficient with this setup. In my experience, when versioning tons of binary objects, Subversion is far, far superior. I don't want to put ridiculous load on the SF.Net CVS servers -- they're running **Fedora Core**! ;)

2. Permissions issues. I see the need to **sudo** to another regular (non-root, of course!) user, in order to update packages.gz and friends. I see the same need to **sudo** to a regular user in order to run an update command on the tree. I need **cron** in order to do routine maintainence on the tree, such as running a cvs update.

3. Quirky server, slow server. SF's servers do not download reliably (we've experienced that, right? ;)), and from my experience with my adambots-live project, their servers are extremely slow at running PHP scripts -- sometimes taking more than 5 seconds to generate a PHPbb forum page. I don't want backports users to put up with this anymore.


So, basically, I need a generous donor to offer me these services! A server that can host subversion repositories (just a mod for apache2), give apache sudo access to another non-privileged account, allow cron usage, have PHP(4/5, don't care)+MySQL,  and have some bandwidth.

I'm a poor high school student, so it's out of my reach! I would "invest" in backports, but I've not even gotten enough donations out of backports to pay for a lunch at my school! Will some kind soul please step up to the plate?  All of us Ubuntu users would be in debt to you forever.

---

### Post by TravisNewman on 2005-01-19
How much bandwidth do you think it'll need, and how fast of a machine do you think needs to host it? I personally can upload at around 32 kilobytes/second, so that may not be enough to fit your needs, but if it is, I can do it.

---

### Post by TravisNewman on 2005-01-19
And in other news, you're only in high school? You seem mature for your age :)

And by the way, I can wipe the system in question and put whatever you need on it, even setting up ssh access on it so I can run it without X at all. In my spare time, basically, I can also help you with anything you need in setting up the infrastructure-- I've got some PHP/MySQL experience under my belt.

Edit: I'll refrain from making a new post this time. Just letting you know even if my machine/connection doesn't meet your needs, I'd like to help out with setting everything up, if you've got room for one more :)

---

### Post by jdong on 2005-01-20
[QUOTE=panickedthumb]And in other news, you're only in high school? You seem mature for your age :)

And by the way, I can wipe the system in question and put whatever you need on it, even setting up ssh access on it so I can run it without X at all. In my spare time, basically, I can also help you with anything you need in setting up the infrastructure-- I've got some PHP/MySQL experience under my belt.

Edit: I'll refrain from making a new post this time. Just letting you know even if my machine/connection doesn't meet your needs, I'd like to help out with setting everything up, if you've got room for one more :)[/QUOTE]
 Panickedthumb, ANY hosting system is well appreciated! I'll check to see if APT can handle HTTP redirects. If so, we can have a bunch of mirrors, and switch around between them!

I'll also definitely need help setting things up. I plan on putting the main website scripts in Subversion, too, so that way we can all work on it together.

---

### Post by jdong on 2005-01-20
I'll try to use Sourceforge and CVS, if at all possible.

---

### Post by jdong on 2005-01-20
An update: David Longo of Somnium Computing (Lives in NJ) has a Gentoo server and a fat Business DSL line. I received e-mail confirmation from him today that it's ok to do our stuff on that server. Let's all thank him for his generous contribution!

---

### Post by jdong on 2005-01-20
To those interested in lending a developing hand: I'm currently in the planning phase.


Can anyone find a good howto of how pools work? I'm deliberating between:

1. Subversion the whole pool, with packages.gz and such -- so that packages are in a ready to use format to serve.

2. Subversion all the packages, generate directory structure using symlinks hourly, then generate packages.gz


#1 seems ridiculously easier. I may just serve the whole repository via subversion. Concurrent versioning will still work, and it'll be a LOT simpler on my side!

---

### Post by jdong on 2005-01-20
Ok, I've finally decided to do it a la #1. Subversion will directly dish out a folder structure almost identical to [http://ubuntu-bp.sf.net/ubuntu](http://ubuntu-bp.sf.net/ubuntu) , only with binary-ppc, etc structures.

Since subversion is fully atomic, upload-in-progress data will be invisible until after the upload completes fully! That way, there's NO problems with upload downtime.

I'll copy over the Warty-backports repository as a working demonstration. I may still continue testing the tree by backporting random Hoary packages to Warty. **THIS NEW TREE MAY BREAK DURING THE PROCESS** == consider it an alpha testing process until I finish!


If you're interested in stepping up to the plate for the non-i386 (ppc, x86-64, etc) backports, or would like to help me do i386 backports, please chime in! I'll make a backports howto now.

---

### Post by J. S. Jackson on 2005-01-21
Yes, SF is extremely slow.  I downloaded several backport items last night.. oh my.  3-5 KB/second.  Painfully slow.

All that aside, I got what I needed.  Thanks for your efforts jdong!

---

### Post by Alessio on 2005-01-21
[QUOTE=J. S. Jackson]Yes, SF is extremely slow.  I downloaded several backport items last night.. oh my.  3-5 KB/second.  Painfully slow.

All that aside, I got what I needed.  Thanks for your efforts jdong![/QUOTE]
 Great job! If you want i am helpful

---

### Post by jdong on 2005-01-22
I'd like to give everyone an update:

I do have the new repository set up (Subversion 1.1.1 on AMD64  Gentoo): [http://cloud9.homelinux.net:81/ubuntu/backports/](http://cloud9.homelinux.net:81/ubuntu/backports/)

I've decided to scrap plans for PHP/MySQL frontends -- Now that I have Subversion, I can have concurrent development, and full atomicity allows me to upload without interrupting downloads.

I will have access to Apache logs, which will give me all the stats I want.


I've made a backports howto. Please proofread and try to find errors. Thanks!

---

