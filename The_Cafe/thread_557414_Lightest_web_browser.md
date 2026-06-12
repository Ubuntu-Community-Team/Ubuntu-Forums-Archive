---
title: "Lightest web browser?"
date: 2007-09-22
forum: The Cafe
---

### Post by Sunnz on 2007-09-22
What is the most light-weight graphical web browser available?

I've got a home File Server which I currently simply have a big time display on its monitor letting it acting as a huge clock in my Lounge room while acting as a central storage on my LAN.

I thought it would be neat to write a web page that reports time, temperature, uptime, cpu load, etc... because I don't need to load a Desktop Environment in it that I could just start X and load a web browser...

Something that supports html, images, javascript would be nice.

---

### Post by chrisxp on 2007-09-22
well phpsysinfo can report temperature, uptime, cpu load, disk usage, network usage, load usage, system info etc, but the temp requires sensors and additional software.. i dont think this is possible without sensors...

anywhere, here is the link: [http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)

hope it helps

---

### Post by Sunnz on 2007-09-22
Thanks for the link!! :)

Though I was really looking for a web browser that would take the least resource for the server... after-all I do stream video and stuff off it!!

As for temperature... I was really supposedly write my own PHP script, which would just go grab whatever the room temperature is off the net for my town/city!! :p

---

### Post by smartboyathome on 2007-09-22
lightest weight web browser - you want it to have some good features still? If so, try seamonkey with browser only. Or also there is kazekage.

---

### Post by jrusso2 on 2007-09-22
Dillo- 
[http://www.dillo.org/](http://www.dillo.org/)

---

### Post by Sunnz on 2007-09-22
> **jrusso2 said:**
> Dillo- 
[http://www.dillo.org/](http://www.dillo.org/)

Whoa, thumbs up!!

---

### Post by bruce89 on 2007-09-22
[GTK+ Webkit's reference browser]("http://packages.ubuntu.com/gutsy/libs/libwebkitgdk0d")

```
./usr/lib/WebKit/GdkLauncher
```

---

### Post by init1 on 2007-09-22
Retawq is the smallest. 
[http://retawq.sourceforge.net/](http://retawq.sourceforge.net/)

---

### Post by kerry_s on 2007-09-22
i would say try links2, it can run with or without X, it has partial java script.
what i would do is just setup one of those mail home pages with all the little widgets and stuff and use that, i would probably use gmails one and add some of those games, just because i can.  :) links2 can also use external app's.

---

### Post by bruce89 on 2007-09-22
w3m actually thinking about it.

---

### Post by ssam on 2007-09-22
> **Sunnz said:**
> I've got a home File Server which I currently simply have a big time display on its monitor letting it acting as a huge clock

i bet thats using a thousand times more electricty than a normal clock.

---

### Post by init1 on 2007-09-22
> **bruce89 said:**
> w3m actually thinking about it.
Retawq is smaller
132     /usr/bin/retawq
1152    /usr/bin/w3m

---

### Post by bruce89 on 2007-09-22
> **init1 said:**
> Retawq is smaller
132     /usr/bin/retawq
1152    /usr/bin/w3m

Depends what you need and what you mean by smaller.

---

### Post by init1 on 2007-09-22
> **bruce89 said:**
> Depends what you need and what you mean by smaller.
I see what you mean by "Depends what you need". Rendering in retawq is not nearly as good as in links, or w3m. But how else could one determine which is smaller?

---

### Post by Bothered on 2007-09-22
Post deleted: Should read the post more carefully

---

### Post by mindtrick on 2007-09-22
Lightest one I've tried is [K-meleon]("http://kmeleon.sourceforge.net/"). It's based on Gecko but last time I checked it was much lighter and faster than Firefox. Don't know why it's Windows only though. It's licensed with GNU GPL

---

### Post by init1 on 2007-09-22
> **Sunnz said:**
> What is the most light-weight **graphical** web browser available?

I've got a home File Server which I currently simply have a big time display on its monitor letting it acting as a huge clock in my Lounge room while acting as a central storage on my LAN.

I thought it would be neat to write a web page that reports time, temperature, uptime, cpu load, etc... because I don't need to load a Desktop Environment in it that I could just start X and load a web browser...

Something that supports html, images, javascript would be nice.
Oh, OK. Dillo then. There's another one kinda like dillo, but I forget the name. I guess I didn't read carefully enough. Retawq is non graphical.

---

### Post by kerry_s on 2007-09-22
dillo don't support java at all.

---

### Post by rsambuca on 2007-09-22
Kazehakase is pretty light but still functional.  It is in the repos.

---

### Post by init1 on 2007-09-22
> **kerry_s said:**
> dillo don't support java at all.
You mean Java**script**, right? Ok, I don't know then. eLinks supports JS but it's non graphical.

---

### Post by reacocard on 2007-09-22
links2 -g

technically not graphical, but with the -g option it does images and uses it's own window under X, and it can also use the framebuffer for the same thing in the console. 

best non-graphical: wget :lolflag:

---

### Post by init1 on 2007-09-23
> **reacocard said:**
> links2 -g

technically not graphical, but with the -g option it does images and uses it's own window under X, and it can also use the framebuffer for the same thing in the console. 

best non-graphical: wget :lolflag:
But links2 -g doesn't have JS. 
wget? LOL, I've used that before. It's hard, but sometimes it's all you have :D

---

### Post by teet on 2007-09-23
> **ssam said:**
> i bet thats using a thousand times more electricty than a normal clock.

Kind of what I was thinking.

But if he could have it display the weather, sports scores, latest headlines, etc it might be worth it.

-teet

---

### Post by Rhapsody on 2007-09-23
Kazehakaze gets my vote as well. Dillo is lighter, but it doesn't have support for JavaScript, which was listed as being required,

---

### Post by reacocard on 2007-09-23
> **init1 said:**
> But links2 -g doesn't have JS. 
wget? LOL, I've used that before. It's hard, but sometimes it's all you have :D

ah, missed the bit about JS. Kazehakaze then, definitely. Just don't use the version from the feisty repos, it has a bug with form submission. Use gutsy's or build from source.

links2 -g is still danged impressive though

EDIT: hm, links2 has an -enable-javascript option :D

---

### Post by Sunnz on 2007-09-23
> **ssam said:**
> i bet thats using a thousand times more electricty than a normal clock.


> **teet said:**
> Kind of what I was thinking.

But if he could have it display the weather, sports scores, latest headlines, etc it might be worth it.

-teet

Ah no it *is* a **file server**, having it to display time and other stuff **as well as serving files**, is going to cost less to go buy a separate clock and stuff.

---

### Post by ssam on 2007-09-23
> **Sunnz said:**
> Ah no it *is* a **file server**, having it to display time and other stuff **as well as serving files**, is going to cost less to go buy a separate clock and stuff.

it does not need the monitor on to serve files.

---

### Post by Sunnz on 2007-09-23
Built-in monitor...

---

