---
title: "Web pages/applications I should run on my home media/NAS server?"
date: 2014-01-18
forum: Server Platforms
---

### Post by ted.drain on 2014-01-18
I configured a headless Ubuntu server last week as a home media/NAS/server system and am really enjoying it. Now that I have a web server at my disposal, I'm wondering what else I could be doing with it.  Here are the web apps I'm currently using:

- plex (LAN): video streaming and transcoding, android app for WAN access
- webmin (LAN): gui based admin (I'm a CLUI guy but I keep this just in case)
- owncloud (LAN/WAN+android app): dropbox style file syncing
- transmission (LAN/WAN+android app): torrent monitoring
- phpsysinfo (LAN): system status
- madsonic (LAN/WAN+ultrasonic android app): music streaming
- calibre (LAN): ebook access - not really that useful w/ all the other file access 

I'd like to find a nice picassa style photo management suite with a web interface but I haven't had much luck yet.  I'm starting to look at the various NAS vendors (qnap, synology, etc) to see what software they provide to get more ideas.  Any other ideas for useful web applications that I can run from a home server?

---

### Post by TheFu on 2014-01-18
Sounds like you are having a great time!

If you are CLI, I would dump webmin - it is a security risk even being loaded, IMHO. 

I'd setup an OpenVPN server so owncloud can be used from outside on the internet safely.

Your needs are very different from mine, but ... I run these:
* email front-end/anti-spam server
* Zimbra Collaboration Suite
* Alfresco document management
* vTiger - CRM app
* FreeNX - remote, secure, desktop access from anywhere in the world over ssh
* ssh - I assume you have that already
* Redmine - project management
* FreeSWITCH (great SIP PBX)
* Blog Server
* Wikimedia server 
* Reverse proxy (nginx) so only 1 static IP is needed, but many different HTTPS connections from the WAN are possible
* Photo Gallery - my security consultant will not allow PHP directly on the internet, so we use a highly modified perl "My Photo Gallery." PM me if you are interested and I'll provide a sample website.
* XBMC - you have Plex - now that I have a roku, plex seems useful.
* gnump3 - simple, powerful, music streaming server
* Virtualization - putting lots of services onto a single "server" makes upgrades harder.  I like to compartmentalize services now through virtualization.
* Storage Network - put all the storage on a different LAN segment than your main LAN. Should help performance between systems, even if just a backup array is used.

You didn't mention anything about backups. I use rdiff-backup, but there are many great tools. For media, where incremental backups aren't so important, something like SnapRAID (which I've never used), might be good.

The NAS providers are very expensive for what you get, IMHO.  Check out the FreeNAS forums for less expensive hardware that can hold 8-12 HDDs easily and blow away the performance of those storage vendors stuff with a great LSI 8-port SAS card.

Regardless - keep going!

---

### Post by tgalati4 on 2014-01-18
Browse through: [http://bitnami.org/stacks](http://bitnami.org/stacks)

For photo management try [gallery]("http://galleryproject.org/").

---

### Post by ted.drain on 2014-01-18
Thanks!  I'll definitely take a look at those.  [http://www.piwigo.org/](http://www.piwigo.org/) also looks like an interest photo app.  Add I just found [RDDTool]("http://oss.oetiker.ch/rrdtool-trac/wiki/SystemMonitorScripts") which makes very nice system status plots.

---

### Post by TheFu on 2014-01-19
> **ted.drain said:**
> Thanks!  I'll definitely take a look at those.  [http://www.piwigo.org/](http://www.piwigo.org/) also looks like an interest photo app.  Add I just found [RDDTool]("http://oss.oetiker.ch/rrdtool-trac/wiki/SystemMonitorScripts") which makes very nice system status plots.

For system monitoring, check out nagios, cacti, sysusage,  .... there must be 20 more that are also high quality.

Might be good to ask yourself, how will I get back everything if my main HDD or MB dies?  Then build a restore method to accomplish that with tools based on the amount of budget you are likely to have during an "emergency."  Basically, money vs time is the tradeoff. We all assume our hardware will work forever, but ...

---

### Post by ted.drain on 2014-02-28
For anyone else building a home server, here are some more services to consider:

- munin: detailed system status plots on a daily/monthly basis

I looked long and hard at various backup systems (BackupPC, burp, bacula, UrBackup) before deciding on UrBackup.  I'm primarily backing up Windows clients (and android devices) to the server and UrBackup handles image backups, increment image backups, file backups, increment file backups, etc. nicely.  I also use a couple of external USB 3 drives that I use rsync to copy files to for offsite backups.  WD Passport Ultra drives are reasonably priced ($120 for 2 TB), USB3, and have built in full disk encryption.

I also thought about running my own name server after my ISP's servers went down last week but I haven't looked into that yet.

---

### Post by m-dw on 2014-03-01
This may be sad.... I'm looking for a web app to deal with grocery shopping lists.  By the time I write my shopping list, I've usually forgotten what I need.

---

### Post by ted.drain on 2014-03-01
> **m-dw said:**
> This may be sad.... I'm looking for a web app to deal with grocery shopping lists.  By the time I write my shopping list, I've usually forgotten what I need.

If you have an Android phone, I recommend the free app Our Groceries.  It lets you have multiple lists and sync them automatically to multiple devices.  Works great for reminding your spouse to get something from the store.  There are any number of shopping list type apps for smart phones that probably are a lot simpler to use than an app on your web server.

---

### Post by m-dw on 2014-03-02
True, installing a smartphone app would be the most straightforward option (if I had a smart phone), but not as good as the only justification for buying a smart phone and signing up to an Internet plan.  On the other hand, a PHP/MySQL grocery app is pretty good as an additional justification for spending £600ish on the bits to make a home server/NAS (which I've already decided to build).

Note that the only person I'm justifying this to is myself, and I've convinced myself that I don't need a Smart Phone now that Angry Birds is available as Chrome app.

---

### Post by TheFu on 2014-03-02
> **m-dw said:**
> This may be sad.... I'm looking for a web app to deal with grocery shopping lists.  By the time I write my shopping list, I've usually forgotten what I need.

Pencil and paper work too. Leave it in the kitchen.  I tried web and android stuff for this ... not worth it. Paper and pen is 1000x better, IMHO. Spending £600ish when a $1 notepad and free pen from the bank solve the issue seems contrived. ;)

---

### Post by m-dw on 2014-03-02
> **TheFu said:**
> Pencil and paper work too. Leave it in the kitchen.  I tried web and android stuff for this ... not worth it. Paper and pen is 1000x better, IMHO. Spending £600ish when a $1 notepad and free pen from the bank solve the issue seems contrived. ;)

Oh yes, definitely very, very contrived :D.  I could live with my existing NV+ for another 4 years, but I want to run other services on it and it's hardly got enough power to run Logitech Media Server to 3 SqueezeBox devices (and I'm bidding on a 4th).

---

### Post by ted.drain on 2014-03-02
> **m-dw said:**
> Oh yes, definitely very, very contrived :D.  I could live with my existing NV+ for another 4 years, but I want to run other services on it and it's hardly got enough power to run Logitech Media Server to 3 SqueezeBox devices (and I'm bidding on a 4th).

You could use OwnCloud.  It's got a To-do/task list module that will work.

---

