---
title: "Beryl 0.1.1"
date: 2006-10-21
forum: The Cafe
---

### Post by PriceChild on 2006-10-21
[SIZE=2]dearie me....
[/SIZE] [SIZE=2]you keep thinking that beryl won't get any smoother on your system

[/SIZE] [SIZE=2]then [B]BAM!

[/B][/SIZE] [SIZE=2]they bring out 0.1.1 and incredibly it is!

Just got the latest version today.

I was a bit hesitant because of a few reports of broken beryl's in the edgy forum, but all my config files were wiped and fresh ones laid down and now i'm drooling :)[/SIZE][SIZE=3][/SIZE]

---

### Post by chaosgeisterchen on 2006-10-21
Note that **0.1.2** is already due in 2 weeks.. their development is racing.

---

### Post by PriceChild on 2006-10-21
uuuuuu... i don't use a window list area any more and aladin lamp animation now still happens on minimize! :D

---

### Post by chaosgeisterchen on 2006-10-21
So you seem to like it ;) great :)

---

### Post by ayoli on 2006-10-21
hum, nice new features, but i must reload beryl after login (even if beryl manager loads and beryl is selected as default manager)...too bad

edit: ah, pb gone after removin .beryl-manager* files and restart a couple of times, now beryl is only cool :) 
oh, dream fx for menu is horrible, i prefer short fade + a bit of wobbly :D
it's a bit hard to find what options are because of new french translation :D

---

### Post by rianquinn on 2006-10-21
I get a strange problem that maybe you guys know how to fix. Sometimes my Beryl System Tray icon disappears. 

Not sure why. How do I get the system tray to come back.

Thanks

---

### Post by jasay on 2006-10-21
> **rianquinn said:**
> I get a strange problem that maybe you guys know how to fix. Sometimes my Beryl System Tray icon disappears. 

Not sure why. How do I get the system tray to come back.

Thanks

The system tray is actually a separate program called beryl-manager.  I don't know why it would be failing, but to get it back fire up alt+F2 and type```
beryl-manager
```

---

### Post by hanzomon4 on 2006-10-21
Performance is great, just no decorations :( and the default settings suck

---

### Post by Wallakoala on 2006-10-21
I just upgraded and there aren't any window borders...how do I fix this?

edit: it fixed itself lol

---

### Post by chaosgeisterchen on 2006-10-21
How did it fix itself, if I may ask?

---

### Post by Wallakoala on 2006-10-21
> **chaosgeisterchen said:**
> How did it fix itself, if I may ask?

Well I switched to metacity and then switched back to beryl and it still didn't have any window borders. I don't really remember what happened next, but the window borders just appeared. I might have clicked in the space where they are supposed to be or something...

Or if you hold down alt and drag a window it moves the window around, the window borders might have appeared after that.

It was really weird, I don't really remember.

---

### Post by Peepsalot on 2006-10-21
I can't get any borders either.

---

### Post by chaosgeisterchen on 2006-10-21
Seems rather buggy.. I see what I can find out about this issue.

---

### Post by Peepsalot on 2006-10-21
Turns out I just needed to edit xorg.conf again, since some settings got overwritten.
added the:
```

    Option "AddARGBGLXVisuals" "True"

```
line to the screens section, from the HOWTO on these forums.

---

### Post by .t. on 2006-10-21
Well, 0.1.1 is a huge improvement. It's much faster, and beryl-manager even has support for Compiz!

---

### Post by chaosgeisterchen on 2006-10-21
@Peepsalot: So I guess your problem vanished ?

---

### Post by killkoy on 2006-10-21
just upgraded and am very impressed, previously had the animations plugin disables because i couldn't stand the dream thing on the menus. Now beryl-settings gives me the option to change it so i have cool animations:D

---

### Post by darkhatter on 2006-10-21
it runs faster, but I'm getting weird problem, sometimes the menu doesn't show up, I'm already addicted to beryl so there is no way I can disable it now. :mrgreen:

---

### Post by Peepsalot on 2006-10-21
> **chaosgeisterchen said:**
> @Peepsalot: So I guess your problem vanished ?
Yes.  After that change, all appears to be working.

---

### Post by darkhatter on 2006-10-21
:confused: :confused: :confused: :confused: 

the problem appears to be gone now

---

### Post by chaosgeisterchen on 2006-10-21
Great that you solved your problem :)

I have to admit that it's great fun seeing Beryl solving its problems by itself :)

---

### Post by darkhatter on 2006-10-21
I think I just set the options to default so that may have been it

---

### Post by mutlu_inek on 2006-10-21
Regarding the window borders see this thread started by chaosgeisterchen (see above), maybe it helps:

[http://forum.beryl-project.org/topic-5639-missing-window-decorations](http://forum.beryl-project.org/topic-5639-missing-window-decorations)

---

### Post by chaosgeisterchen on 2006-10-21
I should really work redundant and post the links in either forum.

Thanks for doing it for me ;)

---

### Post by hanzomon4 on 2006-10-21
I fixed it, [here's a link to the post]("http://www.ubuntuforums.org/showthread.php?p=1645067#post1645067")

---

### Post by hanzomon4 on 2006-10-21
> **chaosgeisterchen said:**
> Great that you solved your problem :)

I have to admit that it's great fun seeing Beryl solving its problems by itself :)

It's Alive :twisted:

---

### Post by aktiwers on 2006-10-21
Mine fixed itself after Ctrl+Shift+Backspace!

Im absolutely loving XGL+Beryl!!

---

