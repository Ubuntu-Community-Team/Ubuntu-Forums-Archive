---
title: "What to look/check for when moving PHP 5.3/4 from Ubuntu 10.04 to Ubuntu 16.04?"
date: 2019-10-08
forum: Server Platforms
---

### Post by soscopyrights on 2019-10-08
Hi guys. I'm in a position where I have to migrate a working Ubuntu 10.04.02 server with PHP 5.3.29 to a Ubuntu 16.04. Don't ask why we're not using PHP 7.3 or 18.04 ... 
My problem is that I don't know how to do it, what's the procedure? What should I look for? I mean, I can't just move the files from one server to another and update its config.


For example, I found out that I need to compare the PHP modules between the two servers. And, since I can't find any PHP 5.3.29 repo, I've decided to use [Sergey's PHP 5.4.45]("https://launchpad.net/~sergey-dryabzhinsky/+archive/ubuntu/php54") with Apache 2.4.18. I've added Sergey's PHP modules repo, compared the PHP modules using "php -m" and started installing the missing modules on the new server. But, this wasn't the only thing I was supposed to compare. I found out I should start comparing the rest of the modules using "pear". Ok, now what? What about Apache?


I mean, how should I proceed further? 


Thank you.








What to look/check for when moving PHP 5.3/4 from Ubuntu 10.04 to Ubuntu 16.04?

---

### Post by slickymaster on 2019-10-08
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2019-10-08
> **soscopyrights said:**
> I mean, I can't just move the files from one server to another and update its config.

That is exactly what I would do (but copy...not move).

I would get a working copy of Ubuntu Server 16.04 running in a virtual machine (I use VirtualBox on my Windows PC) and then install Apache and the version of PHP you are wanting on it.

Once I got the base system setup, I would copy over the website files and then the website configuration and activate it.  If you are using a database, I would also setup a new database server (or at least a new database) and get a working copy of the database running.

If you do not know what modules you need, test the web site and see what breaks.  Then research what is needed and fix it as you go.  You might find that the original server might have too many modules installed that were never needed or no longer needed.

Once you have everything working well, DOCUMENT how you did it.  I would then recommend to delete the 16.04 instance (and related database if any) and do it again following your instructions.  Once you are 100% sure you can re-build the server, you can then proceed with steps to migrate.  If you are running on a physical box, you can temporarily migrate it to a virtual machine and run it from there while you re-format the physical server and load it with 16.04 and follow your DOCUMENTATION to make another working 16.04 installation (but copying the data from the virtual machine) and then migrate the IP back to the physical when ready for it to take over production.

This also assumes you have a complete backup of the original server so that if you have to restore, you can do so even if the operating system was replaced.  You might also want to test and verify that the backup can be restored as well.

LHammonds

---

### Post by soscopyrights on 2019-10-08
> **LHammonds said:**
> 
If you do not know what modules you need, test the web site and see what breaks.  Then research what is needed and fix it as you go.  You might find that the original server might have too many modules installed that were never needed or no longer needed.

Once you have everything working well, DOCUMENT how you did it.

LHammonds

LHammonds, I'm already doing all these things you're saying. But, I was expecting to learn what are the concepts when someone's trying to upgrade to a new server, what are the concepts you should have in your head, in what order should you do X things - though, as I'm writing this, I'm realizing that maybe I should just learn more about PHP and Ubuntu servers. 

Thank you, LHammonds.

---

### Post by TheFu on 2019-10-08
+1 on using virtual machines.  Everywhere I've worked since 2005 has used VMs by default.

What "concepts"?  It is just like backup and recovery, except the underlying programs and OS are different so you need to handle each difference.  Between 10.04 and 16.04, there have been huge changes.  10.04 was the last Ubuntu that felt like "Unix should", IMHO.  Every major release after that has caused some pains to get things working.  
* apache versions changed and the access controls for apache changed.
* networking has changed twice
* The OS init system has changed, twice.

Best to move to a new LTS release every 4 yrs than to be at risk on an unsupported OS for so very long.  I would assume the 10.04 machine has been hacked, a few times, since 2015. I wouldn't blindly copy all the website files over. Each one needs to be checked.  Plus, the version of php **must** have changed to close hundreds of php security issues.

---

### Post by LHammonds on 2019-10-08
> **soscopyrights said:**
> But, I was expecting to learn what are the concepts when someone's trying to upgrade to a new server, what are the concepts you should have in your head, in what order should you do X things
What I said are some basic concepts.  You are going to be hard-pressed to find any documentation out there on taking a PHP application from Ubuntu 10.04 (skipping 12.04, 14.04) and going straight to 16.04.

Each PHP application (especially custom ones) are different.  Going from one version of PHP to the next might break it if using a 3rd-party PHP library that is tied to the older version.  You would need to obtain a newer version of the outdated library and then figure out what in the PHP code needs to be updated since it was likely referencing deprecated functions and whatnot.  Sometimes you cannot upgrade PHP if the dependencies are not yet updated or may never be updated (e.g. defunct company).

If you are not the creator of the PHP application, I hope you have support from the one(s) that did create it.  Going from such an old PHP platform to a newer platform can be painful.  I can guess why you are not going with PHP 7.x due to all the deprecated functions that were completely dropped which tend to break old PHP applications.  However, you can get PHP 5.x to run on Ubuntu 18.04.  I had to do so for a PHP app that had such dependency problems.  ([How to Install Xibo]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=250"))

> **soscopyrights said:**
> as I'm writing this, I'm realizing that maybe I should just learn more about PHP and Ubuntu servers.
I've been doing the same for a while now.  I document how I do it as I go and try to improve my process over time.  I try not to let any of my servers skip major releases.  All of my servers are either on the current LTS or prior LTS...nothing older.

[Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244")
[Ubuntu Server 16.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=220")
[Ubuntu Server 14.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=200")
[Ubuntu Server 12.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=191")
[Ubuntu Server 10.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=188")

LHammonds

---

### Post by soscopyrights on 2019-10-09
> **LHammonds said:**
> What I said are some basic concepts. You are going to be hard-pressed to find any documentation out there on taking a PHP application from Ubuntu 10.04 (skipping 12.04, 14.04) and going straight to 16.04.

Yes, but I was expecting something like:
'Listen, here's what you have to do:

[LIST=1]
[*]Find a respository for your PHP version. Add it to your new server and begin the installation.
[*]On your old server, now, you need to check what PHP modules are being used and after that, install them on your new server. "php -m" will show you the modules the server is using. Once you've installed them, make sure you also check modules using "pear".
[*]Check on your old server to see if there are any crons related to your PHP.
[*]Once finished with PHP, you have to look to Apache. Check what mods are enabled on the old server and reproduce them on the new one.'
[/LIST]

You see what I'm trying to get at? And, yes, I already am being hard-pressed about this task.

> **LHammonds said:**
> I can guess why you are not going with PHP 7.x due to all the deprecated functions that were completely dropped which tend to break old PHP applications. However, you can get PHP 5.x to run on Ubuntu 18.04. I had to do so for a PHP app that had such dependency problems.
LHammonds
The thing is, we, as network and sys admins are aware about these issues. But, we've outsourced to a 3rd party the coding part of the site. Basically, they're maintaining it. They said to keep this old version of PHP on the new Ubuntu. They want it like that. Yes, because there are applications that still need the use of PHP 5. Anyway, I'm trying to say that, I'm trying to do my part (the server) and they said they'll do their part (the app's code and dependencies). And, LHammonds, dude, I just love what you got there on your "legacy". Pretty well documented. 


Anyway, I'm appreciating all of your guys' replies. Keep having a great week.

---

### Post by Tadaen_Sylvermane on 2019-10-09
I don't understand why people don't like to update things when php is concerned, but I know that is my own lack of knowledge. That being said might I suggest forgoing Ubuntu altogether and switching to CentOS instead. A 10 year support cycle is great for this stuff. 16.04 will be EOL in just a year and a half or so and it makes little sense to upgrade a production server to that imho, just a waste of time really. I'm not sure how much support is left on CentOS 7 but I'm sure it is more than 2 years, which puts it well past 16.04 supported time frame. The last thing you want to do is run unsupported.

I know this is the Ubuntu forums, and I'm being bad saying another distro, but you have to pick the right tool for the right job.

---

### Post by LHammonds on 2019-10-10
I get what you are saying soscopyrights, I just don't think you will find anything that will apply.  It sounds like you have a custom app which means nobody out there is going to have a list of steps for things to check that will cover your situation completely.  That is why I said to create a VM to test it out and document how to make it work...and finding those little gotchas such as something running in crontab, or placed in a cron.daily folder or a custom script in /usr/bin or a manually-compiled library, quirky permissions, etc.

If you have a 3rd-party developer that created the code and maintaining it, ask them for migration procedures.  They may have a list already that covers all the checklists for making the app work.

If the code maintainers are actively developing the app and it is still on PHP 5.x, I have to assume it is not because they just like PHP 5.x that much but rather they are leaning heavily on other old 3rd-party software that is not getting updated and/or they cannot replace easily.  Many popular libraries that are no longer maintained are stuck in PHP 5.x because they use the MySQL library which no longer exists in PHP 7 (it is now MySQLi).  It is not very difficult to switch to the new standard but if you do not have the sourcecode or rights to do it yourself...well, that becomes a problem and you need to find an alternative or code it yourself.

Good luck with the migration.

LHammonds

---

### Post by sdsurfer on 2019-10-10
> **Tadaen_Sylvermane said:**
> I don't understand why people don't like to update things when php is concerned.

Usually it's due to a legacy code base and is a ***business ***decision.  The most important thing is to keep a system working and the business  must consider the cost of the updates and debugging required to move to  the next major version. If there is a business loss doing the update, it gets delayed.

A perfect example is I was digging into a  particular PHP 7+ feature and came across a blog of someone who wrote a  plugin for Wordpress and he updated and deployed it. His error:  converting array() to []. As soon as it was deployed, the tickets  started coming in. For whatever reason and many different reasons, many  of his users were "stuck" on a pre-7 version. Broke a lot of web sites.  :-D

---

### Post by soscopyrights on 2019-10-10
> **sdsurfer said:**
> Usually it's due to a legacy code base and is a ***business ***decision.  The most important thing is to keep a system working and the business  must consider the cost of the updates and debugging required to move to  the next major version. If there is a business loss doing the update, it gets delayed.

Exactly. Plus, I'm also in a position where I have to figure out what the guys before me did. Nothing documented.

---

