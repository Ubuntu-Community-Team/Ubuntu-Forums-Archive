---
title: "LUKS: remove last key (slot 0)"
date: 2007-04-30
forum: Server Platforms
---

### Post by havenonick on 2007-04-30
hello,

i've encrypted a partition using LUKS. now i'd like to remove the last remaining key, but it seems to be not that easy as using cryptsetup luksDelKey <partition> 0:
it asks for a remaining key, but as the key i want to remove is the last one, there's no one remaining ):
how to get rid of it? 

thanks!

---

### Post by bobpaul on 2007-07-10
You can't have a luks partition without keys. If you remove the last remaining key you will have no way to access the data. The action you are attempting is therefore forbidden.

Instead, add a key to slot 1, then use the new key to remove the key from slot 0.

---

