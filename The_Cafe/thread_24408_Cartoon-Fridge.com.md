---
title: "Cartoon-Fridge.com"
date: 2005-04-06
forum: The Cafe
---

### Post by BWF89 on 2005-04-06
Just install the Firefox plugin and your good to go:
[http://www.cartoon-fridge.com/](http://www.cartoon-fridge.com/)

I'm not sure if this works for Linux but you can give it a try

---

### Post by totalshredder on 2005-04-06
DARN YOU!! You're making me want to go back to windows.
Must resist the temptation.


Good idea for a website though! I really like it!! Maybe you could use wine?

Luke

---

### Post by HungSquirrel on 2005-04-06
Unfortunately, the plugin is a DLL file.  I tried to be sneaky and wine it to get the plugin, but I don't think the DLL will work and I'm not crazy enough to try.  :)

---

### Post by BWF89 on 2005-04-07
[QUOTE=HungSquirrel]Unfortunately, the plugin is a DLL file.  I tried to be sneaky and wine it to get the plugin, but I don't think the DLL will work and I'm not crazy enough to try.  :)[/QUOTE]
I'll send the owner of the site an email (or post on the forums) asking him to release the plugin under the GPL. Then mabye we could make codecs for Totem or Mplayer or port the plugin to Un*x.

---

### Post by jdodson on 2005-04-07
not sure about the legalities of the site, but it is really cool though.

---

### Post by wmcbrine on 2005-04-07
Looking at the source for the popup page, it appears that the plugin is (or is based on) VP3, which is already open source. But I haven't found a Linux plugin yet.

---

### Post by jdodson on 2005-04-07
[QUOTE=wmcbrine]Looking at the source for the popup page, it appears that the plugin is (or is based on) VP3, which is already open source. But I haven't found a Linux plugin yet.[/QUOTE]

**cough** look at page source, **cough** search for .nsv file.... **hack** download file....

**cough** file plays fine in **WHEEZE** vlc.

---

### Post by gylf on 2005-04-07
[QUOTE=BWF89]I'll send the owner of the site an email (or post on the forums) asking him to release the plugin under the GPL. Then mabye we could make codecs for Totem or Mplayer or port the plugin to Un*x.[/QUOTE]

[Someone supposedly got it working using wine in this thread.](http://www.cartoon-fridge.com/forums/viewtopic.php?t=47)

EDIT: he doesn't elaborate on how he did it, but I'm guessing he's running firefox w/ wine.

As for the legality, here is their answer: 

"Although I don't want to get into details, we are working on moving all of the servers to countries with lax copywrite laws where we face a smaller chance of any networks coming after us."

---

### Post by wmcbrine on 2005-04-08
OK, either VLC or MPlayer can handle this, which means their respective plugins can, too; they just need the appropriate MIME type added. So, I went and grabbed the latest source from [http://mplayerplug-in.sf.net/](http://mplayerplug-in.sf.net/) , thinking to patch it -- and I found that it's already there, in version 2.80. The version in the repositories is a little behind, at 2.70, and doesn't have this yet.

Now stop with all the Windows talk.  :p

---

### Post by kleeman on 2005-04-08
Good call mplayerplug-in 2.80 worked for me on this site! To compile it you need mozilla-dev and libxpm-dev packages installed as well as the standard dev packages.
The interface for 2.80 is better also as it has controls with the right mouse click.

---

### Post by [CF]Peter on 2005-04-08
Hey Guys,

I saw your link in my refer logs, and since I don't use Linux as a desktop (just as a server) I was hoping one of you could explain the best way to setup MPlayer so I could relay it to those Linux of Apple users out there.

Appriciated.

And for those of you whose first thought that comes to mind is "COPYRIGHTS" - Jesus man, just enjoy some toons  \\:D/ 

hehe, Thanks.

Peter

---

### Post by telmo on 2005-04-08
Coughing is good for your health! LOL

---

### Post by endless on 2005-04-22
[QUOTE=jdodson]**cough** look at page source, **cough** search for .nsv file.... **hack** download file....

**cough** file plays fine in **WHEEZE** vlc.[/QUOTE]
Well, your coughing solution did work until recently where the same approach (opening it in vlc) gives me some 404 error: apparently accessing the streams this way automatically redirects (http 302) me to a non-existing url, so it is impossible to see them this way. Anybody know a solution, because I really love ubuntu in combination with this site! \\:D/ 

Thanks in advance!

---

### Post by kleeman on 2005-04-22
As said earlier in the thread: compile mplayerplug-in 2.80. This will display nsv files just like regular movies in firefox

---

### Post by TravisNewman on 2005-04-22
There are a few broken links there though. Particularly (for me) when trying to watch the Clerks toons

---

### Post by syltty on 2005-04-27
Cartoon-fridge appears to be down. If you want to watch cartoon streams, please try my program [lintelkku](http://lintelkku.sourceforge.net). With Lintelkku you get the same streams as you would get with the Winamp in windows. It is still on beta stage and some of the streams may not work but hey, it's better than nothing  :)

---

