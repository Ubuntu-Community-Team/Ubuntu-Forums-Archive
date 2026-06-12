---
title: "Spotify Crash in Beta 1"
date: 2015-03-01
forum: Ubuntu Development Version
---

### Post by martytm42 on 2015-03-01
Just updated to Beta 1 yesterday from 14.10 and when running Spotify I get a consistent crash once I make it about half way through a song. Another user reported this bug on Launchpad under Ubuntu MATE, but it seems to be a general issue as I'm running Xubuntu. Interestingly, when launched from the terminal I haven't been able to reproduce the crash.

As per the other user, this also seems to be an issue on fresh installs so it's not a result of upgrade wonkyness. I'm not sure if this is an issue with Spotify or some updated library somewhere so I don't know if it'd be appropriate to open a standard Ubuntu bug on Launchpad.

EDIT: Just got it to crash when running from a terminal, here's the last few lines of output:
> content-type missing in HTTP POST, defaulting to application/x-www-form-urlencoded. Use QNetworkRequest::setHeader() to fix this problem.20:18:18.989 I [ApplicationPage.cpp:66          ] Unloading application browse.
20:18:18.989 I [AppManager.cpp:535              ] Removing instance of application browse.


Segmentation fault (core dumped)




Not sure exactly the meaning, looks like Spotify might be using some function that's deprecated?

---

### Post by Mateusz Stachowski on 2015-03-01
Yes the crash happens with new gtk+-2.24.26. Users on Spotify forums reported that downgrading this library resolves the problem.

[https://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/td-p/842969/page/29](https://community.spotify.com/t5/Help-Desktop-Linux-Mac-and/Spotify-0-9-11-for-GNU-Linux/td-p/842969/page/29)

There was no response from Spotify devs and I don't think there will be any because they most likely only target the LTS release.

BTW what is the number of bug report that you mention on Launchpad.

---

### Post by martytm42 on 2015-03-01
This is the link: [https://bugs.launchpad.net/ubuntu-mate/+bug/1426726](https://bugs.launchpad.net/ubuntu-mate/+bug/1426726)
Probably should have included that in the OP, sorry about that. I wasn't sure if it'd be appropriate to open a bug for general Ubuntu, but I guess the fault is on Spotify's end. 
Thanks!

---

### Post by martytm42 on 2015-03-01
Sorry for the double post, but I believe I've fixed the issue without having to resort to a system downgrade of the libgtk2.0 package as suggested on the spotify forum. Apparently the AUR includes a fix for the issue by adding the older libraries into Spotify's custom library directory (PKGBUILD here: [https://aur.archlinux.org/packages/sp/spotify/PKGBUILD](https://aur.archlinux.org/packages/sp/spotify/PKGBUILD)).

I adapted this to the ubuntu install by downloading the libgtk2.0 package from the utopic repository, extracting the libgtk and libgdk files from there and copying them to /opt/spotify/spotify-client/Data and recreating the library simlinks found in the original package in that folder as well. After doing this I've had no crashes with Spotify.

---

### Post by Mateusz Stachowski on 2015-03-03
This issue will be soon resolved. Probably tomorrow because today there is a new version of libgtk2.0 in vivid-proposed.

[https://lists.ubuntu.com/archives/vivid-changes/2015-March/006126.html](https://lists.ubuntu.com/archives/vivid-changes/2015-March/006126.html)

> [COLOR=#000000]gtk+2.0 (2.24.26-0ubuntu2) vivid; urgency=medium[/COLOR]  * 0002-gdk-Fix-GdkWindowFilter-internal-refcounting.patch
    0003-gdkwindow-Fix-event-unref-iteration.patch: Cherry-pick two commits
    from upstream gtk2 branch to fix refcounting errors in light of the
    event_apply_filters change in 2.24.26. **This was causing crashes in some **[FONT=Verdana]**applications, such as Spotify**.[/FONT][COLOR=#222222][FONT=Verdana][/FONT][/COLOR]

---

