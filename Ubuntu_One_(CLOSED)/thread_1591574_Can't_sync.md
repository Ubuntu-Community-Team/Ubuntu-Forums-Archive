---
title: "Can't sync"
date: 2010-10-09
forum: Ubuntu One (CLOSED)
---

### Post by PCTinker on 2010-10-09
When I first installed Ubuntuone I was able to sync a couple of folders. Because I was having problems with my CPU sticking at 100% I foolishly removed my computer from my Ubuntuone account. To resurrect it I uninstalled the Ubuntuone client and associated packages, then re-installed them.
That took me back to the Add Computer dialog in my Ubuntuone account.
Now when I launch Ubuntuone the preferences window pops up and correctly shows my Name, login details an account type. Ubuntuone does not log-in automatically and start sync'ing no matter how long I leave it.
If I go to the Devices tab I can either Restart or Remove my computer (don't want to go there again!) The Connect button is greyed out.
If I press Restart I eventually get the Connect button. Press on Connect and I get "Synchronisation in Progress", but only for 2 or 3 seconds before it reads "Disconnected". Sometimes it will have what looks like 2 or 3 attempts to sync before giving up.

Anyone know how to fix this so I can sync?

---

### Post by PCTinker on 2010-10-09
u1sdtol -s returned this when 'Ready'

State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

And this when I press Restart followed by Connect.

State: READY
    connection: Not User Not Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_METADATA

---

### Post by Sir_Pepe on 2010-10-10
Same problem here. Doesn't sync no matter how long I wait or how often I re-install.

---

### Post by Sir_Pepe on 2010-10-13
After one more round of re-installing everything Ubuntu One didn't help, i finally uninstalled everything related to Ubuntu One and cancelled my account. I've had problems like this for months and I don't have time for this kind of crap anymore. Back to Dropbox.

---

