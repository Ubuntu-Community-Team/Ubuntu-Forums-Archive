---
title: "Ubuntu One no connection"
date: 2010-11-09
forum: Ubuntu One (CLOSED)
---

### Post by GuiroZ on 2010-11-09
Ubuntu One says I have no network connection, which I obviously have. When I select System->Preferences->Ubuntu One the windows appear but I cant put my account nowhere. If I click on "manage account" a firefox windows open up and I can login in firefox but ubuntu one window is still without account.
I tried:

u1sdtool -s
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

Than i tried:
u1sdtool -c
than "u1sdtool -s" again with the same result.

I tried to delete the password key in System->Preferences->Password... but there are no UbuntuOne keys there.

I tried to unistall, clear the preferences file than install again but with the same result.
I've look in the forums but I didn't find any suitable solution.

Any idea or suggestion?
Thanks
(sorry for my english)

---

