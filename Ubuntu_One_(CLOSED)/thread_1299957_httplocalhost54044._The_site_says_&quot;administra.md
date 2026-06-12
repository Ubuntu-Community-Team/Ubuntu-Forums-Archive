---
title: "http://localhost:54044. The site says: &quot;administrator&quot;"
date: 2009-10-24
forum: Ubuntu One (CLOSED)
---

### Post by Merovius on 2009-10-24
I am getting this message every time I start Firefox and have traced it to something related to CouchDB called "Erlang"and "Beam" The full thing is: 

"A username and password are being requested by [http://localhost:54044](http://localhost:54044). The site says: "administrator""

Please see this thread for more information on my efforts so far.

[http://ubuntuforums.org/showthread.php?t=1299896](http://ubuntuforums.org/showthread.php?t=1299896)

I can see "Beam" running under system monitor. I can see from synaptic that "Erlang" & "Beam" are associated with CouchDB. CouchDB is associated with Ubuntu1 and Evolution.

I have used Joshua Hoover's instructions to remove and reinstall UbuntuOne. This had no effect. As it only happens under Firefox I believe it has to do with syncing favorites to U1

TIA for any help / ideas.

---

### Post by Merovius on 2009-10-25
This is what I get over and over,

[IMG]http://95whma.blu.livefilestore.com/y1pOLnen_CR34kFve_RWpjmTY5hjzSkXjqcjKZ3eqrq7UEnWRkb8CyU6IkDJBWPm8kNg_wlM60BK6ui9XdxCOyo1639hEbuamQj/Screenshot-Authentication%20Required.png[/IMG]

---

### Post by Merovius on 2009-10-25
Well, I was right about the connection to CouchDB etc. I uninstalled "bindwood" which has to do with syncing Firefox bookmarks and the login requests have stopped. Not sure how bindwood got installed to begin with. Might have done it myself. 

At least it has stopped. :guitar:

---

### Post by joshuahoover on 2009-10-26
> **Merovius said:**
> Well, I was right about the connection to CouchDB etc. I uninstalled "bindwood" which has to do with syncing Firefox bookmarks and the login requests have stopped. Not sure how bindwood got installed to begin with. Might have done it myself. 

At least it has stopped. :guitar:

This bug should be fixed: [https://bugs.edge.launchpad.net/ubuntu/+source/bindwood/+filebug](https://bugs.edge.launchpad.net/ubuntu/+source/bindwood/+filebug) You may need to update Karmic to get the latest Bindwood package and fix. If you enable Bindwood again and still receive the error, please file a bug report at: [https://bugs.edge.launchpad.net/ubuntu/+source/bindwood/+filebug](https://bugs.edge.launchpad.net/ubuntu/+source/bindwood/+filebug)

Thank you,

Joshua

---

### Post by Merovius on 2009-10-26
I will try to reinstall it tonight and see what happens.

Thanks!

---

### Post by Merovius on 2009-10-26
Reinstalled and updated via synaptic. Still asks for user name and password incessantly. Had to disable Bindwood.

Bug report: 461455  Duplicate of 444022

---

### Post by joshuahoover on 2009-10-27
> **Merovius said:**
> Reinstalled and updated via synaptic. Still asks for user name and password incessantly. Had to disable Bindwood.

Bug report: 461455  Duplicate of 444022

Did you do a complete system update? If not, you might want to try that. I have been unable to reproduce this bug with a completely up-to-date Karmic install.

Thank you,

Joshua

---

### Post by Merovius on 2009-10-27
I reinstalled from Synaptic what I had removed before. I ran system update and there was a bindwood update available. I installed all the available updates. No change. I enabled the addon in firefox and the password prompts started. I disabled and they stop. I told firefox to check for updates to my addons and it found none. I restarted the addon (and firefox as required) the password prompts come right back.

:confused:

It may well be that a clean install of Karmic is in order a few weeks from now. This is on a machine upgraded from Jaunty.

---

### Post by Merovius on 2009-10-28
I recieveed another Bindwood update last night 10/27 and installed it. This morning when I launched firefox I got the login windows again. I gues I will have to leave it disabled until I can get a chance to clean install.

---

### Post by manoriax on 2009-10-30
Besides - did anyone has got any success with the firefox-bookmark-sync-thingy until now?

---

### Post by Merovius on 2009-11-01
I have done a clean install and this issue has mostly been fixed. Firefox is constantly grayin out after bindwood install. Might be syncing my large number of bookmarks. 4 gray out while writing this. But no password prompts.

---

### Post by manoriax on 2009-11-01
Yeah, here too. Firefox just grays out and nothing seems to happen; is this normal?

---

### Post by Merovius on 2009-11-01
I don't think so. Unless it was busy syncing my favorites. I have a lot, so maybe. I marked this solved because I no longer get the original log in prompt error.

I have started another thread,

 [http://ubuntuforums.org/showthread.php?t=1309392](http://ubuntuforums.org/showthread.php?t=1309392)

This one is about the graying out stuff. Hopefully we will get some answers there.

---

