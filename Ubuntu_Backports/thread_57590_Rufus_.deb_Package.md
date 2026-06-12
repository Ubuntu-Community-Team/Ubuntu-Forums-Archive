---
title: "Rufus .deb Package"
date: 2005-08-17
forum: Ubuntu Backports
---

### Post by strikeforce on 2005-08-17
Can someone check the .deb package that I have created just in case I have f&&cked up :P



If I have stuffed up please tell me so I can fix it.

Breezy version of 0.6.9 is up so far in use and working :).
Hoary version of 0.6.5 is up there obviously I can't test it but it should be working.

[http://strikeforce.dyndns.org/files/](http://strikeforce.dyndns.org/files/)

I'm only gonna put up the breezy version mainly because I've upgraded my main comp to breezy  \\:D/

stoeptegal has chosen to mirror the files which is great there might be a delay when a new version comes out but stoeptegal as graciously helped out give him some thanks :)

[http://www.ubuntudebs.luxz.net/](http://www.ubuntudebs.luxz.net/)

---

### Post by strikeforce on 2005-08-17
Has there been any issues?  I haven't got feedback at all yet.  I'm wondering whether I lucked it or well replace the l with an f?

---

### Post by rwabel on 2005-08-19
[QUOTE=strikeforce]Has there been any issues?  I haven't got feedback at all yet.  I'm wondering whether I lucked it or well replace the l with an f?[/QUOTE]
 I've downloaded it, but tis' missing some files like /usr/bin/rufus. Here is what was installed:
/.
/usr
/usr/bin
/usr/sbin
/usr/share
/usr/share/doc
/usr/share/doc/rufus
/usr/share/doc/rufus/changelog.gz
/usr/share/doc/rufus/CHANGELOG.TXT.gz
/usr/share/doc/rufus/credits.txt
/usr/share/doc/rufus/GeoIP.LICENSE.txt
/usr/share/doc/rufus/LeoXV.LICENSE.TXT
/usr/share/doc/rufus/LICENSES.TXT
/usr/share/doc/rufus/TODO.TXT
/usr/share/doc/rufus/README.Debian
/usr/share/doc/rufus/copyright
/usr/share/doc/rufus/changelog.Debian.gz
/usr/lib
/usr/lib/menu
/usr/lib/menu/rufus

and the deb file is only 10kb, what is surely to small for rufus
thanks

---

### Post by SKLP on 2005-08-21
this package seems totally broken. i downloaded the source files from your url, and ran dpkg-source -x <name of that .dsc file>.
then when i tried to build a deb from it i got Permission denied error. It apparently tried to write to /usr something when you build the package.. [-X

---

### Post by LeoXV on 2005-08-22
***Updated***
***Fixed seeding bug in StorageWrapper.py***
[http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.5.9.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.5.9.tar.gz)   size 369 KB
Extract the contents of the Rufus file to a temporary location.  
 
cd Rufus  
chmod 744 install  
./install 
 
To run Rufus type rufus  
 
******************************************** 
Depend 
dev-python/wxpython-2.5.3* 
dev-lang/python-2.4* (python-2.3 cjkcodecs & iconvcodec)
******************************************** 

rufus.py
import wxversion
wxversion.select(["2.5.3-unicode", "2.5.4-unicode", "2.5.5-unicode", "2.6-unicode"])

******************************************** 
Uninstall
rm -rf /usr/share/rufus/
rm  /usr/bin/rufus 

/home/user/.Rufus/
/home/user/Rufus
********************************************

---

### Post by strikeforce on 2005-08-23
Its been rebuilt 3 times I have some more editing before hopefully it'll be completed and put into breezy give me a little bit.  I'll post back with more details.  It however will only be compatible with breezy when it comes out.  I now have it working in hoary although not sanctioned by any stretch of the imagination.

[http://www.smlintl.com.au/packages](http://www.smlintl.com.au/packages)

All the info is there.  I need to edit out some files and edit some more bits and pieces over the next few days.  Once its completed it'll revert back to version 1 since thats how they like it.  However I will create a hoary one as I said.

**Edit I will have the finished product hopefully up and running my time tonight or early tommorow my time.  ;-) 

Sorry for the stuff around its been a bit of a  ](*,)

I truly am sorry about the stuff around.

***EDIT

Its all fixed there will be a hoary folder just look in there.  wxgtk2.6 has been fixed and there will be a breezy version there.

---

### Post by LeoXV on 2005-08-24
rufus-0.6.0 - [http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.6.0.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.6.0.tar.gz)
Depend
dev-python/wxpython
dev-lang/python
Optional
dev-python/geoip-python-0.2
dev-python/python-mhash-1.3

Fixed seeding bug in StorageWrapper.py (rufus-0.5.9)

Logs .Rufus/error.log and .Rufus/rufus.log
CPU Usage Fix

Menu (Gnome and KDE)
/usr/share/pixmaps/rufus.png
/usr/share/icons/rufus.png
/usr/share/applications/rufus.desktop

---

### Post by strikeforce on 2005-08-25
[QUOTE=LeoXV]rufus-0.6.0 - [http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.6.0.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.6.0.tar.gz)
Depend
dev-python/wxpython
dev-lang/python
Optional
dev-python/geoip-python-0.2
dev-python/python-mhash-1.3

Fixed seeding bug in StorageWrapper.py (rufus-0.5.9)

Logs .Rufus/error.log and .Rufus/rufus.log
CPU Usage Fix

Menu (Gnome and KDE)
/usr/share/pixmaps/rufus.png
/usr/share/icons/rufus.png
/usr/share/applications/rufus.desktop[/QUOTE]

The packages have been updated.  I don't think however python-mhash-1.3 is in hoary at the moment I have listed it as suggestions but not as anything else. However the package has been updated.  [http://www.smlintl.com.au/packages](http://www.smlintl.com.au/packages)

---

### Post by stoeptegel on 2005-08-30
I used this client in windows the last few months and it rocks.

I tried to install this deb in kubuntu, but my system wouldn't allow me because it's amd64.
Could you please please make a 64bit version?

---

### Post by jdong on 2005-08-30
I was recently building SuSE RPMs for it, and found that it still ain't 100% stable... Anyway, I'll place it in Extras when I get around to it... I'm pretty tied up at the moment.

---

### Post by strikeforce on 2005-08-30
[QUOTE=stoeptegel]I used this client in windows the last few months and it rocks.

I tried to install this deb in kubuntu, but my system wouldn't allow me because it's amd64.
Could you please please make a 64bit version?[/QUOTE]


Unfortunately I can't because I don't have a 64bit system.

---

### Post by stoeptegel on 2005-08-31
I regret i'am to much of a linux starter to mesh with around things like that. (hopefully in  the future) O:)

PS.Ktorrent is running quite stable here at the moment.

---

### Post by strikeforce on 2005-09-02
New Version available rufus-0.6.1 available in about 5 minutes you should see it up there for breezy and hoary shortly.  Have fun.  The changlogs have been updated to represent that.

---

### Post by bored2k on 2005-09-02
[QUOTE=strikeforce]New Version available rufus-0.6.1 available in about 5 minutes you should see it up there for breezy and hoary shortly.  Have fun.  The changlogs have been updated to represent that.[/QUOTE]
 Will try it out for Breezy as soon as its released.

---

### Post by glandula on 2005-09-02
0.6.1 like its predecessors crash and disappear after X minutes on my hoary

---

### Post by strikeforce on 2005-09-02
[QUOTE=glandula]0.6.1 like its predecessors crash and disappear after X minutes on my hoary[/QUOTE]

Does it generate a log.  If it does email it to doc his email address is on the sourceforge forums.

---

### Post by LeoXV on 2005-09-02
[QUOTE=glandula]0.6.1 like its predecessors crash and disappear after X minutes on my hoary[/QUOTE]

Can you run demo.py? - [http://prdownloads.sourceforge.net/wxpython/wxPython-demo-2.6.1.0.tar.gz](http://prdownloads.sourceforge.net/wxpython/wxPython-demo-2.6.1.0.tar.gz)


~/.Rufus/error.log
~/.Rufus/rufus.log (modify or remove confidential information)
You can send logs to me at [email]jukka.lehtomaki@gmail.com[/email]

---

### Post by bored2k on 2005-09-02
I downloaded for about an hour and shut the box down. When I reopened it, it checked for the file percentage and whoa, restarted the download. Back to bittornado and azureus.

---

### Post by strikeforce on 2005-09-03
As in it erased the download and restarted it?

---

### Post by bored2k on 2005-09-03
[QUOTE=strikeforce]As in it erased the download and restarted it?[/QUOTE]
 Apparently. It just started checking the file as usual, then when it finished, it started from scratch.

---

### Post by strikeforce on 2005-09-03
Did any log get generated?  I'm really surprised by that.  I had that ages ago in the earlier versions but I've never had it since.

---

### Post by stoeptegel on 2005-09-06
I just went back from 64bit to 32bit kubuntu and installed rufus from .deb. So far it's running just fine. :-)

Thanks for making my switch more comfortable, rufus rocks! :D

---

### Post by strikeforce on 2005-09-09
I'm glad you appreciate it.  I do the simple work.  Leo and Doc do the real work on the actual coding so I'm sure they will appreciate the thanks.

---

### Post by strikeforce on 2005-09-09
In the next 15-20 mins a new version will be uploaded. Rufus 0.6.4 has a lot of bug fixes in it.  I've updated the linux version of it to represent that.  So if its not there it won't be far away.

Again thanks to Leo and Doc.

---

### Post by stoeptegel on 2005-09-12
Thanks again for a new kickass release strikeforce, Leo and Doc. :D

---

### Post by Gnuklear on 2005-09-15
I haven't had much chance to try it out, but Rufus is the best looking and appears to be the most powerful Python based BitTorrent client I've come across... and I've tried just about all of them. Thanks for putting together such a great application.

However... I'm having a wee bit of trouble. I was recommended to try this client after connections problems with BitTornado and my reluctance to install a proprietary Java system so I could use Azureus (which had been my client of choice before my switch to Ubuntu). I installed 0.6.0 first, not realizing there was a newer version and it worked for about the 5 minutes I used it, no errors installing, all was right with the world. However, when I noticed there was a newer version and installed 0.6.4 (also with no errors) when I try to run Rufus... nothing happens. No error message, nothing from what I can see. (Being rather new to Ubuntu and linux in general, I'm not sure where the log files would be if there were any). So, I uninstalled rufus (rm - rf /usr/share/rufus ; rm /usr/bin/rufus) and no problems were reported. I then tried to reinstall 0.6.0 and was greeted with an error message saying:

```
dpkg: dependency problems prevent configuration of rufus:
 rufus depends on python-wxgtk2.6; however:
  Package python-wxgtk2.6 is not installed.
dpkg: error processing rufus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rufus
```

Now, if I try to run rufus it starts just fine, and from what I can tell continues to work just fine. But when I open Synaptic, it reports one broken package (that being rufus).

I'm not quite sure what to make of all this. Any help would be greatly appreciated.

---

### Post by stoeptegel on 2005-09-16
If i was in your position i would try remove and reinstalling rufus the usual way:
$ sudo apt-get remove rufus
$ sudo dpkg -i package.deb

Maybe it helps.
Note that i am also quite new to linux.

---

### Post by strikeforce on 2005-09-19
[QUOTE=Gnuklear]
```
dpkg: dependency problems prevent configuration of rufus:
 rufus depends on python-wxgtk2.6; however:
  Package python-wxgtk2.6 is not installed.
dpkg: error processing rufus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rufus
```

Now, if I try to run rufus it starts just fine, and from what I can tell continues to work just fine. But when I open Synaptic, it reports one broken package (that being rufus).

I'm not quite sure what to make of all this. Any help would be greatly appreciated.[/QUOTE]

Are you using the hoary version?  That should only show up in the breezy version unless I've stuffed up but I don't think I have since I've updated on my hoary install?

I'm just re-installing hoary since I severly screwed my system up so give me a day or so to re-look at it because it might be my side that I stuffed up on.  I'll update this post either today or tommorow.

*Edit

I've just re-installed it apart from having to install wxpython it was fine.  I'm assuming you grabbed the correct package.  Unless you have breezy installed I would only install the hoary version since the breezy package uses the updated python packages.

---

### Post by rwabel on 2005-09-22
[http://www.smlintl.com.au/packages](http://www.smlintl.com.au/packages)
Not Found
The requested URL /packages was not found on this server.

---

### Post by strikeforce on 2005-09-22
[QUOTE=rwabel][http://www.smlintl.com.au/packages](http://www.smlintl.com.au/packages)
Not Found
The requested URL /packages was not found on this server.[/QUOTE]

Yup as the front page says I'm currently shifting the work back home.  I had no power at my house for 4 months now I've got power at home and I've moved or in the process of moving back.  All the files will be shifted to my home server which has better bandwidth as well.

It'll be finished and updated this weekend. Sorry for the delay :(

---

### Post by rwabel on 2005-09-23
[QUOTE=strikeforce]Yup as the front page says I'm currently shifting the work back home.  I had no power at my house for 4 months now I've got power at home and I've moved or in the process of moving back.  All the files will be shifted to my home server which has better bandwidth as well.

It'll be finished and updated this weekend. Sorry for the delay :([/QUOTE]
 alright, I've overseen that edited part :-)
sorry
thanks for the packages btw

---

### Post by strikeforce on 2005-09-23
I've just updated to 0.6.5 which is completed on my desktop its only created for breezy at the moment I'm going to create the hoary version either later tonight or tommorow and I'll set it up by tommorow some time.

It's going to be a complete revamp following on a lot closer to the debian python policy.

---

### Post by rwabel on 2005-09-23
[QUOTE=strikeforce]I've just updated to 0.6.5 which is completed on my desktop its only created for breezy at the moment I'm going to create the hoary version either later tonight or tommorow and I'll set it up by tommorow some time.

It's going to be a complete revamp following on a lot closer to the debian python policy.[/QUOTE]
 looking forward to a new version. I'm on breezy ;-)
It's a real alternative to azeureus which is too memory hungry and bloated

---

### Post by strikeforce on 2005-09-23
[QUOTE=rwabel]looking forward to a new version. I'm on breezy ;-)
It's a real alternative to azeureus which is too memory hungry and bloated[/QUOTE]


Well its up and going look at the first post. Theres possibly one bug which is the icon which I need to fix.  I'll fix it and upload over the next few days.  However to fix it just edit the rufus.desktop which is in /usr/share/applications.

Sorry for the mistake.

---

### Post by rwabel on 2005-09-23
[QUOTE=strikeforce]Well its up and going look at the first post. Theres possibly one bug which is the icon which I need to fix.  I'll fix it and upload over the next few days.  However to fix it just edit the rufus.desktop which is in /usr/share/applications.

Sorry for the mistake.[/QUOTE]
 works great! But when rufus is already open and I want to open another torrent from firefox it tells mit it's already running. Is there a way to tell rufus just add that torrent?

---

### Post by strikeforce on 2005-09-23
I would think that might be a mime issue however I'm not so sure.  Post a bug on the rufus.sourceforge.net. forums and ask leoxv if thats capable of being done.

If it is then I might have to look into it but at the moment I can't even think where to start looking for it.

---

### Post by mlomker on 2005-09-24
> Unfortunately I can't because I don't have a 64bit system.

It doesn't matter.  The 'source' for this application is just a python script and doesn't have to be compiled.  I assume you'd just have to change the architecture line when creating the .deb.

All I had to do for the 0.6.5 version is unzip the program into a directory and create the /home/username/.Rufus directory.

Rufus has some nice features over Azureus, such as stopping at a certain share ratio and the graphs.  My only complaint at this point is that it doesn't minimize to a tray icon in KDE, whereas Azureus will.

---

### Post by rwabel on 2005-09-24
[QUOTE=mlomker]It doesn't matter.  The 'source' for this application is just a python script and doesn't have to be compiled.  I assume you'd just have to change the architecture line when creating the .deb.

All I had to do for the 0.6.5 version is unzip the program into a directory and create the /home/username/.Rufus directory.

Rufus has some nice features over Azureus, such as stopping at a certain share ratio and the graphs.  My only complaint at this point is that it doesn't minimize to a tray icon in KDE, whereas Azureus will.[/QUOTE]
 neither does it in gnome, it would be great to have a tray icon for it :-)

---

### Post by bored2k on 2005-09-24
Okay I will give Rufus another shot. Does Rufus .6.5 support DHT tracker?

---

### Post by bored2k on 2005-09-24
[QUOTE=bored2k]Okay I will give Rufus another shot. Does Rufus .6.5 support DHT tracker?[/QUOTE]
 [http://strikeforce.dyndns.org/files/](http://strikeforce.dyndns.org/files/)
Is it down? Where can I get it ?

---

### Post by rwabel on 2005-09-24
DHT tracker?
I think it's his own server and he's moving around that weekend. I think it'll be up soon

---

### Post by bored2k on 2005-09-24
[QUOTE=rwabel]DHT tracker?[/QUOTE]Trackerless torrents. Among other things, lets you download stuff even if the tracker is down. [http://azureus.aelitis.com/wiki/index.php/Distributed_tracker_and_database](http://azureus.aelitis.com/wiki/index.php/Distributed_tracker_and_database)

Azureus, BitComet, BitTornado and BitTorrent 4 have this marvelous feature.

---

### Post by bored2k on 2005-09-24
Can someone be kind enough to send me a download link for latest Rufus for Breezy ? Free upload can be done with rapidshare.de

---

### Post by rwabel on 2005-09-24
what a great feature!! I hope they'll implement that, but I've found no information about DHT on the rufus page

sorry, I've already deleted it, but I'm sure his server will be up soon :-)

---

### Post by strikeforce on 2005-09-24
Yes it was down my adsl connection dropped out :(

Anyways its back up now.  My apologies.  The only reason I don't put it on rapidshare is that I work on it if I see problems.

Everything is there for breezy.

In relation to other features.  Have a look at there requests forums  there is a lot there and they are slowly implementing bits and pieces.

For one thing they are going to add bittorrent 4 to it which means 1 port like azureus as well as the other benefits.  However they have mentioned they want to get all the bugs out and get it up to version 1 before they mess around with such massive changes which I agree with.

One thing I used to think was that azureus was faster however after trying leo's throttling I would say leo's is faster in regards to connections both up and down but thats just my opinion.

---

### Post by stoeptegel on 2005-09-24
I've put up a mirror:
[http://www.ubuntudebs.luxz.net/](http://www.ubuntudebs.luxz.net/)

---

### Post by bored2k on 2005-09-24
[QUOTE=stoeptegel]I've put up a mirror:
[http://www.ubuntudebs.luxz.net/](http://www.ubuntudebs.luxz.net/)[/QUOTE]
 Thank you.

---

### Post by strikeforce on 2005-09-24
[QUOTE=stoeptegel]I've put up a mirror:
[http://www.ubuntudebs.luxz.net/](http://www.ubuntudebs.luxz.net/)[/QUOTE]


Thanks for that the only version I have updated fully is the breezy one.  I can do all the layouts for the hoary one but it needs to be built thats it.

Its not a major effort to do it so if someone wants to do it I can explain how.  This is due to the fact that I've got breezy on all my machines now ;)

---

### Post by bored2k on 2005-09-24
[QUOTE=strikeforce]Yes it was down my adsl connection dropped out :(

Anyways its back up now.  My apologies.  The only reason I don't put it on rapidshare is that I work on it if I see problems.

Everything is there for breezy.

In relation to other features.  Have a look at there requests forums  there is a lot there and they are slowly implementing bits and pieces.

For one thing they are going to add bittorrent 4 to it which means 1 port like azureus as well as the other benefits.  However they have mentioned they want to get all the bugs out and get it up to version 1 before they mess around with such massive changes which I agree with.

One thing I used to think was that azureus was faster however after trying leo's throttling I would say leo's is faster in regards to connections both up and down but thats just my opinion.[/QUOTE]
 Okay very good. Implementing bittorrent 4 means DHT support too (at least the beta releases). IF my torrents work and the trackers I use like this client, I will probably switch, however when the trackers are down, I guess I would still have to go to Azureus temporarily :(.

---

### Post by strikeforce on 2005-09-24
Currently doc is working on fast resume for it which I personally think would be a big bonus.

If anyone is interested in helping him out the tread is here.

[https://sourceforge.net/forum/forum.php?thread_id=1354840&forum_id=440415](https://sourceforge.net/forum/forum.php?thread_id=1354840&forum_id=440415)

Also in relation to bittorrent 4 which will be worked on.

[https://sourceforge.net/forum/forum.php?thread_id=1274852&forum_id=440947](https://sourceforge.net/forum/forum.php?thread_id=1274852&forum_id=440947)

---

### Post by rwabel on 2005-09-24
[QUOTE=bored2k]Okay very good. Implementing bittorrent 4 means DHT support too (at least the beta releases). IF my torrents work and the trackers I use like this client, I will probably switch, however when the trackers are down, I guess I would still have to go to Azureus temporarily :(.[/QUOTE]
 I get error message like that in rufus:
[*****.torrent] - Auto-Pausing this torrent. The tracker timed out after 0 attempts
[*****.torrent] - Problem connecting to tracker [[http://fuf.zapto.org/announce]](http://fuf.zapto.org/announce]) - timeout exceeded
[*****.torrent] - Piece 3552 from 67.149.58.44 failed hash check, re-downloading it

would that be solved with DHT? I've quit a lot of torrents at 98% and 99% in such states

---

### Post by bored2k on 2005-09-24
[QUOTE=rwabel]I get error message like that in rufus:
[*****.torrent] - Auto-Pausing this torrent. The tracker timed out after 0 attempts
[*****.torrent] - Problem connecting to tracker [[http://fuf.zapto.org/announce]](http://fuf.zapto.org/announce]) - timeout exceeded
[*****.torrent] - Piece 3552 from 67.149.58.44 failed hash check, re-downloading it

would that be solved with DHT? I've quit a lot of torrents at 98% and 99% in such states[/QUOTE]
 DHT does not fix your torrents. A DHT enabled torrent allows for every single peer and seeder to act as a tracker. Why is this good? Should the tracker ever go down, DHT mode gets enabled and you don't even notice (whereas without it your torrent download would just stop). DHT was implemented the first time a few months ago when the MPAA started getting feisty and arresting the owners of illegal hosting trackers, so with trackerless torrents there is virtually no source for the cops to play "fetch" with. It just rocks because you are sure that as long as there are peers/seeders, your files will downoad no matter what.

This also makes it easier for you to upload files to your friends without the worry of a good tracker, because YOU are the tracker.

---

### Post by rwabel on 2005-09-24
[QUOTE=bored2k]DHT does not fix your torrents. A DHT enabled torrent allows for every single peer and seeder to act as a tracker. Why is this good? Should the tracker ever go down, DHT mode gets enabled and you don't even notice (whereas without it your torrent download would just stop). DHT was implemented the first time a few months ago when the MPAA started getting feisty and arrenting the owner of illegal hosting trackers, so with trackerless torrents there is virtually no source for the cops to play "fetch" with. It just rocks because you are sure that as long as there are peers/seeders, your files will downoad no matter what.

This also makes it easier for you to upload files to your friends without the worry of a good tracker, because YOU are the tracker.[/QUOTE]
 thanks for explanation, that would however solve the second error message :-)

---

### Post by strikeforce on 2005-09-24
If its because the tracker is down theoretically yes it would.  It would connect to someone else that has it without the tracker being there. However security could be an issue at the same time so yeah thats generally an issue.

What I do is leave it on right click and click poll tracker it forces the connection to them.

---

### Post by bored2k on 2005-09-24
[QUOTE=strikeforce]If its because the tracker is down theoretically yes it would.  It would connect to someone else that has it without the tracker being there. However security could be an issue at the same time so yeah thats generally an issue.

What I do is leave it on right click and click poll tracker it forces the connection to them.[/QUOTE]
 Either way, decentralized trackers is the future of BitTorrent. The more they get into closing down trackers, the more it will be needed.

> **You can use the Distributed Tracker alone to create totally decentralized torrents, or as a backup to a normal BitTorrent tracker.** The distributed tracker is an Azureus only feature at this time, although the beta Mainline client has a similar, but incompatible, distributed tracking mechanism. Good thing is, it is not always enabled. It only gets automatically enabled when the torrent's tracker is down (in case it has a main centralized one).

---

### Post by bored2k on 2005-09-24
How do I tell a multifile torrent to **NOT** download certain files? I only see the option to lower their priorities!

---

### Post by stoeptegel on 2005-09-24
By rightclick- Multi-File torrent manager- right click a file and check checkbox. On my rufus 0.6.4 these boxes aren't visual either, so this might be a bug.

---

### Post by bored2k on 2005-09-24
[QUOTE=stoeptegel]By rightclick- Multi-File torrent manager- right click a file and check checkbox. On my rufus 0.6.4 these boxes aren't visual either, so this might be a bug.[/QUOTE]
 That is the thing, i get an invisible checkbox!
So when I load the file, what i CHECK doesnt download  ? Would make sense, as  it would be UNchecking instead right ? But does it work ? I need this

---

### Post by stoeptegel on 2005-09-24
[QUOTE=bored2k]
So when I load the file, what i CHECK doesnt download  ? Would make sense, as  it would be UNchecking instead right ?[/QUOTE] 

Yes, correct.

[QUOTE=bored2k]
But does it work ? I need this[/QUOTE]

It works here.

---

### Post by bored2k on 2005-09-24
[QUOTE=stoeptegel]Yes, correct.



It works here.[/QUOTE]
 In case anyone else does not get this, here it is:
[[IMG]http://img17.imageshack.us/img17/2620/screenshot8co.th.png[/IMG]](http://img17.imageshack.us/my.php?image=screenshot8co.png)

Okay, this is quite weird. Few questions, how much does it take for Rufus to connect at nice speeds (average) ? Also, even when I uncheck files, filesize still says the max GB of the file, is this the Rufus way? Because azureus only displayes the filesize you select to download.

---

### Post by stoeptegel on 2005-09-24
[QUOTE=bored2k]how much does it take for Rufus to connect at nice speeds (average) ? 
[/QUOTE]

On a swarm with a good health and many torrents it is fast, i can't really tell the difference with another client. But i guess it's more swarm dependent then client.
I've noticed it also depends on the choker settings, when setting LEOXV with a too high min. upload you could get low speeds on a swarm much slow uploading peers, so i advise to use it with care and probably only if you feel the need to protect yourself in a slow swarm. Feel free to disagree...

[QUOTE=bored2k]
Also, even when I uncheck files, filesize still says the max GB of the file, is this the Rufus way? Because azureus only displayes the filesize you select to download.[/QUOTE]

This is rufus his way indeed.

---

### Post by bored2k on 2005-09-24
Whoa. It's been a while since I don't juggle with my computer without Azureus eating my resources. I will enjoy this.

---

### Post by bored2k on 2005-09-24
Whatever happened to the tray icon?

---

### Post by bored2k on 2005-09-24
[QUOTE=stoeptegel]
I've noticed it also depends on the choker settings, when setting LEOXV with a too high min. upload you could get low speeds on a swarm much slow uploading peers, so i advise to use it with care and probably only if you feel the need to protect yourself in a slow swarm. Feel free to disagree...
.[/QUOTE]
I left it on the default Rufus choker at it is going at about 1/2 my downloading capabilities. Hope it picks the speed up eventually.

---

### Post by stoeptegel on 2005-09-24
I have never seen a tray icon on one of the linux versions yet, maybe it is in the work though. I've never asked about it nor seen someone else asking for it. 

I agree is would be a nice feature to have.

---

### Post by bored2k on 2005-09-24
[QUOTE=stoeptegel]I have never seen a tray icon on one of the linux versions yet, maybe it is in the work though. I've never asked about it nor seen someone else asking for it. 

I agree is would be a nice feature to have.[/QUOTE]
 I am almost 100% sure a previous version loaded the tray icon for me .. and I have not seen it on any other OS.

---

### Post by stoeptegel on 2005-09-24
I've only used two deb versions made by strikeforce, and have never seen it with these.

---

### Post by drummer on 2005-09-24
How can I install Rufus on Hoary? The .deb doesn't work because it wants python-wxgtk2.6 (Hoary has 2.4). Also, I ran the install script from the source zip which seemed to do stuff, but when I run the command 'rufus', nothing happens, there's no README, no man pages, and I can't find its requirements on the website (?!?)

What can I do??

---

### Post by strikeforce on 2005-09-24
[QUOTE=drummer]How can I install Rufus on Hoary? The .deb doesn't work because it wants python-wxgtk2.6 (Hoary has 2.4). Also, I ran the install script from the source zip which seemed to do stuff, but when I run the command 'rufus', nothing happens, there's no README, no man pages, and I can't find its requirements on the website (?!?)

What can I do??[/QUOTE]


There is a man page I put one in.  man rufus.

The .deb doesn't work because it was made for breezy which you have just said you are'nt on.  python-wxgtk2.6 is what breezy is setup on you would need python-wxgtk2.5.3

For your info I have just uploaded a hoary version my last hoary version which is the current rufus version.  If that makes sense :)  the links are in the first post.

[QUOTE=bored2k]I am almost 100% sure a previous version loaded the tray icon for me .. and I have not seen it on any other OS.[/QUOTE]

The Windows version does do this however I have never seen it work on the linux version.


*bored2k

The choker options and how many connections you have are the key to getting the speed up.
Choker Options
I user leoxv strategy
run choker 10 secs
rotate optimistric -> 30 secs
min upload rate -> 0
peer max u/d ratio -> 3
dl threshold to start -> 1MB
Connections - Depends on how far your connection is.  If you aren't maxing your connections pay with it but not to high since the choker will rotate it.
Max Connections - Total:  -> 80
Max Connections - Local (Outbound): -> 60

If this works great otherwsie just remember there are no big variables going on.  This worked for my 3500/900 connetion

---

### Post by drummer on 2005-09-25
Thanks strikeforce, i got the .deb installed, but when i run rufus still nothing happens...
i do get this in ".Rufus/error.log":```
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/rufus/rufus.py", line 81, in ?
    EVT_INVOKE = wx.PyEventBinder(wxEVT_INVOKE, 0)
AttributeError: 'module' object has no attribute 'PyEventBinder'

```any ideas as to what this is?

---

### Post by strikeforce on 2005-09-25
What version of wxpython have you got?

You should have installed the following. unless you forced the install?  All of those additional packages are in ubuntu already.


[QUOTE=LeoXV]***Updated***
***Fixed seeding bug in StorageWrapper.py***
[http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.5.9.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.5.9.tar.gz)   size 369 KB
Extract the contents of the Rufus file to a temporary location.  
 
cd Rufus  
chmod 744 install  
./install 
 
To run Rufus type rufus  
 
******************************************** 
Depend 
dev-python/wxpython-2.5.3* 
dev-lang/python-2.4* (python-2.3 cjkcodecs & iconvcodec)
******************************************** 

rufus.py
import wxversion
wxversion.select(["2.5.3-unicode", "2.5.4-unicode", "2.5.5-unicode", "2.6-unicode"])

******************************************** 
Uninstall
rm -rf /usr/share/rufus/
rm  /usr/bin/rufus 

/home/user/.Rufus/
/home/user/Rufus
********************************************[/QUOTE]

---

### Post by Jonathan2007 on 2005-10-09
I am on Hoary and I wanted to install this to see how I like it. I updated my wxpython to 2.53 and got it installed but now when I try to run Rufus from my Kmenu listing or from run and typing rufus it acts like it is starting but it doesn't. It comes up with the little spinning thing on my taskbar but then that goes away after maybe 20 seconds. Anyone know what is wrong?

---

### Post by stoeptegel on 2005-10-09
Same problem here Jonathan2007, also caused by an update of i think the same package.

---

### Post by strikeforce on 2005-10-10
[QUOTE=stoeptegel]Same problem here Jonathan2007, also caused by an update of i think the same package.[/QUOTE]

Can you try running it using rufus -OO /usr/lib/python2.4/site-packages/rufus/rufus.py


Tell me if an error in generated.

---

### Post by Jonathan2007 on 2005-10-10
^ So should i try that command from run or from konsole. Doing it from a console produced nothing. Doing it from run made the little busy icon in the taskbar but only for a second or two. When I run just plain rufus from run it shows the busy icon for a lot longer. I don't know if that helps.

---

### Post by strikeforce on 2005-10-10
Yeah run that from the konsole.  If it doesn't load can you have a look in the ~/.rufus/ log and see if something gets put in there?

I need a bit of info.

What version python have you got?

---

### Post by Jonathan2007 on 2005-10-11
Well I have updated to Breezy so I may not be much help to you but maybe stoeptegel can try your suggestion and post back here.

I never got Rufus working under Hoary and since there was a specific Breezy version I removed Rufus (using Synaptic) once I had upgraded to Breezy. I then tried installing the Breezy deb. It gave me some error about a dependency (python 2.6 I believe). So when to install python 2.6 it gave me an error about wxpython-version (or something along those lines). Since I had wxpython 2.5.3 but I was trying to install python 2.6 it didn't like that. So I ended up uninstalling wxpython and then installing python 2.6 (wxpython-version got installed with that). Then I installed wxpython 2.5.3 and it worked fine and I got Rufus installed.

But now I still can't start Rufus. I will try the the command here on Breezy and look in the log file and post back later.

---

### Post by Jonathan2007 on 2005-10-11
I again tried running that command from a terminal and it just took me back to to jonathan@Jonathan:~$

My error.log reads as follows
```

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/rufus/rufus.py", line 81, in ?
    EVT_INVOKE = wx.PyEventBinder(wxEVT_INVOKE, 0)
AttributeError: 'module' object has no attribute 'PyEventBinder'
```
It seems to want python 2.4 for some reason.

Rufus.log has nothing in it.

---

### Post by strikeforce on 2005-10-12
[QUOTE=Jonathan2007]I again tried running that command from a terminal and it just took me back to to jonathan@Jonathan:~$

My error.log reads as follows
```

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/rufus/rufus.py", line 81, in ?
    EVT_INVOKE = wx.PyEventBinder(wxEVT_INVOKE, 0)
AttributeError: 'module' object has no attribute 'PyEventBinder'
```
It seems to want python 2.4 for some reason.

Rufus.log has nothing in it.[/QUOTE]

Yup in the breezy version you need to install wxgtk2.6.
Depends: python (< 2.5), python (>= 2.4), python-wxgtk2.6

This might help you as well.
do you have python2.4 or python2.4-minimal
[http://sourceforge.net/forum/forum.php?thread_id=1358852&forum_id=440416](http://sourceforge.net/forum/forum.php?thread_id=1358852&forum_id=440416)

If that is the error e.g. python-openssl or relating to python please tell me so I can fix it

---

### Post by Leif on 2005-10-12
ok, I'm clearly doing something wrong. I've installed rufus under breezy, but using the deb or installing from source, it starts, but I can never start any torrents (error message : could not start download). and it's not like it tries to download and can't connect. anybody experienced this ?

---

### Post by strikeforce on 2005-10-12
[QUOTE=Leif]ok, I'm clearly doing something wrong. I've installed rufus under breezy, but using the deb or installing from source, it starts, but I can never start any torrents (error message : could not start download). and it's not like it tries to download and can't connect. anybody experienced this ?[/QUOTE]
What does it say in the messages tab. Generally that will provide you a reason why you could not start your download.  Possibly ports and the like.

---

### Post by Leif on 2005-10-12
[QUOTE=strikeforce]What does it say in the messages tab. Generally that will provide you a reason why you could not start your download.  Possibly ports and the like.[/QUOTE]

hi, thanks for the concern. figured it out though. well, kinda. under preferences->folder options, I'd set locations for everything. despite the fact that they are all in my home directory, this seems to have caused the error. I've unchecked all but the "incoming downloads" one, and everything works.

cheers for the package. I've been getting annoyed with azureus for a while, it seems to crash my system, and corrupt the file it's downloading. hopefully rufus works better.

---

### Post by Jonathan2007 on 2005-10-12
[QUOTE=strikeforce]Yup in the breezy version you need to install wxgtk2.6.
Depends: python (< 2.5), python (>= 2.4), python-wxgtk2.6

This might help you as well.
do you have python2.4 or python2.4-minimal
[http://sourceforge.net/forum/forum.php?thread_id=1358852&forum_id=440416](http://sourceforge.net/forum/forum.php?thread_id=1358852&forum_id=440416)

If that is the error e.g. python-openssl or relating to python please tell me so I can fix it[/QUOTE]
So I need python 2.4 - python 2.5.3? I can't use 2.6? I am so confused as to why all these apps use different python versions and some apps need the latest python but then I can't install a lower version that other apps need. Sigh... any suggestions?

---

### Post by strikeforce on 2005-10-13
You said you are in breezy.  Well breezy does not have or did not have I should say the same naming conventions as they did on hoary.

So therefore I had to change it to python-wxgtk however my understanding which can be corrected is that it didn't have version 2.5.3 so I tested rufus under version 2.6 which worked.  However obviously it clashes with 2.5.3 from hoary.  So you need to uninstall rufus from the hoary version and uninstall 2.5.3 then reinstall 2.6 and then install rufus the breezy version.  This should get it to work.

The question I had was whether you have python-openssl installed I do but I'm not sure if its required.  I've tried with pbuilder and it seems it wasn't needed however I'm not 100% sure whether it is or isn't so hence I've asked whether it is needed.
Here is the naming of the packages.
```

python2.4-pyopenssl not sure about this one.

python-minimal

python-wxgtk2.6

Recommends: python-geoip, python-mhash

```
That should be it. If you still have problems with those actual packages I need to ask you to test some stuff so I can improve on the package.

---

### Post by LeoXV on 2005-10-13
Replace line:
import wx

import wxversion
wxversion.select(["2.5.3-unicode", "2.5.4-unicode", "2.5.5-unicode", "2.6-unicode"])
import wx

[http://wiki.wxpython.org/index.cgi/MultiVersionInstalls]("http://wiki.wxpython.org/index.cgi/MultiVersionInstalls")
If both 2.5.4 and 2.6.1 are installed then 2.6.1 will be chosen.

---

### Post by Jonathan2007 on 2005-10-13
In Synaptic searching by Python for all of the following:

I could not find:
python2.4-pyopenssl
python-mhash

I have installed:
python-minimal
python-wxgtk2.6
python-geoip

I also have Python 2.4 installed

Rufus still refuses to install for me on Kubuntu Breezy 5.10.

And I have already done this to no avail:
So you need to uninstall rufus from the hoary version and uninstall 2.5.3 then reinstall 2.6 and then install rufus the breezy version. This should get it to work.

---

### Post by strikeforce on 2005-10-13
[QUOTE=LeoXV]Replace line:
import wx

import wxversion
wxversion.select(["2.5.3-unicode", "2.5.4-unicode", "2.5.5-unicode", "2.6-unicode"])
import wx

[http://wiki.wxpython.org/index.cgi/MultiVersionInstalls]("http://wiki.wxpython.org/index.cgi/MultiVersionInstalls")
If both 2.5.4 and 2.6.1 are installed then 2.6.1 will be chosen.[/QUOTE]

The problem is as I see it is that 2.6 is shipped with breezy but not 2.5.3 I'm yet to see the package apart from it being a virtual package at this point in time.  My understanding is that I was told to refer it to 2.6 since 2.5.3 was 'not' going to be in breezy and obviously you guys use that.

And from my point of view 2.6 has not caused me any issues Leo I've had no issues installing it and or running it.

[QUOTE=Jonathan2007]In Synaptic searching by Python for all of the following:

I could not find:
python2.4-pyopenssl
python-mhash

I have installed:
python-minimal
python-wxgtk2.6
python-geoip

I also have Python 2.4 installed

Rufus still refuses to install for me on Kubuntu Breezy 5.10.[/QUOTE]

pyhton-mhash is still a virtual package in ubuntu which is the same as kubuntu.
```

marc@ubuntu:~$ sudo aptitude search python-pyopenssl
i   python-pyopenssl                                      - Python wrapper around the OpenSSL library (dummy package)

```

mhash is not required so don't worry to much.

---

### Post by Jonathan2007 on 2005-10-13
It found that and said I already have the latest verison so now I am really stumped. And thanks for your fast responses.

---

### Post by strikeforce on 2005-10-14
[QUOTE=Jonathan2007]It found that and said I already have the latest verison so now I am really stumped. And thanks for your fast responses.[/QUOTE]


Can you try and overwrite your rufus.py file with this one [http://www.smlintl.com.au/bt/torrent/rufus.py](http://www.smlintl.com.au/bt/torrent/rufus.py)

You can find the rufus.py file here 
/usr/lib/python2.4/site-packages/rufus/

If that works tell me.

---

### Post by Jonathan2007 on 2005-10-14
Nope. Still didn't load. Still got the busy icon in the taskbar that says loading app. :(

---

### Post by strikeforce on 2005-10-15
Have you tried loading it from the commandline to see what spits out with the file that I gave you?  Also do you have a home directory e.g. ~/Rufus

---

### Post by Jonathan2007 on 2005-10-15
jonathan@Jonathan:~$ rufus
jonathan@Jonathan:~$

It does nothing it just pauses and takes me back to $

Yes I have a Rufus folder in my home /home/jonathan/.Rufus
The error.log says this:
```
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/rufus/rufus.py", line 1865, in run
    app = MyApp(False)
  File "/usr/lib/python2.4/site-packages/rufus/rufus.py", line 1845, in __init__
    wx.App.__init__(self, flag)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/lib/python2.4/site-packages/rufus/rufus.py", line 1850, in OnInit
    frame = Reba(path, sys.argv[1:])
  File "/usr/lib/python2.4/site-packages/rufus/rufus.py", line 164, in __init__
    self.friends = friend.FriendList(self.btconfig.Get("path"))
  File "/usr/lib/python2.4/site-packages/rufus/friend.py", line 119, in __init__
    path = self.btconfig.Get("path")
AttributeError: 'str' object has no attribute 'Get'
```

My rufus.log says this:
```
Rufus requires wxwindows 2.5.2.8u
Installed wx version: 2.6.1.1pre
Web Browser
Software package rely on your $BROWSER variable being set.
export BROWSER='firefox'
File Browser
Software package rely on your $FILEBROWSER variable being set.
export FILEBROWSER='konqueror'
If you have filenames encoded in the encoding of your locale, then
you may want to set the G_BROKEN_FILENAMES=1 environment variable.
Loading Images /usr/lib/python2.4/site-packages/rufus
```
That seems to indicate I need wxpython 2.5.3 I believe but I thought you said I could have 2.6.1?

---

### Post by strikeforce on 2005-10-16
Your best chance is to jump on the rufus forums and post there and or email your error.log and basically all your other files to Doc and or Leo both are in the man pages.  

e.g. man rufus will give you the email addresses.  If there is a bug I would like to find it since I don't have wxpython2.5.3 and a lot of people don't either so I think its another issue or if it is an issue with the packaging then I'd like to know but I don't think it is.

---

### Post by Jonathan2007 on 2005-10-16
I took your advice and posted on the forums over there. [here]("https://sourceforge.net/forum/forum.php?thread_id=1368527&forum_id=440416") is the link.

---

### Post by riggits on 2005-10-17
hi guys, i realize that this is probably the most obvious thing in the world to some of you, but I've been trying to install rufus for ages with no success.  i'm running Ubuntu 5.10 breezy, tried downloading the .deb with Firefox and saved it to my home directory...
then i double-clicked on the .deb package, and got this error:

"Could not open "rufus_0.6.5-0ubuntu1_i386.deb"
Archive type not supported."

Is the archive corrupt?  i've also used synaptic to search for the rufus package, and it apparently doesn't exist in the main archives.
How can I find and install a working rufus?  or is it only for Kubuntu?

thanks to you kind souls for your support :)  any advice at all is appreciated.

---

### Post by Jonathan2007 on 2005-10-17
Go to a command line/terminal and cd to the place where you saved it. But I don't think you need to do that since you saved it to your home folder and that is the default starting location for a terminal. So now do a ```
sudo dpkg --install rufus_0.6.5-0ubuntu1_i386.deb
```  That should get it installed for you. But you may have some dependency issues you will need to resolving using Synaptic first (it should let you know).

---

### Post by riggits on 2005-10-17
[QUOTE=Jonathan2007]Go to a command line/terminal and cd to the place where you saved it. But I don't think you need to do that since you saved it to your home folder and that is the default starting location for a terminal. So now do a ```
sudo dpkg --install rufus_0.6.5-0ubuntu1_i386.deb
```  That should get it installed for you. But you may have some dependency issues you will need to resolving using Synaptic first (it should let you know).[/QUOTE]

thanks a million!  now i'm getting totally different errors, which is somewhat encouraging.  Seems that the ubuntu sources in my apt list are invalid, all giving 404 errors.  Maybe the packages were deleted.  
Is there an installer that has all the dependencies in one bundle?  I can't find the python packages anywhere, even with google :(    Somebody earlier in this thread mentioned that the 2.6 Python package ships with Breezy, but I can find no mention of it using the Synaptic search function, the apt-get -install python command, or anywhere else.

The Package Manager says I have broken packages now, and when I try to install it gives reams of errors:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

It all looks kinda fishy, like the american ubuntu mirror doesn't even exist?  or possibly it's restricted.
Argh.

EDIT:  looks like sourceforge doesn't even have .deb packages.  I've been burned by RPM stuff before, not looking forward to trying that out again.
Does anybody know of a version of dpkg or apt that automatically resolves dependencies?

---

### Post by Jonathan2007 on 2005-10-17
Hmm. Well Synaptic and the like (ie package managers) can resolve dependencies for you. But in order for that to work you need to have the package you want to install available in the repositories and since you are installing from a .deb file Synaptic can't automatically resolve the dependency issues. I don't know of anything that will resolve dependency issues when installing a .deb. But I am somewhat new to Linux too so maybe someone else could better help you. You might wanna post over in the regular Ubuntu desktop forum and see if anyone knows of a deb installer that can resolve dependencies automatically.

And I have python 2.4 which is the newest that I am aware of. Maybe you were thinking of wxpython 2.6.1. It was in my list for Synaptic so...

P.S. You might try a sudo apt-get update or do a refresh in Synaptic to try and get rid of those Ubuntu repository errors.

---

### Post by LeoXV on 2005-10-17
[QUOTE=Jonathan2007]I took your advice and posted on the forums over there. [here]("https://sourceforge.net/forum/forum.php?thread_id=1368527&forum_id=440416") is the link.[/QUOTE]

[INDENT]Loading Images /usr/lib/python2.4/site-packages/rufus[/INDENT]
The default installation folder for Rufus is /usr/share/rufus/

[INDENT]
 File "/usr/lib/python2.4/site-packages/rufus/friend.py", line 119, in __init__
    path = self.btconfig.Get("path")
AttributeError: 'str' object has no attribute 'Get'[/INDENT]
This is not the fault of the wxPython.

---

### Post by strikeforce on 2005-10-18
As per the debian python policy. [http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html](http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html)

It needs to be placed as a site-package.  I replaced the current place of /usr/share/rufus to python -OO  /usr/lib/python2.4/site-packages/rufus/rufus.py

It works fine on my system which means I have done something that somebody else hasn't.  I installed the same package on my system.

To add to that.
```

path = self.btconfig.Get("path")

        if win32_flag:
            self.friends_file = join(path, "friends.ini")
        else:
            self.friends_file = join(os.path.expanduser('~/.Rufus'), 'friends.ini')

```
THe path = self.btconfig.GET("path")
it would pull the correct path. Which puts the question as to why I get the correct path listed and it loads for me.  I've just re-packaged it using pbuilder and tested it after deleting my ~/Rufus and ~/.Rufus directories and I have no issues it loads up.

```

Rufus requires wxwindows 2.5.2.8u
Installed wx version: 2.6.1.1pre
Web Browser
Software package rely on your $BROWSER variable being set.
export BROWSER='firefox'
File Browser
Software package rely on your $FILEBROWSER variable being set.
export FILEBROWSER='konqueror'
If you have filenames encoded in the encoding of your locale, then
you may want to set the G_BROKEN_FILENAMES=1 environment variable.
Loading Images /usr/lib/python2.4/site-packages/rufus
Loading Friend List
ERROR: reading friends ini file
Loading RSS Feeds
ERROR: reading from RSS ini file
loading work state
/home/marc/.Rufus/torrents.ini
G3XMLRPCServer Started
On Close
saving work state
saving options
/home/marc/.Rufus/torrents.ini
stopping
Mainloop joining
G3XMLRPCServer Stopped
Killing sessions 0
Destroying all open/minimised torrent progress dialogs
Destroying window

```

Thats all I've received which begs the question is it not finding your images file?

---

### Post by Jonathan2007 on 2005-10-18
So did you upload a new version I can test or what? I am really anxious to get this working. I hate the resource hog Azureus and Ktorrent won't download anything well at all.

---

### Post by strikeforce on 2005-10-18
[QUOTE=Jonathan2007]So did you upload a new version I can test or what? I am really anxious to get this working. I hate the resource hog Azureus and Ktorrent won't download anything well at all.[/QUOTE]

I've uploaded an updated version.  I don't think it'll make a difference for you but you can try.

---

### Post by Jonathan2007 on 2005-10-18
Still no go...

P.S. Anyone know any other good BT clients? I have tried Azureus and I refuse to use it anymore. I have also tried Bittornado and I wasn't overly impressed.

---

### Post by riggits on 2005-10-19
[QUOTE=Jonathan2007]Still no go...

P.S. Anyone know any other good BT clients? I have tried Azureus and I refuse to use it anymore. I have also tried Bittornado and I wasn't overly impressed.[/QUOTE]

if I could get WINE working I'd recommend BitComet :)  
or utorrent, it's really tiny.  They have native Linux support on the horizon, but that's probably next year.

---

### Post by stoeptegel on 2005-10-20
[QUOTE=riggits]if I could get WINE working I'd recommend BitComet :)  
[/QUOTE]

I am a crew member on some trackers, and you made me cry with that :---)   No serious, bitcomet is all about fooling the user, tracker and swarm.

---

### Post by riggits on 2005-10-21
[QUOTE=stoeptegel]I am a crew member on some trackers, and you made me cry with that :---)   No serious, bitcomet is all about fooling the user, tracker and swarm.[/QUOTE]

well, the main thing that led me to rufus is the visual similarity to BitComet :)  It's basically got the same layout, minus the annoying vertical pane on the left (w/all those stupid links)
I do confess that the DHT and other features have strengthened my downloading considerably, compared w/BitLord/G3/ABC et al. I think I've used every bt client on the planet by now.

If/when i get rufus working I just hope it works with all those private trackers I'm on.  Argh.  (I really have no idea what trackers have to deal with behind the scenes)

---

### Post by stoeptegel on 2005-10-23
> **riggits]I think I've used every bt client on the planet by now.[/QUOTE]

Me too! I always install many(almost any) programs, just for testing...  said:**
> If/when i get rufus working I just hope it works with all those private trackers I'm on.  Argh.

G3 is quite banned on trackers, but rufus has it's own peerid and useragent and hasn't got the bad reputation as g3 has and deserved. I use rufus everywhere without problems, it's not a perfect client, but it is the best for me.

---

### Post by strikeforce on 2005-10-23
[QUOTE=stoeptegel]
G3 is quite banned on trackers, but rufus has it's own peerid and useragent and hasn't got the bad reputation as g3 has and deserved. I use rufus everywhere without problems, it's not a perfect client, but it is the best for me.[/QUOTE]

They took out the parts that caused g3 to be banned thats why.  It hasn't been banned from anywhere to the best of my knowledge because of that reason.  The developers are very proactive which is great to see.

One question I do have what makes your system different to other peoples who can't get it to work?  I would be interested in finding this out because my opinion is that its a package thats installed thats not on their system.

---

### Post by stoeptegel on 2005-10-23
AFIAK i did nothing special:  a clean breezy install, apt-get update & upgrade, extended some sources.list entries, installed python-wxgtk2.6, and dpgk -i your newest rufus package. It was one of the first apps i installed.

---

### Post by strikeforce on 2005-10-23
[QUOTE=stoeptegel]AFIAK i did nothing special:  a clean breezy install, apt-get update & upgrade, extended some sources.list entries, installed python-wxgtk2.6, and dpgk -i your newest rufus package. It was one of the first apps i installed.[/QUOTE]

Thats exactly what I did yet some people are having issues with it?  I'm still trying to figure out why they are having issues.  Anyways I'll keep on searching as to why there are issues.

---

### Post by bored2k on 2005-10-23
When I load a torrent file that has multiple files inside, in the screen that pops up asking me what to download (torrent manager), I **don't ** get a visible checkbox! Instead, I have to *guess* what is it that I am selecting, which can become very frustrating when dealing with torrents with a lot of files inside. Besides that, it's the close to perfect app.
[CENTER]
[I][IMG]http://img485.imageshack.us/img485/4039/ruf0bt.jpg[/IMG]

Is **there** still no way to fix this? It is incredibly annoying.[/I][/CENTER]

---

### Post by strikeforce on 2005-10-23
I'll have a look over the next couple of days with the latest test version I have if it still occurs I'll submit an upstream bug report. 

Thanks for pointing that out since I don't use it :)

---

### Post by bionnaki on 2005-10-24
just installed rufus...I loved g3 on windows, so I'll be checking this out. thanks!

---

### Post by stoeptegel on 2005-10-24
bored2k,
I did put a thread in support forum 2 weeks ago.
[http://sourceforge.net/forum/forum.php?thread_id=1364870&forum_id=440416](http://sourceforge.net/forum/forum.php?thread_id=1364870&forum_id=440416)

---

### Post by strikeforce on 2005-10-24
Yep in the latest beta test I'm trying it still has that bug.  I'm testing out version 0.6.8 atm so I'm working with the developers on beta testing at the moment.

Currently one of the developers has had his computer die so as soon as that is fixed he will start to work on it again.

Sorry about the bug but he'll fix it another thing you can do is see if an error.log gets generated under ~/.Rufus/error.log

---

### Post by stoeptegel on 2005-10-25
No need to be sorry about Strikeforce, Doc is a nice guy and always does his best to help us. Wow that's nasty about his laptop, i hope he's back soon.

---

### Post by bionnaki on 2005-10-28
I'm using rufus over ktorrent & azureus...
I used to love g3, but im on linux now.
hopefully these bugs will be worked out.
this could be the choice torrent client on ubuntu.

---

### Post by strikeforce on 2005-10-30
[QUOTE=bionnaki]I'm using rufus over ktorrent & azureus...
I used to love g3, but im on linux now.
hopefully these bugs will be worked out.
this could be the choice torrent client on ubuntu.[/QUOTE]

Rufus is getting worked on constantly  I think you will be pleasantly surprised.  They are however at times sporadic due to testing as well as the fact that Doc is flat out with work as well.

However the releases are very frequent and generally bug free.  However current issues are one of those things that can't be avoided :(

---

### Post by Wandering Wombat on 2005-11-12
I couldn't get Rufus installed for the life of me and read through all of this thread and had many similar problems to what was in the forum. I am no expert let me say that now, I can't remember everything I did eg. installing uninstalling etc. All I can say is that I had Rufus Installed and it came up as a broken package, so I kept messing about and trying things, I saw python wxtools and thought why not, I will install that and see what happens. I selected it and held my breath lol, it installed a few dependencies (not sure which ones or how many...sorry) and I eagerly awaited to see if Rufus was still broken. Guess what it wasn't, so I now have a working Rufus.....woohoo. I know this isnt much info but thats what I did and it now works for me. Sorry if this is wasting time just thought I would share my experiences. Cheers....Darin.

Oh and thanx for Rufus its excellent!!! :D
Edit: spelling

---

### Post by stoeptegel on 2005-11-13
The will to help each other out can't be wasting time Wandering Wombat, as it's one of the things why linux is evolving IMO.  Thanks for the tips. :)

---

### Post by strikeforce on 2005-11-22
New Rufus version has been released. The package has been uploaded to my server and I've got it running as is now.  No major issues mainly bug fixes.  For further information have a look at the changelog included with the package.

Enjoy :)

---

### Post by stoeptegel on 2005-11-23
Package works splendid, thanks again. :KS

---

### Post by bored2k on 2005-11-23
I still have the old No checkbox mark bug :(.

---

### Post by strikeforce on 2005-11-23
[QUOTE=bored2k]I still have the old No checkbox mark bug :(.[/QUOTE]

Yup so do I I'll re-post it in the forums

---

### Post by cowlip on 2005-11-26
Hi I like this client, how do I get it to appear in the system tray/notification area of gnome though?

---

### Post by Wandering Wombat on 2005-11-27
Thanx guys, just installed, works a treat well done ;)

---

### Post by strikeforce on 2005-11-27
[QUOTE=cowlip]Hi I like this client, how do I get it to appear in the system tray/notification area of gnome though?[/QUOTE]

Its a bug at the moment they are working on making it appear in your system tray when minimized.

---

### Post by cowlip on 2005-11-27
I see, thank you for responding

---

### Post by dexae on 2005-12-18
[quote=cowlip]Hi I like this client, how do I get it to appear in the system tray/notification area of gnome though?[/quote]

you can use [alltray]("http://alltray.sourceforge.net/")

---

### Post by strikeforce on 2005-12-20
Someone has created an amd64 package so I'll wait for that to get through to me and I'll update the front page with more info.

I'll host it on the same computer.  Only issues I'll have are stupid electricity problems if its down :(

---

### Post by hav0x on 2005-12-23
Rufus hurts my eyes .. i get some serious flickering of the GUI, plus those anoying interface bugs. I hope they improve on that.


And i mean fast .. could really use a bt client like this one ... dont really like azureus. It's not ready (imho) for prime time.

---

### Post by cowlip on 2006-01-28
It looks like .7.0 is out

---

### Post by stoeptegel on 2006-01-28
0.7.0 is out for 2months already, but it is a testing release.

@hav0x
The flickering can be much less when you disable the keep sorted function. (right klik in peerlist)

---

### Post by Jonathan2007 on 2006-01-29
Perhaps the flickering you see is actually Rufus refreshing the window. I believe the default refresh rate is 1 second. That is way too much for me so I have mine set to refresh every 5 seconds.

---

### Post by hav0x on 2006-01-29
It stilll flickers not only the peer/file lists the whole window just flickers... 5 seconds or not, together with the bad/defective buttons/separators it's really a sign of poor UI design.
Hope they/he improve on that.

---

### Post by indo on 2006-02-04
[QUOTE=Jonathan2007]Perhaps the flickering you see is actually Rufus refreshing the window. I believe the default refresh rate is 1 second. That is way too much for me so I have mine set to refresh every 5 seconds.[/QUOTE]
Where is that setting located?

I would be happy to provide an FTP account for you StrikeForce.  It's on a pretty fast server.

---

### Post by stoeptegel on 2006-02-04
[QUOTE=indo]Where is that setting located?
[/QUOTE]

Preferences-> general options(already there)-> Update GUI every x seconds.

---

### Post by indo on 2006-02-11
[QUOTE=stoeptegel]Preferences-> general options(already there)-> Update GUI every x seconds.[/QUOTE]
Der ; )  Thanks

Out of curiosity is the problem and is it with X, the window manager, or wxWidgets?

BTW for a UI element to seem instant it needs to happen within 50 milliseconds.  Just a thought.
-inod

---

### Post by strikeforce on 2006-02-17
[QUOTE=indo]Der ; )  Thanks

Out of curiosity is the problem and is it with X, the window manager, or wxWidgets?

BTW for a UI element to seem instant it needs to happen within 50 milliseconds.  Just a thought.
-inod[/QUOTE]

Its not X or the window manager its the fact of the refresh rate within python itself I would think since my g/f complains about it on her windows machine if I set the refresh rate to quick.

Its not instant at 1 second but it does flicker when you have a hell of a lot of seeders and or leechers.

---

### Post by indo on 2006-02-17
> Its not X or the window manager its the fact of the refresh rate within python itself I would think since my g/f complains about it on her windows machine if I set the refresh rate to quick.

Its not instant at 1 second but it does flicker when you have a hell of a lot of seeders and or leechers.
Ah, no, my question is as to why it flickers, there seems to be plenty of other computer programs that can update themselves without such flickering.

---

### Post by Freddd on 2006-05-22
[QUOTE=strikeforce]Breezy version of 0.6.9 is up so far in use and working :).
Hoary version of 0.6.5 is up there obviously I can't test it but it should be working.

[http://strikeforce.dyndns.org/files/](http://strikeforce.dyndns.org/files/)
[/QUOTE]
The link above doesn't work. I have installed an old version, 0.6.5 but I would really like to get 0.6.9 to work. Can anyone help me?

---

### Post by samir85 on 2006-05-23
[QUOTE=Freddd]The link above doesn't work. I have installed an old version, 0.6.5 but I would really like to get 0.6.9 to work. Can anyone help me?[/QUOTE]

I agree, is there somebody how can provide a debian package of Rufus 0.6.9 or 0.7.0 ?

The Strikeforce mirror is like Freddd already stated down. If somebody can give me the package, I can also upload it to my webspace ...

---

### Post by Freddd on 2006-05-23
Maybe someone is kind enough if we just show some patience :)

Rufus 0.6.5 doesn't work good at all for me. If I try to open a torrent in Opera or Firefox, Rufus is loaded but not the torrent. Rufus seems to be exactly what I want if I only get it to work. Maybe a new version will help?

I use qtorrent at the moment but it lacks functionality..

---

### Post by Wandering Wombat on 2006-05-23
Check ya PMs Fredd and samir85 I think I can help. ;o)

---

### Post by samir85 on 2006-05-25
Ok, thanks to Wandering Wombat. He emailed me the package.

I uploaded it to my webspace, in case someone else wants it.

[http://fix85.de.ms/pub/ubuntu/Rufus/](http://fix85.de.ms/pub/ubuntu/Rufus/)

---

### Post by Freddd on 2006-05-25
Thanks Wandering Wombat and samir85 for putting it here!
I still have some problems with Rufus though. I get "another instance of rufus is already running" if I have rufus open and try to open a torrent in rufus with opera. Rufus is loaded but not the torrent if I close rufus before trying to open the torrent in opera. This problems make rufus unusable, does anyone know how to solve it?

---

### Post by samir85 on 2006-05-25
[QUOTE=Freddd]Thanks Wandering Wombat and samir85 for putting it here!
I still have some problems with Rufus though. I get "another instance of rufus is already running" if I have rufus open and try to open a torrent in rufus with opera. Rufus is loaded but not the torrent if I close rufus before trying to open the torrent in opera. This problems make rufus unusable, does anyone know how to solve it?[/QUOTE]

I'm having the same issue.
At the moment I'm avoiding the problem by saving the torrent at my disk and then I click in Rufus "add torrent".
I know this is not very practical, but maybe you can get some more feedback by describing your problem in the Sourceforge Rufus forum.

---

### Post by strikeforce on 2006-05-29
Its a bug.  The guy got a heap of hate mail he will be starting up slowly again.

I'm keeping an eye on the forums but I figured 0.70 is worse.

Yes my server died from old age.  I'll be setting it up again shortly on my home computer.  Or putting it up somewhere for you guys to get e.g. fileshare.

---

### Post by numb401 on 2006-06-06
Wow thanks both of you for hosting and making that package, I was in wayy too deep trying to make the source code work for me with basically NO linux or compiling experience, THANKS!

---

### Post by strikeforce on 2006-06-20
Just for your info the server will be back up tonight my time hopefully.  Just finalising it.

Yay for crappy hardware :(.  Anyways I'll put it on filefront as well.  I should have version 0.7 out in a couple of days.

There will be bugs with it.  Just post them on the rufus forum included with the man page.

*Edit

I just found out one of my ram has died so my server keeps crashing with running out of memory.  I'll get on to it and update when I can.  Unfortunately at the moment I can't do much.

---

### Post by dolby on 2006-07-04
any news on this one? rufus seems like a nice substitute

---

### Post by Merit on 2006-08-04
+1 I can't find a .deb version of rufus 0.7.
I gonna test the 0.6.9 anyway.

---

### Post by redDEADresolve on 2006-09-24
i love it, works great.

just one thing, how do i get it to go into the tray?

---

### Post by motang on 2006-10-12
> **samir85 said:**
> Ok, thanks to Wandering Wombat. He emailed me the package.

I uploaded it to my webspace, in case someone else wants it.

[http://fix85.de.ms/pub/ubuntu/Rufus/](http://fix85.de.ms/pub/ubuntu/Rufus/)

Wow thanks man, it worked like charm.  :-D

---

