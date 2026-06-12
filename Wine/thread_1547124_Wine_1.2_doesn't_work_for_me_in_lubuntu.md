---
title: "Wine 1.2 doesn't work for me in lubuntu"
date: 2010-08-06
forum: Wine
---

### Post by jlunse on 2010-08-06
**Note!** This is about Lubuntu 10.04 and not Ubuntu 10.04.

I would like to install a program called spotify.exe using Wine 1.2 in lubuntu 10.04. However nothing happens when I right click the downloaded installer named: "SpotifyInstaller.exe" and when select the installation with Wine.

Installed Wine 1.2.0 using package manager where I selected playonlinux.

The installation of Spotify works just fine in Ubuntu 10.04 but I can't get this working in Lubuntu 10.04.

I need a lightweight GUI like Lubuntu since my daughter have a very old IMB R31 computer and she desperatly needs the Spotify for music listening.

Any ideas?

---

### Post by dino99 on 2010-08-06
open a console and run: wine SpotifyInstaller

you might find usefull errors logged too if it fail, look at .wine/spotify/log

*** note: install latest 1.3

---

### Post by jlunse on 2010-08-06
I tested: wine SpotifyInstaller
..ends up in:
[I]herlo@Herlo:~$ wine spotifyinstaller
wine: cannot find L"C:\\windows\\system32\\spotifyinstaller.exe"
[/I]

I then tried to copy 'spotifyinstaller.exe' with no success. Nothing happens when I try to 'Open C:\' in the Wine program menu.

---

### Post by dino99 on 2010-08-06
take care of the exact name (case sensitive) and the location (where this exe is downloaded)

---

### Post by jlunse on 2010-08-06
Yes, taking care of exact name and location is a good idea, thanks!
I managed to install Spotify using Wine 1.2 in Lubuntu 10.04:
1. Copied Spotify Installer.exe to the desktop.
2. Started Uninstall Wine programs.
3. Install - Success!
Still strange:
- why nothing happens when I just RMB Spotify installer program and try to launch it.
- why Wine's the menu option "Navigate C:\" doesn't work.

Anyway, I'm happy now - thanks!!

---

### Post by cogadh on 2010-08-06
Doesn't Spotify have a Linux Native client? Checking.....

Yep: [http://www.spotify.com/int/download/previews/](http://www.spotify.com/int/download/previews/)

Spotify isn't available in my region, so I can't really comment on how the Linux client works, but if running it through Wine isn't working for you, going native might be the best solution.

---

### Post by jlunse on 2010-08-06
Good News! I didn't know about this. Will try it and come back.

thanks!//Johan

***Updated*** native client installs nicely but it seems like I need a different a account type (maybe premium) to login :(

bad for them, since they wont get any early test feedback from me.

still, "wine + spotify" works fine in both ubuntu and lubuntu.

---

