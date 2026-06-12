---
title: "google-music-manager on a Ubuntu Server without GUI, only CLI"
date: 2012-02-11
forum: Server Platforms
---

### Post by nukleuzN on 2012-02-11
Hi.

I'm using Ubuntu Server 11.04 on a media server solution at home. This media server streams my music wireless at home through various proctols; DAAP, DLNA  etc.

But... I would love to stream my music with the Google Music framework as well - since I have an Android 4.0 based phone wich have Google Music Player pre-installed. But this seems to be a mess on system that is only CLI based. 
```
joachim@custom-media-server:/tmp$ sudo dpkg -i gmm.deb(Reading database ... 63222 files and directories currently installed.)
Preparing to replace google-musicmanager-beta 1.0.24.7712-r0 (using gmm.deb) ...
Unpacking replacement google-musicmanager-beta ...
dpkg: dependency problems prevent configuration of google-musicmanager-beta:
 google-musicmanager-beta depends on libqt4-network (>= 4:4.5.3); however:
  Package libqt4-network is not installed.
 google-musicmanager-beta depends on libqtcore4 (>= 4:4.6.1); however:
  Package libqtcore4 is not installed.
 google-musicmanager-beta depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not installed.
dpkg: error processing google-musicmanager-beta (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 google-musicmanager-beta
joachim@custom-media-server:/tmp$ sudo apt-get install libqt4-network libqtcore4 libqtgui4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libqt4-network : Depends: libqt4-dbus (= 4:4.7.2-0ubuntu6.3) but it is not going to be installed
 libqtgui4 : Depends: libaudio2 but it is not going to be installed
             Depends: libmng1 (>= 1.0.10) but it is not going to be installed
             Recommends: appmenu-qt but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

DAAP works OK when Im not at home, but the DAAP Music Player for Android or Banshee DAAP-plugin is not working well. Bad caching, not easy to create "offline playlists". Probably a limitation within the DAAP-protocol.

Anyone knows if there is possible to run/sync the Google Music Manager from a server (cli-based)? Dont want to store my music on both my laptop and my server. My laptop only has a 120 GB SSD harddrive, and I need my space to other more important files.

**EDIT**: Actually. I just want the "sync to google music cloud" option, not to play music from the server itself. The server doesn't have any speakers connected to it.

---

### Post by swmiller6 on 2012-03-05
I installed the google-musicmanager deb file (run this command to get dependencies "sudo apt-get -f install") then add this command to cron
```
google-musicmanager -a <gmail address> -p <password> -s <path-to-music-to-upload> -m <name of my server> x11vnc -display :2 -bg -nopw -listen localhost -xkb
```
It is working really well, I also use beets to tag my collection which works awesome.

---

### Post by nukleuzN on 2012-03-25
Hi,

Thanx for your reply! Doesn't seem to work, unfortunally!

This is how my crontab looks like:
```
1,21,41 * * * * google-musicmanager -a MyUsername@gmail.com -p MyPassword -s /media/MiniDLNA/DLNA/Music -m CustomMediaServer  x11vnc -display :2 -bg -nopw -listen localhost -xkb
```

When I run the command in CLI: 
```
google-musicmanager -a MyUsername@gmail.com -p MyPassword -s /media/MiniDLNA/DLNA/Music -m CustomMediaServer  x11vnc -display :2 -bg -nopw -listen localhost -xkb
```
nothing seems to happens. No output!

Any clue on how I can debug?

---

### Post by nukleuzN on 2012-03-26
Hmm. Needed to install x11vnc:

```
sudo apt-get install x11vnc
```

And I also used a bash-script, instead:

[LIST]
[*][http://development.giaever.org/pastebin/Ubuntu/google-musicmanager/install-gmm-headless.sh](http://development.giaever.org/pastebin/Ubuntu/google-musicmanager/install-gmm-headless.sh)
[*][http://development.giaever.org/pastebin/Ubuntu/google-musicmanager/gmm-headless-script.sh](http://development.giaever.org/pastebin/Ubuntu/google-musicmanager/gmm-headless-script.sh)
[/LIST]

---

### Post by swmiller6 on 2012-06-08
Is this setup still working for you? I took a update of google music manager beta and now it no longer uploads the music I add to my google account.

---

### Post by sanicki on 2012-10-02
> **swmiller6 said:**
> Is this setup still working for you? I took a update of google music manager beta and now it no longer uploads the music I add to my google account.

No longer working for me either.

---

