---
title: "Ubuntu One, Existing Solutions No Help"
date: 2012-11-08
forum: Ubuntu One (CLOSED)
---

### Post by alkh3myst on 2012-11-08
I am also getting this IPC error message from the Ubuntu One GUI. It worked fine until I got stuck one day, and took a long time entering the keyring password. It hasn't worked since then. It won't sync, and a Python process hijacks the CPU, freezing my whole system until I can stop it. I tried updating to the absolute latest version, as I saw elsewhere here, ran in to unmet dependencies, then went back to the standard version.I also tried to add the PPA for the latest version, which is 404'ed. 

Running "u1sdtool" in the terminal has similar sad results. It seemed to still be "connected", even though I had exited the control pannel and I tried --refresh-volumes. This was the result.

musa@Mawhrin-Skel:~$ u1sdtool --refresh-volumes
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.NoReply:

Then my terminal window froze. After opening a new one, this happened. 

musa@Mawhrin-Skel:~$ u1sdtool --connect

Oops, an error ocurred:
org.freedesktop.DBus.Error.NoReply: 

None of the fixes I've seen on the Forums are working for me. Can somebody please advise me on which script I can run to get a full diagnostic of my problem?

musa@Mawhrin-Skel:~$ u1sdtool --status
State: LOCAL_RESCAN
    connection: With User With Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING

 
](*,)

It worked for about 15 minutes. I shut the computer down and go home, now it's back to being useless. Nobody has any ideas huh?

---

