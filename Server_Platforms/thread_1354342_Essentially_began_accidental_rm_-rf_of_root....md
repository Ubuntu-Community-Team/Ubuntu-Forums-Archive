---
title: "Essentially began accidental rm -rf of root..."
date: 2009-12-13
forum: Server Platforms
---

### Post by charmedguy18 on 2009-12-13
Yes, I know. Wtf?

What happened was I have a server I use over ssh. I use OS X at home and the server is an Ubuntu Jaunty server.

I tried using Fuse's SSH file system

```
sshfs
```

I found it was not letting me unmount it. And it wouldn't let me access it except through terminal. So, I attempted to unmount it by rm -rf'ing the link that it made. I thought this would just destroy the link, but no, it must have started to delete everything. I stopped it quickly after realizing it wasn't just deleting the link.

Luckily, I can still log in (I don't have Gnome installed, I just use ssh through terminal to log in). But I get these warnings when I log in:

```
bash: /usr/bin/groups: /bin/sh: bad interpreter: No such file or directory
bash: /usr/bin/lesspipe: /bin/sh: bad interpreter: No such file or directory
```

I haven't noticed anything happening other than those warnings. It just happened, though, so I have no idea what all this will affect.

I tried running:

```
sudo apt-get install --fix-broken
```
and
```
sudo apt-get install -f
```

None of that worked though. It came up as everything updated and installed correctly:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Is there anything else I can do to fix this? I can't upgrade to Karmic because it doesn't work with those servers for some reason. All they say is, don't do it or we get a re-image because it will create some error that will not otherwise be fixable. So is there anything else I may be able to do to fix it or would I have to probably get a re-image anyway?

Thanks

EDIT:
I realized /bin/sh would just be a hardlink to /bin/bash so I created one. I don't get the above warnings anymore.... However, I'm still wondering if there would be anything I could run to verify everything that should be in place is and to repair it if not. Thanks.

EDIT:
Okay so I saw that lesspipe could be involving .deb installations, so I tried to install something to test and make sure it would work. It didn't:
```
root:/bin# sudo apt-get install ed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ed
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 52.8kB of archives.
After this operation, 160kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/main ed 0.7-3ubuntu1 [52.8kB]
Fetched 52.8kB in 0s (248kB/s)
E: Sub-process gzip returned an error code (100)
E: Prior errors apply to /var/cache/apt/archives/ed_0.7-3ubuntu1_amd64.deb
debconf: apt-extracttemplates failed: Bad file descriptor
Selecting previously deselected package ed.
(Reading database ... 41264 files and directories currently installed.)
Unpacking ed (from .../ed_0.7-3ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up ed (0.7-3ubuntu1) ...
sh: gzip: command not found
install-info(/usr/share/info/ed.info.gz): 
dpkg: error processing ed (--configure):
 subprocess post-installation script returned error exit status 127
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by craigp84 on 2009-12-13
Haha :) Lesson learned tho right :)

sudo dpkg-reconfigure should do the trick, it'll go through every installed package, make sure all the files are still installed, with the right permissions etc.

It will prompt you to verify your configuration for packages where they're  setup to ask questions via debconf so even if you've blasted some config files, you should get back up and running pretty quick.

Hope it helps

---

### Post by charmedguy18 on 2009-12-13
> **craigp84 said:**
> Haha :) Lesson learned tho right :)

sudo dpkg-reconfigure should do the trick, it'll go through every installed package, make sure all the files are still installed, with the right permissions etc.

It will prompt you to verify your configuration for packages where they're  setup to ask questions via debconf so even if you've blasted some config files, you should get back up and running pretty quick.

Hope it helps
Another lesson learned after I rebooted and now there's absolutely no accessing it. :( Guess I'm getting a re-image.

Thank you though! Hopefully someone in the future will see this and do what you suggested before they reboot so it's not all totally in vain.

---

