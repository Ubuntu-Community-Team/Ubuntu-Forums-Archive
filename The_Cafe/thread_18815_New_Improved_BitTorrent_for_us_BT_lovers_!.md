---
title: "New Improved BitTorrent for us BT lovers !"
date: 2005-03-08
forum: The Cafe
---

### Post by bored2k on 2005-03-08
[IMG]http://img180.exs.cx/img180/1039/bittorrentlg4eq.gif[/IMG] 
BitTorrent ver 4.0.0 Source Code (Python)

BitTorrent is a free speech tool.

BitTorrent gives you the same freedom to publish previously enjoyed by only a select few with special equipment and lots of money. ("Freedom of the press is limited to those who own one" -- journalist A.J. Liebling.)

# 2005-03-07: 4.0.0 is now available.
Changes since the last stable release:

   * All new queue-based user interface
   * Many options are now modifiable from the interface, including upload rate
   * Lots of other interface improvements
   * Extra stats are visible, for those who like it
   * Remembers what it was doing across restarts
   * New .torrent maker "btmaketorrentgui" replaces "btcompletedir"
   * Better performance, as always
   * License has changed to the BitTorrent Open Source License
   * Torrent fields are correctly created and interpreted as utf8
   * Too many little things to list

A few technical notes, for those interested:

   * Single port: launchmany can seed and client can download many files from a single port and thread
   * Interface now uses GTK instead of wxWidgets
   * BitTorrent packets are marked as bulk data to make traffic shaping easier

[http://www.bittorrent.com/](http://www.bittorrent.com/)

---

### Post by BWF89 on 2005-03-08
I heard that BitTorrent was being attacked by the MPAA.

---

### Post by bored2k on 2005-03-08
[QUOTE=BWF89]I heard that BitTorrent was being attacked by the MPAA.[/QUOTE]
 No dude why .

BT is open source, and its one of the only legal filesharing programs.

What is being attacked by MPAA are sites hosting illegal files on .torrent format. The application can not be attacked, it is completely legal.

More info on MPAA and attacked/murdered/axed/scared torrent sites here [http://www.slyck.com/](http://www.slyck.com/) .

Also for something really funny clic [here](http://www.lokitorrent.com/)


[Legal Torrents - No. 1 Legal Torrent Site](http://www.legaltorrents.com/)

---

### Post by BWF89 on 2005-03-08
> Also for something really funny clic here
That was the site I read about them attacking.

I tried to install BitTorrent but it wouldn't work. I use LimeWire (because it's Open Source) to steal all of my music.

---

### Post by bored2k on 2005-03-08
[QUOTE=BWF89]That was the site I read about them attacking.

I tried to install BitTorrent but it wouldn't work. I use LimeWire (because it's Open Source) to steal all of my music.[/QUOTE]
 I also use Limewire 4.8 Pro

But hey, if you got Limewire that means you hava Java, so rush to [Azureus](http://azureus.sourceforge.net/screenshots_v2.php) and download Azureus GTK, extract and open it just like you would open Limewire. Et voila , you got a working killer Bittorrent client .

And btw you can just apt-get install bittornado-gui. Its not nearly as good as Azu, but its lightweight. Some torrents wont dl thru that one tho. To open it you just type > btdownloadgui

---

### Post by TravisNewman on 2005-03-08
yes, azureus does rock hard.

I think I'll just stick to that, unless the resource hogging gets too annoying, then I might give this new BT a shot on its own.

---

### Post by bored2k on 2005-03-08
[QUOTE=panickedthumb]yes, azureus does rock hard.

I think I'll just stick to that, unless the resource hogging gets too annoying, then I might give this new BT a shot on its own.[/QUOTE]


I don't really like Azu much, but I do know its the best BT app around. I only use it for UDP tracker .torrents, not yet supported by BitTornado [thus I always try 2 get http tracker .torrents]. If they included UDP support , then I would be a very happy guy [haven't tested new BT as I'm waiting for 1.5gb *24SEASON1DISC3EPISODES9101112DVDRIPFRENCH.torrent* *backup* to download . 

Probably Hoary's sources will soon update to this BT, wich will be awsome.  :-D

---

### Post by Rule on 2005-03-08
[QUOTE=panickedthumb]yes, azureus does rock hard.

I think I'll just stick to that, unless the resource hogging gets too annoying, then I might give this new BT a shot on its own.[/QUOTE]

azureus hogs resources??? I never noticed hahaha

---

### Post by bored2k on 2005-03-08
[QUOTE=Rule]azureus hogs resources??? I never noticed hahaha[/QUOTE]
 Maybe you haven't noticed because you've never used it on Windows. But they're you can clearly notice how slow Java Azureus is.

On Linux it's really not that big of a deal, but bittorrent/tornado is noticeably faster, and they both do the same thing [only Azureus has a lot of options a newbie might want to touch, without knowing they could greatly affect it's download performance] .

---

### Post by jayded on 2005-03-09
Why the outdated 'java is too slow' attack regarding Azureus ?

I've been using it a long time and you're the first person that has put out such FUD about Java on a thread regarding Azureus.  =D> 

BTW: What you refer to as 'Java Azureus', is just Azureus since there is only a Java version. It pretty much performs the same on all platforms.  8) 


[QUOTE=bored2k]Maybe you haven't noticed because you've never used it on Windows. But they're you can clearly notice how slow Java Azureus is.

On Linux it's really not that big of a deal, but bittorrent/tornado is noticeably faster, and they both do the same thing [only Azureus has a lot of options a newbie might want to touch, without knowing they could greatly affect it's download performance] .[/QUOTE]

---

### Post by oddabe19 on 2005-03-09
ahhh yes... the whole pirating issue....

shameless plug for my favorite music... but....

one of the many great reasons about christian music is that you can get a good deal of mp3's, ogg's, movies, whatever from the artists or record labels website absolutely free... and legal. Not to mention a lot of free concerts. They're not about the money so the artists don't care about giving stuff away for free (leaving the meaning of the songs out of this discussion). So very little risk of US law breaking.

But yeah, torrents aren't illegal, its the type of things you share on torrents that can be illegal. Sharing movies that are copyrighted and liscenced is illegal. it's just like boot legging and selling on streets.
But sharing opensource software, sharing broadcasted shows (VHF, UHF, NON-Cable), and freely distrubatable music is completely legal.


AZAREUS ROCKS MY FACE OFF!!!

:-P

---

### Post by bored2k on 2005-03-09
[QUOTE=jayded]Why the outdated 'java is too slow' attack regarding Azureus ?

I've been using it a long time and you're the first person that has put out such FUD about Java on a thread regarding Azureus.  =D> 

BTW: What you refer to as 'Java Azureus', is just Azureus since there is only a Java version. It pretty much performs the same on all platforms.  8)[/QUOTE]
 It might perform the same, but when  you mix it with a crappy resource handler like Windows opening/using Azureus hurts. Even more when you hit <ctrl shift escape> and you notice it's chewing your box. :P I have no beef with Azureus, but I just like bittornado a lot.

I'd love to see TorrentStorm for linux, but its "the windows torrent app" :(

---

### Post by bored2k on 2005-03-09
[QUOTE=oddabe19]ahhh yes... the whole pirating issue....

shameless plug for my favorite music... but....

one of the many great reasons about christian music is that you can get a good deal of mp3's, ogg's, movies, whatever from the artists or record labels website absolutely free... and legal. Not to mention a lot of free concerts. They're not about the money so the artists don't care about giving stuff away for free (leaving the meaning of the songs out of this discussion). So very little risk of US law breaking.

But yeah, torrents aren't illegal, its the type of things you share on torrents that can be illegal. Sharing movies that are copyrighted and liscenced is illegal. it's just like boot legging and selling on streets.
But sharing opensource software, sharing broadcasted shows (VHF, UHF, NON-Cable), and freely distrubatable music is completely legal.


AZAREUS ROCKS MY FACE OFF!!!

:-P[/QUOTE]
 Hey I have never really found a free christian music/sermons [sorry if that is not the correct term, i'm hispanic] sites. Can you direct me to some ? Even I have some *sermons* [in spanish tho :\] here .

---

### Post by chrisw on 2005-03-09
For torrents I'm more than happy with btlaunchmany from the command line...... just set it up to  look at a specific directory, set your bandwidth settings and then when you get a new torrent file drop it in the directory and off it goes.

(btlaunchmany  ~user/torrents/ --max_upload_rate 3  > /tmp/btlog &) &

You can then

tail /tmp/btlog    

to see the stats, how long your downloads are going to take or if they are completed.

It then runs happily in the background using virtualy no resources.

Now if only I could find a fully featured news bin grabber like the latest version of Grab-It for Windows, only in a command line version.... I would be realy happy.

BNR2 sucks, I'd rather use the old version of Grab-It under Crossover......... new version allows you to search all news groups with out having to subscribe or download the headers *the word "rocks" comes to mind*

---

### Post by poofyhairguy on 2005-03-09
[QUOTE=bored2k]:P I have no beef with Azureus, but I just like bittornado a lot.[/QUOTE]

Second that. Nado kicks ass.

I like it more than  regular bittorrent. When I had it on Fedora, it kept nagging me to donate!

---

### Post by bobmitch on 2005-03-09
IMHO, the best torrent client is ABC.  

It fits in with Ubuntu's ethos (it`s written in python) - and it has a decent gui.
It doesn`t have all the bells and whistles that azureus has - but then, how many of those bells and whistles do most people use?

If you want a great, efficient, powerful yet easy to use client, then ABC is the one for you.

---

### Post by Dylanby on 2005-03-09
Back when I used Azureus under Windows it was always fast. It did leak memory though.

---

### Post by bored2k on 2005-03-11
[QUOTE=bobmitch]IMHO, the best torrent client is ABC.  

It fits in with Ubuntu's ethos (it`s written in python) - and it has a decent gui.
It doesn`t have all the bells and whistles that azureus has - but then, how many of those bells and whistles do most people use?

If you want a great, efficient, powerful yet easy to use client, then ABC is the one for you.[/QUOTE]
 ABC hasnt been updated in a while, some trackers will refuse it.

Anyway, I'm testing Bittorrent 4.0 on the Hoary torrent, it ROCKS.

---

### Post by bobmitch on 2005-03-11
[QUOTE=bored2k]ABC hasnt been updated in a while, some trackers will refuse it.

Anyway, I'm testing Bittorrent 4.0 on the Hoary torrent, it ROCKS.[/QUOTE]

As in, the official client?  Must have had a decent makeover since the last version I played with. :)

Is it in universe?

---

### Post by bored2k on 2005-03-12
[QUOTE=bobmitch]As in, the official client?  Must have had a decent makeover since the last version I played with. :)

Is it in universe?[/QUOTE]
 Haven't seen it in repositories no where.

The source download from bittorrent.com is a breeze. You just extract and run with python btdownloadgui.py.
Its way prettier than I expected, and, being the official BT from where the others create theirs, performance is awsome.

Anyway here it is attached.

---

### Post by bobmitch on 2005-03-12
[QUOTE=bored2k]Haven't seen it in repositories no where.

The source download from bittorrent.com is a breeze. You just extract and run with python btdownloadgui.py.
Its way prettier than I expected, and, being the official BT from where the others create theirs, performance is awsome.[/QUOTE]

Cheers mate!  

You`re right - it *is* a huge improvement on previous versions.

All the functionality of other new clients with the sweet sweet aroma of officiality. :)

---

### Post by bored2k on 2005-03-12
[QUOTE=bobmitch]Cheers mate!  

You`re right - it *is* a huge improvement on previous versions.

All the functionality of other new clients with the sweet sweet aroma of officiality. :)[/QUOTE]
 Yup, loving it so far.

I wonder if it has UDP tracker support though ... i'll have to *ask* Deimos :roll:

---

### Post by bobmitch on 2005-03-12
Finding it hanging up now and again tho - have to force kill it.
You finding this at all?

---

### Post by bored2k on 2005-03-12
[QUOTE=bobmitch]Finding it hanging up now and again tho - have to force kill it.
You finding this at all?[/QUOTE]
 Nope , yesterday I downloaded the whole Hoary PRE disc without a problem.

Haven't tested it on Hoary though.

Edit -> When does the hanging occur ?

---

### Post by bobmitch on 2005-03-12
[QUOTE=bored2k]Nope , yesterday I downloaded the whole Hoary PRE disc without a problem.

Haven't tested it on Hoary though.

Edit -> When does the hanging occur ?[/QUOTE]

I`m on hoary RC - fully updated.  I managed to hang it initially by drag & dropping a torrent file onto it.  Though this worked when I tried it again, so I couldn`t reproduce that one.

No biggie really.

---

### Post by bored2k on 2005-03-12
[QUOTE=bobmitch]I`m on hoary RC - fully updated.  I managed to hang it initially by drag & dropping a torrent file onto it.  Though this worked when I tried it again, so I couldn`t reproduce that one.

No biggie really.[/QUOTE]
 Drag n' Drop ... that's something I haven't tested :roll: .

I hope they do upgrade ABC-client to this 4.0 version. Again, I don't know what could be lacking on this version, but I hope they get creative ;).

---

### Post by Belarios on 2005-03-29
I can't find anywhere in BitTorrent 4.0 where it tells you how many seeders and peers are in the swarm for your torrent.  I like this feature in Azureus.

When I start downloading something, I want to know if there are 0 seeds or 10 seeds; 10 peers or 1000 peers; so I know what transfer rates I can expect or if I'm wasting my time.  Also, when I go to remove a torrent, I like to know that there are a few seeds, so that I'm not the last one.  I can open up the window to tell me who is connected, but that doesn't tell me the total number in the swarm.  I can be connected to 20 peers, but there may be 0 seeds, and my likelihood of getting the whole torrent is poor.

Perhaps I'm just overlooking this feature.  The official BitTorrent client does a good job of hiding its features to keep the interface simple.  I'd be happy to abandon Azureus except for this one feature.

---

### Post by thechitowncubs on 2005-05-19
[http://www.ubuntuforums.org/showthread.php?t=35660](http://www.ubuntuforums.org/showthread.php?t=35660)

---

### Post by bored2k on 2005-05-19
[QUOTE=thechitowncubs][http://www.ubuntuforums.org/showthread.php?t=35660](http://www.ubuntuforums.org/showthread.php?t=35660)[/QUOTE]
 Dude you just woke up a two month sleeper lol.

---

### Post by pdk001 on 2005-05-20
i have a router and i cant upload something on web
any ideas?

---

### Post by bored2k on 2005-05-20
[QUOTE=pdk001]i have a router and i cant upload something on web
any ideas?[/QUOTE]
 You need to forward your bittorrent ports. Read azureuz's wiki on how to do that ;).

---

### Post by jdodson on 2005-05-20
[QUOTE=jayded]Why the outdated 'java is too slow' attack regarding Azureus ?
[/QUOTE]

because it is.  on my ubuntu machine i downloaded a game called spice trade.  its a java .jar file.  i downloaded the jvm.  i ran the game.  it was pretty chunky.  after playing it for two hours i got a Java.outOfMemory error.  WAH!  i have a gig of ram!  shessh, thought java was better at memory management than that.

and it was slow.

i have a AMD 64 3000+ with a gig of ram.  no simple GUI app game should be chunky.

---

### Post by jro on 2005-05-20
Its probably just the coding. Don't blame the code if the coder hasn't optimized his/her program. Azureus used the Eclipse libraries anyway, so the GUI rendering is better than Swing IMHO. 

But, you've used one java app so you must be teh master java programmer. So I guess you know what your talking about. :razz:

---

### Post by bored2k on 2005-05-20
[QUOTE=jro]But, you've used one java app so you must be teh master java programmer. So I guess you know what your talking about. :razz:[/QUOTE]
> **Troll**. In the context of Internet discussions, a troll refers to a person who makes inflammatory or hostile comments, which by effect or design cause disruptions in discourse. Such individuals may have a sociological disorder, which is expressed through the Internet platform, or may simply be mischievous —using the percieved anonymity of the Internet as a platform to test an alternate persona . 
:roll:

---

### Post by jdodson on 2005-05-20
[QUOTE=jro]Its probably just the coding. Don't blame the code if the coder hasn't optimized his/her program. Azureus used the Eclipse libraries anyway, so the GUI rendering is better than Swing IMHO. 

But, you've used one java app so you must be teh master java programmer. So I guess you know what your talking about. :razz:[/QUOTE]

ok.   where do i start.  i am sure you know all about this, so i am wasting my time, but here goes.

first off.  java is a programming language that manages memory for you.  its the great thing about most modern programming languages, you dont have to worry about de-allocating memory.  the java vm is supposed to free up memory so you dont run out, its a great thing really.  thing is, it doesnt always do that very well.  case in point, spicetrade.  java was supposed to de-allocate the memory, it did not, thus the java.outofmemory exception that caused the program to dead lock.  i got no other errors beyond that one.  that is a java problem as java is supposed to take memory management and put it in the vms hands, not the users.  java = java - 1;

second.  spicetrade uses awt.  not terribly fast.  then again i have never seen a fast java gui.  ever.  awt is not known for its speed.

i am sure you also know eclipse is a ide that uses the jdt.  the jdt is an abstraction above other layers of gui code.  abstractions are slower than native calls.  and at times there are many layers of abstraction on top of a GUI.  in fact i think (correct me if i am wrong please) but i think the jdt is a wrapper around swing and awt.  unless the jdt makes native calls per OS, which i doubt(but could be true), but if were the case depending on implementation could be slower or faster than swing depending on the conventions the programmers used.  

and third.  yes, i have used java.  i have used java to create many GUI apps.  i have used awt, swing, netbeans and eclipse.  check out the code from an eclipse or netbeans app.  the gui code is a monstrosity.  even when i handcoded a GUI it was still slow(swing, awt).  now i have not handcoded and jdtGUI, however i am sure you can provide us all with a code sample of its breakneck speed increase(handcoded) over the RAD development model.   

from my GUI programming experience, java GUIs are the slowest.  now java is not slow when you compare it to math calculations due to how it is compiled at runtime and smart compiler optimizations.  python GUIs seem(to me) to be much more responsive, however python does lag behind java in terms of math calculations per second.  now if we compare java GUIs with C/C++ GUIs, its no contest.  C/C++ own Javas house.  though java is not far off with c even for some kinds of math calls.  i am not dissing java, i think it is a fine language.  though the freedom aspect bothers me.  however we always have gcj(which doesnt use swing, awt or jdt fwiw).  i think with gcj you can use gtk and gtk2.  and since gcj is native machine code as apposed to java bytecode(which is runtime compiled to native machine code and therefore slower due do the abstraction), it is faster(gcj). 

anyways, dont mean to ramble.

---

### Post by jro on 2005-05-20
Heh, bored2k pegged me on that one. Sorry, I am a sucker for trolling people that call Java slow. Most call it slow 'cause its popular to say.

Looks like you got more of a head on you than I thought. Kudos on the breakdown.

---

### Post by tit4tat on 2005-06-17
I noticed the newer Official BitTorrent 4.1.2 is now available for downlaod as .deb file. This seems my only hope for a decent linux GUI linux client with multiple active torrents listed on one window. (I don't have access to network firewall to forward ports for Azureus), Can anybody layout the stept for installing this file? Also, how do I go about adding the start file to the Application -> Internet Menu.

Thnx.

---

### Post by bored2k on 2005-06-17
[QUOTE=tit4tat]I noticed the newer Official BitTorrent 4.1.2 is now available for downlaod as .deb file. This seems my only hope for a decent linux GUI linux client with multiple active torrents listed on one window. (I don't have access to network firewall to forward ports for Azureus), Can anybody layout the stept for installing this file? Also, how do I go about adding the start file to the Application -> Internet Menu.

Thnx.[/QUOTE]
 Do -not- download teh deb. It is crooked, or, at least does not work with us. CLick on [http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125](http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125) and download the tgz [http://prdownloads.sourceforge.net/bittorrent/BitTorrent-4.1.2.tar.gz?download](http://prdownloads.sourceforge.net/bittorrent/BitTorrent-4.1.2.tar.gz?download) (I would suggest getting the 4.0.2 -older, but more stable-). After that is done, in your browser, extract the .tgz package, then double clic on it. It should show a open/run ?

---

### Post by tit4tat on 2005-06-17
Yeah this works fine. I just have to figure out now how to make shurtcurts either to the application menu or desktop.

Btw, what's the difference between a .deb install where the files get spread all over the place and this one where all files stay in one folder. Just wondering :)

---

### Post by bored2k on 2005-06-17
[QUOTE=tit4tat]Yeah this works fine. I just have to figure out now how to make shurtcurts either to the application menu or desktop.

Btw, what's the difference between a .deb install where the files get spread all over the place and this one where all files stay in one folder. Just wondering :)[/QUOTE]
 .deb are handled by apt, your package manager -so to say- You can type man apt-get for more information. They get upgraded -if possible- and dealt with their dependencies there. Python packages like this, stay in the folder, and you would have to manually upgrade them.

For the shortcut, grab btdownloadgui.py and drop in your panel :d.

---

### Post by carlc on 2005-06-17
[QUOTE=bored2k]Do -not- download teh deb. It is crooked, or, at least does not work with us. CLick on [http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125](http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125) and download the tgz [http://prdownloads.sourceforge.net/bittorrent/BitTorrent-4.1.2.tar.gz?download](http://prdownloads.sourceforge.net/bittorrent/BitTorrent-4.1.2.tar.gz?download) (I would suggest getting the 4.0.2 -older, but more stable-). After that is done, in your browser, extract the .tgz package, then double clic on it. It should show a open/run ?[/QUOTE]

I got lost here somewhere. Which file should I double click. I extracted the .tgz package which leaves me with these file:

BitTorrent           btdownloadheadless.py  btmaketorrent.py   bttrack.py         images            locale       redirdonate.html  winsetup.py
bittorrent.nsi       btlaunchmanycurses.py  btreannounce.py    build.bat          INSTALL.unix.txt  makei18n.sh  setup.py
btdownloadcurses.py  btlaunchmany.py        btrename.py        BUILD.windows.txt  khashmir          PKG-INFO     test
btdownloadgui.py     btmaketorrentgui.py    btshowmetainfo.py  credits.txt        LICENSE.txt       README.txt   TRACKERLESS.txt

---

