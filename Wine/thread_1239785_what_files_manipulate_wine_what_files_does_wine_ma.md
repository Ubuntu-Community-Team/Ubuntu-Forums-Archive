---
title: "what files manipulate wine? what files does wine manipulate?"
date: 2009-08-13
forum: Wine
---

### Post by Meow27 on 2009-08-13
ok so ive been using Wine for two years already. and ive noticed that the older my OS is (usage wise) the crappier wine works, regardless if i install it new, or purge the whole .wine directory.

there are certain glitches i get, regardless of the version of Wine im using. i find them fixed when i reinstall or upgrade my ubuntu os.

therfore i come to the conclusion that Wine or some other programs, interact with the OS and Wine, and can get pretty screwy giving me consistently bad results.

---

### Post by Meow27 on 2009-08-25
bump

---

### Post by donkyhotay on 2009-08-25
Wine stands for "wine is not an emulator", and there is a reason for that. Wine takes the instructions given by the windows program and passes them to the linux system as if it was a native linux program. It also passes information from the system back to the program in the same way. Because of this linux just sees a 'regular' native program and the windows program sees a 'regular' windows environment. Thats the theory at least and the reality can be seen in just about every post on this forum. Because wine passes the instructions along like a native program, changes to your linux system will affect they way they work. This is especially true with games where you have 3D graphics, sound systems, networking, etc. involved. There aren't any specific 'files' that wine uses you can simply modify/replace (which I think is what you really want to know) since it uses the entire system just like any native linux program. Sometimes you can find a problem area and replace that (like maybe updating drivers on graphics issues) but there are no guarantees.

---

