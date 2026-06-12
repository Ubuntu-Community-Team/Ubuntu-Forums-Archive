---
title: "nautilus via samba slow after update"
date: 2009-02-10
forum: Server Platforms
---

### Post by 80aless on 2009-02-10
Hi, I am a kind of newbie so be patient. I also posted this on bugreport. I often connect to a remote server with ssh and with nautilus thru samba (eg: smb://remote.server.nl/loginName/path ) . After an Ubuntu update ssh is all right, nautilus is extremely slow. Also the ubuntu desktop is irresponsive (cannot click on a second desktop but I can switch to it with Ctrl+Alt+arrows, cannot open an existing window but I can use Alt+Tab, old windows are not there etc).
The update was the following:
[PHP]Commit Log for Wed Feb 4 09:34:06 2009

Upgraded the following packages:
ufw (0.16.2.3) to 0.16.2.4
xserver-xorg-video-ati (1:6.8.0-1) to 1:6.8.0-1ubuntu1
xserver-xorg-video-intel (2:2.2.1-1ubuntu13.7) to 2:2.2.1-1ubuntu13.8
[/PHP]
Removing ufw does not help.
```

apt-cache policy nautilus
nautilus:
  Installed: 1:2.22.5.1-0ubuntu1
  Candidate: 1:2.22.5.1-0ubuntu1
  Version table:
 *** 1:2.22.5.1-0ubuntu1 0
        500 http://nl.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.22.2-0ubuntu4 0
        500 http://nl.archive.ubuntu.com hardy/main Packages
```

Any help?
Alex

---

### Post by 80aless on 2009-02-27
I did
sudo apt-get remove xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-ati
and it fixed another problem occurring with the sound. I did the same with xserver-xorg-video-intel but no improvement with nautilus.
Any help would be appreciated

---

### Post by 80aless on 2009-03-11
noooobody knows

---

