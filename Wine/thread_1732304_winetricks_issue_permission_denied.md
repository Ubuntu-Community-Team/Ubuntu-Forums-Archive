---
title: "winetricks issue: permission denied"
date: 2011-04-18
forum: Wine
---

### Post by chipppy on 2011-04-18
using 
ubuntu 10.10 fully updated as of 19/4/2011
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)

my problem is running Perfect World International[/URL] [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923")

I ran winetricks from terminal and got the following when i tried to install VCRUN6

```
chipppy@chipppy-desktop:~$ sh winetricks
winetricks: 14393: cannot create /home/chipppy/.cache/winetricks/track_usage: Permission denied
winetricks: 14393: cannot create /home/chipppy/.cache/winetricks/track_usage: Permission denied
winetricks: 14393: cannot create /home/chipppy/.cache/winetricks/track_usage: Permission denied
Executing w_do_call vcrun6
Executing load_vcrun6
Executing mkdir -p /home/chipppy/.cache/winetricks/vcrun6
mkdir: cannot create directory `/home/chipppy/.cache/winetricks/vcrun6': Permission denied
------------------------------------------------------
Note: command 'mkdir -p /home/chipppy/.cache/winetricks/vcrun6' returned status 1.  Aborting.
------------------------------------------------------
chipppy@chipppy-desktop:~$ 
```

I read the winetricks shouldnt be run as sudo so how do i change what to give it the correct permissions

cheers 
chipppy

---

### Post by cogadh on 2011-04-19
Did you happen to use sudo to run winetricks previously? If so, that is likely what has caused this problem. Basically, you no longer own the winetricks directories in your home directory, only root does. You should check the permissions on the directories, starting with /home/chipppy/.cache/winetricks and alter the permission on each accordingly. Instruction on doing that found here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by chipppy on 2011-04-19
Good Morning

Clicked Places and found the winetricks folder where you said it would be. checked the properties via right click --> properties --> permissions tab and you are correct the folder is owned by root

Opened terminal applications --> Terminal
Changed folders via cd .cache (terminal opens into home/chipppy)
Use sudo chown chipppy winetricks

When back to the properties windows and the owner had changed to chipppy, while there i changed the group from root to chipppy.

Ran winetricks and installed my vcrun6 without any problems.

All workig great now

Thanks heaps

---

### Post by d3v1150m471c on 2011-04-19
you shouldn't need to be root to run winetricks. if you got winetricks through the repositories you can call it simply by using `winetricks' and not `sh winetricks'.

---

