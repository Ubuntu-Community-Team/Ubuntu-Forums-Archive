---
title: "managing disparate cloud storage - make it a turn key device?"
date: 2013-07-10
forum: The Cafe
---

### Post by thefoodmonkey on 2013-07-10
i don't know about everybody else but i assume that most of us have got multiple cloud storage sites scattered all over the place (i know at last count i had something like 7 or 8)

is there any way that i can sanely manage all this disparate storage in ubuntu - the cool solution would be to just have a single "virtual" cloud drive and plug all the providers into it - let the virtual "cloud drive" behave like a physical drive and allocate space across them all according to size, speed, importance of data etc etc.

anything like that in the ubuntu? we used to do it the mainframe world quite a bit (lol) where you had storage (memory) online storage tier 1 (SSD) tier 2 (DASD - disk) and nearline storage (tier 3 - slower drives) tier 4 (robot silo) tier 5 (send the operator to fetch a tape)

should cloud storage behave just like another tier of "disk storage" - if you look at it it would be basically the same tier 1 (memory) tier 2 (swap file) tier 3 (filesystem) tier 4 (dvd) - cloud storage could be inserted as tier4 as near-line storage (depending on the network speed)

just a thought - is there any pieces of the puzzle out there that could be adapted to bring something like this about? as opposed to (re)inventing the wheel?

just a thought (food for thought?)

---

### Post by Dragonbite on 2013-07-10
[Jolidrive]("https://drive.jolicloud.com/welcome"), it collects multiple location into one interface.  Not ideal, but they are working on it.

---

### Post by Roasted on 2013-07-10
Not that it's a direct solution to your particular question, but it wouldn't be a bad idea to look into ownCloud if you get the chance. There's something about a 3TB RAID'd server in my basement that is just dreamy. An old computer + 1 TB HDD + ownCloud would be a pretty pro setup, though it does come with some caveats, as you have to manage and back up the data. Just a thought in case you were interested. If not, sorry to intrude. :D

---

### Post by coffeeforkarma on 2013-07-10
I've been using [Backup That]("http://www.backupthat.com") for my cloud storage.  They use multiple email accounts to store all my files so I can get as much storage as I want.  Plus, I have access to all of my files through my email so I can access them on machines that I haven't ever used it on in a flash.

---

### Post by Copper Bezel on 2013-07-11
I've played with [cloudHQ]("http://www.cloudhq.net") and [StorageMadeEasy]("http://storagemadeeasy.com/lite_filemanager/") before while trying some stuff with Drive and Dropbox that failed to simplify my life. Unlike Jolidrive, both cloudHQ and StorageMadeEasy support moving and syncing files between separate cloud storage providers, and both provide web interfaces. cloudHQ is businessy and apparently $10 USD / month (pretty sure it used to be free) which is a little crazy, but it supports most of the leading clouds out there. StorageMadeEasy is free, is a little finicky looking, and supports *everything*, and it takes ftp connections (so you can access your clouds through Nautilus) for a one-time fee of $20 (and I'm tempted to try that myself,) but I remember running into some minor hangups with it (but the memories are vague and it's possible that the only problems I ran into weren't SME's, but related to documents getting formatted weirdly when I tried to two-way sync Dropbox and Drive, which I shouldn't have been doing in the first place.) It *does *have a monthly bandwidth cap.

Not as awesome as the "single drive" idea, but in principle (though probably not in practice) a way of making one's cloud work transparently as a "device."

---

