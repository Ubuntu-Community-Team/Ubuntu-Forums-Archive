---
title: "Apparmor blocked flash"
date: 2016-05-21
forum: Security
---

### Post by f5b059c3 on 2016-05-21
Hi,

i enforced */etc/apparmor.d/usr.bin.firefox* and everything worked fine for years until a couple of weeks ago flash stopped working on some sites (yout**e for instance worked fine; other sites would just show white boxes where flash should be). I thought it was because of my heavy use of addons like noscript etc., but after a clean re-install of ubuntu, several of firefox and flash as well as several new firefox-profiles created with and w/out noscript, all to no avail, i disabled */etc/apparmor.d/usr.bin.firefox *and voilá, everything is "fine".

before, i got messages like this one:
```
May 21 18:04:38 host kernel: [ 1232.422919] audit: type=1400 audit(1463846678.124:1857188): apparmor="DENIED" operation="mknod" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/shm/org.chromium.KgsmJL" pid=3376 comm="plugin-containe" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
```

and now did an aa-logprof which added
  ```
/dev/shm/org.chromium.KgsmJL w,
```
which i had to change to
  ```
/dev/shm/org.chromium.* rw,
```
in order for flash to work again w/out disabling firefox's apparmor completely...

so for anyone with similar problems, try this. but more importantly: what the hell did i allow rw to there?? :P and why was it suddenly necessary?


i would very much appreciate any insights you might be able to share!
thanks a lot!! :)


ps: i maybe should also mention that apart from the following additional line */etc/apparmor.d/usr.bin.firefox* was always in its original state: */etc/adobe/* r,* (this allegedly has some privacy enhancing effects, as suggested here: [http://ubuntuforums.org/showthread.php?t=2230541](http://ubuntuforums.org/showthread.php?t=2230541)) which i also had configured before, not distrubing anything. i moved the .cfg and removed the */etc/adobe/* r* from */etc/apparmor.d/usr.bin.firefox* to see if it caused flash to break - it did not.

---

### Post by f5b059c3 on 2016-08-17
Hmmmm. Have had this issue now with two additional machines, both running Ubuntu 14.04 and Firefox with the apparmor profile enabled... any ideas? This seems to occur only on my machines? ;)

---

### Post by &amp;KyT$0P# on 2016-08-17
Are you using freshplayerplugin Flash?

---

### Post by f5b059c3 on 2016-08-17
Nope, default flashplugin-installer

---

### Post by ajgreeny on 2016-08-17
It might be worth enabling the canonical partner repos if not already in use and then installing **adobe-flashplugin** which will automatically remove **flashplugin-installer**

If you also install the **browser-plugin-freshplayer-pepperflash** package you find you are now using flash version 22.0.0.209 in firefox, the same  as is used in chrome or chromium.

---

### Post by mook765 on 2016-08-24
I don't use flash anymore since I found this:
[https://addons.mozilla.org/en-US/firefox/addon/video-without-flash/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/video-without-flash/?src=ss)
Works just fine for me...

---

