---
title: "Sync thunderbird contacts/calendars"
date: 2010-10-21
forum: Ubuntu One (CLOSED)
---

### Post by sambarluc on 2010-10-21
Hi,

is it possible to sync thunderbird contacts and calendars (lightning) through Ubuntu One, for sharing from different machines? Or, are there any plans in the future to implement such thing?
I know I could probably go through google calendar, but I don't want to do so.

Thanks

---

### Post by pfnorris on 2010-10-22
There is no direct support for this under Ubuntu One at present, so I tried to do this using the file sync process. My logic was if I sync the .thunderbird folder, in my home folder, then I should end up with the same Thunderbird profile on all machines.

Unfortunately it did not work. The first time I launched Thunderbird on a second PC it renamed the synced .thunderbird folder to something else, and created a new one. When I changed that arrangement back to how I wanted it and re-launched Thunderbird, it still could not make sense of the synced profile, particularly so far as extensions were confirmed.

I have yet to discover a solution to this.

Nobby

---

### Post by gogolink on 2011-01-02
You could keep the entire profiles folder in your Ubuntu One folder.  I'm keeping Thunderbird fully synchronized (mail folders, address books, calendar) across two Ubuntu computers using Dropbox; but I believe it would work the same way using Ubuntu One.  I describe what I did [here]("http://ubuntuforums.org/showthread.php?t=1651563").

---

