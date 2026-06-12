---
title: "Don't install Wine 1.3"
date: 2010-10-20
forum: Wine
---

### Post by Daemn on 2010-10-20
At least for me, right off the bat, it has issues. It takes 1-2 minute delay to load, which I assume is because on the Drives tab it has nothing, just says "Failed to connect to mount manager, the drive configuration cannot be edited.". I guess it has a huge timeout or keeps retrying and retrying, for every single application (.exe).

Virtual desktop is also crazy messed up, moving the window around is choppy like nothing I've seen before.

Edit: Had to delete wine config, seems to be working. Virtual desktop still very much screwed up.

---

### Post by cwwilson721 on 2010-10-20
1.3 works perfectly fine for me. Never had that issue.

Try this: Rename your ~<user>/.wine folder, then rerun winecfg. That way your previous setup is still there, so you don't lose anything

 Bet the issue wasn't 1.3. It was something you previously setup in wine

---

