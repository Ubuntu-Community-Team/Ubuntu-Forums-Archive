---
title: "[SOLVED] Unable to update Thunderbird after system upgrade to Hardy"
date: 2008-05-08
forum: Ubuntuzilla
---

### Post by MrHobbes on 2008-05-08
Hello,
I've been looking for several hours for a solution or a similar case in the forums but I didn't get anything. As I managed to solve my problem by myself, I thought it would be nice to share the thing, even if it is not really interesting, because 1) I think that if it could help someone it worth the point and it would be in the best place, and 2) because it's a cool way to post a first message : sharing before asking !

The symptoms:
=============================
I recently bought a laptop with Gusty preinstalled, and I quickly found and installed Ubuntuzilla, then Thunderbird to get the latest available version.
Everything was fine and I upgraded my system to Hardy 1 week after it was released.
2 weeks after, a new version of Thunderbird is available, and the scheduled check informed me I should run the update.
So I try in a term:
 gksudo thunderbird &
then "Help > Check for updates" and then a message saying I was up to date.

 ubuntuzilla.py -a checkforupdatetext -p thunderbird
says the version on my system was 2.0.0.12 and the latest was 2.0.0.14

So I couldn't update Thunderbird because it didn't find a newer version.

The cause:
=============================
During the system upgrade, the link to Thunderbird in /usr/bin/ which was pointing to the Ubuntuzilla version was replaced by one pointing to the official one, which was up-to-date at the release time.
The update-check of Ubuntuzilla check the version of the executable pointed by the "thunderbird" in PATH, comparing the distro version with the latest available.
Meanwhile, when I tried to update Thunderbird, it used the distro repositories, which didn't contained a more recent version !

To know which application is launched, I used
 which thunderbird


The cure:
=============================
Long post for a small problem: just restore the link in /usr/bin after a quick backup:
 sudo mv /usr/bin/thunderbird /usr/bin/thunderbird-ubuntu-8.04
 sudo ln -s  /opt/thunderbird/thunderbird /usr/bin/

then I tried again
 gksudo thunderbird &
"Help > Check for updates" and it worked.

Hope it will help.

---

### Post by nanotube on 2008-05-13
hey, thanks for the note.

just a suggestion - instead of just "mv" ing the ubuntu thunderbird link out of the way, use dpkg-divert. otherwise, next time a thunderbird upgrade package comes through the repos, it will overwrite your link again.

use this:
```
sudo dpkg-divert --divert /usr/bin/thunderbird.ubuntu --rename /usr/bin/thunderbird
```

---

### Post by MrHobbes on 2008-05-17
Thanks for pointing this out !
In fact, I think that the right way to use Ubuntuzilla is to uninstall the official package so as to avoid this kind of "collision" between the programs.
So, as I have been testing Ubuntuzilla for a few weeks and it seemed fully functional, I finally removed the official package and kept only Ubuntuzilla :)
Futhermore, I had to manually recreate the link to /opt/thunderbird/thunderbird because the official package was updated and silently restored the previous version !
Quick tip : the icon of thunderbird can be found at /opt/thunderbird/icons/mozicon50.xpm (for your quick launch widgets).

---

### Post by the.phantom on 2008-05-31
i'm a bit of a lightweight
but
i found the easy to do it for me was to just get into synaptic package manager and "freeze" the version of t-bird and firefox! that way it won't upgrade it and for a lightweight i could change it if i needed to

---

