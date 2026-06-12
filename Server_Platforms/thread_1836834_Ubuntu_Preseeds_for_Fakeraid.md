---
title: "Ubuntu Preseeds for Fakeraid"
date: 2011-08-31
forum: Server Platforms
---

### Post by openfly on 2011-08-31
Has anyone ever successfully setup a network install to a Fakeraid ( dmraid ) disk target?

I can't find any references to it on the internet at all.  It's like no one has ever even tried.  The disk targets show up... but they show up as /dev/mapper/ devices with unique names.  And there's no way to predict them that I can tell.  So how the hell do you setup a preseed recipe for them?

Anyone have any ideas?

---

### Post by openfly on 2011-08-31
So, 

  I tried a few things. 

  The two main directions I thought would work were attempting to manually configure the volume names using the dmraid utility itself.  With ism, this appears to be something of an impossibility.  Not only that the utility is not exactly full featured or documented.

  I did not 100% confirm this route is impossible, but I am sure enough that it is that I am abandoning it.

  The only alternative I can think of is attempting to do some sort of string "sed ..." magic to identify the volumes with their unique identifiers.  And I am still pretty sure you end up in trouble that way anyways.

  So I went back to software raid.  I suggest you do the same.  That at least works with preseed info.  And it's pretty much better than any FakeRAID.

---

