---
title: "Those little &quot;details&quot; I hate"
date: 2005-07-13
forum: The Cafe
---

### Post by RastaMahata on 2005-07-13
First of all, I wont change ubuntu, I wont come back to linux or anything like that. This is a list of the little thigs I hate that I hope get solved for the next release (or the next one after that).

- Whenever I'm typing OR reading in a textbox, leafpad, or any place in the screen, I would like the mouse to dissapear. Its quite annoying.
- If I have a music playlist, I would like it to be compatible in every player I have. I just made a playlist in totem, I cant open it with rhythmbox, and graveman wont read it.
- If I want to record a cd, I want easy to use tools.example:
     I made a playlist in totem
     I installed serpentine from backports
     I open the playlist in serpentine, and click on the burn button... It starts converting from mp3/ogg/etc to wav
     It stops at preparing the recorder.... 
     I remove serpentine (after 3 more tries), and get Graveman
     It doesnt accept the totem playlist as an actual playlist! So I add all the files in the folder, and rearrange them by hand
     Click on the record button, and graveman crashes.
     Start graveman again, same steps. It actually starts recording! until it reaches track 2. then it fails.
     Remove graveman, install gnomebaker
     Doesnt accept playlist, go by hand
     Click on "bake", it converts the files
     Little window saying "insert the cd"... I didnt (just to test) and clicked on "accept"... it gives me an error, but it deletes the cache, so I have to convert the files again...
     It's actually recording now... lets see how it goes..

- I dont want to quit some software just to be able to hear sounds from the next one. I would like to play quake to the rhythm of some music... 
- I cant watch a flash movie without sound delay...
- Gnome look configuration is confusing. I can edit the look of my windows, but I cant edit the mouse... 
- Gedit is slow, and takes too much time to load... why doesnt ubuntu ship with leafpad by default?
- Why is the System > Administration menu visible to users without admin privileges?
- Why cant I eject a cd from the places menu?
- If I insert a dvd movie in the computer, it automatically plays. If I close the movie, and double click on the dvd icon in the desktop, it opens a folder... Shouldnt it play the movie?
- Why do mp4 files dont have icons?
- xorg.conf configuration can be confusing. Why doesnt gnome or ubuntu provide a gtk tool to configure it? It could allow to install drivers, select which (working) driver to use, what resolutions to use, etc...
- Fun fact: the calculator takes more time to load than leafpad...
- Why do I have a dictionary in English, If I speak spanish?

I would love to see these problems go... Until then, I'll live with them.
Please dont flame me :(

---

### Post by maruchan on 2005-07-14
No offense taken, these lists can be found for all existing operating systems. ](*,)

I especially agree with the "double-clicking DVD icon" issue. Silly, isn't it?

Have you tried using m3u playlists for your mp3s? Totem will open those. So will Beep, XMMS, and most other media players.

---

### Post by RastaMahata on 2005-07-14
[QUOTE=maruchan]No offense taken, these lists can be found for all existing operating systems. ](*,)

I especially agree with the "double-clicking DVD icon" issue. Silly, isn't it?

Have you tried using m3u playlists for your mp3s? Totem will open those. So will Beep, XMMS, and most other media players.[/QUOTE]
 the playlist created in totem is m3u, IIRC

---

### Post by mattheweast on 2005-07-14
This is a cool list of ideas: such lists can really help distributions like Ubuntu prosper. Try filing some of these are bugs (some of them are enhancement bugs) and I'm sure that even if they are not all resolved, at least some will be!

M

---

### Post by bored2k on 2005-07-14
[QUOTE=RastaMahata]
- Gnome look configuration is confusing. I can edit the look of my windows, but I cant edit the mouse... [/QUOTE]
sudo apt-get install gcursor ?

---

### Post by Kvark on 2005-07-14
[QUOTE=RastaMahata]- Whenever I'm typing OR reading in a textbox, leafpad, or any place in the screen, I would like the mouse to dissapear. Its quite annoying.[/QUOTE]
Have to disagree here. I would be very annoyed if the mouse did dissapear other then when I play games or watch movies on fullscreen.

[QUOTE=RastaMahata]- If I have a music playlist, I would like it to be compatible in every player I have. I just made a playlist in totem, I cant open it with rhythmbox, and graveman wont read it.[/QUOTE]
Yes, all file formats should be open standards, like xml and html are. The multitude of various encodings and undocumented obscure storage algorithms are a hell.

This is a heritage from windows where something as standard as .doc is deliberately designed to be incompatible with other programs (unless they reverse engineer it) or even with older versions of word. And you have to pay $60k to be allowed to make a program that can read .mp3.

[QUOTE=RastaMahata]- I cant watch a flash movie without sound delay...[/QUOTE]
And I can see only some of the text in flash movies. Which makes it impossible to navigate flash menues.

[QUOTE=RastaMahata]- Why cant I eject a cd from the places menu?[/QUOTE]
Why can't I unmount+eject a CD by pushing the eject button on the CD tray? What does linux think that button is there for???

[QUOTE=RastaMahata]- Why do I have a dictionary in English, If I speak spanish?[/QUOTE]
There is nothing more confusing then two languages randomly combined. In hoary it is swedish and english mixed all over the place for me, even worse then in warty. It makes my head spin trying to switch back and forth between them in my mind. 

I'll just accept that multi language support means multiple languages at once and stick to english only in the future.

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=RastaMahata] Why doesnt gnome or ubuntu provide a gtk tool to configure it? It could allow to install drivers, select which (working) driver to use, what resolutions to use, etc...
[/QUOTE]

Because no one has made it...and the Ubuntu developer's hands are full.

If anyone has time to do this, it would be appreciated.

---

### Post by Kvark on 2005-07-14
[QUOTE=poofyhairguy]Because no one has made it...and the Ubuntu developer's hands are full.

If anyone has time to do this, it would be appreciated.[/QUOTE]
Isn't that what the bounties are for. To get others to do specific things the ubuntu devs want but don't have time for...

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=Kvark]Isn't that what the bounties are for. To get others to do specific things the ubuntu devs want but don't have time for...[/QUOTE]

Except for the fact that the lack of an GUI Xorg config tool has appeared NOWHERE on the official radar.

(aka if we wait for a bounty to make it or an official developer to make it it might never come).

---

### Post by RastaMahata on 2005-07-14
[QUOTE=bored2k]sudo apt-get install gcursor ?[/QUOTE]
 yeah, I've told people to use that tool, but it would be more effective to include that tool in the Preferences window, or even in Preferences > Mouse.

---

### Post by bored2k on 2005-07-14
[QUOTE=RastaMahata]yeah, I've told people to use that tool, but it would be more effective to include that tool in the Preferences window, or even in Preferences > Mouse.[/QUOTE]
 Doesn't it get included in preferences ? aT Least it does here.

---

### Post by UbuWu on 2005-07-14
[QUOTE=RastaMahata]yeah, I've told people to use that tool, but it would be more effective to include that tool in the Preferences window, or even in Preferences > Mouse.[/QUOTE]

It will be there in gnome 2.12 / breezy.
See: [http://bugzilla.gnome.org/show_bug.cgi?id=110670](http://bugzilla.gnome.org/show_bug.cgi?id=110670)
There is a screenshot there.

---

### Post by UbuWu on 2005-07-14
[QUOTE=bored2k]Doesn't it get included in preferences ? aT Least it does here.[/QUOTE]

Only when you install it  ;-)

---

### Post by UbuWu on 2005-07-14
[QUOTE=UbuWu]It will be there in gnome 2.12 / breezy.
[/QUOTE]

May even be there in a few days if you are using breezy... Does anybody know how fast changes in gnome are imported into ubuntu???

---

### Post by RastaMahata on 2005-07-14
[QUOTE=UbuWu]It will be there in gnome 2.12 / breezy.
See: [http://bugzilla.gnome.org/show_bug.cgi?id=110670](http://bugzilla.gnome.org/show_bug.cgi?id=110670)
There is a screenshot there.[/QUOTE]
 yey! one down... some to go... :P

---

### Post by UbuWu on 2005-07-14
[QUOTE=poofyhairguy]Because no one has made it...and the Ubuntu developer's hands are full.

If anyone has time to do this, it would be appreciated.[/QUOTE]

Actually, Sebastien Bacher, who is one of the Ubuntu developers, committed the changes in gnome  :razz: (he didn't write the code by the way)

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=UbuWu]Actually, Sebastien Bacher, who is one of the Ubuntu developers, committed the changes in gnome  :razz: (he didn't write the code by the way)[/QUOTE]

Sounds good. This + new ndiswrapper tool makes me happy person today.

---

### Post by doclivingston on 2005-07-15
[QUOTE=RastaMahata]If I have a music playlist, I would like it to be compatible in every player I have. I just made a playlist in totem, I cant open it with rhythmbox, and graveman wont read it.[/quote]
Breezy includes "libtotem-plparser", which is the playlist reading/writing library that has been broken out of Totem. The cvs version of Rhythmbox uses this to read and write playlists, but I'm not aware of anything else using it (yet).

---

### Post by raid996 on 2006-06-21
I have a number of similar problems, every time i burn an audio cd a number of tracks just wont play... this didnt happen in windows so my burner just works.
The most annoying thing for me anyway is that whenever i'm using a text-editor, or my browser the cursor moves to my mouse position without me clicking it, so some times i just realize i'm writing right in the middle of other text.
I'm a student and i use a lot my ubuntu laptop and this really makes me lose plenty of time...

Anyway, one more thing, i want to thank ubuntu developpers for giving me an outstanding OS which is safe, free and that wokrs for 98% of my needs, I can do webpages, graphics, ingeneering studies, music, videos, text editing, desktop publishing and i even mange to play some good old games like mechwarrior 2 and 3 that with my old XP i had to bury.

I can only say THANK YOU GUYS!!!!!!!

---

### Post by frodon on 2006-06-21
[QUOTE=poofyhairguy]Because no one has made it...and the Ubuntu developer's hands are full.

If anyone has time to do this, it would be appreciated.[/QUOTE]Here is a project about configuring xorg with a GUI, if you add a feature to install drivers it would be really near to be "the solution".
[http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)


Anyone tried that ?

---

### Post by 3rdalbum on 2006-06-21
I absolutely agree with the Linux audio suggestion. Linux is overdue for an audio system that actually works properly. However, it's interesting to note that on Windows I can't play Elastomania when I have an audio file playing in the background. I haven't tried the same with WINE, but I reckon it would work.

The only problem I've ever had with Graveman was when I stopped burning a CD before I even realised that it had actually started burning stuff to it. The subsequent error messages I got when trying to write to it again were completely uninformative. ("Operation Failed!").

Command-line burning. That's the best way to do it. It's not even that difficult!

---

