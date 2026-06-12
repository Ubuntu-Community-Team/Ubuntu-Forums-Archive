---
title: "GSreamer illegal in the U.S.A., why?"
date: 2007-07-07
forum: The Cafe
---

### Post by Puppy fam on 2007-07-07
From what I understand, GSreamer is illegal in the U.S.A. I also understand that any other software that would do what GStreamer does is also illegal. So what does this software do to make it illegal?

Thanks,
-Puppy fam

---

### Post by reacocard on 2007-07-07
> **Puppy fam said:**
> From what I understand, GSreamer is illegal in the U.S.A. I also understand that any other software that would do what GStreamer does is also illegal. So what does this software do to make it illegal?

Thanks,
-Puppy fam

Gstreamer itself is not, but some of the media-playing plugins for it are. If you do not install these plugins, there is nothing at all illegal about gstreamer.

---

### Post by macogw on 2007-07-07
Most codecs are "protected" by patents.  Patents != copyright.  Copyright is the specifics of the code.  Patents are on general ideas.  So, anything that's general idea is to encode or decode mp3, for example, has to be paid for to the person who filed the patent.  Since you don't pay some random dude like $30 or whatever to install the codecs, you're "stealing" his idea.

To give you an idea of how general patents are (and therefore how lame), Apple patented using menus to go through the songs on an mp3 player using the id2/id3 tags on the file to sort them.  Anything that lets you do Artist > Album > Song or Genre > Artist > Song or whatever would be violating it.

---

### Post by stmiller on 2007-07-07
It's not illegal, it's just that the licenses around what is included are not GPL. So Ubuntu is not allowed to distribute the contents, or rather doesn't want to. (To remain a 100% free distro on the CD).  But legally, you CAN accept the license by downloading 'gstreamer ugly' yourself and installing it.

libdvdcss however is a grey issue...

---

### Post by vexorian on 2007-07-07
No stmiller, in the US it is actually illegal, you got to thank how good of a government they have such that it thought software patents were a huge idea.

Shame on apple, I wonder why we still have people that think it is different to microsoft.

---

### Post by Anthem on 2007-07-07
> **vexorian said:**
> No stmiller, in the US it is actually illegal
Link please.

I know it's trendy to bash the USA these days, but the GStreamer **framework **is not illegal.  Nobody has alleged any patents against it, and nobody has been told to stop using it.

Specific plugins are a different story, depending on the plugin.  But please back up your claim... who says Gstreamer is illegal?

---

### Post by stmiller on 2007-07-07
> **vexorian said:**
> No stmiller, in the US it is actually illegal, you got to thank how good of a government they have such that it thought software patents were a huge idea.

Shame on apple, I wonder why we still have people that think it is different to microsoft.

? Nothing is illegal in the US except DVD playback, which is a grey area. 

This page has a little info, but doesn't really clear anything up:

[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

The MP3 patents have nothing to do with America; the patent is actually held by a German company (fraunhofer).

And what does this have to do with Apple?

---

### Post by vexorian on 2007-07-07
> **Anthem said:**
> Link please.

I know it's trendy to bash the USA these days, but the GStreamer **framework **is not illegal.  Nobody has alleged any patents against it, and nobody has been told to stop using it.

Specific plugins are a different story, depending on the plugin.  But please back up your claim... who says Gstreamer is illegal?
I wasn't speaking about gstreamer, I thought you were talking about other stuff in your post (since it was a reply to the other posts), sorry for the confusion.

---

### Post by Puppy fam on 2007-07-07
I don't know if [this]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-legal.html") will clear things up or not.

---

### Post by az on 2007-07-07
In terms of the Gstreamer plugins, the issue is actually with distribution rather than use.

The patent holders allow you to use them freely for non-commercial use.  They don't allow anyone to distribute them, though.  That's why the ubuntu cd can't ship with them on it.

---

