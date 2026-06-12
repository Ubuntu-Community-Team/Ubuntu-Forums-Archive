---
title: "Nautilus will not search for files"
date: 2013-03-11
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-11
As the topic suggests .. nautilus will not search.  Just nothing.

Anyone else?

---

### Post by dino99 on 2013-03-11
i get that issue since a few weeks (months) now; i suppose its one more feature removed (that new gnome way to get less maintenance)
i've simply added (add to panel) the search applet; which works fine. (gnome-classic, aka fallback)

---

### Post by serdotlinecho on 2013-03-11
Yep, same for me. Press the search button or Ctrl+F and i'm trying to search my raring iso located inside Downloads folder. No actions and no results appeared. Only when I switched to Downloads folder, press the search button, then it will search my raring iso. But also I can search from Unity dash :)

[[IMG]http://i.imgur.com/d8Odecbs.png[/IMG]]("http://imgur.com/d8Odecb")      [[IMG]http://i.imgur.com/izbKiRUs.png[/IMG]]("http://imgur.com/izbKiRU")     [[IMG]http://i.imgur.com/NHTRxcus.png[/IMG]]("http://imgur.com/NHTRxcu")      [[IMG]http://i.imgur.com/jp85L7ms.png[/IMG]]("http://imgur.com/jp85L7m")

---

### Post by ventrical on 2013-03-11
> **dino99 said:**
> i get that issue since a few weeks (months) now; i suppose its one more feature removed (that new gnome way to get less maintenance)
i've simply added (add to panel) the search applet; which works fine. (gnome-classic, aka fallback)


What search applet ?

---

### Post by ventrical on 2013-03-11
> **dino99 said:**
> i get that issue since a few weeks (months) now; i suppose its one more feature removed (that new gnome way to get less maintenance)
i've simply added (add to panel) the search applet; which works fine. (gnome-classic, aka fallback)


aww mann .. this is just so frustrating...

---

### Post by mc4man on 2013-03-11
recursive search, (which works well),  was added back to nautilus shortly after 3.6.x release, has not been patched into current 13.04 nautilus nor has 13.04 moved (yet?) to use nautilus-3.7/8 where it's long fixed.
There is a request to do so (3.7/8),  -  current status no review yet
(see no reason why 13.04 can't go to 3.8, with or without gtk upgrade

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1077415](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1077415)

---

### Post by mc4man on 2013-03-11
> **ventrical said:**
> What search applet ?
For a unity session you could install 
```
sudo apt-get install gnome-search-tool
```

While awaiting some resolution

---

### Post by ventrical on 2013-03-11
> **mc4man said:**
> For a unity session you could install 
sudo apt-get install gnome-search-tool

While awaiting some resolution


Thank you very much mac4man.  I had also seen your other research on this matter and thank you for keeping all of us apprised of the various situations with nautilus and all the other multifaceted research that you do here in the forums , which  without, would be be extremely difficult for a lot of us to get a handle on many of the difficulties that  ubuntu-beta-testings presents us with.

Regards,
Ventrical

---

### Post by AlanR8 on 2013-03-11
The Unity Dash search works well for me BTW

---

### Post by mc4man on 2013-03-11
> **AlanR8 said:**
> The Unity Dash search works well for me BTW
It is worth noting that the Dash file lens/file search does work pretty well now for _'recent' & or  files in home directory_
When found the r. click on > preview has 2 handy options, 'Open' & 'Show in Folder' that work reasonably well

---

### Post by ventrical on 2013-03-11
> **mc4man said:**
> For a unity session you could install 
sudo apt-get install gnome-search-tool

While awaiting some resolution


It will not work for the file/s I mentioned;

mir-doc: /share/doc/mir-doc/html/dummy__input__manager_8cpp.html

no matter how I truncate it.

It will only work if I use a wildcard * and .html.

Looks like something I am doing wrong here.

---

### Post by mc4man on 2013-03-11
> **ventrical said:**
> It will not work for the file/s I mentioned;

Must of missed that, no matter

It's possible that  - 
you should do a restart & or the search tool doesn't like searching the "File system"

So help it out & narrow down a bit, noting that the further away the longer it will take, a far point of /usr should work, /usr/share a bit quicker, ect.
see screen 1
screen 2 example of nautilus (really fixed), searching from /

---

### Post by ventrical on 2013-03-12
:)....  one of those days .. I had been using only a single '_' for android__buffer which is actually 2 "__" underscores during my search...

these days happen ... yes they do :)

---

### Post by philinux on 2013-03-12
Very odd.

It will search for wav files but not txt , png or jpg nor ogg. It will find folders however.

Dash search works fine.

---

### Post by P-I H on 2013-03-12
In my installation Nautilus will find files and folders that are shown in the open window.
When I open Computer and search with b, it shows the folders that include a b.
If I open usr and searh with config, it shows files and folders that include config.

Before a search was recursive and if you knew the name of a file you were able to found it. Now it will be much harder to explore the file system.

The Dash also behaves strange. When I search for var, the Dash shows the log and crash folders, which is nice, but not the var folder.

---

