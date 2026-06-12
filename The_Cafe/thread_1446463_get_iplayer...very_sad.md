---
title: "get_iplayer...very sad"
date: 2010-04-04
forum: The Cafe
---

### Post by UbuSheldon on 2010-04-04
Sigh.  get_iplayer was amazing and now it looks like it's dead.  It was working but now I get this when I try to download some progs (some still download)...

INFO: No specified modes (iphone,flashhigh,flashstd,flashnormal) available for this programme with version 'default' (try modes: flashhd1,flashhd2)
ERROR: Failed to record 'Tinga Tinga Tales - Why Porcupine Has Quills (b00r4x41)

I've read other threads on the demise of get_iplayer and am really pi$$ed about it.  Can anyone help with the above? 

I do hope someone picks up the get_iplayer baton sometime soon.

CD

---

### Post by UbuSheldon on 2010-04-04
Actually folks it seems to be just the HD content that's not downloading.  Any fixes?

I'm so cross with the BBC.  So mean spirited.

---

### Post by Greenwidth on 2010-04-04
I don't see a listing for 'Tinga Tinga Tales - Why Porcupine Has Quills' on the HD site..

'Tinga Tinga Tales - Why Lions Roar' is on there (currently) so try:
```
get_iplayer -g --pid b00qtn10 --vmode=flashhd
```
works for me.

Also, someone has forked it on github, so hopefully it's not dead.
[http://github.com/jjl/get_iplayer](http://github.com/jjl/get_iplayer)

---

