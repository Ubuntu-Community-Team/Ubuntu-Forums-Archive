---
title: "How to resolve a hacked website?"
date: 2014-07-22
forum: Security
---

### Post by mastablasta on 2014-07-22
I am not a programmer. I have a wordpress website on LAMP server at a host (I think it is centos). I am looking for some pointers and advice here besides total reformat. 

Here is what happened - a person (that shall not be named) forgot to apply regular updates and patches. someone hacked into the website and placed a PHP file which started sending out nasty emails in my or rather sites/owners name. i noticed that the plugin in question (the TinyMCE wysiwyg editor) where this file appeared was abandoned at the end of April.

so I removed the plugin, made the updates, changed passwords and it was quiet for a week or so. until now suddenly a new file like that appeared in the theme's folder and again started sending out emails in owners name (as info [ad]mywebsite.com): .com/wp-content/themes/ifeature/cyberchimps/lib/css/model.php mail as then send as somefake.name [at] mywebsite.com
I checked for possible solution and was advised that the only solution is to delete everything and set it all up page by page by copy pasting the text. there is about 250 pages there with pics so that could take a while.

i have a few questions:
1. how did they gain access to be able to place files on server into folders that have view permission only? i mean they would need to know the wordpress password at least to be able to modify some files, right?
2. how can they be sending emails without email password pretending to be mywebsite.com?
3. is it possible that database is compromised?
4. is it possible that the whole server account is compromised?

now possible solutions and i am wondering are the even worth attempting:
1. remove and delete the theme, reinstall it. perform a scan with security plugin.
2. database - i have a copy of database (clean) from a year ago. since then we added a couple of sites. i actually wanted to perform full backup but the download was always interrupted by server when i attempted it. so database is all i have. i also have one after last breach which might already be compromised. i tried to add a backup plugin but none of them worked or perhaps they were blocked by server when attempting backups to google drive or dropbox. :( anyway question - if delete all from server, install website fresh and restore that old database (majority of pages are there) would i have my site back preety much as it was before?
3. if i asked the host to restore all files on my part of server from about a month ago and then do the all the updates & change password would that work? or will it create problems due to database?

i am not sure how i could protect myself better. ok backups but i tried those and couldn't make them as i wanted. but i removed the admin user, I've got files chmoded properly... the only thing that wasn't done is apply updates regularly (the person maintaining the site is at fault here).

right now the site is blocked by host. is there a way a host could help me here?

---

### Post by SeijiSensei on 2014-07-22
> I checked for possible solution and was advised that the only solution is to delete everything and set it all up page by page by copy pasting the text. there is about 250 pages there with pics so that could take a while.


All the textual content is stored in the database, though not the images.  I doubt the database is corrupted.  The problem seems to be a script that was inserted under /wp-content/.  You should not need to rebuild the site page-by-page.

Most exploits I've heard of attack that directory because it needs to be writable by the WP application in order to perform updates, install plugins, upload images, etc.  You might consider turning off write privileges in the /wp-content/ tree except perhaps to the /uploads/ subdirectory.  Blocking /themes/ seems especially important as it seems a common vector for exploitation.  You would need to re-enable write privileges during updates.  Since you're not directly responsible for the site, this would be a difficult thing to manage.

Perhaps a policy of relying on users to run updates isn't the best idea.  Is this the only WP site on the server?  Perhaps you should consider updating all the sites yourself.  I just checked my blog; the current version of WP is 3.9.1 and should be the only version running on any of your server's sites.

---

### Post by TheFu on 2014-07-22
In my mind, "urgent" == paid help.

While you may be able to find the core issue and correct it, how can you be certain?  I wouldn't trust it, but it is your site to manage.  Perhaps a WP + php + security expert should be brought in? I suspect backing up everything (even tgz is fine after dumping the DB), wiping and carefully reloading all the content would be less expensive and faster. Then reloading the plugins, 1-by-1 from known good, current, sources.   Use the WP migration tools.

And versioned backups need to be working, period.

---

### Post by thnewguy on 2014-07-22
I would wipe the account and start fresh from backup, but it seems you don't have recent backups.... So in that case you will probably want to remove and re-install your theme and clean out any scripts from the wp-content/uploads directory. The database is unlikely to be touched.

You asked about how a script could sent out e-mail without your account password. E-mail doesn't require a password, PHP scripts can send out e-mail that appears to come from any address.

---

### Post by mastablasta on 2014-07-22
> **SeijiSensei said:**
> All the textual content is stored in the database, though not the images.  I doubt the database is corrupted.  The problem seems to be a script that was inserted under /wp-content/.  You should not need to rebuild the site page-by-page.

Most exploits I've heard of attack that directory because it needs to be writable by the WP application in order to perform updates, install plugins, upload images, etc.  You might consider turning off write privileges in the /wp-content/ tree except perhaps to the /uploads/ subdirectory.  Blocking /themes/ seems especially important as it seems a common vector for exploitation.  You would need to re-enable write privileges during updates.  Since you're not directly responsible for the site, this would be a difficult thing to manage.

Perhaps a policy of relying on users to run updates isn't the best idea.  Is this the only WP site on the server?  Perhaps you should consider updating all the sites yourself.  I just checked my blog; the current version of WP is 3.9.1 and should be the only version running on any of your server's sites.

It's actually what the hosts suspects.

I have only one WP site. I will remove and reinstall the theme, lock down the folders as read-only then. and unlock them only to perform updates and when updating the website. It's not done everyday anymore (I mean adding new site). At best it is done bi-weekly.


> **TheFu said:**
> In my mind, "urgent" == paid help.


I was thinking about that as well. and checking my current state of finances. I was advised a site from a com,pany that specialises in this. Security audit + site move by moving text & pics only. but 150 EUR is a lot to pay right now.

> 
While you may be able to find the core issue and correct it, how can you be certain?  I wouldn't trust it, but it is your site to manage.  Perhaps a WP + php + security expert should be brought in? I suspect backing up everything (even tgz is fine after dumping the DB), wiping and carefully reloading all the content would be less expensive and faster. Then reloading the plugins, 1-by-1 from known good, current, sources.   Use the WP migration tools.


I dumped the DB recently  - as you said we can't be sure now if it was compromised or not.

I also have a dump from last year. not many pages were added since then. and we could more easily read them. so maybe I could use that to rebuild.

another option is perhaps to use a safety copy of server (image of my site from a month ago). and then update that. would that work? I mean ok again assuming that the site was not compromised before that date, and the spam only triggered later on.

> 
And versioned backups need to be working, period.

I know but I am not sure why I can't have them working. I mean the host is flexible but like in this security breach I am not sure why things are not working to tell them "hey, can you set it up like this...". I tried with plugins and while I could setup DB dump to server folder and arrange a versioned backup I can not make it to be dumped outside and preferably with pictures as well. the whole thing is about 700-800 MB big. before I could just download the site to my computer and I would then version it. manual backup is better than nothing. but then for some reason server started to interrupt the connection and treat it as spam.

---

### Post by Habitual on 2014-07-22
```
mysqldump -u <dbuser> -p <dbpassword>  > /path/to/file.sql
tar -pczf /path/to/<name_of_backup>_$(date +%F).tar.gz /path/to/file.sql /path/to/site/  /etc/apache2/sites-enabled/000-default 
rm /path/to/file.sql
```


```
59 23 * * * /path/to/mydump.sh > /dev/null 2>&1
```

Rename the admin account.
Change the admin password several times in several days.
I'd reserve usage on additional plugins and additional themes until you are sure.
I'd consider any export.sql suspect and should be visually inspected for any references to mail functions (this occurs in the "insert into wp-content" block, I believe and it's a LOT of visual)

644 for files.
755 for directories
lock down access to wp-login.php
```
<Files wp-login.php>
order deny,allow
deny from all
allow from <IP0>
Allow from <IP1>
</Files>
```

I use and pay for the wordfence plugin, but the free version is not lacking anything. ;)
Better WP Security seems to be a good plugin.

[http://www.gregfreeman.org/2013/how-to-tell-if-your-php-site-has-been-compromised/](http://www.gregfreeman.org/2013/how-to-tell-if-your-php-site-has-been-compromised/)
[http://www.gregfreeman.org/2013/steps-to-take-when-you-know-your-php-site-has-been-hacked/](http://www.gregfreeman.org/2013/steps-to-take-when-you-know-your-php-site-has-been-hacked/)

Most of this is covered at [http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)
Good Luck.

---

### Post by TheFu on 2014-07-22
Dump the DB somewhere on the system first, then do an rsync backup script [http://debian-handbook.info/browse/wheezy/sect.backup.html](http://debian-handbook.info/browse/wheezy/sect.backup.html) . rsync should be available on every hosting provider, IHMO.  Just like ssh should be THE ONLY allowed shell connection method. 

Using rsync for daily backups setup hardlinks on the remote storage makes the most sense when we don't completely own the web server.  I'd "pull" the backups, not "push" them.  Also, ensure the sync is over ssh (which is the default).

As to whether restoring a 1 month old backup is good - it might be the best you can do, but how do you know that the hack is closed? THAT is the main job, right after the main page is put back as a static page with a tiny explanation to what has happened, at least in my mind.

This issue just points out to all of us, including me, how important having a **plan of action** for getting a hacked web-property back running is **BEFORE it happens**.  I'll be reviewing our corporate plan ASAP - then actually TESTING IT - to ensure we don't miss something simple/stupid (as happens more than we like to admit) to everyone.  I worked in a place that did DR testing annually - about 90% of the tests failed on systems brought up since the last testing cycle - just say'in.  While it isn't rocket science (and I know that), it isn't as easy as it appears to be.

Oh - and the biggest mistake that I've seen made is assuming the wiki with all the restore instructions is available.  DR documentation needs to be so far away from the production systems it isn't funny - at least 500 miles.  Having a local copy is good, since that system may not go down, but trying to work through a complex DR plan without updated documentation is asking for many failuers.

---

### Post by mastablasta on 2014-07-22
A BIG BIG thanks to all who contributed with soem good advice and offer of help!

I used a malware scan plugin and uncovered many pontential issues. I had the files checked by an expert and they confirmed the files are infected.

I have a clean db form last August. Since then we only added two pages (so i saved the text from those two on my computer).

iI believe i was on the receiving end of this attack: [http://blog.sucuri.net/2014/07/malware-infection-breaking-wordpress-sites.html](http://blog.sucuri.net/2014/07/malware-infection-breaking-wordpress-sites.html)

though site have not been broken as i deleted non essential plugins i mean those that are not used on front end.

what i plan to do:
- have host restore an image form a month ago or it can be older
- update all plugins
- install malware scan app and perform a scan to find any suspicious files and to report further breakin attempts and give some security alerts
- lock all files down for editing
- change all passwords

hopefully that should do it.


if not i have the old db and i can rebuild from scratch and then just add the two pages that are not there.

i will be doing the debian handbook a closer look on weekend to setup some backups. i think it is really high time i automate these processes and maybe buy a server for backups. just waiting how much new glasses and major car service will put me back for... if i can't get anything i think i will use the "ultra old" laptop and put some external HD on it :-D

---

### Post by Habitual on 2014-07-22
If you want some off-site storage for backups, shoot me a PM and I'll hook you up.
I have ***tons*** of storage.

---

### Post by TheFu on 2014-07-22
If your home connection is on broadband, that can easily be used for automatic backups over rsync+ssh with minimal $$ commitment.
A new Atom-class $150 storage "server" (not storage device, but Ubuntu/CentOS/Debian) can easily pull incremental daily backups from 20-200 small-scale websites. It isn't about the size of the site, but the daily data changes.

Unless you have full, strong, encryption, I wouldn't put anything in "the cloud" - all the ramifications still aren't well understood and once it is "out", there isn't any way to get it back.

Oh - and I found a great rdiff-backup tutorial ... [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) much better than anything I've written, while still being short and to the point. Of course, that mean you'll need to have it on the host AND the client.

I am definitely NOT suggesting heavy, redundant-everything, server-class hardware for this, until you need it. Old servers are really cheap for a reason. They are power-hungry, noisy and HOT (heat).  OTOH,  I would NOT use a laptop for this either.  Always on systems really need good cooling, which tends to be the downfall of laptops. A microATX "atom" system with 6 SATA ports and a GigE port can do amazing things as a backup/storage system on a home LAN.

In terms of locking down the files from editing ... I love to use read-only mounts. This is a good idea for static content too.  It is fun to watch scripts trying to **sudo chmod** and nothing happen ... then they try to setfacl to reset ACLs ... and nothing happens.  

Good times!  We all need a little joy in life. ;)

---

### Post by CharlesA on 2014-07-22
I don't have much to add other than a +1 to restoring from backups and adding the missing pages manually.

if a box is compromised, you can never be "too sure" it is completely clean.

@TheFu: Thanks for mentioning rdiff-backup. I've been using rsync with hardlinks for a while and it becoming a royal pain to sort thru the different (dated) folders to find an earlier version of a file.

---

### Post by CharlesA on 2014-07-22
I don't have much to add other than a +1 to restoring from backups and adding the missing pages manually.

if a box is compromised, you can never be "too sure" it is completely clean.

@TheFu: Thanks for mentioning rdiff-backup. I've been using rsync with hardlinks for a while and it becoming a royal pain to sort thru the different (dated) folders to find an earlier version of a file.

---

### Post by TheFu on 2014-07-23
> **CharlesA said:**
> @TheFu: Thanks for mentioning rdiff-backup. I've been using rsync with hardlinks for a while and it becoming a royal pain to sort thru the different (dated) folders to find an earlier version of a file.

I love **locate** / **updatedb** for finding files instantaneously.
Still - rdiff-backup makes versioned backups with very little hassle to storage that you control completely i.e. not encrypted or shared with other people.

---

### Post by CharlesA on 2014-07-23
> **TheFu said:**
> I love **locate** / **updatedb** for finding files instantaneously.
Still - rdiff-backup makes versioned backups with very little hassle to storage that you control completely i.e. not encrypted or shared with other people.

I usually just grep the rsync log files, but it's still a bit of a pain.

---

### Post by 1clue on 2014-07-23
I don't know yet if your site is business or personal.  Or rather I guess the question is, what is this site worth to you?

Personally I've had a system hacked on several occasions over the years, and once that happened I have never been able to dispel the nagging itch that I might not have cleaned everything out.  In the cases where I waited long enough, most of them that itch proved correct.  I have in every case wound up formatting the drive and starting over.

I recommend that you get current backups of the files containing your work.  Even if they're infected, they might be enough to salvage most of your work.  Then I'd scrape it off and start over, and maybe consider a hardened install and some additional measures you didn't take before.

This is extremely unwelcome I know, but it is what it is.

You might consider [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) as a starting point for some reading.  If your site is truly centos, you can certainly find a similar site aimed specifically at centos, or whatever distro you're using.  And start using real passwords, and possibly multi-factor authentication.  You can get all sorts of helpful ideas by googling "<distro> security best practices". I'm not trying to put you off here, but if you don't know what distro there's only so much help a guy can give.

If this is just a personal site, I would call this incident an opportunity to learn.  If it's a business site then obviously your focus must be to get it back up, but again it's an opportunity to learn.  It sucks, but you gotta take something good from the bad IMO.

Good luck and have fun.

---

### Post by mastablasta on 2014-07-23
site is business but also personal
:)

I got all the files down and even windows antivirus picked up a malicious PHP file and quaranteened it.


I know the only way to be sure is to start from scratch but at the moment I do not have the time to do this. I figure that the site wasn't compromised for example 6 months ago since there were no spam messages. in the link I posted it seems these attacks happened recently. I am still not sure how they got in, because passwords were strong - 20 random characters. I think it must be some vulnerability in wordpress.

I can harden the site but only up to the point that it will not be inconvenient to users. so the backend part could be hardened a bit more but the front end should be normally accessible.

---

### Post by 1clue on 2014-07-23
How many users have logins and actually use the site?  A large percent of compromises are phishing or trojan horse attacks.  If you have people doing work there, then you might actually have to worry about that.

There's no way to prevent a careless admin from breaking security, no matter how good the setup is.

---

### Post by mastablasta on 2014-07-24
I know the phishing issue.

I have only two admin users - me and my significant other who is now feeling bad for not applying the updates on time... eventhough I am not sure that would protect us. we used to have the website on SBI where she learnt how to create websites etc, but then after they tampered with SEO and google dropped us and many others to 3rd page we decided to move. also it was way too expencive there.

I also have a normal user (myself) that can't do any editing. I use it to test and see if there are any issues - eg. guest vs. logged in user.

I've setup wordfence so I am monitoring the infection spreading (or rather their "eval function" commands). no one attempted or even logged in as admin.

I got a note from he host they've had issue with other guests accounts on server & wordpress recently. they monitored my site for 2 hours and found out that attack is coming from uploads folder. I told them bad code is now all over the place and increasing and asked again for restore of older copy. apparently the attackers were able to dump PHP script into that folder. but I asked them how they did that, since folder was 755. if it was because of plugin then subfolder from plugin would have execute and write permissions, but it didn't. in fact malicious code was placed in main uploads folder and I also found it in one of the folders with pictures.

I think I need to check the logs to see if anyone actually logged to server from another, unknown IP

the good news is they do have a backup copy, the bad news is it is dated 2 day prior to attack. :( 

I will see if the infection really stopped now, then I will remove infected files or edit them manually. it's just 56 of them now...Good news is I haven't seen any alert form wordfence this morning. perhaps encouraging...

---

### Post by mastablasta on 2014-07-25
so it turns out the old backup is infected as well. and them deleting the entire uploads folder didn't help. no kidding... :) luckilly i downloaded the pics just before they managed to do that. they are not really listening to me. i think they are small company. and they told me others with wordpress on their servers also suffered attacks.

anyway i have this healthy db from August last year. there are 3 pages missing in there since we added them later. but i have the text and pictures for them.and the only thing i can't remember how i did was a nice rotating galery. i remember i modified some plugin script. oh well... 

i will do a full fresh reinstall and remove a couple of plugins in the process as i was chekcing this site [http://smackdown.blogsblogsblogs.com/2008/06/24/how-to-completely-clean-your-hacked-wordpress-installation/](http://smackdown.blogsblogsblogs.com/2008/06/24/how-to-completely-clean-your-hacked-wordpress-installation/) 

i have two problems now :
1.  if i delete the wp folder is the infected database deleted? or do i somehow need to remove it in phpmyadmin?
2. i used a complex password for database and wrote it down. but we can't find the notebook :) so... would that be an issue?

---

### Post by 1clue on 2014-07-25
Consider using source control.  Wordpress is probably mostly a database backup, but for any static files you might consider putting them into git or similar.

Give the website's user read-only access to your repository, and lock your official repository down as tight as you can.  You make changes to your main setup (offline or inaccessible at all via web) and then when you're ready you push it to your public server.  Then lock your firewall down on your internal copy, so it can't be reached.

This gives you several things:
[LIST=1]
[*]A test site
[*]The ability to have multiple developers on several boxes working concurrently
[*]Security (they mess it up, you just reload)
[*]History and rollback capability.
[*]Failover.  Every copy on git is a full backup.
[/LIST]

---

### Post by SeijiSensei on 2014-07-25
If you are not happy with your current provider, I suggest you give [Linode]("http://www.linode.com") a try.  You can spin up a 14.04 server in just a few minutes, and they'll only charge you for the days you use.

---

### Post by TheFu on 2014-07-25
Can't help with anything else (assuming you get versioned backups working), but ... 

> **mastablasta said:**
> 2. i used a complex password for database and wrote it down. but we can't find the notebook :) so... would that be an issue?

This sounds like a job for a password manager?
[http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)

---

### Post by CharlesA on 2014-07-25
> **SeijiSensei said:**
> If you are not happy with your current provider, I suggest you give [Linode]("http://www.linode.com") a try.  You can spin up a 14.04 server in just a few minutes, and they'll only charge you for the days you use.

+1. Also [RamNode]("http://ramnode.com/") is a really nice provider too.

I would definitely look into version control. I need to do that for my site, but I haven't gotten around to doing it just yet.

---

### Post by 1clue on 2014-07-26
I work with Linode ***Edit:** as a customer*.  It's pretty good, they're a basic provider with good automatic services, we've never had to actually get a human involved I think.

---

### Post by SeijiSensei on 2014-07-26
> **1clue said:**
> we've never had to actually get a human involved I think.

I have, and they are excellent.  Quick responses and a knowledgeable staff.

---

### Post by 1clue on 2014-07-27
Actually that "never had to get a human involved" part is outstanding no matter what their customer service is like.  I use 3 different hosting sites for my job.  The other two are excellent, but you rely heavily on the support staff for some things.

BTW, Contegix is one, no real complaints and otherwise similar to Linode.  I think I prefer Linode though.  The other is Firehost, and they're outstanding if you're doing something aimed at PCI compliance.

---

### Post by SeijiSensei on 2014-07-27
Well, I needed customer service after I managed to crash my VM.  They helped me through the process of spinning up another machine and restoring from the backups.  At the time I was only backing up one machine through Linode; now I pay the $5/month for both my servers.

One other useful feature is being able to log into the host server itself and mount one's VM as a filesystem.  I once accidentally deleted an openssl library on a CentOS machine and promptly broke all the other applications that depended upon it, SSH in particular.  I obtained a copy of the missing library, then mounted the VM and put the file back into /usr/lib where it belonged.  Rebooted and was back up and running again.

Linode's services themselves are highly reliable.  Me, less so!

---

### Post by mastablasta on 2014-07-28
So I did a full restore from last year's database. had to "fight" the host and wordpress during that. And I still need to change a few passwords, but will have to check how to do it first. and I need to add 3 sites that were added in this year.

good thing I downloaded the whole thing down to disk the first time it happened. the second time they just said : the infection came form uploads folder so we deleted everything there. while in reality the infection was all over the place. I've found out how it happened on the internet: [http://blog.sucuri.net/2014/07/mailpoet-vulnerability-exploited-in-the-wild-breaking-thousands-of-wordpress-sites.html](http://blog.sucuri.net/2014/07/mailpoet-vulnerability-exploited-in-the-wild-breaking-thousands-of-wordpress-sites.html)

I've hardened the Wordpress (firewall, locked down some crucial PHP files...), and will do it even more once I have some peace and go through the articles& instructions.

> **TheFu said:**
> 

This sounds like a job for a password manager?
[http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](http://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)

The notebook WAS the password manager. :)

Anyway I've been telling my wife for some time now to put all passwords into KeyPass so as to not forget them and to be able to have more complex passwords. I share the passwords over spideroak hive. spideroak encrypts the files (again) before sending them out and the user is the one with they key. they can't access/unlock the files. might be slow but it is ok for these small files. and they have a Linux client.

also I checked rdiff guide and I was also checking rsnapshot which seems to be slightly better. at the moment I set it to do backups to dropbox account via updraft plugin (zip full site and then transfer as well as database backup). that should be about 1 GB all together. but I am contemplating my next move to be able to do backups of my other things (pictures, funniest home videos...) at home. I've been doing this for the last 6 months following various threads. maybe it's time.

> **SeijiSensei said:**
> If you are not happy with your current provider, I suggest you give [Linode]("http://www.linode.com") a try.  You can spin up a 14.04 server in just a few minutes, and they'll only charge you for the days you use.

I've checked Linode and RamNode. these are virtual servers or rather you need to deploy and maintain all by yourself. the idea with this hose was that I pay them to do some work for me since I do not have much time and lately I am also having problem s with access from where I work. So my wife has to have simple access to it. besides it would be same as setting up my own server. I have 20/20 internet and with a really small monthly payment increase I could have 50/50 which is actually enough for these relatively small traffic sites.

hat we have at the moment is a 10 GB plan with unlimited download and 1Mbit/s limited upload. 1 GB RAM for the site and can have 4 domain names for free and unlimited subdomains. the price is ok and they used to be quite good and more responsive than they are now which is why I took them long time ago (10+ years). they are actually also quite flexible. 
but I guess things change with time. I've never had this sort of thing before. and in this case I would expect them not only to completely lock me out (including cpanel access etc), but for them to find out how infection happened and to let me know how to repair it instead of just randomly deleting files etc. am I expecting too much from a webhost?

I couldn't download the site backup I remember that server kept interrupting me. I was thinking maybe it's some security anti- flooding measure. so back then I asked them do you keep backups and they said sure we keep it It's in the price. and they would restore upon request. little did I know they keep the oldest backup from 10 days back. no monthly?

anyway I think this is solved and I will now be opening a new thread about backups in server section...

---

### Post by TheFu on 2014-07-28
The key thing to me from your link is this:
>  To be clear, the MailPoet vulnerability is the entry point, it doesn&#8217;t mean your website has to have it enabled or that you have it on the website; if it resides on the server, in a neighboring website, it can still affect your website. 

I guess that is part of the reason why our CSO doesn't allow php on internet-facing websites?  Cheap shared-hosting seems to be the issue and having a dedicated VPS the solution - well - at least it removes another client's failure from 
being the cause.

When using a password manager - a key thing is to back it up to multiple places after every change.  I put mine on more than 5 different physical systems daily, automatic. I'm trying to get to 100% ZERO risk of losing that data - ever.

---

### Post by mastablasta on 2014-07-28
well I removed the mail poet completely now. we'll see how well the host has the sites separated. i am also hardening wordpress. we'll see If it happens again. if it does, I am moving to VPS immediately. restore should be easy enough as I have backups...

---
yeah the passwords file is on 3 computers and USB key and get's moved to them after any password update.

---

### Post by TheFu on 2014-08-04
A few relevant articles:
* [http://www.gregfreeman.org/2013/steps-to-take-when-you-know-your-php-site-has-been-hacked/](http://www.gregfreeman.org/2013/steps-to-take-when-you-know-your-php-site-has-been-hacked/)
* [http://www.gregfreeman.org/2013/how-to-tell-if-your-php-site-has-been-compromised/](http://www.gregfreeman.org/2013/how-to-tell-if-your-php-site-has-been-compromised/)

Out of my depth (we don't us PHP on the internet), but thought these were from a reputable source.

---

### Post by mastablasta on 2014-08-04
the links are good and informative. i am getting attempts to post things into the wordpress site, but it was hardened so they get access denied or rather a 404 error on the folder.

i am still checking the database (will need host help to identify any other users than the ones i created).

then i need to secure more the other site a bit more that is also on server.

---

