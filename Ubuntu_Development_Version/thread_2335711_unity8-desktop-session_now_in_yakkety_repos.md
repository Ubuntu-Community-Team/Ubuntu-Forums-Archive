---
title: "unity8-desktop-session now in yakkety repos"
date: 2016-08-31
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-31
No longer need ppa. (Probably for a while now.)

Libertine still having issues with control center but will create containers and run deb apps like firefox, gedit and xterm will work.

I had to do a fresh install. Typing this from a machine with NVIDIA GF110 [GeForce GT 610] with Gallium 0.4 on NVD9

regards..

---

### Post by ventrical on 2016-08-31
Comment:

 I will continue to test unity8 on nVidia graphics based form factors to see how it all pans out.  It is obvious that unity8 with libertine is more Intel friendly but there is always a chance that this may change. If it is any consolation to anyone testing unity8 stack I am assured that top developers from Canonical have taken up the task to burn the midnight oil until they get it right. 

...to be continued :)

... whether or not unity8 desktop and mir works well this round there is a novelty in having the libertine containers on the side.  So if they can make this solid, stable and reliable on several various form factors that are amd64/i386 based it will be a bonus IMHO. Personally I like it. I can do things with containers more securely  and I can run programs concurrently from different containers, actually getting the chance to push Intel VT chip features and actually use them.

Regards..

---

### Post by #&amp;thj^% on 2016-08-31
> Comment:

 I will continue to test unity8 on nVidia graphics based form factors to  see how it all pans out.  It is obvious that unity8 with libertine is  more Intel friendly but there is always a chance that this may change.  If it is any consolation to anyone testing unity8 stack I am assured  that top developers from Canonical have taken up the task to burn the  midnight oil until they get it right. 

...to be continued [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

... whether or not unity8 desktop and mir works well this round there is  a novelty in having the libertine containers on the side.  So if they  can make this solid, stable and reliable on several various form factors  that are amd64/i386 based it will be a bonus IMHO. Personally I like  it. I can do things with containers more securely  and I can run  programs concurrently from different containers, actually getting the  chance to push Intel VT chip features and actually use them.

Regards..
And I will be all eyes and ears here..
Thanks Vent :D

---

### Post by mc4man on 2016-08-31
Curious - have you tried playback of video or  audio files with a libertine installed player such as totem or vlc?
(the built-in mediaplayer (mediaplayer-app??), doesn't seem able to handle any codecs except the 'free' ones such as ogg/vorbis & maybe flac, plus has no stop/pause button or any controls at all.
Here no media  player in libertine can initiate audio, not to mention the menus of players in libertine are 50-50 whether they drop down to use. (with no DnD in libertine app menus are a must.

Where is the file manager in unity8? There is little possibility people will use on Desktop installs without one.

---

### Post by ventrical on 2016-08-31
> **1fallen said:**
> And I will be all ears here..
Thanks Vent :D

..hehehe... thanks .. actually as I read over what I wrote I wonder if it is all a big yawner and to be honest .. when I think of unity8  I sometimes get the urge to go take a snooze or somthing :)  But no .. really .. I am mostly enthusiastic most of the time about our new unity8 desktop. I think some real kewl and unique things will come to the forefront. I am not all that concerned about the apps store .. etc.. but I really like the libertine scope. It makes computering very simple yet intriguing and I think intrigue will motivate others to explore and discover.

Regards..

---

### Post by seeker5528 on 2016-09-03
First problem I had, when attempting to run an app, outline of a window, poof, no app.

Found [http://mhall119.com/2016/05/dogfooding-unity-8](http://mhall119.com/2016/05/dogfooding-unity-8) containing this tidbit....

sudo systemctl enable cgmanager

Theory being that previous attempts to play with Unity 8 left some configuration stuff that resulted in cgmanager being disabled.

Second problem, some error message about no being able to create a temporary file causing libertine to fail creating a container. 
Found [https://lists.linuxcontainers.org/pipermail/lxc-users/2015-July/009761.html](https://lists.linuxcontainers.org/pipermail/lxc-users/2015-July/009761.html)

"The issue is caused by pam_tmpdir.  The purpose of the pam module is
to create a secure per-user tmpdir.  The directory perms end up being
0700 which denies everyone except for the user (and root)."
.
.
.
"Workaround 1: Remove pam_tmpdir although it has its uses.  For Ubuntu
the package is libpam-tmpdir.  It is pulled in as a recommend to tmux
usually."

In addition to removing pam_tmpdir, I also removed tmux, since it's not something I use and don't know any reason for it to be installed.

Later, Seeker

---

### Post by enricobe on 2016-09-10
This is what I see from Unity8.

[ATTACH=CONFIG]271055[/ATTACH]

The scopes app doesn't work at all for me... Anyway, I think that Unity 8 will be stable and really usable in many years :(

---

### Post by ventrical on 2016-09-11
> **enricobe said:**
> This is what I see from Unity8.

[ATTACH=CONFIG]271055[/ATTACH]

The scopes app doesn't work at all for me... Anyway, I think that Unity 8 will be stable and really usable in many years :(

Yes.. his is what has happened to me continually with ppas  or without ppas, on 16.04 and 16.10 installs. Any given update/upgrade will rip out all the scopes but I have seen this in testing with unity7 and nVidia back many cycles.  It is frustrating that just when you tweak a working unity8 desktop to work with some  functionality it gets ripped out out of the desktop.

---

### Post by enricobe on 2016-09-12
> **ventrical said:**
> Yes.. his is what has happened to me continually with ppas  or without ppas, on 16.04 and 16.10 installs. Any given update/upgrade will rip out all the scopes but I have seen this in testing with unity7 and nVidia back many cycles.  It is frustrating that just when you tweak a working unity8 desktop to work with some  functionality it gets ripped out out of the desktop.

Some months ago (or maybe some years...) I've tried a Unity 8 desktop ISO (I remember it was called Ubuntu Next, but I may be wrong) and the scopes worked fine that time. Do you think this problem can be due to a conflict between Unity 7 and Unity 8?

---

### Post by ventrical on 2016-09-12
All I know is that Mark has affirmed that he is committed to getting the job done, to have  a working unity8 by release time (16.10) . This type of major breakage is expected around this time of the development cycle.  Canonical has about 90 developers committed to just working on the unity8 desktop, at least that is how I understood Marks public comment on the issue.

  I have several install with varied degrees of success. Some , the apps store will work. Libertine will work really well on both nVidia and Intel based graphics but then , out of the blue , the scopes get ripped out and I can't seem to get them back so I settle for fresh installs which seem to solve the problem. The ppa is still releasing updates but I am using both ppa based installs and non ppa based installs .. so I guess we just have to keep updating/upgrading .. maybe even turn off proposed repos.

Regards..

---

### Post by enricobe on 2016-09-12
> **ventrical said:**
> All I know is that Mark has affirmed that he is committed to getting the job done, to have  a working unity8 by release time (16.10) . This type of major breakage is expected around this time of the development cycle.  Canonical has about 90 developers committed to just working on the unity8 desktop, at least that is how I understood Marks public comment on the issue.

I hope they can do it. unity8+mir is a big step forward (like Wayland) and I hope they can be used everyday as soon as possible.

EDIT: sorry for triple post I had connection problems!!!! Can a mod delete the duplicates? Thank you

---

### Post by cariboo on 2016-09-12
moved the extra posts to the jail.

---

### Post by ventrical on 2016-09-12
> **enricobe said:**
> I hope they can do it. unity8+mir is a big step forward (like Wayland) and I hope they can be used everyday as soon as possible.

EDIT: sorry for triple post I had connection problems!!!! Can a mod delete the duplicates? Thank you


Only my assumptions but you had asked earlier if there might be a problem between unity8 and unity7 desktop experience. Obviously this is the case.  It has been a real feat  using V chip technology to run Xorg and xmir concurrently with different sessions of containers running seperatley from each other while xmir and unity8-system-compositor is running unity8 concurrently also. Scopes within unity8 will have issues with scopes in unity7 and vis a versa. There could be some depends at this stage of the game where the only way to bootstrap the scopes is to remove them entirely from unity8. This of course takes all Libertine created scopes and containers along with it.

What we are seeing  is what we should expect to see during this convergence process. It may prove out to be that Unity8 may have to be a separate DE running standalone. We had done some testing with Ubuntu Next which was Ubuntu Personal DE which was a standalone image using snappy core.

  So the conventional wisdom with a unity8 personal snappy image would be the  right way to ad all the stacks and not as a shim-through using the the Unity greeter. This is where systemd is really  causing dysfunction-conjunctions between the two DEs. Also .. nVidia drivers (nouveau) are most likely in need of serious mark-up and this may be a big problem with running xorg and xmir concurrently. These are my 2 cents as I see it atm. A good positive note in all of this... if you are seeing breakage then you must be doing something right :)

Regards..


Regards..

---

### Post by ventrical on 2016-09-12
I can get synaptic package manager now in containers running from xterm using:
```

sudo synaptic

```

---

### Post by ventrical on 2016-09-12
> **enricobe said:**
> I hope they can do it. unity8+mir is a big step forward (like Wayland) and I hope they can be used everyday as soon as possible.

EDIT: sorry for triple post I had connection problems!!!! Can a mod delete the duplicates? Thank you

You can try this and see what you get:

```

sudo apt-get install scopes*

```

Here is what I get on my yakkety install..

```

ventrical@ventrical-System-Product-Name:~$ sudo apt-get install scopes*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libscope-upper-perl' for regex 'scopes*'
Note, selecting 'cscope-el' for regex 'scopes*'
Note, selecting 'astro-telescopecontrol' for regex 'scopes*'
Note, selecting 'unity-scope-click-init-departments' for regex 'scopes*'
Note, selecting 'unity-scope-firefoxbookmarks' for regex 'scopes*'
Note, selecting 'unity-scope-askubuntu' for regex 'scopes*'
Note, selecting 'python3-scope-harness' for regex 'scopes*'
Note, selecting 'unity-scope-yahoostock' for regex 'scopes*'
Note, selecting 'unity-scope-tool' for regex 'scopes*'
Note, selecting 'unity-scope-virtualbox' for regex 'scopes*'
Note, selecting 'libertine-scope' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-10' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-11' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-12' for regex 'scopes*'
Note, selecting 'unity-scope-mediascanner2' for regex 'scopes*'
Note, selecting 'libunity-scopes-qt0.2' for regex 'scopes*'
Note, selecting 'll-scope' for regex 'scopes*'
Note, selecting 'unity-scopes-json-def' for regex 'scopes*'
Note, selecting 'unity-scope-gmusicbrowser' for regex 'scopes*'
Note, selecting 'libunity-scopes-cli' for regex 'scopes*'
Note, selecting 'unity-scope-imdb' for regex 'scopes*'
Note, selecting 'tscope' for regex 'scopes*'
Note, selecting 'unity-scope-github' for regex 'scopes*'
Note, selecting 'libunity-scopes-dev' for regex 'scopes*'
Note, selecting 'libunity-scopes-doc' for regex 'scopes*'
Note, selecting 'unity-scope-audacious' for regex 'scopes*'
Note, selecting 'libb-hooks-endofscope-perl' for regex 'scopes*'
Note, selecting 'unity-scope-video-remote' for regex 'scopes*'
Note, selecting 'diffoscope' for regex 'scopes*'
Note, selecting 'dicomscope-doc' for regex 'scopes*'
Note, selecting 'unity-china-photo-scope' for regex 'scopes*'
Note, selecting 'unity-scope-onlinemusic' for regex 'scopes*'
Note, selecting 'unity-scope-gourmet' for regex 'scopes*'
Note, selecting 'unity-scope-manpages' for regex 'scopes*'
Note, selecting 'unity-scopes-runner' for regex 'scopes*'
Note, selecting 'unity-scope-colourlovers' for regex 'scopes*'
Note, selecting 'threadscope' for regex 'scopes*'
Note, selecting 'libanyevent-http-scopedclient-perl' for regex 'scopes*'
Note, selecting 'unity-scope-zotero' for regex 'scopes*'
Note, selecting 'xcscope-el' for regex 'scopes*'
Note, selecting 'unity-scope-click-departmentsdb' for regex 'scopes*'
Note, selecting 'unity-scope-gdrive' for regex 'scopes*'
Note, selecting 'libunity-scopes0' for regex 'scopes*'
Note, selecting 'libunity-scopes1' for regex 'scopes*'
Note, selecting 'libunity-scopes2' for regex 'scopes*'
Note, selecting 'libunity-scopes3' for regex 'scopes*'
Note, selecting 'unity-scope-launchpad' for regex 'scopes*'
Note, selecting 'unity-scope-yelp' for regex 'scopes*'
Note, selecting 'geany-plugin-scope' for regex 'scopes*'
Note, selecting 'unity-scope-asklibreoffice' for regex 'scopes*'
Note, selecting 'unity-scopes-impl' for regex 'scopes*'
Note, selecting 'unity-china-music-scope' for regex 'scopes*'
Note, selecting 'unity-scope-click' for regex 'scopes*'
Note, selecting 'unity-scope-sumo' for regex 'scopes*'
Note, selecting 'trydiffoscope' for regex 'scopes*'
Note, selecting 'cscope' for regex 'scopes*'
Note, selecting 'unity-scope-soundcloud' for regex 'scopes*'
Note, selecting 'unity-scope-home' for regex 'scopes*'
Note, selecting 'unity-scope-googlenews' for regex 'scopes*'
Note, selecting 'libscope-harness-dev' for regex 'scopes*'
Note, selecting 'unity-scope-musique' for regex 'scopes*'
Note, selecting 'xoscope' for regex 'scopes*'
Note, selecting 'unity-scope-openclipart' for regex 'scopes*'
Note, selecting 'unity-scope-calculator' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-0' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-1' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-4' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-6' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-7' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-8' for regex 'scopes*'
Note, selecting 'unity-scopes-impl-9' for regex 'scopes*'
Note, selecting 'libdicomscope-jni' for regex 'scopes*'
Note, selecting 'unity-china-video-scope' for regex 'scopes*'
Note, selecting 'libunity-scopes-json-def-phone' for regex 'scopes*'
Note, selecting 'libscope-harness3' for regex 'scopes*'
Note, selecting 'libscope-guard-perl' for regex 'scopes*'
Note, selecting 'unity-scope-musicstores' for regex 'scopes*'
Note, selecting 'bitscope' for regex 'scopes*'
Note, selecting 'unity-plugin-scopes' for regex 'scopes*'
Note, selecting 'unity-scope-openweathermap' for regex 'scopes*'
Note, selecting 'unity-scope-deviantart' for regex 'scopes*'
Note, selecting 'unity-scope-sshsearch' for regex 'scopes*'
Note, selecting 'unity-scopes-master' for regex 'scopes*'
Note, selecting 'libunity-scopes1.0' for regex 'scopes*'
Note, selecting 'unity-scope-diodon' for regex 'scopes*'
Note, selecting 'libunity-scopes-json-def-desktop' for regex 'scopes*'
Note, selecting 'dicomscope' for regex 'scopes*'
Note, selecting 'unity-scope-tomboy' for regex 'scopes*'
Note, selecting 'unity-scope-click-autopilot' for regex 'scopes*'
Note, selecting 'unity-scope-gdocs' for regex 'scopes*'
Note, selecting 'unity-scope-gallica' for regex 'scopes*'
Note, selecting 'unity-scope-scopes' for regex 'scopes*'
Note, selecting 'unity-scopes-master-default' for regex 'scopes*'
Note, selecting 'seascope' for regex 'scopes*'
Note, selecting 'unity-scope-texdoc' for regex 'scopes*'
Note, selecting 'unity-scope-clementine' for regex 'scopes*'
Note, selecting 'unity-scope-devhelp' for regex 'scopes*'
Note, selecting 'unity-scope-chromiumbookmarks' for regex 'scopes*'
Note, selecting 'libconfig-scoped-perl' for regex 'scopes*'
Note, selecting 'jack-oscrolloscope' for regex 'scopes*'
Note, selecting 'libunity-scopes-qt-dev' for regex 'scopes*'
Note, selecting 'libunity-scopes-qt-doc' for regex 'scopes*'
Note, selecting 'kscope' for regex 'scopes*'
Note, selecting 'unity-lens-music' instead of 'unity-scope-musicstores'
Note, selecting 'unity-scopes-master-default' instead of 'unity-scopes-master'
Note, selecting 'unity-scope-home' instead of 'unity-scope-asklibreoffice'
Note, selecting 'unity-scope-home' instead of 'unity-scope-askubuntu'
Note, selecting 'unity-scope-home' instead of 'unity-scope-sumo'
Note, selecting 'bitmeter' instead of 'bitscope'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-0'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-1'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-10'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-11'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-12'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-4'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-6'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-7'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-8'
Note, selecting 'unity-plugin-scopes' instead of 'unity-scopes-impl-9'
libunity-scopes-json-def-desktop is already the newest version (7.1.4+16.10.20160516-0ubuntu1).
libunity-scopes-json-def-desktop set to manually installed.
unity-lens-music is already the newest version (6.9.1+16.04-0ubuntu1).
unity-lens-music set to manually installed.
unity-scope-calculator is already the newest version (0.1+14.04.20140328-0ubuntu1).
unity-scope-calculator set to manually installed.
unity-scope-chromiumbookmarks is already the newest version (0.1+13.10.20130723-0ubuntu1).
unity-scope-chromiumbookmarks set to manually installed.
unity-scope-colourlovers is already the newest version (0.1+13.10.20130723-0ubuntu1).
unity-scope-colourlovers set to manually installed.
unity-scope-devhelp is already the newest version (0.1+14.04.20140328-0ubuntu1).
unity-scope-devhelp set to manually installed.
unity-scope-firefoxbookmarks is already the newest version (0.1+13.10.20130809.1-0ubuntu1).
unity-scope-firefoxbookmarks set to manually installed.
unity-scope-gdrive is already the newest version (0.9+16.04.20151125-0ubuntu1).
unity-scope-gdrive set to manually installed.
unity-scope-home is already the newest version (6.8.2+16.04.20160212.1-0ubuntu1).
unity-scope-home set to manually installed.
unity-scope-manpages is already the newest version (3.0+14.04.20140324-0ubuntu1).
unity-scope-manpages set to manually installed.
unity-scope-openclipart is already the newest version (0.1+13.10.20130723-0ubuntu1).
unity-scope-openclipart set to manually installed.
unity-scope-texdoc is already the newest version (0.1+14.04.20140328-0ubuntu1).
unity-scope-texdoc set to manually installed.
unity-scope-tomboy is already the newest version (0.1+13.10.20130723-0ubuntu1).
unity-scope-tomboy set to manually installed.
unity-scope-video-remote is already the newest version (0.3.15+16.04.20160212.1-0ubuntu1).
unity-scope-video-remote set to manually installed.
unity-scope-virtualbox is already the newest version (0.1+13.10.20130723-0ubuntu1).
unity-scope-virtualbox set to manually installed.
unity-scope-yelp is already the newest version (0.1+13.10.20130723-0ubuntu1).
unity-scope-yelp set to manually installed.
unity-scope-zotero is already the newest version (0.1+13.10.20130723-0ubuntu1).
unity-scope-zotero set to manually installed.
unity-scopes-master-default is already the newest version (6.8.2+16.04.20160212.1-0ubuntu1).
unity-scopes-master-default set to manually installed.
unity-scopes-runner is already the newest version (7.1.4+16.10.20160516-0ubuntu1).
unity-scopes-runner set to manually installed.
libertine-scope is already the newest version (1.3.2+16.10.20160812-0ubuntu1).
libunity-scopes1.0 is already the newest version (1.0.6+16.10.20160617-0ubuntu1).
libunity-scopes1.0 set to manually installed.
unity-plugin-scopes is already the newest version (0.5.7+16.10.20160624.2-0ubuntu2).
unity-plugin-scopes set to manually installed.
unity-scope-click is already the newest version (0.1.1+16.10.20160808-0ubuntu1).
unity-scope-click set to manually installed.
unity-scope-click-departmentsdb is already the newest version (0.1.1+16.10.20160808-0ubuntu1).
unity-scope-click-departmentsdb set to manually installed.
unity-scope-mediascanner2 is already the newest version (0.2+16.10.20160620.1-0ubuntu2).
unity-scope-mediascanner2 set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libunity-scopes-json-def-desktop : Conflicts: unity-scopes-json-def
                                    Conflicts: unity-scopes-json-def:i386
 libunity-scopes-json-def-phone : Conflicts: unity-scopes-json-def
                                  Conflicts: unity-scopes-json-def:i386
 unity-scope-home : Conflicts: unity-scope-deviantart
                    Conflicts: unity-scope-gallica
                    Conflicts: unity-scope-github
                    Conflicts: unity-scope-googlenews
                    Conflicts: unity-scope-openweathermap
                    Conflicts: unity-scope-soundcloud
                    Conflicts: unity-scope-yahoostock
E: Unable to correct problems, you have held broken packages.
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2016-09-13
I was able to use synaptic to download some packages to fix broken depends but this has now given me total blackspace. Not even the 'arrow of mir'. This on nVidia  graphical form factor.

unity7 works just fine.

Regards..

---

### Post by enricobe on 2016-09-13
> **ventrical said:**
> You can try this and see what you get:

```

sudo apt-get install scopes*

```

Here is what I get on my yakkety install..


I got the same final errors. It is in Italian, but I think you can understand it well

```

Lettura elenco dei pacchetti...
Generazione albero delle dipendenze...
Lettura informazioni sullo stato...
libunity-scopes-json-def-desktop is already the newest version (7.1.4+16.10.20160516-0ubuntu1).
È stato impostato libunity-scopes-json-def-desktop per l'installazione manuale.
unity-lens-music is already the newest version (6.9.1+16.04-0ubuntu1).
È stato impostato unity-lens-music per l'installazione manuale.
unity-scope-calculator is already the newest version (0.1+14.04.20140328-0ubuntu1).
È stato impostato unity-scope-calculator per l'installazione manuale.
unity-scope-chromiumbookmarks is already the newest version (0.1+13.10.20130723-0ubuntu1).
È stato impostato unity-scope-chromiumbookmarks per l'installazione manuale.
unity-scope-colourlovers is already the newest version (0.1+13.10.20130723-0ubuntu1).
È stato impostato unity-scope-colourlovers per l'installazione manuale.
unity-scope-devhelp is already the newest version (0.1+14.04.20140328-0ubuntu1).
È stato impostato unity-scope-devhelp per l'installazione manuale.
unity-scope-firefoxbookmarks is already the newest version (0.1+13.10.20130809.1-0ubuntu1).
È stato impostato unity-scope-firefoxbookmarks per l'installazione manuale.
unity-scope-home is already the newest version (6.8.2+16.04.20160212.1-0ubuntu1).
È stato impostato unity-scope-home per l'installazione manuale.
unity-scope-manpages is already the newest version (3.0+14.04.20140324-0ubuntu1).
È stato impostato unity-scope-manpages per l'installazione manuale.
unity-scope-openclipart is already the newest version (0.1+13.10.20130723-0ubuntu1).
È stato impostato unity-scope-openclipart per l'installazione manuale.
unity-scope-texdoc is already the newest version (0.1+14.04.20140328-0ubuntu1).
È stato impostato unity-scope-texdoc per l'installazione manuale.
unity-scope-tomboy is already the newest version (0.1+13.10.20130723-0ubuntu1).
È stato impostato unity-scope-tomboy per l'installazione manuale.
unity-scope-video-remote is already the newest version (0.3.15+16.04.20160212.1-0ubuntu1).
È stato impostato unity-scope-video-remote per l'installazione manuale.
unity-scope-virtualbox is already the newest version (0.1+13.10.20130723-0ubuntu1).
È stato impostato unity-scope-virtualbox per l'installazione manuale.
unity-scope-yelp is already the newest version (0.1+13.10.20130723-0ubuntu1).
È stato impostato unity-scope-yelp per l'installazione manuale.
unity-scope-zotero is already the newest version (0.1+13.10.20130723-0ubuntu1).
È stato impostato unity-scope-zotero per l'installazione manuale.
unity-scopes-master-default is already the newest version (6.8.2+16.04.20160212.1-0ubuntu1).
È stato impostato unity-scopes-master-default per l'installazione manuale.
unity-scopes-runner is already the newest version (7.1.4+16.10.20160516-0ubuntu1).
È stato impostato unity-scopes-runner per l'installazione manuale.
libunity-scopes1.0 is already the newest version (1.0.6+16.10.20160617-0ubuntu1).
È stato impostato libunity-scopes1.0 per l'installazione manuale.
unity-plugin-scopes is already the newest version (0.5.7+16.10.20160624.2-0ubuntu2).
È stato impostato unity-plugin-scopes per l'installazione manuale.
unity-scope-click is already the newest version (0.1.1+16.10.20160808-0ubuntu1).
È stato impostato unity-scope-click per l'installazione manuale.
unity-scope-click-departmentsdb is already the newest version (0.1.1+16.10.20160808-0ubuntu1).
È stato impostato unity-scope-click-departmentsdb per l'installazione manuale.
unity-scope-mediascanner2 is already the newest version (0.2+16.10.20160620.1-0ubuntu2).
È stato impostato unity-scope-mediascanner2 per l'installazione manuale.
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
 libunity-scopes-json-def-desktop : Va in conflitto: unity-scopes-json-def
                                    Va in conflitto: unity-scopes-json-def:i386
 libunity-scopes-json-def-phone : Va in conflitto: unity-scopes-json-def
                                  Va in conflitto: unity-scopes-json-def:i386
 unity-scope-home : Va in conflitto: unity-scope-deviantart
                    Va in conflitto: unity-scope-gallica
                    Va in conflitto: unity-scope-github
                    Va in conflitto: unity-scope-googlenews
                    Va in conflitto: unity-scope-openweathermap
                    Va in conflitto: unity-scope-soundcloud
                    Va in conflitto: unity-scope-yahoostock

```

---

### Post by ventrical on 2016-09-13
Ok.. thanks.

I downloaded the daily amd64 ubuntu .iso and fresh hard installed. I installed unity8 and libertine (non ppa) and I am still getting scopes blackspace. I think there is serious problems with nVidia drivers.  Basically , unity8 is useless on nVidia based graphics form factors.

 Please disregard my last verbose post. Unity8 is broke. Period.

 I will try fresh install of the daily on Intel Xeon based graphics.

Regards..

---

### Post by enricobe on 2016-09-13
> **ventrical said:**
> Ok.. thanks.

I downloaded the daily amd64 ubuntu .iso and fresh hard installed. I installed unity8 and libertine (non ppa) and I am still getting scopes blackspace. I think there is serious problems with nVidia drivers.  Basically , unity8 is useless on nVidia based graphics form factors.

 Please disregard my last verbose post. Unity8 is broke. Period.

 I will try fresh install of the daily on Intel Xeon based graphics.

Regards..

I have and AMD graphic card

---

### Post by ventrical on 2016-09-13
Actually the daily is worse on Intel based form factors. Locks right up, scopes black space and who knows what else is busted.

Regards..

---

