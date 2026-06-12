---
title: "The Democracy Player"
date: 2006-04-27
forum: The Cafe
---

### Post by tikal26 on 2006-04-27
I just wnated to let you know taht democracy player for linux is out and they have made ubuntu packages, Cool. Democracy player is a player like songbird for video its like open source TV
[http://www.getdemocracy.com/](http://www.getdemocracy.com/)
and here is the linux info
[http://www.getdemocracy.com/downloads/](http://www.getdemocracy.com/downloads/)
try its kind of nice, specially for people that like videocast.

---

### Post by maruchan on 2006-04-27
Darn, couldn't get it working in Dapper...some sort of Python dependancy. :( I'd love to try it though.

---

### Post by engla on 2006-04-27
Great to see that they are putting out versions for virtually everyone and every OS, and making a specific Ubuntu package.

I'm looking for one specific thing though.. anyone found the source of the ubuntu package? I need it to build for my powerpc, there is no ready binary for ubuntu/ppc..

---

### Post by tikal26 on 2006-04-27
I installed on my laptop which curently doesn't use fedora, I tried it an had some dependency erro and then I -f intalle it and now It just hangs at strat up, but they do have source code tarball here
[ftp://ftp.osuosl.org/pub/pculture.org/democracy/src/](ftp://ftp.osuosl.org/pub/pculture.org/democracy/src/)
it would be nice to get the ubuntu version working though.

---

### Post by BathroomNinja on 2006-04-27
I'm using Dapper, here is what I have so far:

ok, so I did:
```
sudo dpkg --force-all -i Democracy-0.8.2-i386-ubuntu.deb
```

and it installed.  Then, I ran 'democracyplayer' and got this:


```
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 26, in ?
    import app
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 2, in ?
    import feed
  File "/usr/lib/python2.4/site-packages/democracy/feed.py", line 1, in ?
    from downloader import grabURL
  File "/usr/lib/python2.4/site-packages/democracy/downloader.py", line 1, in ?
    from database import DDBObject, defaultDatabase
  File "database.pyx", line 13, in database
ImportError: libboost_python-gcc-mt-1_33.so.1.33.0: cannot open shared object file: No such file or directory

```


That's a step in the right direction.  I'll keep working on it.

---

### Post by Project 318 on 2006-04-28
I linked the newer libboost-python library to the older one democracyplayer looks for and I haven't had any problems.
```
sudo ln -s /usr/lib/libboost_python-gcc-mt-1_33_1.so.1.33.1 /usr/lib/libboost_python-gcc-mt-1_33.so.1.33.0
```
edit: assuming you have libboost-python1.33.1 installed

---

### Post by pulp on 2006-04-28
You don't even have to link to the newer library as you can use this package from the repositories:

[http://archive.ubuntu.com/ubuntu/pool/main/b/boost/libboost-python1.33.0_1.32.0+1.33.0-cvs20050727-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/boost/libboost-python1.33.0_1.32.0+1.33.0-cvs20050727-1ubuntu1_i386.deb)

the only thing, that bothers me is the mozilla dependency.

---

### Post by ketsugi on 2006-04-28
I can't seem to install the Ubuntu package that's just been released for Democracy Player.

[Download Link](http://www.getdemocracy.com/downloads/ubuntu.php)

I get the following unmet dependency error:

```
ketsugi@Asahara:~/Downloads$ sudo dpkg -i Democracy-0.8.2-i386-ubuntu.deb
Password:
Selecting previously deselected package democracyplayer.
(Reading database ... 105870 files and directories currently installed.)
Unpacking democracyplayer (from Democracy-0.8.2-i386-ubuntu.deb) ...
dpkg: dependency problems prevent configuration of democracyplayer:
 democracyplayer depends on libboost-python1.33.0 (<< 1.32.0+1.33.0-cvs20050727-99); however:
  Package libboost-python1.33.0 is not installed.
 democracyplayer depends on libboost-python1.33.0 (>= 1.32.0+1.33.0-cvs20050727-0); however:
  Package libboost-python1.33.0 is not installed.
dpkg: error processing democracyplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 democracyplayer

```

The thing is, I have libboost-python1.33.1 installed. Seems like the deb won't accept more recent versions. Is there any workaround for this?

---

### Post by jobezone on 2006-04-28
EDIT: I'm using Debian testing!! But nevertheless, this is something ubuntu users also need to to.

I've manage to solve it myself, by doing:
1 - sudo dpkg -i --force-install Democracy-0.8.2-i386-ubuntu.deb
2 - sudo ln -s /usr/lib/libboost_python-gcc-mt-1_33_1.so.1.33.1 /usr/lib/libboost_python-gcc-mt-1_33.so.1.33.0

This thread ([http://ubuntuforums.org/showthread.php?t=167056&highlight=democracy+player](http://ubuntuforums.org/showthread.php?t=167056&highlight=democracy+player)) talks of another way, by downloading and installing a lowered version libboost-python package.

This application is cool!!! Other than crashing with certain videos (like the macTV channel ones), which according to the developers, seems to be related to a certain video encoding that isn't supported in xine (and other free players, it seems), it's pretty good. The search functionality is impressive (searches the net with Yahoo for videos): I tried searching various non-mainstream things, from 'stallman', '911'(eh!), to 'chomsky', etc., and found much stuff.
I also saw a debian developer saying he will put it in debian unstable, so it could be backported to Dapper.

---

### Post by jobezone on 2006-04-28
I'm using debian testing, and doing the link thing worked, and the program runs.
Expect crashes with movies encoded with a certain codec, which xine doesn't like. You can't see which codec a movie is encoded with before playing it, so it may happen from time to time.

The "macTV Videocast" channel videos is one example of crashing videos.

Other than this problem, it's a very, very good program. Especially once more people start adding "democracyplayer" capabilities to their video podcasts. It can also search for videos on the entire web, I think. At least that's what it seemed, as I got many results.

EDIT:spoke a bit too soon. I'm finding that sometimes I can subscribe to channels, and others I can't, meaning, when I click the subscribe button, nothing happens. If I navigate a bit around my current channels, perhaps view a video, then I can do it, until it stops working again...

---

### Post by jobezone on 2006-04-28
> the only thing, that bothers me is the mozilla dependency.
Maybe this is obvious, but have you tried telling apt-get to **f**ix it?
**sudo apt-get -f install**

---

### Post by ketsugi on 2006-04-28
Linking didn't work for me, but installing the older package did. Thanks!

---

### Post by jobezone on 2006-04-28
Yes, because I forgot to say I forced the installation of democracy player...:/...

---

### Post by briguy on 2006-04-28
```
 1 - sudo dpkg --force-all -i Democracy-0.8.2-i386-ubuntu.deb
2 - sudo ln -s /usr/lib/libboost_python-gcc-mt-1_33_1.so.1.33.1 /usr/lib/libboost_python-gcc-mt-1_33.so.1.33.0
``` 
Worked for me.  Thanks!  Now if only it would sync to the iPod...

---

### Post by no1wantdthisname on 2006-04-28
Worked for me as well, however video is messed up.  I think it's using xv which doesn't work well with my i915 card, aiglx, and compiz setup.  
It seems to be using xine as a backend, but where do I specify the video output driver to use?  Changing it in xine doesn't seem to do anything, and there's no option in the gui that modifies it.

---

### Post by FredTech on 2006-04-28
I managed to install it using the methods described here, and using
```
sudo apt-get -f install
```
to install the missing dependencies.

I love the concept, but the program has one nasty bug. Whenever I start watching a list of movies and the last movie on the playlist finishes, the program abruptly terminates. Has anyone else experienced this (and found a solution?)

---

### Post by Omer on 2006-04-28
Here's a fixed version, just remove the .zip extension and install.

Fixing:
* libboost-python dependency problem.
* linking libboost-python libs.

---

### Post by ShiftyPowers on 2006-04-28
I managed to get it working with the fix above but now everytime I do a dist-upgrade it complains about democracy and wants to remove it.  Any ideas?

---

### Post by KingBahamut on 2006-04-28
The Participatory Culture Foundation just released Democracy Player 0.8.2 for Linux, the first beta version for Linux. It's a free software internet TV client with built in support for both RSS video podcasts and downloading using BitTorrent. It can even scrape web pages for videos. It's an excellent way to find great internet video. For example, once you've installed Democracy, make sure to check out The Postal Service - Such Great Heights on the Telemusicvision channel.

External Link 
[http://getdemocracy.com/downloads](http://getdemocracy.com/downloads)

Anyone run this little guy yet? Hows it work? Look and feel? 

> It can even scrape web pages for videos

---

### Post by tenn on 2006-04-28
I went to install it on dapper beta but it required an older version of gstreamer than the one installed so I did not bother with it.:/

---

### Post by helpme on 2006-04-28
[http://ubuntuforums.org/showthread.php?t=167056](http://ubuntuforums.org/showthread.php?t=167056)
[http://ubuntuforums.org/showthread.php?t=167245](http://ubuntuforums.org/showthread.php?t=167245)

---

### Post by jobezone on 2006-04-28
[QUOTE=ShiftyPowers]I managed to get it working with the fix above but now everytime I do a dist-upgrade it complains about democracy and wants to remove it.  Any ideas?[/QUOTE]
Hm.. Isn't there a way in synaptic to "lock" a certain package from being touched/upgraded/removed by apt-get?

---

### Post by jazzmuzik on 2006-04-28
Can one play the Democracy videos with other media players?

---

### Post by simplyw00x on 2006-04-28
Yes, select the package and go Package/Lock

---

### Post by jobezone on 2006-04-28
Yes. They are downloaded to **~/Movies/Democracy/** .

---

### Post by theh0g on 2006-04-28
No matter what I try, I get:
```
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 26, in ?
    import app
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 389, in ?
    import frontend
  File "/usr/lib/python2.4/site-packages/democracy/frontend.py", line 13, in ?
    import MozillaBrowser
  File "MozillaBrowser.pyx", line 3, in MozillaBrowser
ImportError: No module named gtkmozembed
```

I tried install everything possible, but I dunno how to solve this mozembed thingie. Anyone?

---

### Post by cbudden on 2006-04-28
Why does the Linux version of Democracy use xine as a video player, when the Windows version uses VLC.  I would have prefered VLC.

---

### Post by cbudden on 2006-04-28
[QUOTE=jobezone]Yes. They are downloaded to **~/Movies/Democracy/** .[/QUOTE]

Can this be changed?

---

### Post by lazyd2 on 2006-04-28
Works great. Nice one!

---

### Post by jobezone on 2006-04-28
> Can this be changed?
I've seen some comments from the developers saying that this wouldn't be done until after 1.0 release, since aparently it would need a major(!) rewrite.

---

### Post by cbudden on 2006-04-28
[QUOTE=jobezone]I've seen some comments from the developers saying that this wouldn't be done until after 1.0 release, since aparently it would need a major(!) rewrite.[/QUOTE]


Ah ok then.  Thanks

---

### Post by pulp on 2006-04-28
[QUOTE=jobezone]Maybe this is obvious, but have you tried telling apt-get to **f**ix it?
**sudo apt-get -f install**[/QUOTE]

Well, yes. Sure. The dependencies are all met but what I intended to say was that I don't like to have to install mozilla-browser if I already have firefox installed (which is only installed to let epiphany work, so now I have 2 unused browsers :???: ).

[QUOTE=cbudden]Why does the Linux version of Democracy use xine as a video player, when the Windows version uses VLC. I would have prefered VLC.[/QUOTE]

Now that made me think of how useful the recently announced Phonon project in KDE actually is. "Democracy" would only depend on Phonon, no matter if you have gstreamer, vlc, xine, nmm or whatever as backend (if I understood the whole thing correctly).

---

### Post by briguy on 2006-04-28
Use this link below to install libboost, then install democracy.  Works for me, and I can apt-get upgrade to my heart's content.

[http://archive.ub......0050727-1ubuntu1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/b/boost/libboost-python1.33.0_1.32.0+1.33.0-cvs20050727-1ubuntu1_i386.deb")

---

### Post by roostishaw on 2006-04-29
[QUOTE=briguy]Use this link below to install libboost, then install democracy.  Works for me, and I can apt-get upgrade to my heart's content.

[http://archive.ub......0050727-1ubuntu1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/b/boost/libboost-python1.33.0_1.32.0+1.33.0-cvs20050727-1ubuntu1_i386.deb")[/QUOTE]

Just writing to say it work excellent, thanks!
For anyone else, just run the deb and it takes care of the dependancies. ( <-- Spelled that wrong...)

---

### Post by jobezone on 2006-04-29
[QUOTE=cbudden]Ah ok then.  Thanks[/QUOTE]
sorry, I must have imagined what I just said ... I think I'll probably make sure I know what I know before writting about it.

Someone has found a way to change the download directory: [http://forum.getdemocracy.com/viewtopic.php?id=112](http://forum.getdemocracy.com/viewtopic.php?id=112)

---

### Post by pulp on 2006-04-29
It'd be great if this thread could be merged with this one [http://ubuntuforums.org/showthread.php?t=167056](http://ubuntuforums.org/showthread.php?t=167056)

---

### Post by Roel Groeneveld on 2006-04-29
[QUOTE=briguy]Use this link below to install libboost, then install democracy.  Works for me, and I can apt-get upgrade to my heart's content.

[http://archive.ub......0050727-1ubuntu1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/b/boost/libboost-python1.33.0_1.32.0+1.33.0-cvs20050727-1ubuntu1_i386.deb")[/QUOTE]
That worked for me, too. Thanks! 
(now watching The Postal Service - The District Sleeps ;) )

---

### Post by ubuntu_demon on 2006-04-29
[QUOTE=helpme][http://ubuntuforums.org/showthread.php?t=167056](http://ubuntuforums.org/showthread.php?t=167056)
[http://ubuntuforums.org/showthread.php?t=167245](http://ubuntuforums.org/showthread.php?t=167245)[/QUOTE]
thnx I merged them.

---

### Post by MetalMusicAddict on 2006-04-29
The links to the Democracy player arent working. Id really like to see some screenshots.

Anyone using this on Dapper?

---

### Post by lazyd2 on 2006-04-29
[quote=MetalMusicAddict]The links to the Democracy player arent working. Id really like to see some screenshots.

Anyone using this on Dapper?[/quote]Here you go

---

### Post by cbudden on 2006-04-29
[QUOTE=jobezone]sorry, I must have imagined what I just said ... I think I'll probably make sure I know what I know before writting about it.

Someone has found a way to change the download directory: [http://forum.getdemocracy.com/viewtopic.php?id=112](http://forum.getdemocracy.com/viewtopic.php?id=112)[/QUOTE]


Thanks, but the website is down at the moment :(

---

### Post by jobezone on 2006-04-29
Anyway, this is what this person did:
> About 1/3 of the way down the platformcfg.yo file file you'll find the following entries:

_findDirectories()

def _getMoviesDirectory():
    path = os.path.join(_baseMoviesDirectory, config.get(config.SHORT_APP_NAME))
    try:
        os.makedirs(os.path.join(path, 'Incomplete Downloads'))
    except:
        pass
    return path

Change the

path = os.path.join(_baseMoviesDirectory, config.get(config.SHORT_APP_NAME))

entry so as to read:

path= <enter the name of your chosen download location here>

Hope this helps


---

### Post by tikal26 on 2006-04-29
I don't get it to work, It isntalls but it just hangs when I opend it and then nothign happens

---

### Post by DigitalDuality on 2006-04-29
Looks good

---

### Post by ssam on 2006-04-30
built it on powerpc dapper.

somthing like
```

sudo apt-get install build-essential subversion python2.4 libboost-python-dev python2.4-gnome2 python2.4-gnome2-extras python-gnome2-extras-dev python2.4-pyrex python2.4-gtk2 python2.4-glade2 python-gtk2-dev mozilla-dev mozilla-psm libxine-dev

mkdir democracy
cd democracy
svn co https://svn.participatoryculture.org/svn/dtv/trunk/tv
cd tv/platform/gtk-x11
./test.sh

```

after that you just need to run the ./test.sh script to run it.

also running
```
svn update
```
in the tv directory would get the latest version

---

### Post by ddonky on 2006-05-08
It mostly works ok for me, sometimes when I click to subscribe to a channel, it open the .xml file in firefox instead of adding it to my subscribed channel list.

I can't wait for them to work out that particular bug, and I like the idea of it scraping the 'net for vids.

---

### Post by gamma on 2006-05-18
Wow this is a great application. I like how they build in bittorrent support. The only thing is I wish they changed the dependencies, or made them more customizeable. For example, firefox for the web browser and gstreamer for playback..

---

