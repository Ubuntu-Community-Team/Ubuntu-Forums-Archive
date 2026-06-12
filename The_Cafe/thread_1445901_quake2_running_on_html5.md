---
title: "quake2 running on html5"
date: 2010-04-03
forum: The Cafe
---

### Post by madjr on 2010-04-03
on your browser and no plugins weeeeeeee!

video
[http://googlewebtoolkit.blogspot.com/2010/04/look-ma-no-plugin.html](http://googlewebtoolkit.blogspot.com/2010/04/look-ma-no-plugin.html)

---

### Post by dearingj on 2010-04-03
Are you sure that's not an April Fools joke? I mean, look at the date it was posted.

---

### Post by kaivalagi on 2010-04-03
Must be a really good hoax: [http://code.google.com/p/quake2-gwt-port/](http://code.google.com/p/quake2-gwt-port/)

I just pulled the source down but haven't looked much at it:
```
hg clone https://quake2-gwt-port.googlecode.com/hg/ quake2-gwt-port
```

from the readme:
```
Google's HTML5 port of Bytonic Software's Java port of Id Software's Quake II

To install and run: http://http://code.google.com/p/quake2-gwt-port/wiki/BuildingAndRunning
Eclipse setup: http://http://code.google.com/p/quake2-gwt-port/wiki/EclipseSetup

```

Niether of the 2 urls work though :-k

---

### Post by chriswyatt on 2010-04-03
It it is an April Fools joke it does look very convincing.

---

### Post by kaivalagi on 2010-04-03
> **chriswyatt said:**
> It it is an April Fools joke it does look very convincing.

Yeah, Google have got to be the best at April fools, they really put the effort in! I wonder if they have projects close to the end of March specifically for this...:)

---

### Post by Yes on 2010-04-03
> **kaivalagi said:**
> Must be a really good hoax: [http://code.google.com/p/quake2-gwt-port/](http://code.google.com/p/quake2-gwt-port/)

I just pulled the source down but haven't looked much at it:
```
hg clone https://quake2-gwt-port.googlecode.com/hg/ quake2-gwt-port
```

from the readme:
```
Google's HTML5 port of Bytonic Software's Java port of Id Software's Quake II

To install and run: http://http://code.google.com/p/quake2-gwt-port/wiki/BuildingAndRunning
Eclipse setup: http://http://code.google.com/p/quake2-gwt-port/wiki/EclipseSetup

```

Niether of the 2 urls work though :-k

They don't work cause you have an extra 'http://' in front of them.

---

### Post by kaivalagi on 2010-04-03
> **Yes said:**
> They don't work cause you have an extra 'http://' in front of them.

:lolflag: Whoops

So is it a hoax or not then...

Will I have to go through the whole process of building it to fins out it says "Haha April Fools". Admittedly it really doesn't look like a hoax to me, not now I have the correct URL (BTW the url was copied straight from the README file as was)

I'm running a dedicated server build now...

edit, success:
```
[INFO] 
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary:
[INFO] ------------------------------------------------------------------------
[INFO] GwtQuake .............................................. SUCCESS [2:43.416s]
[INFO] GwtQuake Client ....................................... SUCCESS [5:16.428s]
[INFO] GwtQuake Dedicated WebSocket Server ................... SUCCESS [2:48.578s]
[INFO] GwtQuake Demo Installer ............................... SUCCESS [6.225s]
[INFO] ------------------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESSFUL
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 10 minutes 55 seconds
[INFO] Finished at: Sat Apr 03 18:12:20 BST 2010
[INFO] Final Memory: 58M/284M
[INFO] ------------------------------------------------------------------------
```

edit2: I'm running a dedicated server now :) I just don't have a bloody browser that supports WebGL.......yet

Definitely NOT a hoax :lolflag:

---

### Post by madjr on 2010-04-03
> **kaivalagi said:**
> :lolflag: Whoops

So is it a hoax or not then...

Will I have to go through the whole process of building it to fins out it says "Haha April Fools". Admittedly it really doesn't look like a hoax to me, not now I have the correct URL (BTW the url was copied straight from the README file as was)

I'm running a dedicated server build now...

edit, success:
```
[INFO] 
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary:
[INFO] ------------------------------------------------------------------------
[INFO] GwtQuake .............................................. SUCCESS [2:43.416s]
[INFO] GwtQuake Client ....................................... SUCCESS [5:16.428s]
[INFO] GwtQuake Dedicated WebSocket Server ................... SUCCESS [2:48.578s]
[INFO] GwtQuake Demo Installer ............................... SUCCESS [6.225s]
[INFO] ------------------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESSFUL
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 10 minutes 55 seconds
[INFO] Finished at: Sat Apr 03 18:12:20 BST 2010
[INFO] Final Memory: 58M/284M
[INFO] ------------------------------------------------------------------------
```

edit2: I'm running a dedicated server now :) I just don't have a bloody browser that supports WebGL.......yet

Definitely NOT a hoax :lolflag:

awesome

hey i dont post HOAXES!

well not that many anyways ^^

which browsers support webGL?

in the vid is safary but then any webkit browser will do then?

---

### Post by kaivalagi on 2010-04-03
> **madjr said:**
> awesome

hey i dont post HOAXES!

well not that many anyways ^^

which browsers support webGL?

in the vid is safary but then any webkit browser will do then?

It provides this url for a list when it doesn't work: [http://code.google.com/p/quake2-gwt-port/wiki/CompatibleBrowsers](http://code.google.com/p/quake2-gwt-port/wiki/CompatibleBrowsers)

I have chromium installed but it can't be the latest, which I find a bit strange as I am running Arch....and I have run it with the suggested options...

---

