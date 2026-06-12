---
title: "a software idea for music collaboration"
date: 2009-02-11
forum: The Cafe
---

### Post by yaaarrrgg on 2009-02-11
Here's an idea for a music application: 

A tool that allows two musicians (or more) to work on a project in real time, each recording tracks, from two or more different physical locations.

Newly recorded audio tracks would stream (p2p) to all other running instances of the application.  So that after each track is recorded, each person has a complete copy of the media files.  One person can assume control of the mix, then saving the project would propagate changes.  If this used compressed audio as the native format, you could stream this in real time without much latency. 

Also this app should run natively on the target platforms, without any additional services required.  It would not have a business model wrapped around it, since the goal would be to make it easier for musicians to make music.

Or if there are any servers, it would be very light-weight, only handling routing the machines together, then passing all processing to the target machines for p2p file sharing.  This way, any one person in a cluster could run the service.  The bottom line, is there's no business model wrapped around it ... limiting services, bandwidth, storage, etc.

Overall this software would be a cross between a multi-track recorder (like ardour or traverso), p2p file sharing, and maybe a simple instant messenger.  I suppose some form of file merging or locking might be useful (like svn/cvs) but a simpler approach would just be to allow individual contributers to fork a copy of the project.

Just a random thought ... :)

---

### Post by u'b'u'n't'u on 2009-02-11
Thats a great idea, submit it to ubuntu brainstorm!!:)

---

### Post by yaaarrrgg on 2009-02-27
That's a good idea... I added it here :) 

[http://brainstorm.ubuntu.com/idea/17985/](http://brainstorm.ubuntu.com/idea/17985/)

Really I suppose for a "poor man's version" of this, svn and ardour/traverso  could be used together to do about 90% of it.  

The only thing, a person would have to add/commit/checkout after each operation.  The repository would have to be setup manually as well.  Cleaning up sources could be tricky though.

Ideally, it would be better to catch the operations in the multitrack recorder and automatically fire off an svn command in the background.

Though it might not be hard to patch ... I'll have to keep looking into it.

---

### Post by Keyper7 on 2009-02-27
You are proposing the development of a new software. Brainstorm is popular but has very short reach in this regard. You would have more success posting this in musicians and developers forums. The programming section of this forum and the Ardour community might be good starting points.

---

