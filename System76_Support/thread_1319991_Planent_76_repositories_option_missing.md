---
title: "Planent 76 repositories option missing"
date: 2009-11-08
forum: System76 Support
---

### Post by Eyore15 on 2009-11-08
I have a new Starling.  I wondered why I wasn't getting the same updates to the system76 driver that were being discussed here.  I found the reference in the knowledge base that said to check "Planet76.com Repositories" to receive the updates.

When I went to software sources, and chose third-party software, I discovered I don't have a "planet76.com repositories" option available.

I can't find a place in the knowedge base that tells me how to add it either.

The current driver on my starling is 2.3.7 -- the one that came installed with it.  I found the directions for doing a manual upgrade in the middle of the instruction set for upgrading to 9.10, so at least I've got the new driver.

It's pretty obvious that I need the planet76.com repositories though so I can get the automatic updates.  Can someone tell me how to go about adding the repositories option to my third-party software tab in software sources?

tnx

mcm

---

### Post by marshmallow1304 on 2009-11-08
The line you need to add is
```
deb http://planet76.com/repositories/ ./ #System76
```

Then go to a terminal and run
```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```
so you don't get authentication warnings.

---

