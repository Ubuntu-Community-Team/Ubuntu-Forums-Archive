---
title: "If you add a &quot;shortcut&quot; to your Music/photos, for example, will it sync to Ubuntu One"
date: 2009-11-01
forum: Ubuntu One (CLOSED)
---

### Post by blackbird3216 on 2009-11-01
After having a near heart attack after losing my 9.10 install(I was able to retrieve my encrypted data w/ sudo cp), I am interested in this Ubuntu One service. However, if it only syncs what I put onto the folder, and what I upload, then it is pretty much useless for me. Can I link a "shortcut"(i don't know what they call it in linux) to my Documents or Photos, which would then sync with the service? That way, I don't have to keep copying my files to the folder to be able to sync them automatically, and the shortcut would just refer it to my documents.

---

### Post by paxmark1 on 2009-11-03
No,  not until Lucid in the 4th month of 2010.  sym-links (technical term for short cuts) are not yet workable with ubuntuone

But you can use dropbox and it goes in between linux boxen, windows boxen and also mac boxen with the same prices.

I still use an over-priced but good company in chicago that lets me 
use rsync -ssh scripts to back up what I choose.

---

### Post by James Henstridge on 2009-11-03
One option would be to move your music folder to the UbuntuOne folder, and then create a symlink back to ~/Music so applications that check the standard XDG folders can find it.

---

