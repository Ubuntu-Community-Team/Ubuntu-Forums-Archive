---
title: "Do you have the tracker enabled?"
date: 2007-11-14
forum: The Cafe
---

### Post by vishzilla on 2007-11-14
I dont think the tracker tool in Gutsy is that useful!!!! I have disabled it

---

### Post by FuturePilot on 2007-11-14
I use it a lot. Although for some reason it doesn't recognize the word Maybe.:???:

---

### Post by n3tfury on 2007-11-14
it rendered my pc practically useless while it indexed after a new gutsy install, so i disabled and removed it.  no need for it anyway, i know where i keep things.

---

### Post by 50words on 2007-11-14
It doesn't find what I need, so I have it disabled and use Beagle, instead. I need something to search the file contents, not just the meta data.

---

### Post by Depressed Man on 2007-11-15
I've been meaning to try out the new beagle (.30 or 3.0?). Since I read in the dashboard hackers that they implemented IPTC support in images. 

Currently beagle and tracker only index data if the images were in F-Spot or another program...which wasn't helpful for me. 

But the beagle site is down..does it work for anyone else?

[www.beagle-project.org/](www.beagle-project.org/)

---

### Post by inversekinetix on 2007-11-15
> **n3tfury said:**
> it rendered my pc practically useless while it indexed after a new gutsy install, so i disabled and removed it.  no need for it anyway, i know where i keep things.

ditto

---

### Post by hanzomon4 on 2007-11-15
> **50words said:**
> It doesn't find what I need, so I have it disabled and use Beagle, instead. I need something to search the file contents, not just the meta data.

It searches file contents on my system, It works quiet well actually.

---

### Post by misfitpierce on 2007-11-15
Negative I know where I keep my files usually. Altho my friends do use it and leave it active, I do not. Preference I suppose. :)

---

### Post by AndyCooll on 2007-11-15
I  have it enabled but I'm thinking of disabling it. It seems to do the search ok, but then refuses to show me the results in the right-hand pane. I've yet to get around to investigating why. And since I clearly don't use it very often I'm wondering whether it's worth the hassle.

:cool:

---

### Post by Rinzwind on 2007-11-15
> **misfitpierce said:**
> Negative I know where I keep my files usually.<..> :)

Me too :)

---

### Post by PartisanEntity on 2007-11-15
On the one or two occasions that I used it, it worked fine. Most of the time I forget that it is there.

---

### Post by Jonne on 2007-11-15
I use Beagle, although i haven't figured out how to get it to index id3 tags yet, as for some reason it won't do this.
It's not such a huge problem because I usually use amarok to handle my audio needs, butIi sometimes use beagle-query from the command line from somewhere else, so in those cases that would be handy.

I tried tracker after I upgraded, but I didn't like the interface.

---

### Post by igknighted on 2007-11-15
Thank god kubuntu ships with strigi... it runs circles around tracker (or beagle or google desktop for that matter).  Results are relevant, and it can search inside .zip and .tar archives and everything.

---

### Post by dbera on 2007-11-15
> **igknighted said:**
> Thank god kubuntu ships with strigi... it runs circles around tracker (or beagle or google desktop for that matter).  Results are relevant, and it can search inside .zip and .tar archives and everything.

Its funny how strigi always advertises searching inside zip and tar archives ... every desktop search program can do it. Nothing special :)

---

### Post by dbera on 2007-11-15
beagle is supposed to index id3 tags ... can you post the output of

$ beagle-extract-content /path/to/somefile.mp3

---

### Post by dbera on 2007-11-15
> **Depressed Man said:**
> I've been meaning to try out the new beagle (.30 or 3.0?). Since I read in the dashboard hackers that they implemented IPTC support in images. 

Currently beagle and tracker only index data if the images were in F-Spot or another program...which wasn't helpful for me. 

But the beagle site is down..does it work for anyone else?

[www.beagle-project.org/](www.beagle-project.org/)

There is a problem with the DNS for that site. 0.3.0 is not released yet, the devs are trying to get 0.3.0 out within the next few days, and also hoping to fix the DNS problem by then.

---

### Post by Depressed Man on 2007-11-15
Yeah I read it in the email today, though I was going build it from the trunk. Though if they're going release it soon I guess I'll just wait.

---

### Post by Jonne on 2007-11-15
> **dbera said:**
> beagle is supposed to index id3 tags ... can you post the output of

$ beagle-extract-content /path/to/somefile.mp3
```
Filename: file:///media/nas/media/music/Daft Punk/Daft Punk - Discovery/Daft Punk - Discovery - 01 - One More Time.mp3
Debug: Loaded 53 filters from /usr/lib/beagle/Filters/Filters.dll
Filter: Beagle.Filters.FilterTotem (determined in 2.21s)
MimeType: audio/mpeg

Properties:
  Timestamp = 2006-07-26 23:31:05 (Utc)
  dc:extent = 320
  dc:title = One More Time
  fixme:album = Discovery
  fixme:artist = Daft Punk
  fixme:audio:bitrate = 192
  fixme:audio:codec = MPEG 1 Layer 3 VBR
  fixme:tracknumber = 1
  fixme:year = 2001

Content:
(no content)
HotContent:
(no hot content)

Text extracted in .14s
```
I guess it does work then ;). But I could've sworn that there were files I couldn't find with Beagle. I guess I'll try that command if I ever encounter one of them. Maybe they just weren't indexed or something, since my music is on a NAS, which probably means that every time I'm not in my home network Beagle will forget about the files on the nas, and see /media/nas as an empty folder...

---

### Post by Paul820 on 2007-11-15
I had real problems with it indexing, it was using 936Mb at one point and made my laptop unusable to i turned it off. I am very organised anyway so i don't miss it at all.

---

### Post by Lord_Dicranius on 2007-11-15
Like a few others have said, I know where I keep my files.  So nope, I don't use it either.

---

### Post by dbera on 2007-11-15
> **Jonne said:**
> 
I guess it does work then ;). But I could've sworn that there were files I couldn't find with Beagle. I guess I'll try that command if I ever encounter one of them. Maybe they just weren't indexed or something, since my music is on a NAS, which probably means that every time I'm not in my home network Beagle will forget about the files on the nas, and see /media/nas as an empty folder...

You should not point beagle to any such shared directories; it will confuse beagle since files and directories will suddenly reappar and disappear. Instead you should build static index (beagle-build-index).

---

### Post by Jonne on 2007-11-15
> **dbera said:**
> You should not point beagle to any such shared directories; it will confuse beagle since files and directories will suddenly reappar and disappear. Instead you should build static index (beagle-build-index).
Will the static index keep track of changes to my nas?

I'm also reluctant to experiment with it due to the big warning that says:
```
** WARNING **
beagle-build-index will *delete all existing data* within the target
directory.  Ensure that the target path is set correctly before running.
```

What's the correct thing to do here? Will
```
beagle-build-index --recursive --deny-pattern .beagle*  --target /media/nas/.beagle-static /media/nas/
``` do what I want without deleting all my files in /media/nas/ ? (I based this on the example in [http://beagle-project.org/Static_Indexes](http://beagle-project.org/Static_Indexes) )

---

### Post by dbera on 2007-11-15
> **Jonne said:**
> Will the static index keep track of changes to my nas?

I'm also reluctant to experiment with it due to the big warning that says:
```
** WARNING **
beagle-build-index will *delete all existing data* within the target
directory.  Ensure that the target path is set correctly before running.
```

What's the correct thing to do here? Will
```
beagle-build-index --recursive --deny-pattern .beagle*  --target /media/nas/.beagle-static /media/nas/
``` do what I want without deleting all my files in /media/nas/ ? (I based this on the example in [http://beagle-project.org/Static_Indexes](http://beagle-project.org/Static_Indexes) )

:) the "target" directory (--target xxx) might be affected, nothing else.
Unfortunately static index will not watch for changes in real time. You have to rerun it and it will quickly register the changes. But if you have a network mount point which is sometimes unmounted and sometimes mounted beagle might act differently (i.e. it might think all the file in the unmounted network share is gone and remove them from its index).

---

### Post by roachk71 on 2007-11-16
This applet (with its corresponding library and daemon) brings back memories of painfully slow WinXP with the indexing service enabled. The daemon also uses too much memory, forcing swap to be used all the time.

For the sake of performance, I have completely removed it.

It's not entirely a bad idea, it is simply that most users like their systems to have a snappier feel.

---

### Post by sports fan Matt on 2007-11-16


If im thinking right, from what i've read, if i uninstall the tracker it would kill my system and force the kernel into a panic?  Yes No?

---

### Post by Depressed Man on 2007-11-16
> **Lord_Dicranius said:**
> Like a few others have said, I know where I keep my files.  So nope, I don't use it either.

I know where I keep my files too..all my pictures are in folders sorted by year, month, then date. 

My music is sorted into Artist, then album. Easier on my laptop then on my desktop though, since my desktop has a couple year's worth of music (40+ GBs) so it's hard sorting everything into folders..especially if I only put one song by that artist onto the computer. So ID3 tags help out. 

But having search tools like Beagle, GDS, Tracker, whatever is still helpful. :). Yeah I could always start Picasa then do my search from there but it's nice when I just use Copernic Desktop Search or Microsoft's and all my images of say my friend Victoria come up when I search Victoria.

---

### Post by pt123 on 2007-11-16
The problem is that they integrated Tracker into Nautilus without much thought and there are  bugs because of this. Nautilus search has become useless.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/148701](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/148701)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150379](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150379)

Like other Gnome affiliated applications there has been vey little development on it since september
[http://www.gnome.org/projects/tracker/](http://www.gnome.org/projects/tracker/)

It is a pity Novell are interested funding Mono based apps.

---

### Post by Tundro Walker on 2007-11-17
> **sox fan Matt said:**
> If im thinking right, from what i've read, if i uninstall the tracker it would kill my system and force the kernel into a panic?  Yes No?

I didn't have any problems after uninstalling it.  First thing I did after upgrading to Gutsy was go through my Synaptic list and bump off Compiz, Tracker, etc.  Not that I have anything against these programs...they're wonderful for what they do...it's just I'm a minimalist and I don't utilize them.

The default Places > Search for Files... has worked fine for me, and still worked after Tracker hit the bit bucket.  Haven't had problems with Nautilus or anything else, either.

I don't think the Linux/Ubuntu folks are as zealous about integrating things as Microsoft was...you know, how they integrated Internet Explorer into every nook and cranny of Win98 and such, so you couldn't really "uninstall it".  No, Linux dev's have mostly been about modularity.  If you don't like something, you just remove it, but leave the underlying libs and such.  When Synaptic makes its next refresh, it'll let you know if removing Tracker made any lib's obsolete, and you can then remove them.

---

### Post by Billy_McBong on 2007-11-17
i have it enabled but don't use it very much

---

### Post by pt123 on 2007-11-17
> **Tundro Walker said:**
> 

The default Places > Search for Files... has worked fine for me, and still worked after Tracker hit the bit bucket.  Haven't had problems with Nautilus or anything else, either.
.


But with it you have to browse to a folder to search within it.

While with Nautillus if your were in a folder you can search from there.

---

### Post by Lostincyberspace on 2007-11-17
yes I'm to lazy to get rid of it. :)

---

