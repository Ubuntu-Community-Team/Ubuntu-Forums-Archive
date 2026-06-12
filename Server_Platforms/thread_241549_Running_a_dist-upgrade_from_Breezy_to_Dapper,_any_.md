---
title: "Running a dist-upgrade from Breezy to Dapper, any tips?"
date: 2006-08-22
forum: Server Platforms
---

### Post by OneSeventeen on 2006-08-22
This Saturday morning I will be running a dist-upgrade on my departments live webserver that has a few tools on it that are required to be used each time an employee in the company changes salary/position/etc (including new hires and when people leave the company)

As our states largest employer, this is a rather big deal to have up and running (which is why I'm running it on linux :D)

Anyway, as I said, this coming Saturday (26 August, 2006) a co-worker and I will be upgrading the server.

I have heard a dist-upgrade isn't too hard on servers, since they don't have too many special graphics needs.  (My previous attempt at a dist-upgrade resulted in formatting and starting over)

I am running an Ubuntu desktop, and can SSH into the server easily, and have mounted a couple of folders on my desktop so I can transfer files back and forth very easily.

With that in mind, what can I do to make this go as smoothly as possible?

I'm thinking of making a tar.bz2 file of the entire contents of the server, since I should be able to fit them on the hard drive of this machine.  I am not too familiar with tar.bz2, not to mention the dramatic differences between the tar command from hoary to dapper.  (when excluding files, the syntax is slightly different, and I can't remember what that difference is)

Any tips and suggestions, as well as how to actually do a dist-upgrade using the server install (is it any different than the instructions on the  [DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) wiki entry?)

Any help is appreciated, thanks!

---

### Post by OneSeventeen on 2006-08-23
Another question is, could I do a dist-upgrade remotely?

Or do I need to be on the server to make sure it starts properly?

---

### Post by und3rtug4 on 2006-08-23
You can upgrade the distro smoothly by ssh!

In my experience, if you use mysql server, you better back up it ALL

The difference betwen mysql 4x to 5 is kinda huge...
If your database is on 4X you better stick on 4X, or it's gonna be kinda rough...

The upgrade worked just fine for me, just in one of my servers, i had troubles with it... and it was mysql...

Has I noticed, all major configurations on the servers still ok, and the changes that you will need to do "by hand" are minimal...

Always remenber, there are many types of configs and services running! In my "scenario" it went smooth as it should be!

Regards!

---

### Post by OneSeventeen on 2006-08-23
Thanks for the tips.

The only MySQL databases are accessed via PHP and don't take advantage of any advanced features.

Is there a way to block it from being upgraded if it is going to be a big issue?

Also, was there any difference between the dist-upgrade instructions I linked to and what you needed to do to actually get it up and running?

I expect to do little things here and there, like re-running some of my update scripts, and possibly re-installing my SSL certificate, but I'm hoping not a whole lot other than that.

(Since I only use SSH, PHP5, MySQL, PostgreSQL, and Apache2, and I have backups of the standard configs for network interfaces, postgres and apache)

---

### Post by OneSeventeen on 2006-08-26
We just ran the upgrade via SSH, went to go to the server room while it was re-booting to re-assign IP addresses, and an alarm went off and we had to talk to the cops (who wouldn't let us into the server room since we didn't have a pass-code), and including our conversation with the cops and a little bit of troubleshooting, the dist-upgrade from breezy to dapper took about 43 minutes.

I now have a fully functional dapper server!!!

[size=5]w00t!![/size]

---

