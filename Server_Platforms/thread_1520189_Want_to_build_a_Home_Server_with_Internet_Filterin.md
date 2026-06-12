---
title: "Want to build a Home Server with Internet Filtering"
date: 2010-06-29
forum: Server Platforms
---

### Post by xanderwhite on 2010-06-29
Hi,
I'm looking at building a server which can act both as a Home Server, to hold media in one central location as well as back-up personal files to over the LAN, I'd also like it to run Squid or some such Proxy server software to protect my young family from the darker side of the web!
Any ideas if it's possible and if so how I could do it.
I already have a server box with everything it needs to go, and it's running a pretty good spec for a home server.
Would appreciate any ideas/tips on how best to do this.
Thanks in advance.

Alex

---

### Post by three_jeeps on 2010-06-29
Not being sure exactly how you define the terms 'media server' and 'backup' here are some suggestions:

Mythtv is a Linux based equivalent of M$ Media Center...
If you envision more of a real server for both audio and video, MediaTomb is worth looking into.

If your backup philosophy is performing daily, weekly, monthly backups then BackupPC is worth looking into. It can use a number of protocols to configure the client and server (i.e. rsynch, Samba). If your philosophy of back up is synching the client with the server, you can simply run BackupPC using rsynch. Using Backup PC as a samba server is very handy.  BackupPC also supports writing the backups to CD or DVDs or tape.
I personally found the documentation confusing/lacking some detail, and as a result, did away with it.  I also have a situation where I wanted to backup linux, windoz, and x10 based machines which is why I chose backupc but .  
Google searches for media server and backup should give you lots of information.
Good luck
John

---

### Post by BobVila on 2010-06-29
It's definitely doable. I've got a home server running fine on Ubuntu, samba, nfs, some internal web sites (Tracks, wtorrent, sabnzbdplus), and using Bacula for my backups. Bacula's not the most user-friendly, but it's in use at work, so I needed to learn it. As for the web filter, I'd check out DansGuardian. Not a personal recommendation, as I don't use any at home, but I see enough mention of it on these forums to at least take it into account along with Squid before you make your decisions.

---

### Post by stlsaint on 2010-06-29
There are many content filters. A few can be found in repos by default. I would suggest dansguardian. It has very basic gui and can be configured with white list/black list and many other options.

---

### Post by drdos2006 on 2010-06-29
I found this howto very useful.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

