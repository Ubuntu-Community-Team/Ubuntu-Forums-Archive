---
title: "Client Won't Start and Now Music Downloads aren't working."
date: 2010-03-31
forum: Ubuntu One (CLOSED)
---

### Post by josemuniznyc on 2010-03-31
Hello All:

I had the "set-cap" exception problem, so when the fix was released, I updated. Since then, the ubuntuone-preferences dialog will not start or work. I tried the me bar, the system menu, and the CLI.

Now, I bought some music the first day the store opened and it downloaded fine. Then yesterday I bought another album and the store hangs on "downloading the files."  Six hours later, it still won't move. 

It gets weirder. The music store says its trying to download a couple of tracks from the first album (even though they are already downloaded), the second album shows up as downloaded under the Web UI, but doesn't show up at all on my desktop .ubuntuone folder.

I've tried the IRC a couple of times, with no response. (In fairness, it may have been bad timing, I'm in New York) I don't mind trying to sort this out myself, but I'd just like some more hints. I've looked at the syncd log and found the exception, but I don't know how else to restart the syncd. 

At the same time, my files *are* synching, and *one* of my address books is synching (my gmail account contacts aren't). I know this is alot at once, but I'm afraid of dividing the problem and missing something.

Ideas?

---

### Post by josemuniznyc on 2010-03-31
UPDATE:

I followed the advice on the board to use u1sdtool -c and then u1sdtool -s.

Which got me this:

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

the is_connected sounds good, but I have no idea about the IDLE. Still no downloading from the store (or u1) to the client.

---

### Post by joshuahoover on 2010-03-31
> **josemuniznyc said:**
> UPDATE:

I followed the advice on the board to use u1sdtool -c and then u1sdtool -s.

Which got me this:

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

the is_connected sounds good, but I have no idea about the IDLE. Still no downloading from the store (or u1) to the client.

I'm sorry to hear the Ubuntu One Music Store isn't working properly for you. You're definitely connected with the service based on the output you posted. If you're able to get on #u1msbeta on Freenode IRC from 13:00-22:00 UTC we can help you in real time. Otherwise, your best bet is to file a bug here: [https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+filebug](https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+filebug) and attach the log files from ~/.cache/ubuntuone/log to the bug report.

Thank you,

Joshua

---

