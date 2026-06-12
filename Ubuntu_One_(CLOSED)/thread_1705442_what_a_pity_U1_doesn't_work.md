---
title: "what a pity: U1 doesn't work"
date: 2011-03-12
forum: Ubuntu One (CLOSED)
---

### Post by claing on 2011-03-12
I am spending lots of time trying to get ubuntu one working.
But it's useless.
I followed instructions on this forum but maybe I didn't get the right one.
It seems that I succeeded in connecting, but sync doesn't start.
Here follow some more about what I got.


 claudio@claudio-ThinkPad-X41:~$ u1sdtool -s
State: LOCAL_RESCAN
    connection: With User With Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

claudio@claudio-ThinkPad-X41:~$ u1sdtool -w

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

What could I do?

Thanks Claudio

---

### Post by duanedesign on 2011-03-14
Does u1sdtool -c return the same error as the -w command?

I think this might be happening because there is a less-than-optimal storage of metadata in versions prior to what is now in nightlies and Natty Narwhal.

f you are interested in testing the new improved metadata storage (which takes syncdaemon about a second or two to start) then please have a look at [https://launchpad.net/~ubuntuone/+archive/nightlies](https://launchpad.net/~ubuntuone/+archive/nightlies). Please note that the nightlies releases are only automatically tested and there is a possibility that not all features are working at all times. (also you can not downgrade to a previous release once you upgrade)

Here are the commands to upgrade to the newest version. **You will not have a GUI if you run this on lucid or older releases**. You would need to use the command line (u1sdtool) to control U1. The ubuntuone-control-panel package only builds on Maverick and Natty right now.

```

sudo add-apt repository ppa:ubuntuone/nightlies

sudo apt-get update;

sudo apt-get upgrade; sudo apt-get install ubuntuone-control-panel
```

---

