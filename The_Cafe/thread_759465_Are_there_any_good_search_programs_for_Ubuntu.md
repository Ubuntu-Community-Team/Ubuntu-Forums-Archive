---
title: "Are there any good search programs for Ubuntu?"
date: 2008-04-19
forum: The Cafe
---

### Post by Mazza558 on 2008-04-19
...other than Beagle or Tracker?

Tracker simply doesn't track (and can't find files at all - they don't appear in the Tracker window), and Beagle looked promising until it crashed with:

```
beagle-search

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Gnome.Program.HardenRef () [0x00000] 
  at Gnome.Program..ctor (System.String app_id, System.String app_version, Gnome.ModuleInfo module, System.String[] argv, System.Object[] props) [0x00000] 
  at Search.MainWindow.Main (System.String[] args) [0x00000] 

```

So, are there any other GUI search tools, or are these 2 the main ones? The one built into Nautilus doesn't work either.

---

### Post by ghostdog74 on 2008-04-19
use the command line find command. You are on linux after all, try to learn some command line commands. This way, you don't feel like its the end of world when you don't have any GUI options

---

### Post by Mazza558 on 2008-04-19
> **ghostdog74 said:**
> use the command line find command. You are on linux after all, try to learn some command line commands. This way, you don't feel like its the end of world when you don't have any GUI options

*cough* see my signature ;)

I know the command line fairly well, but i still prefer GUI. It's just nicer to work with. For example, what if I wanted to also OPEN the file I was looking for? I'd have to open nautilus and locate it that way (or use cd). With tracker, I can just double-click and it opens the file with the right application (if it actually finds the file I'm looking for).

---

### Post by ghostdog74 on 2008-04-19
depending on what you use to OPEN a file
```
find  /path -maxdepth 1 -name "file_i_am_looking_for" | xargs -i kwrite "{}" &

```
or
```

find  /path -maxdepth 1 -name "file_i_am_looking_for" -exec kwrite "{}" \; &

```
not that difficult right?

---

### Post by mister_pink on 2008-04-19
The thing that bugs me about searching in ubuntu is none of the GUI tools seem to offer any way to set things like "search in this folder, and its subfolders, for files of type X size at least X kB" or whatever. I can always find a specific file if thats what I'm after, but even that can be a bit of a mission, but sometime I want to use it as a filter to select certain files.

---

### Post by ghostdog74 on 2008-04-19
> **mister_pink said:**
> The thing that bugs me about searching in ubuntu is none of the GUI tools seem to offer any way to set things like "search in this folder, and its subfolders, for files of type X size at least X kB" 
look at the man page of find. there are many options you can use. for size
just use -size 
```

find /path -type f -size +10M -ls

```

---

### Post by mister_pink on 2008-04-19
That not really the point though, yes I can use terminal and personally I'm fairly happy to, but its pretty basic functionality for a search tool to be able to do these things. On the plus side, at least there's not a $*$£"*%& stupid dog asking me what I want to look for. Way to go MS, your customers obviously need cartoons to help them feel at ease with your software.

---

### Post by rune0077 on 2008-04-19
> **mister_pink said:**
> On the plus side, at least there's not a $*$£"*%& stupid dog asking me what I want to look for. Way to go MS, your customers obviously need cartoons to help them feel at ease with your software.

What?!? I liked the dog. It's the one thing I miss the most since ditching Windows. Maybe we could get a search-penguin?

---

### Post by gn2 on 2008-04-19
sudo apt-get install catfish

I discovered Catfish in Zenwalk, it's superb. (well I like it anyway)

[http://software.twotoasts.de/?page=Screenshots](http://software.twotoasts.de/?page=Screenshots)

---

### Post by mister_pink on 2008-04-19
I'm always disappointed that openoffice doesn't have a friendly paperclip to help me write a letter!

Edit: Just installing catfish now, that looks to be just the kind of thing!

---

### Post by ghostdog74 on 2008-04-19
> **mister_pink said:**
> Way to go MS, your customers obviously need cartoons to help them feel at ease with your software.

the MS search function do actually have advance search options that you can specify, eg by date, size etc.

---

### Post by mister_pink on 2008-04-19
Yeah I know, one of the first things I always did when installing windows XP, kill the dog and turn on the old style start menu! That was partly my point though - you know things are going wrong when the functionality is actually better in windows.

Catfish looks good, unfortunately doesn't seem to work with the latest tracker as a backend but then that doesn't really matter.

---

### Post by Zeotronic on 2008-04-19
> ...other than Beagle or Tracker?
I never liked them either... and while I would try something else if it came out... I admit, I use Terminal for searching with great results.

---

### Post by rune0077 on 2008-04-19
If you just want to find a file, you could just do Places > Search for files. It's the same as what the terminal gives you, but with some "advanced" search features (that aren't really all that advanced).

---

### Post by andrek on 2008-04-19
**sudo updatedb** and **locate **;)

---

### Post by Mazza558 on 2008-04-19
> **Zeotronic said:**
> I never liked them either... and while I would try something else if it came out... I admit, I use Terminal for searching with great results.

I like beagle, but as I say, it's broken.

---

### Post by gn2 on 2008-04-19
> **Mazza558 said:**
> I like beagle, but as I say, it's broken.

Tried Catfish yet? It's in the repos and is the best Linux GUI search tool I've used.

---

### Post by Oldster on 2008-04-19
I'm pretty happy using Catfish as a frontend for locate.

---

### Post by Mazza558 on 2008-04-19
Beagle decided to start working now, so I guess that's good...

---

### Post by dbera on 2008-04-19
> **Mazza558 said:**
> ...other than Beagle or Tracker?

Tracker simply doesn't track (and can't find files at all - they don't appear in the Tracker window), and Beagle looked promising until it crashed with:

```
beagle-search

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Gnome.Program.HardenRef () [0x00000] 
  at Gnome.Program..ctor (System.String app_id, System.String app_version, Gnome.ModuleInfo module, System.String[] argv, System.Object[] props) [0x00000] 
  at Search.MainWindow.Main (System.String[] args) [0x00000] 

```

So, are there any other GUI search tools, or are these 2 the main ones? The one built into Nautilus doesn't work either.

Some of the mono packages in Hardy are broken - they either face crash-on-exit or crash-on-startup. Here is the Ubuntu bug for your case

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/219381](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/219381)

---

### Post by Mazza558 on 2008-04-19
> **dbera said:**
> Some of the mono packages in Hardy are broken - they either face crash-on-exit or crash-on-startup. Here is the Ubuntu bug for your case

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/219381](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/219381)

As a matter of fact, I think today's update (or yesterday's) fixed it. I didn't update until midday today, and after restarting X (messing with Xorg), it was working. Someone in the comments for that bug report says his problem was fixed today too.

---

### Post by danbuter on 2008-04-19
This is one area where Microsoft blows away Linux. Tracker and Beagle are not up to snuff. And while I don't mind the command line, most people avoid it like the plague.

---

### Post by mister_pink on 2008-04-19
I think tracker does a good job of indexing things, and searches are certainly really quick. Its just its GUI lacks fine tuning of your search. I always forget about the file search in the places menu. Thats actually pretty good...

---

### Post by smartboyathome on 2008-04-19
I can't believe no one said this, but Google desktop pawns everything else in my opinion. It may not be open source, but its really good. Try it.

---

### Post by Polygon on 2008-04-19
Deskbar applet sucks, to get a real search, you should use tracker-search-tool or something, but it works a lot better then deskbar applet for finding your tracker indexed results.

I like tracker over beagle. Trackers index's are smaller, while beagles are over 2gb for me. Not to mention tracker can have tags and thumbnails

---

### Post by Superkoop on 2008-04-19
Personally I like the Places > Search for Files... search. It has always been better at finding what I want to find, and finding it quickly, than tracker or Beagle does for me. Anyways, both Beagle and Tracker take up more resources than I care to give just for searching (windows gave a lot of resources to file searching too)

---

### Post by jrusso2 on 2008-04-20
I have to agree with google desktop.  Once the initial first time index is done it hardly uses any resources only indexes when things are changed.

Also if you use gmail it indexes your gmail account which is really handy and your chat logs if someone gave you some information in chat and you forgot what it was.

---

