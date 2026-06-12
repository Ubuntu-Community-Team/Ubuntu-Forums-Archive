---
title: "I've wrongly ch-moded apache's stuff"
date: 2008-08-08
forum: Server Platforms
---

### Post by cmatte on 2008-08-08
Hi,
I'm new to Ubuntu's world, but I am progressively learning and it's very fun :popcorn:
Ok, let's explain a bit what I've done: 
I've downloaded and installed manually the latest version of Apache2 from their website(in the repository there's an old version): "./configure.." setting the path to /etc/apache2, choosing modules I wanted, then I've done the "make" and the "sudo make install" (I knew checkinstall --fstrans=no only after).
I've personalized my httpd.conf & the ssl one with my "old" cert used with stunnel and it was working perfectly if run from the command line doing "sudo /etc/apache2/apachectl -k start".
After this discovered how to do a symbolic link to apachectl into /etc/init.d and did the "update-rc.d apachectl defaults" from there.
It rocked :guitar:

Here's the real problem now:
I wanted to "secure" logs (moved to ~/logs/Apache2/PLAIN and ~/logs/Apache2/SSL for ssl), apache2 dir, the cert moved from a windows dir to an apache2 subdirectory, the /etc/init.d/apachectl script. 
So I did some ""tricks"" with chown and chmod but...seems they were not right, as Apache2 "apachectl -k start" doesn't say anything and the web page(nor http nor https) doesn't open any more.
Could you help me with better understanding how to chmod these dirs:
/etc/apache2 (install dir)
/etc/apache2/ssl (certs)
/home/matte/logs/Apache2 (logs, with PLAIN and SSL subdirs)
/etc/init.d/apachectl (symbolic link to /etc/apache2/bin/apachectl).
I'd like to open/read logs when I want, and not be able to change/modify/delete them if I'm not root.

Many thanks.

---

### Post by windependence on 2008-08-08
Well you might want to consider a re-install and I almost never recommend this. It was probably not necessary to compile the package from source, and it will bit you in the @ss later on when your package management is screwed up. the version in the repositories is certainly not "old". Having the latest and greatest is not always the best.

The other issue is since you have the permissions messed up, if you try to fix them it may appear to work OK now but something will almost surely bite you later on.

If it was me I would just uninstall your compiled version and do 

```
sudo apt-get install apache
```

Or install the entire LAMP stack if you need it. Things will go a lot smoother down the line that way.

-Tim

---

### Post by cmatte on 2008-08-08
Hi windependence,
thanks for your answer.

My subconscious knew there was an 'easy' way, but I am really -almost always- interested in having the latest version...or better, the latest 'marked as stable' version, especially if it's about important data.
  
Anyway, I've just figured out what was wrong, it wasn't permissions, but the fact I deleted logs folder from apache2 dir and it still wants to use it to write the httpd.pid file! If it can be useful to someone, I got these info launching apachectl from its own folder.

As root, under terminal, I set the permissions for all critical files to 755.Nautilus says root can read/write, the root group can read, others can read.Is this right and 'secure' enough?

P.S. One fact made me reflect a bit...googleing I found many are running apache with a "www-data" user and give "him" all the permissions.
Since I installed from source I don't have it and I think I'm running apache as root?or as my user? Should I create and configure this www-data user too? 
I'd like to understand all this better,
Thanks.

---

### Post by windependence on 2008-08-08
755 is fine.

You don't want to have the document root owned by the Apache user though. Apache should be running as www-data or sometimes just www, that's fine but don't change the ownership of the files to have www-data own them or else if someone compromises your site, they can do all kinds of things including putting up other sites on your server. Leave the document root (usually /var/www) owned by root.

You can check by running top as to what your apache processes are running under. They should not be running as root.

-Tim

---

### Post by StickyStyle on 2008-08-08
> **cmatte said:**
> 
My subconscious knew there was an 'easy' way, but I am really -almost always- interested in having the latest version...or better, the latest 'marked as stable' version, especially if it's about important data.


Keep in mind that all major bugs and security fixes from the upstream release are backported into the version that is released with ubuntu.  So as long as that version of ubuntu is supported, you will receive critical bug and security fixes for apache or any package installed from the main repo. 

The latest 'marked as stable' version of software is not always the *most stable*, it's just the version they decided that the critical bugs that where found in testing are squashed - there could be more.

---

### Post by cmatte on 2008-08-09
StickyStile,
are you telling me that I should expect to find security fixes I see in [Apache2 2.2.9 changelog]("http://www.apache.org/dist/httpd/CHANGES_2.2.9") into Ubuntu repository's package marked as 2.2.8-1ubuntu0.3?

How can I be sure of this? I mean, are there any Ubuntu package precise changelogs with the date of the last update? Why isn't version changed to 2.2.9 so? Is it because they only updated security bugfixes and not the new functionalities?

I'm -very- confused :confused:
And I still don't understand why isn't a 2.2.9 package there since it was released about 2 months ago, and there is a Ubuntu server version out there too...

[B.T.W...]
Just to continue stressing you all with Apache's stuff...I were willing to make it run as www-data or simply www.
I created a group called www into "Users and Groups", giving it a progressive ID and not adding any current user to it. 
How should I do the rest now?
I've just noticed the
> User daemon
Group daemon
part into httpd.conf, and it's not commented!
Into system-administration-users and groups there isn't any daemon, nor in users nor in groups.
How can Apache work in these conditions?!

How to solve this all :) ? I mean, I think I should change daemon to www and then give www the ability to read files in /etc/apache2, to write logs(append only and not modify/delete, is this possible?), and to read the DocumentRoot (which is, btw, a Windows disk, in which I'm not able to change permissions, all can read all can write etc but this is only a test right now and another story, I will solve in some other way...like forgetting Windows later :popcorn:).
So, since I always changed permissions with chmod with sudo for me or with su root -c "...", how can I create a "hidden" www user and change its permissions? Shouldn't I create a password for it? 

I would really like to understand this, it would be useful for every other service I currently run or I will run... thanks!

---

### Post by mbeach on 2008-08-09
is apache working under those conditions?

you likely have a user 'daemon' and probably has uid of 1.  Since you've chmod'ed your apache folders to 755, daemon can read them.  Did you select the option to show all users when looking for the daemon user?  Try something like:
cat /etc/passwd | cut -d":" -f1
to list all the users, I'm sure daemon will be in there.

interesting take on your question:
[http://bethesignal.org/blog/2008/03/31/understanding-the-ubuntu-package-repositories/](http://bethesignal.org/blog/2008/03/31/understanding-the-ubuntu-package-repositories/)

why is there not a package for a two month old release?  Has it been fully tested?  Does it cause any problems with other programs?  Does it break any functionality previously working?  Simply stated, its not mature enough.  See:
[http://en.wikipedia.org/wiki/Debian#Development_procedures](http://en.wikipedia.org/wiki/Debian#Development_procedures)

Because you've made things so custom, and there's nothing wrong with that other than to cause yourself extra effort, a lot of the advice you may get here on future posts/problems may end up being not quite correct.  Most people are going to assume you have a default setup, so go easy on folks when they respond based on default setups.

If you need to create a user with a uid less than 1000, which is what I think you mean when you say 'hidden', you could start with:
[http://kheyali.blogspot.com/2008/07/users-with-uid-of-less-than-1000-not.html](http://kheyali.blogspot.com/2008/07/users-with-uid-of-less-than-1000-not.html)


Good luck,
mb.

---

### Post by cmatte on 2008-08-10
Many thanks mbeach, you gave me great starting points and I happily found/modified users into /etc/passwd and its passwords in /etc/shadow.
daemon was there, with id 1 as you said :)

I still have some questions unanswered and didn't find any suggestion elsewhere.
Apache2 IS working, and seems as daemon looking at the vars into /etc/init.d/apachectl (or into the the default one into /etc/default, don't remember).
I still have to understand how can it read my ssl cert, as it's readable and even listable only by root, and not his group(neither me)!
Shouldn't I give it the permissions to read the files it needs?
How can I do it?
I thought with su *user*, but these particular users don't have a password set (it's * OR ! into shadow file, what does these wildcards mean btw?), so I'm asked for it but can't provide it, and I don't think I should set one for them only for this!

I'm having the exact problem with mediatomb, which doesn't start because it doesn't have the permissions to read its database as mediatomb:mediatomb...so understanding this would help me 2 times :popcorn:

Thanks again.

---

### Post by cmatte on 2008-08-13
Up! Someone?

---

### Post by StickyStyle on 2008-08-13
> **cmatte said:**
> 
I still have to understand how can it read my ssl cert, as it's readable and even listable only by root, and not his group(neither me)!
Shouldn't I give it the permissions to read the files it needs?


When apache is started it has a master process that runs as root which spawns all the worker processes that actually answer web requests.  It has to do this because web traffic is normally on port 80 and ports < 1024 require root privileges to bind to.  So while starting up as root apache grabs the ssl certs and keys, so you don't need to change the permissions.

Regarding your 'daemon' user/group in httpd.conf, I assume that is from your custom compiled version of apache (as ubuntu doesn't use httpd.conf, it uses apache2.conf)?  To create a user for 'system usage' you do the following...
```
$sudo adduser --system www-data
```
The --system automatically puts the user in the system UID range, sets the shell to /bin/false, and disables login (and a think a couple other things that i cant remember).  The 'addgroup' command also uses the --system parameter.

Also regarding your question to me about security updates, yes all pertinent security updates are backported to the version of ubuntu you are running for the full support term of that release.

See [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
and [https://wiki.ubuntu.com/SecurityUpdateProcedures](https://wiki.ubuntu.com/SecurityUpdateProcedures)

The security announce list is here [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

### Post by cmatte on 2008-08-14
> **StickyStyle said:**
> 
When apache is started it has a master process that runs as root which spawns all the worker processes that actually answer web requests.  It has to do this because web traffic is normally on port 80 and ports < 1024 require root privileges to bind to.  So while starting up as root apache grabs the ssl certs and keys, so you don't need to change the permissions.

This was the point I was missing, thanks :popcorn:
> **StickyStyle said:**
> 
Regarding your 'daemon' user/group in httpd.conf, I assume that is from your custom compiled version of apache (as ubuntu doesn't use httpd.conf, it uses apache2.conf)?

You assume right.
> **StickyStyle said:**
> 
To create a user for 'system usage' you do the following...
```
$sudo adduser --system www-data
```
The --system automatically puts the user in the system UID range, sets the shell to /bin/false, and disables login (and a think a couple other things that i cant remember).  The 'addgroup' command also uses the --system parameter.

Thanks for this...before I had edited the file manually to do it, this is a lot more professional, secure and fast:lolflag:

> **StickyStyle said:**
> 
Also regarding your question to me about security updates, yes all pertinent security updates are backported to the version of ubuntu you are running for the full support term of that release.

See [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
and [https://wiki.ubuntu.com/SecurityUpdateProcedures](https://wiki.ubuntu.com/SecurityUpdateProcedures)

The security announce list is here [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I'll take a look!
Oh...I've already said 'thanks' :rolleyes: :)

Oh, btw, in the meanwhile I have found a great guide which also helps to maniacally set every permission of the folders of Apache2,
if it's useful to someone [here it is]("http://xianshield.org/guides/apache2.0guide.html").

---

