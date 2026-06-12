---
title: "GLScube: WinFS for Linux"
date: 2006-07-09
forum: The Cafe
---

### Post by Cap'n Refsmmat on 2006-07-09
Just spotted this on Digg.

[http://www.glscube.org/index.html](http://www.glscube.org/index.html)

It manages to do real-time searching of file metadata, as well as creating "virtual directories" containing search results. So you can tag a file as "work" and then create a virtual directory labeled "work" that contains all of those files - and it's accessible via a psuedo-filesystem to any other program, even if they don't know what GLScube is.

Awesome stuff. I hope it actually becomes mature and gets into a distro like Ubuntu soon :D

edit: why do we use the phpBB smilies?

---

### Post by drizek on 2006-07-09
thats really cool. It would be awesome if it ends up in edgy, i doubt it though. Hopefully edgy+1

---

### Post by hopstah on 2006-07-09
is this really any different from beagle's capabilities?

---

### Post by kripkenstein on 2006-07-10
Beagle is primarily search-oriented, GLScube intends to do more: files are stored on an underlying RDBMS (postgresql, currently), searches create 'virtual directories' (a file can belong to more than one), and meta-data via tagging. Some of these features may be in Beagle by now (I don't follow it closely), though.

Another difference is that Beagle is a Mono app, and GLScube is in C++, which may make GLScube faster (but we should wait for benchmarks, to be fair).

Look at the [demos]("http://www.glscube.org/download.html") - it seems very impressive to me. This is certainly a project to watch; I'd want it for my desktop.

---

### Post by bruce89 on 2006-07-10
Looks a bit like [GNOME Storage]("http://en.wikipedia.org/wiki/GNOME_Storage") to me.

---

### Post by tom-ubuntu on 2006-07-10
That looks awesome. Yes, I think it is comparable to Gnome Storage. This is the FS we are waiting for ;) At least I hope so :D

Perhaps WinFS comes to life again. Now they can have a look at some opensource code that works ;) :razz:

---

### Post by Brunellus on 2006-07-10
> **tom-ubuntu said:**
> That looks awesome. Yes, I think it is comparable to Gnome Storage. This is the FS we are waiting for ;) At least I hope so :D

Perhaps WinFS comes to life again. Now they can have a look at some opensource code that works ;) :razz:
...what, and taint their precious, secure OS with cancerous communistic GPL code?

---

### Post by Adamant1988 on 2006-07-10
this was my favorite canceled featuer from windows vista... Virtual directories would make life great for me.

---

### Post by RAOF on 2006-07-10
> **bruce89 said:**
> Looks a bit like [GNOME Storage]("http://en.wikipedia.org/wiki/GNOME_Storage") to me.

Man, that project looked **cool**.  It's a pity it seems to have died.

---

### Post by tikal26 on 2006-07-10
it would  be nice to have this or something like this on edgy. I mean i love the demo where he filter all the avi's. Its a shame that Gnome storage seem to have die just like tenor. Those are the project that would compete with FS, but I still have hope that tenor will get resurected.

---

### Post by Senori on 2006-07-10
This doesn't seem to be on the same level as WinFS; reading their (rather lengthy) technical document doesn't suggest to me that this is anything more than a metadata indexer with a nice interface; metadata is stored in a database, yes, but the files aren't, hence use of inotify. WinFS was a very low-level thing, from what Microsoft was claiming.

Things like virtual directories, metadata tagging, and whatnot are all possible with Beagle or Tracker; the former has already been partially implemented via Nautilus, and the latter is being implemented as part of the Summer of Code through Leaftag. All it would take to make these outwardly resemble GLScube is a more complete interface, either in Nautilus or elsewhere.

I'm skeptical, however, of the end benefit of tagging files into collections as opposed to arranging them in file system hierachies. The amount of work required for both is the same, if not more, and the only real benefit of the latter I see is conveniently having the document in multiple locations (which could end up being confusing anyway).

---

### Post by MadMan2k on 2006-07-11
I compiled some tracker enabled nautilus packages so you can use that one too. (see my homepage or the fdo Tracker page)

but both will get an FUSE module and should even work with lagacy applications.

regarding WinFS: it doesnt seem to be more than Tracker with FUSE to me:

[IMG]http://msdn.microsoft.com/library/en-us/dnwinfs/html/winfs03112004-01.gif[/IMG]

---

### Post by bruce89 on 2006-07-11
> **MadMan2k said:**
> 
[IMG]http://msdn.microsoft.com/library/en-us/dnwinfs/html/winfs03112004-01.gif[/IMG]
It's a good thing they pulled the plug on it, even I think that is confusing.  That is why they removed WinFS, as it confused people.

---

### Post by PhilipGanchev on 2006-07-14
From what I've read, WinFS was initially implemented on top of NTFS, but is intended to eventually store the data itself.

Unlike Beagle, Tracker and GLS3, WinFS supposedly represents not just documents, but objects such as people.  This is very important, because these objects are what users care about, and representing them as first-class objects opens up a lot of possibilities.  It also removes the need to convert data between different formats in order for it to be used by different applications.  You can search for "the phone numbers of all people who live in Acapulco and each have more than 100 appearances in my photo collection and with whom I have had e-mail within last month".  

Gnome Storage was planned to represent objects like people, conversations, projects, etc ([http://www.gnome.org/~seth/](http://www.gnome.org/~seth/)  -- search for Storage)  There is also interesting comparisons on Seth's blog between various systems.

I expect that soon after WinFS demonstrates the benefits of document stores, the FOSS community will go back to work on storage systems.  As Stallman says, free software is always late.

---

