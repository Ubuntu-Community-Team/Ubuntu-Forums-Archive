---
title: "Setting up a Murmur server [Mumble]"
date: 2010-12-22
forum: Server Platforms
---

### Post by MarkusDavey on 2010-12-22
Hello, 

I am currently having issues setting up a mumble-server, with regards to when people connect to the server, they cannot rightclick > register self, nor is there the ability for the SuperUser to edit the ACL to allow self registration, as it is not an option.

any ideas?

i would give you more information but i do not recall what version this PC is running. 9.04 Desktop maybe.

---

### Post by eriktheblu on 2011-01-04
As SuperUser, add a new ACL below the current @all. The lower ACL will override the other.

---

