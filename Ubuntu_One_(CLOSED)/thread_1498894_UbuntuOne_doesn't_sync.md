---
title: "UbuntuOne doesn't sync"
date: 2010-06-01
forum: Ubuntu One (CLOSED)
---

### Post by al.adab on 2010-06-01
hello,

my pc was correctly linked to UbuntuOne. I dragged a number of folders (none very big) into the UbuntuOne folder in my system, and one day later no file has been uploaded to UbuntuOne. Only the folders appear under "files" in UbuntuOne online. 

If I click on UbuntuOne on my taskbar, the UbuntuOne preferences is launched. It seems to connect fine, in fact it shows my name and the name of my device. It also says "sync in progress". But nothing really happens. No files are being uploaded. The connection is fairly fast, so that shouldn't be an issue. Also every single file in my UbuntuOne folder (in my system) shows an "upload icon" (a sort of white curved arrow). 

What do you think the matter might be? Since I've upgraded to Ubuntu 10.04 UbuntuOne has given me a lot of troubles...

---

### Post by philinux on 2010-06-01
Moved to ubuntuone forum.

---

### Post by sk1887 on 2010-06-03
It happens to me too. I keep trying pressing the button restart and connect. I've just happened to have recursively deleted the home folders, UbuntuOne isn't updating a thing. Practically it should be like I am using another computer, it just hangs on synchronization in progress... nothing happens.

---

### Post by vinx on 2010-06-04
Same here. It just doesn't sync files. Also adding new directories fails and files in the "Ubuntu One" folder don't get to the server.

> u1sdtool -s

```
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH
```
Which should be ok, according to [https://wiki.ubuntu.com/UbuntuOne/MusicStore](https://wiki.ubuntu.com/UbuntuOne/MusicStore)
When reconnecting with "u1sdtool -q; u1sdtool --start; u1sdtool -c", I see LOCAL_RESCAN, AUTHENTICATE, SERVER_RESCAN, QUEUE_MANAGER
(sloooowwwww).

In ~/.cache/desktop-couch/log/desktop-couch-replication.log I see loads of errors for other sync-problems (service offline), but nothing about uploading files.

See also [https://bugs.launchpad.net/ubuntuone-client/+bug/580399](https://bugs.launchpad.net/ubuntuone-client/+bug/580399) 

This might be helpful for figuring out what's wrong: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/932](https://answers.edge.launchpad.net/ubuntuone-client/+faq/932)

---

### Post by Leed on 2010-06-04
Should have looked at the forums first, I wasted some hours wondering if I'm just to daft to get it working with all my machines. 

Looks like we all have to wait for the Dev's to get it fixed. Hope that comes soon, as I'm really beginning to like U1

---

### Post by sk1887 on 2010-06-04
my u1sdtool -s:
State: AUTHENTICATE
    connection: With User With Network
    description: doing auth dance
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH
dance? haha

---

### Post by wojox on 2010-06-04
```

wojox@wojox-desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

```

I don't know what the problem is? All good here.

---

### Post by sk1887 on 2010-06-06
> **wojox said:**
> ```

wojox@wojox-desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

```I don't know what the problem is? All good here.
It got fixed yesterday. Now the sync is so fast !

---

### Post by duanedesign on 2010-06-07
yep, it looks like the code changes have made it onto the servers and things are improving.

---

### Post by al.adab on 2010-06-08
magically fixed! :) thanks whoever did this!!!

---

### Post by duanedesign on 2010-06-08
The Ubuntu One team has been working tirelessly to fix the performance degradation that happened when tens of thousands of new users joined the  service on the release of Lucid. I am happy to see the performance of Ubuntu One improving. I hear there are even more changes coming that will speed things up  even more.

---

### Post by HornedBeast on 2010-06-09
My Ubuntu One wasn't syncing either, looked everywhere, posted logs on Launchpad. Then suddenly, this morning, it started working! And really quickly too...

One thing that I think should be made ALOT clearer though, is that Ubuntu One DOES NOT WORK through a Proxy. I think this needs to be made insanely clear as it tripped me up for a few weeks.

Glad things are on the up. Next thing is to upgrade to a 50gb plan and write some tools to filter out things like .iso's from syncing automatically :).

---

### Post by mickcalcara on 2010-06-09
Mine started working again too.. Glad to hear more improvements are in the works. Thanks.

---

