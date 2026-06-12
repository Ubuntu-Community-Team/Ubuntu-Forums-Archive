---
title: "okay some forum database aid"
date: 2007-10-27
forum: The Cafe
---

### Post by SunnyRabbiera on 2007-10-27
Well I know this is right up the linux alley so I might as well ask.
Here is the situation, a forum I frequent is going to move to a new server and a probably new system.
They are currently dealing with a VERY outdated free version of invision power boards and the new forum will most likely be based on vbullitin or possibly simplemachines.
the problem is that we are dealing with a database that is a great 50 megs in text, the webmaster doesnt want to lose anything so I want to see if there is something that can help transfer the database.
Its a wide load but I have seen it done, so any advice on how to do it is appreciated.

---

### Post by kidders on 2007-10-28
Hi there,

The size of the database is largely irrelevant, really. Two major gotchas to watch out for are...
[LIST]
[*]**Software versioning** - Ideally, the source and destination should both be exactly the same version of the same server app.
[*]**Character encoding** - It's wise to be very careful not to jumble up character sets ... something that's far easier to do than you might think![/LIST]What database back-end are we talking about?

---

