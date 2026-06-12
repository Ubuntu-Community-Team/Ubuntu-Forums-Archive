---
title: "System Sounds"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by nesl247 on 2007-10-18
It would be nice if we could have some more sounds such as a suspend sound, hibernate sound, etc.

Also, integrating the gdm sound selection into the sound capplet would also make sense (sounds should probably be in the same location).

---

### Post by Zdravko on 2007-10-19
Yeah, I'd love more sounds!

---

### Post by Next.Step on 2007-10-20
I'd love NEW sounds!
I've been listening to that clappy joke login sound since edgy. It would be nice if somebody changed it for something more like Dapper had. You know, something more....relaxing and less disturbing

---

### Post by NilsE on 2007-10-20
> **Next.Step said:**
> I'd love NEW sounds!
I've been listening to that clappy joke login sound since edgy. It would be nice if somebody changed it for something more like Dapper had. You know, something more....relaxing and less disturbing
You can put whatever .wav sound files you like in /usr/share/sounds

Then go into sound preferences and select it using the "Select Sound File" option on the sounds tab.

As a matter of fact the file can be anywhere and you browse to it but I think it only works with wav files.

---

### Post by Next.Step on 2007-10-20
Yea I already have dapper login.
But that's not the point. The point is that sounds should comply to the "new" feeling of each release

---

### Post by Awalton on 2007-10-20
The real endgame of this is that Ubuntu should help finish Bango and implement it.

[http://www.freedesktop.org/wiki/Bango](http://www.freedesktop.org/wiki/Bango)
[http://tango.freedesktop.org/Bango](http://tango.freedesktop.org/Bango)
[http://ubuntuforums.org/showthread.php?p=919723](http://ubuntuforums.org/showthread.php?p=919723)

The spec could use some fleshing out to bring it up to parity with Tango (such as styles and compression formats for sound or whether we really care about these things).

On top of that, all that's really missing are the sound files themselves, and a way to manage Bango themes. The latter could be done with 15 minutes and Python (or by adapting/reworking Gnome's current Sound-Preferences dialog), the former, well, is up to the Arts and Crafts boys and gals.

---

### Post by GOfree on 2008-05-21
> The real endgame of this is that Ubuntu should help finish Bango and implement it.

Has anything been done about this since Gutsy?

---

### Post by AmbiguousOutlier on 2008-09-27
Sorry to revive an old post but I was wondering if anyone has made anything to install a new sound theme?

EDIT:

Does anyone know how i can get this sound to play whenever I start mozilla?

[http://www.saunalahti.fi/frog1/wavs/welcomenet.wav](http://www.saunalahti.fi/frog1/wavs/welcomenet.wav)

---

### Post by gnomeuser on 2008-09-27
> **Awalton said:**
> The real endgame of this is that Ubuntu should help finish Bango and implement it.

[http://www.freedesktop.org/wiki/Bango](http://www.freedesktop.org/wiki/Bango)
[http://tango.freedesktop.org/Bango](http://tango.freedesktop.org/Bango)
[http://ubuntuforums.org/showthread.php?p=919723](http://ubuntuforums.org/showthread.php?p=919723)

The spec could use some fleshing out to bring it up to parity with Tango (such as styles and compression formats for sound or whether we really care about these things).

On top of that, all that's really missing are the sound files themselves, and a way to manage Bango themes. The latter could be done with 15 minutes and Python (or by adapting/reworking Gnome's current Sound-Preferences dialog), the former, well, is up to the Arts and Crafts boys and gals.

Why.. the FreeDesktop.org spec is infact inspired by Bango, which is what libcanberra uses.

[http://freedesktop.org/wiki/Specifications/sound-theme-spec](http://freedesktop.org/wiki/Specifications/sound-theme-spec)

Seeing as the spec is not 1.0 yet (currently it's 0.3 draft), you can make your suggestions as bugs on bugzilla.freedesktop.org or partake in the debate on the mailing list.

---

### Post by Lachinchon on 2008-09-28
Am I missing it somewhere, or is there no sound option for "empty trash"? That was my favorite sound to switch around in Windows, You can't have a silent trash bin!

---

### Post by gnomeuser on 2008-09-28
> **Lachinchon said:**
> Am I missing it somewhere, or is there no sound option for "empty trash"? That was my favorite sound to switch around in Windows, You can't have a silent trash bin!

Again the spec is in draft status, if you want this then state your case on the mailing list as a well reasoned argument. You can change the future.. today.

[http://lists.freedesktop.org/mailman/listinfo/xdg](http://lists.freedesktop.org/mailman/listinfo/xdg) <-- the key to salvation

But before you do so please read the existing spec, so you can make as good a first proposal as to naming and placement in the spec.

[http://freedesktop.org/wiki/Specifications/sound-theme-spec](http://freedesktop.org/wiki/Specifications/sound-theme-spec)

But to save you time. From the current spec.

trash-empty - The sound used when the user empties the trash. 

So as soon as Ubuntu integrates libcanberra this is going to be on your desktop. We preempted you. However the method still applies, you have full freedom to participate and you are most welcome, not just with the sound spec, everywhere.

---

### Post by macabro22 on 2008-10-20
will we have system sounds in Intrepid Ibex?

---

