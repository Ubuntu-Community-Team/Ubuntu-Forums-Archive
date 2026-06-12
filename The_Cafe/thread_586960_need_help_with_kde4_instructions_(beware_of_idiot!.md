---
title: "need help with kde4 instructions (beware of idiot!)"
date: 2007-10-22
forum: The Cafe
---

### Post by fuscia on 2007-10-22
ok, so far, i've gotten all the kde4 stuff installed and i want to run it as a seperate session (it's even to the point where i have a seperate entry for it in kdm). here's the last part i don't get: i can't seem to figure out how to get this last step done...

"To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4."

these are the four export lines...

"export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4"

but i can't seem to get them into /usr/lib/kde4/bin/startkde. i've tried opening it with *kdesu kate*, but the stubborn, little bugger doesn't seem to want me to add anything. is this something i should leave to the big kids, or am i almost there?

---

### Post by justin whitaker on 2007-10-22
> **fuscia said:**
> ok, so far, i've gotten all the kde4 stuff installed and i want to run it as a seperate session (it's even to the point where i have a seperate entry for it in kdm). here's the last part i don't get: i can't seem to figure out how to get this last step done...

"To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4."

these are the four export lines...

"export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4"

but i can't seem to get them into /usr/lib/kde4/bin/startkde. i've tried opening it with *kdesu kate*, but the stubborn, little bugger doesn't seem to want me to add anything. is this something i should leave to the big kids, or am i almost there?

The only way I could get that thing open was firing up a terminal, becoming root, and editing it that way. kdesu did not work.

---

### Post by osxcapades on 2007-10-22
This should probably be moved to an appropriate support forum.

---

### Post by FuturePilot on 2007-10-22
> **fuscia said:**
> ok, so far, i've gotten all the kde4 stuff installed and i want to run it as a seperate session (it's even to the point where i have a seperate entry for it in kdm). here's the last part i don't get: i can't seem to figure out how to get this last step done...

"To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4."

these are the four export lines...

"export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4"

but i can't seem to get them into /usr/lib/kde4/bin/startkde. i've tried opening it with *kdesu kate*, but the stubborn, little bugger doesn't seem to want me to add anything. is this something i should leave to the big kids, or am i almost there?
You're probably almost there. Try Nano instead;)
Also I think kdesu has been replaced with kdesudo.

---

### Post by fuscia on 2007-10-22
> **osxcapades said:**
> This should probably be moved to an appropriate support forum.

which one would that be? the "morons shouldn't try this stuff" forum? 


i'll try it in a terminal when i get home. thanks for the responses, so far. i'll let you all know if i managed, or not.

---

### Post by fuscia on 2007-10-22
woohoo! i made it! nano was the key. thanks, guys. (hope the birds haven't eaten that breadcrumb trail yet...)

---

