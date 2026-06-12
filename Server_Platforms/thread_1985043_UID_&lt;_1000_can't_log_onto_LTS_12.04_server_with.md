---
title: "UID &lt; 1000 can't log onto LTS 12.04 server with Unity GUI !"
date: 2012-05-22
forum: Server Platforms
---

### Post by dchen on 2012-05-22
Just upgraded from 11.10 to 12.04 LTS server version.
Then installed with the Desktop GUI (via 'sudo apt-get install ubuntu-desktop')
After reboot, the Unity GUI showed up, but only showed up with UID >= 1000 users !!
Those UIDs > 500 and < 1000 WON'T show !

Under 11.10, the Unity GUI showed up all users with UID > 500.
The UIDs between 500 and 1000 which were migrated from Fedora to Ubuntu a couple months ago!

Those UIDs > 500 and < 1000 users can  ssh to the 12.04 LTS server though !

Is this the Unity or 12.04 LTS problem ?!

---

