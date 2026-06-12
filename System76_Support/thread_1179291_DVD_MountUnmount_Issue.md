---
title: "DVD Mount/Unmount Issue"
date: 2009-06-05
forum: System76 Support
---

### Post by jpoRS on 2009-06-05
Whenever I boot the computer WITHOUT a DVD in the drive, I can pop in a DVD, wait a few seconds, and it auto-opens in VLC.  Hooray!  But then the problems arise.

If I press the eject button, nothing happens.  My processor jumps about 10% for a second or two (or at least my processor-tachometer widget says so) then nothing happens and everything goes back to how it was before I pressed the button.

If I right click>Eject it will eject, and the icon will disappear off of my desktop.  However when I put in a new DVD it will not mount, and if I go to Places, instead of saying "CD-R/DVD Drive" it says "Enter the Dragon" or whatever the ejected DVD was called.

I have a Panp4i running a fresh install of Jaunty 64.  I haven't had the chance to try it on a CD yet and see what happens, but will do so asap and post the result.

Thanks,
jim

---

### Post by yaroto98 on 2009-06-05
What happens if you rightclick->Unmount before you rightclick->eject?

---

### Post by thomasaaron on 2009-06-05
Enter the Dragon, nice. Did you hear about David Carradine? Sounds like his death is a bit... shady. But he actually beat Bruce out for the part or Caine in the old Kung Fu series.

In addition to the above suggestion (which is a good one), what if you shut down VLC first?

---

### Post by jpoRS on 2009-06-05
I did know that Bill died but I did not know there was anything suspicious about it.  Will definitely wikipedia that later. Anyway!

Anyway, if I Unmount Volume I can then use the tray button to eject, and I can then load and mount another DVD.  So I guess that works for now, but I would like the tray button to work normally.

Thanks!
jim

---

### Post by thomasaaron on 2009-06-05
[http://en.wikipedia.org/wiki/David_Carradine#Death](http://en.wikipedia.org/wiki/David_Carradine#Death)

I may be wrong, but I'm thinking that the eject button communicates directly with the firmware in the drive. Not sure there is an "unmount" associated with it.

But I know there are instances when the eject button is overridden too. It's definitely something the devs should have a look at.

---

### Post by yaroto98 on 2009-06-05
I'm pretty sure it's directly connected to the firmware, and dvd player specific. However, if you can figure out a way to map the key, you could bind it to a script that unmounts and then ejects. However, that seems like a lot of work for what you were probably hoping was just a quick fix.

---

### Post by jpoRS on 2009-06-05
Hmm.  I feel like on my previous install (factory installed Hardy) it worked with just hitting the tray button.  Or am I recalling incorrectly?

Had a guy I graduated High School with go out like that.  It was sad until we got more details then it was sad and embarrassing.

jim

---

### Post by miniyak on 2009-06-05
i just had an issue similar to this on a mint 7(jaunty) install. System eject works but. physical eject button fails to respond after puting disc in. i would think that the button directly communicates to the drive but if im wrong, this could be a bug in jaunty base on what your saying. maybe our drives are similar? i'll try to find the model number, i think i going to have to take the drive out for that though... I bring model into this cause my pangolin drive seems to be void of this issue and its also running jaunty, 64vs.32 mint7 however.(if that makes a difference...)

---

