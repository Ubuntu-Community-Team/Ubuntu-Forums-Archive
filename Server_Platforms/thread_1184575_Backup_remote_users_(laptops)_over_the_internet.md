---
title: "Backup remote users (laptops) over the internet"
date: 2009-06-11
forum: Server Platforms
---

### Post by Zinder on 2009-06-11
I've been playing with open-source backup solutions lately (Bacula and BackupPC) but I really need a way to backup files of remote users over the internet.  Does anyone know of any open-source solutions to this?  Also, although our servers in-house are linux and windows, all of the remote users are windows :(

Thanks

---

### Post by HermanAB on 2009-06-11
Howdy,

A good backup solution is a one line rsync script in cron.daily.

Every other solution is unnecessarily complex and far more difficult to maintain than a one line rsync script...

---

### Post by Zinder on 2009-06-11
> **HermanAB said:**
> Howdy,

A good backup solution is a one line rsync script in cron.daily.

Every other solution is unnecessarily complex and far more difficult to maintain than a one line rsync script...

I think even this will get complicated real quick if I implement it the way I need to.  So, I need it to be somewhat secure transer over internet (ecrypted connection).  I need to be able to open up the firewall as little as possible, so preferably only one port (I'll google rsync + port in a minute) and I need reporting of success/failure which I'm assuming I can do with the Nagios setup I'm implementing.

A little background info: I have 10+ years of windows / networking experience with some casual linux tinkering here and there so I'm pretty new to the nitty gritty linux admin stuff.  I now do SMB consulting and it seems that most of our customer's budget's dropped significantly due to the economy.  So, in response I've been playing almost exclusively with linux and open-source solutions for the last month.  I've replace 2 aged Backup Exec installs with Bacula and am using BackupPC for workstation/laptop backup.  I'm currently planning and beginning to implement a pretty complex (at least to me) Nagios monitoring network that will monitor roughly 15 sites and offer a pretty display for our customers.  

So, that being said... Ideally I would like something with a web interface that I can show off to customers and say "see how easy it is to for me to restore your files" (BackupPC is a PERFECT example of this.  The delay I'm running into is being able to do this over the internet without relying on VPN.

Thanks for the good reply :)  I've found that the Ubuntu community is FAR more helpful and generally nicer than the Microsoft community.

---

### Post by grantemsley on 2009-06-11
rsync works via ssh, which is automatically encrypted, probably already open on your linux servers, and uses file differences to transfer as little as possible (ideal for internet traffic).

I used to have my windows computer backing up via cygwin rsync and a script in scheduled tasks.

---

### Post by Zinder on 2009-06-11
> **grantemsley said:**
> rsync works via ssh, which is automatically encrypted, probably already open on your linux servers, and uses file differences to transfer as little as possible (ideal for internet traffic).

I used to have my windows computer backing up via cygwin rsync and a script in scheduled tasks.

Nice! Yes, I already have SSH open to this server.  Now I either have to A) figure out how to get scheduled rsync to push to BackupPC over the internet... or B) Develope my own pretty web interface for file restores with no prior programming experience... :-k

Thanks for the help guys!

---

### Post by HermanAB on 2009-06-11
The trick with rsync is to use '-e ssh' which makes it secure and uses only one TCP port.  To specify the backup set, select /home and then *exclude* the file patterns that you *don't* want to backup.  That creates a maintenance free script that will backup everything that is new.

Do read the rsync man page.  It is easy to use.

Rsync is the reason why all backup GUI tools are crappy - new users look around for a backup tool, find nothing good and then proceed to write yet another crappy backup GUI based tool.  In the process they learn how to do it the right way using a one line rsync script and the crappy GUI tool gets abandoned, to trip up the next new user...
;)

---

### Post by Zinder on 2009-06-11
> **HermanAB said:**
> The trick with rsync is to use '-e ssh' which makes it secure and uses only one TCP port.  To specify the backup set, select /home and then *exclude* the file patterns that you *don't* want to backup.  That creates a maintenance free script that will backup everything that is new.

Do read the rsync man page.  It is easy to use.

Rsync is the reason why all backup GUI tools are crappy - new users look around for a backup tool, find nothing good and then proceed to write yet another crappy backup GUI based tool.  In the process they learn how to do it the right way using a one line rsync script and the crappy GUI tool gets abandoned, to trip up the next new user...
;)

Sadly that makes perfect sense... ;)

Sounds like I'll be heading in the right direction now.  Thanks :)

---

### Post by danrche on 2009-06-11
Zinder,

1st off, little something that may help with Windows PC's [http://www.gfi.com/backup-hm](http://www.gfi.com/backup-hm) .... and it's free


Amanda is a widely used Opensource backup tool, [http://amanda.zmanda.com/](http://amanda.zmanda.com/)


CloneZilla -- opensource disk imaging software (works on windows)
	[http://www.clonezilla.org](http://www.clonezilla.org)       [http://clonezilla.sourceforge.net/clonezilla-live](http://clonezilla.sourceforge.net/clonezilla-live)

clonezilla - I like this one for images and use it to backup images to a NAS. I've been playing with a test on a laptop of this to partition off part of the HDD and use that as the collection point for the image and when ready, pop in the restore cd and it pulls image right from the HDD. (not ready yet, still a few bugs to work out). 


I know most of this will probably not help but maybe others looking into the same thing will see this and know of the other options and maybe get some ideas of their own to pursue. 

Cheers...

---

### Post by grantemsley on 2009-06-11
For the restoring side of it, there's one very simple solution:

Setup a web server, with directory indexes turned on, and pointed at the backup directory on the server.  Setup access restrictions and passwords as appropriate.

Then if people want to restore a file, they can just login to the web site, browse their latest backup, and download whatever files they are missing.

---

### Post by Zinder on 2009-06-11
> **danrche said:**
> Zinder,

1st off, little something that may help with Windows PC's [http://www.gfi.com/backup-hm](http://www.gfi.com/backup-hm) .... and it's free


Amanda is a widely used Opensource backup tool, [http://amanda.zmanda.com/](http://amanda.zmanda.com/)


CloneZilla -- opensource disk imaging software (works on windows)
    [http://www.clonezilla.org](http://www.clonezilla.org)       [http://clonezilla.sourceforge.net/clonezilla-live](http://clonezilla.sourceforge.net/clonezilla-live)

clonezilla - I like this one for images and use it to backup images to a NAS. I've been playing with a test on a laptop of this to partition off part of the HDD and use that as the collection point for the image and when ready, pop in the restore cd and it pulls image right from the HDD. (not ready yet, still a few bugs to work out). 


I know most of this will probably not help but maybe others looking into the same thing will see this and know of the other options and maybe get some ideas of their own to pursue. 

Cheers...


Thanks!  I didn't realize that GFI had a free home version!  That'll be nice to recommend to people (like my mother-in-law who destroys her computer monthly by clicking on seemingly everything)

I looked into Amanda first and got it working on our network.  However, the lengthy CLI config, lack of easy restore (couldn't find a way to bare-metal restore windows withough a LOT of time), and nothing pretty to show the customer (sad as that is) pretty much made me put it on the back burner.  I'd really like to see the enterprise version some day.

I'll definitely checkout clonezilla as I am fed up with Acronis...

Thanks!

---

### Post by danrche on 2009-06-11
Glad to have helped.... :) :o

---

### Post by Zinder on 2009-06-11
> **grantemsley said:**
> For the restoring side of it, there's one very simple solution:

Setup a web server, with directory indexes turned on, and pointed at the backup directory on the server.  Setup access restrictions and passwords as appropriate.

Then if people want to restore a file, they can just login to the web site, browse their latest backup, and download whatever files they are missing.

Gah! Why didn't I think of that... this is exactly what I need for the remote users.  Now... I just need to find a way to talk my wife into making me a nice web interface... She's much better at the pretty web stuff than me ;)

Thank you very much :)

---

### Post by danrche on 2009-06-11
> **grantemsley said:**
> For the restoring side of it, there's one very simple solution:

Setup a web server, with directory indexes turned on, and pointed at the backup directory on the server.  Setup access restrictions and passwords as appropriate.

Then if people want to restore a file, they can just login to the web site, browse their latest backup, and download whatever files they are missing.



humm, that's an interesting idea.... here's another, you can point your backups to a NAS (like freenas or openfiler). Link 'em to your LDAP server, then share out the files by dept then users, same as the web page but the NAS resources can grow to how ever many HDD you can fit in the system, and in Openfiler you can take snapshots of the NAS system. Best part, it's all web based, and supports smb, nfs, ftp, etc....

---

### Post by grantemsley on 2009-06-12
A script to give the option to download directories as a zip file might be handy too.

---

### Post by K4KEP on 2009-06-19
RE: GFI

Read the data very carefully. From what I see, it calls home very often and who knows what it is "taking off" your computer during its numerous calls home. All of us have private information on our hard drives. Do you want companies reading your private stuff.

Oh by the way, on their opt out of call home. I tried and it refused to accept it repeatedly.

---

### Post by mande01 on 2011-05-07
Ok... this thread totally got me hooked.

So how do i do all this, I have a server and I want to pull in backups from outside to this server.
Can someone walk me through the abc's of this? A feature for me would that the back up never deletes a file, ie only if client deletes a file the backup will not delete the same file during a sync.

I can do basics (configuration, installs etcc) but it's user access, permissions, firewalls, networks, services etc. I'm weak at this stuff.

Any help would be great.

Should I set up a separate thread?

Thanks for any info.
Derry

---

### Post by danrche on 2011-05-09
> **mande01 said:**
> Ok... this thread totally got me hooked.

So how do i do all this, I have a server and I want to pull in backups from outside to this server.
Can someone walk me through the abc's of this? A feature for me would that the back up never deletes a file, ie only if client deletes a file the backup will not delete the same file during a sync.

I can do basics (configuration, installs etcc) but it's user access, permissions, firewalls, networks, services etc. I'm weak at this stuff.

Any help would be great.

Should I set up a separate thread?

Thanks for any info.
Derry

Derry, this is an old post, but these days you may want to look into just dropbox, it's easy to setup and hands free, as well as lightweight. I guess it really depends on what you're backing up.

---

### Post by mande01 on 2011-05-09
My bad,
Should have checked the date.

Thanks for that, I use dropbox already but as I said above.Its not from me but I want to sell a backup service to clients.

Thanks,
Derry

---

### Post by danrche on 2011-05-09
> **mande01 said:**
> My bad,
Should have checked the date.

Thanks for that, I use dropbox already but as I said above.Its not from me but I want to sell a backup service to clients.

Thanks,
Derry

Derry,

I miss understood you. If you're looking to resell a solution, you'll want to start playing with some scripting technology to build out a client to do the decision making for what's getting backup and what's not. Are you supporting windows clients? linux only? If you're going to support windows are you going to do servers? Exchange stores, and sql as well as SBS system state?

There's a lot to think of when trying to build a solution on your own. if you're just looking to sell disk space take a look at CrashPlan [http://www.crashplan.com/](http://www.crashplan.com/)

it runs on mac, linux, and windows. me and a few other guys at work actually put a server at the office (fedora box) and it stores all our data securely and encrypted so I can't see the other guy and he can't see mine. I don't think you could sell the app, but you could sell disk space.

---

### Post by danrche on 2011-05-09
> **mande01 said:**
> My bad,
Should have checked the date.

Thanks for that, I use dropbox already but as I said above.Its not from me but I want to sell a backup service to clients.

Thanks,
Derry

Derry,

I miss understood you. If you're looking to resell a solution, you'll want to start playing with some scripting technology to build out a client to do the decision making for what's getting backup and what's not. Are you supporting windows clients? linux only? If you're going to support windows are you going to do servers? Exchange stores, and sql as well as SBS system state?

There's a lot to think of when trying to build a solution on your own. if you're just looking to sell disk space take a look at CrashPlan [http://www.crashplan.com/](http://www.crashplan.com/)

it runs on mac, linux, and windows. me and a few other guys at work actually put a server at the office (fedora box) and it stores all our data securely and encrypted so I can't see the other guy and he can't see mine. I don't think you could sell the app, but you could sell disk space.

---

