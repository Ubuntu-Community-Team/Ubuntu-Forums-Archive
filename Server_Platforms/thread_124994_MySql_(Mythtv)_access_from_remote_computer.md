---
title: "MySql (Mythtv) access from remote computer"
date: 2006-02-02
forum: Server Platforms
---

### Post by andrewsawyer on 2006-02-02
Hiya,

I hope someone can help me with this.  I have mythtv setup on my living room computer, with both front and back-ends running.

I have installed mythtv-frontend on another computer, however I am unable to access the database.  The message I'm getting is as follows:

```
andrew@192.168.0.106:/usr/share/menu$ mysql -umythtv -pmythtv -h192.168.0.101 mythconverg
ERROR 2003: Can't connect to MySQL server on '192.168.0.101' (111)

```

I've checked in the my.cnf file, and rather than having an entry about --skip-networking, it has the following lines:

```
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1

```

Obviously this allows the localhost to connect to the database but no-one else.  How do I change this?  Either open it up fully (port 3306 is closed on the firewall anyway), or open it up for local host + 192.168.0.106 + 192.168.0.102?

If anyone could help clear this up for me it would be much appreciated.

Many thanks,

Andy

---

### Post by andrewsawyer on 2006-02-21
Ping

---

### Post by andrewsawyer on 2006-02-26
Bump?

---

### Post by majikstreet on 2006-02-26
comment it out..

put a # in front of it, in other words.

hth,
majik

---

### Post by andrewsawyer on 2006-02-26
[QUOTE=majikstreet]comment it out..

put a # in front of it, in other words.

hth,
majik[/QUOTE]

Thank you!

I did that, then restarted mysql, however now I am getting the following error:

```
$ mythtv
2006-02-27 13:51:04.273 New DB connection, total: 1
2006-02-27 13:51:04.282 Unable to connect to database!
2006-02-27 13:51:04.282 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

Total desktop width=2720, height=1024, numscreens=1
2006-02-27 13:51:04.289 Unable to connect to database!
2006-02-27 13:51:04.289 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.289 Database not open while trying to load setting: XineramaScreen
2006-02-27 13:51:04.301 Unable to connect to database!
2006-02-27 13:51:04.302 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.303 Database not open while trying to load setting: RunFrontendInWindow
2006-02-27 13:51:04.303 Using screen 0, 2720x1024 at 0,0
2006-02-27 13:51:04.309 Unable to connect to database!
2006-02-27 13:51:04.309 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.309 Database not open while trying to load setting: Style
2006-02-27 13:51:04.315 Unable to connect to database!
2006-02-27 13:51:04.315 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.316 Database not open while trying to load setting: Theme
2006-02-27 13:51:04.316 Switching to square mode (blue)
2006-02-27 13:51:04.321 Unable to connect to database!
2006-02-27 13:51:04.321 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.321 Database not open while trying to load setting: GuiOffsetX
2006-02-27 13:51:04.331 Unable to connect to database!
2006-02-27 13:51:04.331 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.331 Database not open while trying to load setting: GuiOffsetY
2006-02-27 13:51:04.337 Unable to connect to database!
2006-02-27 13:51:04.337 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.338 Database not open while trying to load setting: GuiResolution
2006-02-27 13:51:04.345 Unable to connect to database!
2006-02-27 13:51:04.345 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.345 Database not open while trying to load setting: GuiWidth2006-02-27 13:51:04.356 Unable to connect to database!
2006-02-27 13:51:04.356 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.356 Database not open while trying to load setting: GuiHeight
2006-02-27 13:51:04.364 Unable to connect to database!
2006-02-27 13:51:04.364 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.364 Database not open while trying to load setting: MenuTheme
2006-02-27 13:51:04.372 Unable to connect to database!
2006-02-27 13:51:04.372 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.372 Database not open while trying to load setting: QtFontBig
2006-02-27 13:51:04.381 Unable to connect to database!
2006-02-27 13:51:04.381 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.381 Database not open while trying to load setting: QtFontMedium
2006-02-27 13:51:04.388 Unable to connect to database!
2006-02-27 13:51:04.388 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.388 Database not open while trying to load setting: QtFontSmall
2006-02-27 13:51:04.409 Unable to connect to database!
2006-02-27 13:51:04.409 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.409 Database not open while trying to load setting: HideMouseCursor
2006-02-27 13:51:04.417 Unable to connect to database!
2006-02-27 13:51:04.417 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:04.418 Database not open while trying to load setting: RunFrontendInWindow
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-02-27 13:51:05.305 Joystick disabled.
2006-02-27 13:51:05.309 Unable to connect to database!
2006-02-27 13:51:05.309 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.318 Unable to connect to database!
2006-02-27 13:51:05.318 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.326 Unable to connect to database!
2006-02-27 13:51:05.326 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.336 Unable to connect to database!
2006-02-27 13:51:05.336 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.345 Unable to connect to database!
2006-02-27 13:51:05.345 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.351 Unable to connect to database!
2006-02-27 13:51:05.351 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.358 Unable to connect to database!
2006-02-27 13:51:05.358 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.365 Unable to connect to database!
2006-02-27 13:51:05.365 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.371 Unable to connect to database!
2006-02-27 13:51:05.371 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.387 Unable to connect to database!
2006-02-27 13:51:05.387 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.397 Unable to connect to database!
2006-02-27 13:51:05.397 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.409 Unable to connect to database!
2006-02-27 13:51:05.409 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.418 Unable to connect to database!
2006-02-27 13:51:05.418 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.428 Unable to connect to database!
2006-02-27 13:51:05.428 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.437 Unable to connect to database!
2006-02-27 13:51:05.437 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.444 Unable to connect to database!
2006-02-27 13:51:05.444 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.451 Unable to connect to database!
2006-02-27 13:51:05.451 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.457 Unable to connect to database!
2006-02-27 13:51:05.457 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.466 Unable to connect to database!
2006-02-27 13:51:05.466 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.471 Unable to connect to database!
2006-02-27 13:51:05.472 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.483 Unable to connect to database!
2006-02-27 13:51:05.483 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.489 Unable to connect to database!
2006-02-27 13:51:05.489 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.495 Unable to connect to database!
2006-02-27 13:51:05.495 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.501 Unable to connect to database!
2006-02-27 13:51:05.501 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:05.501 Database not open while trying to load setting: Language2006-02-27 13:51:06.921 Unable to connect to database!
2006-02-27 13:51:06.921 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:06.921 Database not open while trying to save setting: Language2006-02-27 13:51:06.929 Unable to connect to database!
2006-02-27 13:51:06.929 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:06.929 Database not open while trying to load setting: Language2006-02-27 13:51:06.937 Unable to connect to database!
2006-02-27 13:51:06.937 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:06.937 Database not open while trying to save setting: Language2006-02-27 13:51:06.943 Unable to connect to database!
2006-02-27 13:51:06.943 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:10.783 Unable to connect to database!
2006-02-27 13:51:10.783 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@192.168.0.102' (Using password: YES)

2006-02-27 13:51:10.783 Failed to init MythContext, exiting.
$
```

If I try 
```
ssh mythtv@192.168.0.101
``` 192.168.0.101 being the computer that the Mythtv Server is based on, I can log in fine.  The username and password for the sql database is the same as the username and pasword for the user id on the server machine also.  I'm guessing this has something to do with access rights that may not now be specific to MySql but rather Ubuntu generally.

If anyone could point me in the correct direction, it'd be much appreciated.  The day when I can watch tv from my laptop without having to get out of bed is one that I'm looking forward to with great anticipation :-)

---

### Post by majikstreet on 2006-02-27
***********please see bottom of next post***********
Yeah, I think it has to do with access rights...

try this if you have set a password for root:

sudo mysql --user=root --password
then type in the password you set up as root

***********note: if you didn't set up a root password, you can take away the --password part there, but you really should set on up.. read how on say ubuntuguide***********

then it should say "mysql>" or similar
then something like
grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
then
flush privileges;

then just
exit

this is what the mythtv guide said to do... you used their sql file right?


***********please see bottom of next post***********

---

### Post by majikstreet on 2006-02-27
**_****don't try this post yet, look at "LOOKIE" then possibly try the above post****_**

also, I know this is a double post, but I don't think it should go in the above post..

what you could do to make it be more secure, would be to do this rahter than grant all on mythconverg.* to mythtv@"%" identified by "mythtv";

```

grant all on mythconverg.* to mythtv@"192.168.1.%" identified by "mythtv";

```
changing 192.168.1 to the part of your network ip - I dunno how to explain it.. lemme give you an example:
my network ip right now is 192.168.2.6, so I would put 192.168.2.% there.

hth,
majik

**LOOKIE!**
ok, now that I've got your attention..
I assumed something that could possibly mess this up, I thought you had compiled from source. But, I'm starting to believe that your probably just apt-get'd it, right? Now, I'm not really sure what the package does, like for instance what tables it sets up, so I'll have to install it myself to see. I'll get back to you once I install it. *beep* Well, that's not happening.. I'll have to figure something else out then. 
Are you sure that the mythtv user is there? I hope it is. But I think that if you try what I said in the above post, you may be able to get it

---

### Post by andrewsawyer on 2006-02-28
Hey,

Thank you so much!  This is now working!  I stuck another tuner into it today too, so it's working really well.  Just need to get lirc working now!

---

### Post by majikstreet on 2006-02-28
*searches brain for what lirc is* * remembers * that's that program for remote control with IR right? Sorry, can't help you there... (I don't even have mythtv!)

out of curiousity, what tuner card do you have? in case I ever decide to do this project :D

---

### Post by andrewsawyer on 2006-02-28
I've got a DViCO FusionHDTV Plus and a DViCO FusionHDTV Lite card.  Stuck the lite card in yesterday.  They are both fully supported under the current kernel (Breezy & Dapper) and you just have to modprobe the drivers to get them recognised.  5 minute job to get the tunercards setup, 5 day job to get Mythtv setup (ok, bit of an exageration).

If anyone else is using these cards and needs some help on setup, please let me know.  And likewise if anyone has got the remote on either of these to work (or the iMON MultiMedian), then please post how you did it with links to current downloads/patches.

---

### Post by majikstreet on 2006-03-03
[QUOTE=andrewsawyer]I've got a DViCO FusionHDTV Plus and a DViCO FusionHDTV Lite card.  Stuck the lite card in yesterday.  They are both fully supported under the current kernel (Breezy & Dapper) and you just have to modprobe the drivers to get them recognised.  5 minute job to get the tunercards setup, 5 day job to get Mythtv setup (ok, bit of an exageration).

If anyone else is using these cards and needs some help on setup, please let me know.  And likewise if anyone has got the remote on either of these to work (or the iMON MultiMedian), then please post how you did it with links to current downloads/patches.[/QUOTE]

Oh yeah - I happened to be browsing the net (a little del.icio.us :D ) and found this site: [http://www.abarbaccia.com](http://www.abarbaccia.com)  it is a howto for ubuntu mythtv - check the lirc section, maybe it'll help you...

majikstreet from school

once I get home I'll probably PM you this just in case you aren't subscribed to this thread.

---

### Post by andrewsawyer on 2006-03-03
Hiya,

Thank you for the link.  I actually used a mixture of that one and [this one]("http://www.users.on.net/~jani/dvico-mythtv.html") which uses my specific DVB card.  I'll have another double check and see if it can help me out.  Problem is, it relates to lirc versions that are no longer available for download and so the patches that are issued no longer work.

---

### Post by majikstreet on 2006-03-03
Ah. Ok.. just saw that and didn't know if you had seen it before :)

---

### Post by Fisslefink on 2006-10-01
Sorry to resurrect an old thread, but I just ran into a similar problem, and these fixes did not quite get me there.

While trying to set up [Mythtv Filters]("http://dsmyth.sourceforge.net/"), I kept getting the same "Access denied for user 'mythtv'@'192.168.1.3' (using password: YES)" message that everyone else seems to have gotten.

Prior to that, I got no connection whatsoever.  The solution to that was commenting out the "bind address" line in /etc/mysql/my.cnf, as was recommended above.

Then I got the "Access denied" message no matter what I tried, despite allowing access from all IP's as indicated [here]("http://www.mythtv.org/docs/mythtv-HOWTO-6.html#modify_perm_mysql").

Finally, I found a solution... After logging into the mysql server as 'root', type:
```
SET PASSWORD FOR 'mythtv'@'192.168.1.%' = PASSWORD('*<your password here>*');
flush privileges;
```

Be sure to use the same password that your mythtv-frontend is configured to use (type **locate mysql.txt** to find your password)

For some reason, that did it for me.  Hope that helps someone.

---

### Post by BrianH on 2006-11-03
> **Fisslefink said:**
> Sorry to resurrect an old thread, but I just ran into a similar problem, and these fixes did not quite get me there.

While trying to set up [Mythtv Filters]("http://dsmyth.sourceforge.net/"), I kept getting the same "Access denied for user 'mythtv'@'192.168.1.3' (using password: YES)" message that everyone else seems to have gotten.

Prior to that, I got no connection whatsoever.  The solution to that was commenting out the "bind address" line in /etc/mysql/my.cnf, as was recommended above.

Then I got the "Access denied" message no matter what I tried, despite allowing access from all IP's as indicated [here]("http://www.mythtv.org/docs/mythtv-HOWTO-6.html#modify_perm_mysql").

Finally, I found a solution... After logging into the mysql server as 'root', type:
```
SET PASSWORD FOR 'mythtv'@'192.168.1.%' = PASSWORD('*<your password here>*');
flush privileges;
```

Be sure to use the same password that your mythtv-frontend is configured to use (type **locate mysql.txt** to find your password)

For some reason, that did it for me.  Hope that helps someone.
Thanks Fisslefink!

I am so glad you posted this information.  The SET PASSWORD line above is what solved my problem and I've been looking all day.

---

### Post by superm1 on 2006-11-03
The edgy packages will by default generate a random password during the installation of mythtv-database.  

This password is saved in /etc/mythtv/mysql.txt and only readable by users in the mythtv group or the mythtv user (or root).  You shouldn't have to be changing the password on all frontends, but instead just setting the frontends to use this password.

---

### Post by Abhi Kalyan on 2006-11-04
> **superm1 said:**
> The edgy packages will by default generate a random password during the installation of mythtv-database.  

This password is saved in /etc/mythtv/mysql.txt and only readable by users in the mythtv group or the mythtv user (or root).  You shouldn't have to be changing the password on all frontends, but instead just setting the frontends to use this password.
Watching this thread with great interest

---

### Post by macjones on 2007-04-28
This worked for me getting the frontend to work (all with latest (2007) knoppmyth, not ubuntu)

Starting the mythbackend server it reported that it could not connect to MySQL. Using the mysql client I knew that the MySQL server was running. Then I tried the -h option with the box' IP address and sure enough it failed with this message: ERROR 2003 (HY000): Can't connect to MySQL server on. Searching around with Google I found some entries but none of them helped my any further. Short of getting in panic mode I discovered the mysql working directory /var/lib/mysql and checked out the log file. E voila, the log showed that it could not use (?create?) its temp directory. So I fix the issues once and for all with:


   1. Create a tmp directory in /var/lib/mysql

   2. Changed the ownership of that directory to mysql:mysql

   3. Changed the access rights to 700

   4. Restarted MySQL: /etc/init.d/mysql restart


This fixed my problem and I could finally start the backend as well as the frontend in its original configuration.

---

