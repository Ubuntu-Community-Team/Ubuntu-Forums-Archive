---
title: "My old Pangolin..."
date: 2011-06-06
forum: System76 Support
---

### Post by NerdcoreSteve on 2011-06-06
Ah my old Pangolin Performance.

I've been using a mac mini and a windows netbook mostly, but I'd like to get my old Linux Laptop back into shape.

It's got this problem where if I put a DVD it just keeps revving indefinitely.

If I put a cd in there it will rev pretty loudly and then be able to read it most of the time. If it can't I just eject it and try again.

I just want to check, there's no way that could be a software issue is there? Sounds like I need to get a replacement.

What y'all think?

---

### Post by isantop on 2011-06-08
Try cleaning the lens on the optical drive. You'll want to be careful, or you can use one of those lens-cleaning DVDs that are available, as that should work as well, though you may need to install support for DVD video playback if you haven't yet.

---

### Post by Dragonbite on 2011-06-08
My work Thinkpad drive is very, very loud and sometimes cannot read the disk.  I have found this usually happens with disks from a particular vendor.  Sometimes it is loud enough people close their office doors!

If you are just looking at for installing a more up-to-date version you could try using a Live USB instead of CD/DVD/etc.

---

### Post by NerdcoreSteve on 2011-06-25
I tried a DVD cleaner and it's much better now. I've also done a new install (for some reason my laptop was having trouble upgrading from 10 to 11) and it looks all OSX-y and shiny. :)

But I still can't get it to play dvd's. When I load a dvd it asks if I want to open Movie Player, which I do. Then it says "Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed."

So, what exactly do I need to install?

---

### Post by nevius on 2011-06-25
> **NerdcoreSteve said:**
> I tried a DVD cleaner and it's much better now. I've also done a new install (for some reason my laptop was having trouble upgrading from 10 to 11) and it looks all OSX-y and shiny. :)

But I still can't get it to play dvd's. When I load a dvd it asks if I want to open Movie Player, which I do. Then it says &quot;Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.&quot;

So, what exactly do I need to install?

libdvdcss2  I think it is in the medibuntu repository but I could be wrong.  [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by NerdcoreSteve on 2011-06-26
That did it!!!! Yay for Back to the Future 2 on my laptop! :popcorn:

One more dvd related question: I couldn't find an easy way to get movie player to play my dvd while it was still in the drive. I found the easiest way was to eject it and put it back in to make that little "do you want to play this dvd?" dialog pop up. What is the easier way that I haven't seen yet. :D

---

### Post by Eldera on 2011-06-26
In Lucid I went to Applications > Sound & Video > Movie Player, then Movie > play disk.

In Natty (I am dual booting both OSs) there was still an icon for the DVD on the launcher just above the trash and an icon for the DVD on the desktop after quitting the movie with the disc still in the drive. Clicking the one on the launcher or double clicking the one on the desktop opened a screen with "open movie player" on the right side fairly close to the top. "open movie player" started the movie.

From the dash, "movie" brought up Movie Player under Applications and Hobbit under Files and Folders. Trying to open Movie Player from there got nothing useful. Clicking the Hobbit icon brought up the screen I already mentioned from which "open the movie player" starts the movie.

---

### Post by NerdcoreSteve on 2011-06-26
That option doesn't appear for me. I found that clicking on the icon for the dvd in my doc opens a window that gives me a button for movie player to open.

---

