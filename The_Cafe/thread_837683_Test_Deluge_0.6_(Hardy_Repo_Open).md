---
title: "Test Deluge 0.6 (Hardy Repo Open)"
date: 2008-06-22
forum: The Cafe
---

### Post by zachtib on 2008-06-22
I've got a repo open for nightly builds of Deluge 0.6.  For those of you that don't know, 0.6 is a complete rewrite of the client.  It adds support for client/daemon mode, meaning the interface can run on a different computer than the backend.  The user interface has also been redesigned.  While I'm no longer one of the developers, I have to say I'm very happy with the progress the project has made with this release. :)

[http://launchpad.net/~zachtib/+archive](http://launchpad.net/~zachtib/+archive)

```
deb http://ppa.launchpad.net/zachtib/ubuntu hardy main
deb-src http://ppa.launchpad.net/zachtib/ubuntu hardy main
```

---

### Post by Ub1476 on 2008-06-22
Wow, that's awesome! I most admit that the previous design was a bit akward, things got a bit in the way of each other.

I think it's time to compile this. Do I have to remove  ~/.config/.deluge first?

---

### Post by Kingsley on 2008-06-22
Thanks for the picture uploads. Now I'm interested in buiding 0.6 on my Fedora install. :D

---

### Post by mivo on 2008-06-22
How stable are the builds currently?

---

### Post by Barrucadu on 2008-06-22
It is very nice, I've got the deluge-0.6-svn package installed on Arch and it seems completely stable.

---

### Post by zachtib on 2008-06-22
> **Ub1476 said:**
> Wow, that's awesome! I most admit that the previous design was a bit akward, things got a bit in the way of each other.

I think it's time to compile this. Do I have to remove  ~/.config/.deluge first?

I didn't have to

> **mivo said:**
> How stable are the builds currently?

I'm running it fine, I've only downloaded one Ubuntu ISO so far, though.  It's nearing RC stages, though, so it's pretty solid

---

### Post by pt123 on 2008-06-22
does it have the ability of blocking peers using right click as in Ktorrent?

---

### Post by ghindo on 2008-06-22
It sounds stable, but I may wait for 0.6.1.  When are they supposed to have a CLI client, again?

---

### Post by zachtib on 2008-06-23
> **ghindo said:**
> It sounds stable, but I may wait for 0.6.1.  When are they supposed to have a CLI client, again?

There's one now, kinda, start deluge 0.6:
```
deluge -u null
```
to start the deluge shell.  There's also a commandline client in development here:
[http://code.google.com/p/python-gnt/](http://code.google.com/p/python-gnt/)

EDIT: Screenshots: [http://pidgin.im/~sadrul/ss/apps.html](http://pidgin.im/~sadrul/ss/apps.html)

---

### Post by kpkeerthi on 2008-06-23
Deluge has come a long way, I should say. Thanks for posting this. I will wait for 0.6 final, though.

---

### Post by vishzilla on 2008-06-23
This one's needed for the Linux community. I hope 0.6 satisfies ppl who complain "will Linux ever have a decent torrent client" (I'm not one of 'em ;))

I too will wait for the final

---

### Post by Ub1476 on 2008-06-23
I have some problem with this version..

When I press "Start Daemon" or "Connect", it just crashes. It's the default settings, localhost:58846.

Installed from Arch AUR, like another guy in this thread did.

```
[DEBUG   ] 00:21:31 configmanager:88 Getting config 'hostlist.conf'
[DEBUG   ] 00:21:31 config:47 Config created with filename: hostlist.conf
[DEBUG   ] 00:21:31 config:48 Config defaults: {'hosts': ['localhost:58846']}
[DEBUG   ] 00:21:31 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 00:21:31 connectionmanager:495 on_selection_changed
[DEBUG   ] 00:21:32 config:117 Setting 'window_pane_position' to 301 of <type 'int'>
[DEBUG   ] 00:21:39 connectionmanager:393 on_button_startdaemon_clicked
[INFO    ] 00:21:39 connectionmanager:423 Starting localhost:58846 daemon..
[DEBUG   ] 00:21:44 connectionmanager:432 on_button_connect_clicked
[WARNING ] 00:21:44 connectionmanager:455 Host does not appear to be online..
[INFO    ] 00:21:44 connectionmanager:423 Starting localhost:58846 daemon..
```

---

### Post by olskar on 2008-06-23
Come on people, try it and look for bugs! Its better to find them now then in final release, right? ;)

Worked good for me btw!

When can we except final?

---

### Post by banjobacon on 2008-06-23
I don't like that I'm greeted with a connection manager upon opening the program. Similarly, I'm not a fan of the two "Quit" items in the file menu. Shouldn't the daemon/client setup should be an *advanced* feature that doesn't interfere with how most people will use the program?

---

### Post by zachtib on 2008-06-23
> **banjobacon said:**
> I don't like that I'm greeted with a connection manager upon opening the program. Similarly, I'm not a fan of the two "Quit" items in the file menu. Shouldn't the daemon/client setup should be an *advanced* feature that doesn't interfere with how most people will use the program?

If you expand the options in the connection dialog you can change this.  Also, you can enable "classic" mode in the preferences dialog to have it behave like the old client.

Just uploaded a new version, 0.6~svn3276

EDIT:
> **olskar said:**
> When can we except final?

I'm not sure, but andar seemed to imply they were nearing RC stages.

---

### Post by zachtib on 2008-06-24
Bumping this up,

Please test and submit bugs

---

### Post by etnlIcarus on 2008-06-25
Question: With most stats being moved from the Details tab to the Statistics tab, what's left on the Details tab? Is there still a graphic displaying which pieces have been downloaded?

---

### Post by zachtib on 2008-06-26
> **etnlIcarus said:**
> Question: With most stats being moved from the Details tab to the Statistics tab, what's left on the Details tab? Is there still a graphic displaying which pieces have been downloaded?

not at the moment, though it could still be added in, or in a future release like 0.6.1

---

### Post by barbedsaber on 2008-06-26
oooh, new deluge. brb. :)

---

### Post by mivo on 2008-06-29
OK; I switched to this version as well since 0.5.9.2 and 0.5.9.3 do not correctly save checksums and I just lost several gigs of downloaded data that neither Deluge nor any other client recognises (due to the [checksum proble]("http://forum.deluge-torrent.org/viewtopic.php?f=7&t=7055")m). This bug only occurs if a torrent needs to be rechecked or was moved, but it's severe and losing over a week of downloaded data is just bad. There have been issues and bugs of this type with the 0.5.x branch for several "stable" releases now. It's unusable for me since a torrent client just shouldn't lose gigs of data. So I'll give 0.6.0 a try since I don't really like any of the other clients all that much.

EDIT: Actually, 0.6.0 as of today suffers from the same checksum problem, so it too will lose data if you recheck or try to move the data and reload it. Can easily test this (without losing anything) by looking at the "total download" percentage of a torrent and then at the individual completion rate of the individual file. Easier to see if there is only  one big file in the torrent, so for example you'll see that the torrent is 30% completed, but the individual file, which is all the torrent consists of, is only completed 2%. If you recheck now, or import the data into another client, you will start again at 2%. The discrepancy becomes smaller to the end of the download.

So Deluge in any recent version is currently unusable for any larger torrent downloads that may require you to recheck the data. (Rechecking is not the actual problem, the problem is that the checksums are not or incorrectly stored, as far as I can tell.)

---

### Post by smbm on 2008-06-29
Is anyone else finding that port forwarding isn't working with 0.6?

It could just be me, it works flawlessly in 0.5 though.

---

### Post by zekopeko on 2008-06-29
same here

---

### Post by mivo on 2008-06-29
Another issue I had was that 0.6.0 uses 100% of one of my two cores (so 50% of the CPU time).

---

### Post by zachtib on 2008-06-30
Please, don't just post bugs here, go to [http://dev.deluge-torrent.org](http://dev.deluge-torrent.org)

---

### Post by mrgnash on 2008-06-30
Deluge is by far the best torrent client I have ever used, and 0.6 seems even better :) Thanks!

---

### Post by keiichidono on 2008-06-30
Thanks for the info, i'll wait for .6 to come out as a final though. :D

---

### Post by apoulos on 2008-07-04
I already have deluge 0.6 installed by svn (sudo python setup.py install).  I put your sources in the sources.list and used aptitude to install your package, but it would not overwrite the files already in place.  

How do I uninstall the svn version?

---

### Post by wrtpeeps on 2008-07-04
GUI looks amazingly similar to uTorrent. :)

---

### Post by Polygon on 2008-07-05
well, thats what people like. So many people on this forum praise the all holy utorrent and claim that "no other program will come EVEN CLOSE to utorrent"

so trying to emulate what people like is not a bad thing at all

---

### Post by Masoris on 2008-07-05
> **Polygon said:**
> well, thats what people like. So many people on this forum praise the all holy utorrent and claim that "no other program will come EVEN CLOSE to utorrent"

so trying to emulate what people like is not a bad thing at all
I cannot understand that why some people praise utorrent? Deluge is perfect for me. It also has many very nice plugins :)

---

### Post by pt123 on 2008-07-05
Ktorrent is the best, but it doesn't have the "Date Added" feature like Utorrent. There is also noway to search your torrents. 

I don't like Deluge because you can't right click and ban a peer (those bloody leechers)

---

### Post by SlugO on 2008-07-08
I have to say that I like 0.6 a lot more than the older versions. It feels less awkward and more robust.

I might even ditch Transmission for this :)

---

### Post by Vadi on 2008-07-08
Thanks for this

---

