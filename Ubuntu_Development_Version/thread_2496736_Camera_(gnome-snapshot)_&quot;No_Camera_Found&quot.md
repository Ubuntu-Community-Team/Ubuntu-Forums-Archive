---
title: "Camera (gnome-snapshot) &quot;No Camera Found&quot;"
date: 2024-04-10
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-04-10
In Ubuntu 24.04 cheese has been removed and replaced by Camera (gnome-snapshot) but camera does not work
tested on 3 different PC with different webcams.
[https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2058131](https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2058131)
same problem with gnome-snapshot new version 
[https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2060390](https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2060390)

---

### Post by Claus7 on 2024-04-10
Hello,

also affected from this bug. In app store is found under debian packages as camera. Also, it doesn't follow the light theme.

Regards!

---

### Post by jbicha on 2024-04-12
We should be getting a new pipewire version soon that improves some issues with webcams, but it still doesn't completely fix my issues.

You may want to report your issues upstream to either Snapshot or Pipewire or both. I have done that this week.

---

### Post by corradoventu on 2024-04-16
After installing pipewire 1.0.5-1 from proposed and reboot Snapshot is working

---

### Post by jbicha on 2024-04-16
Yay!

I still have something like a race issue with wireplumber on my computers. [https://gitlab.freedesktop.org/pipewire/pipewire/-/issues/3960](https://gitlab.freedesktop.org/pipewire/pipewire/-/issues/3960)

---

### Post by #&amp;thj^% on 2024-04-16
Not related to the topic, but yesterday's upgrades with Bluez, Wireplumber fixed all audio on my end.

Thanks for the Link jbicha

EDIT:
```
apt-cache policy wireplumber pipewire
wireplumber:
  Installed: 0.4.17-1ubuntu4
  Candidate: 0.4.17-1ubuntu4
  Version table:
 *** 0.4.17-1ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
pipewire:
  Installed: 1.0.5-1
  Candidate: 1.0.5-1
  Version table:
 *** 1.0.5-1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by corradoventu on 2024-04-18
same wireplumber and pipewire ... fixed all audio, but camera still does not work for me

---

### Post by #&amp;thj^% on 2024-04-18
Mine works with:
```
apt policy webcamoid
webcamoid:
  Installed: 9.1.1-1build6
  Candidate: 9.1.1-1build6
  Version table:
 *** 9.1.1-1build6 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```
Hardware is: "Bison Electronics Inc. Integrated Camera" and snapshot works as well on my end.

It has a few more depends than cheese:
```
 apt depends webcamoid
webcamoid
  Depends: qml-module-qt-labs-folderlistmodel
  Depends: qml-module-qt-labs-settings
  Depends: qml-module-qtqml-models2
  Depends: qml-module-qtquick-controls
  Depends: qml-module-qtquick-controls2
  Depends: qml-module-qtquick-dialogs
  Depends: qml-module-qtquick-extras
  Depends: qml-module-qtquick-privatewidgets
  Depends: qml-module-qtquick-templates2
  Depends: qml-module-qtgraphicaleffects
  Depends: qml-module-qt-labs-platform
  Depends: webcamoid-data
  Depends: webcamoid-plugins
  Depends: libavkys9 (>= 9.1.1)
  Depends: libc6 (>= 2.34)
  Depends: libgcc-s1 (>= 3.0)
  Depends: libqt5core5t64 (>= 5.15.1)
 |Depends: libqt5gui5t64 (>= 5.11.0~rc1)
  Depends: libqt5gui5-gles (>= 5.11.0~rc1)
  Depends: libqt5network5t64 (>= 5.9.0~beta)
  Depends: libqt5qml5 (>= 5.1.0)
 |Depends: libqt5quick5 (>= 5.9.0~beta)
  Depends: libqt5quick5-gles (>= 5.9.0~beta)
  Depends: libqt5quickcontrols2-5 (>= 5.12.2)
  Depends: libqt5widgets5t64 (>= 5.0.2)
  Depends: libstdc++6 (>= 5.2)
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> apt depends cheese
cheese
  Depends: libc6 (>= 2.34)
  Depends: libcanberra-gtk3-0t64 (>= 0.26)
  Depends: libcheese-gtk25 (= 44.1-1build4)
  Depends: libcheese8 (= 44.1-1build4)
  Depends: libclutter-1.0-0 (>= 1.16)
  Depends: libclutter-gtk-1.0-0 (>= 0.91.8)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.25.2)
  Depends: libglib2.0-0t64 (>= 2.79.0)
  Depends: libgnome-desktop-3-20t64 (>= 3.17.92)
  Depends: libgstreamer1.0-0 (>= 1.0.0)
  Depends: libgtk-3-0t64 (>= 3.21.5)
  Depends: cheese-common (>= 44.1-1build4)
  Depends: gnome-video-effects
  Recommends: gvfs
  Recommends: yelp
  Suggests: gnome-video-effects-frei0r

```

---

### Post by corradoventu on 2024-04-18
webcamoid is NOT==  gnome-snapshot

---

### Post by #&amp;thj^% on 2024-04-18
> **corradoventu said:**
> webcamoid is NOT==  gnome-snapshot

I understand that:
```
snapshot
2024-04-18T16:38:57.810028Z  INFO snapshot::application::imp: Snapshot (org.gnome.Snapshot)    
2024-04-18T16:38:57.810145Z  INFO snapshot::application::imp: Version: 46.2    
2024-04-18T16:38:57.810150Z  INFO snapshot::application::imp: Datadir: /usr/share/snapshot    

```

I guess you are just bug-triaging and did not need an alternative. So shoot me for being helpful...LOL

---

### Post by corradoventu on 2024-04-18
as I said in my bug I have a great alternative in guvcview

---

### Post by #&amp;thj^% on 2024-04-18
okie  dokie you win...

NOI uomini italiani possiamo essere forti di mente

---

### Post by Claus7 on 2024-04-21
Hello,

> **corradoventu said:**
> as I said in my bug I have a great alternative in guvcview

ditto.

Regards!

---

### Post by jbicha on 2024-04-21
I filed [https://launchpad.net/bugs/2061687](https://launchpad.net/bugs/2061687) for one particular issue with Snapshot with a link to the upstream bug/discussion and a simple workaround. We aren't yet sure how to fix the issue.

---

### Post by corradoventu on 2024-04-22
On my system camera works just adding video group to my user

---

### Post by jbicha on 2024-04-22
Right, but we're not going to do that for everyone.

There was another workaround in the upstream bug:

```
systemctl edit --user wireplumber.service
```

Add this then save the file and exit:

```
[Service]
ExecStartPre=/bin/sleep 1

```
(And if one second isn't long enough, you could try a larger number.)

The problem with that suggestion is remembering to undo it after the issue is fixed for everyone.

---

### Post by Claus7 on 2024-04-22
Hello,

> **jbicha said:**
> Right, but we're not going to do that for everyone.

There was another workaround in the upstream bug:

```
systemctl edit --user wireplumber.service
```

Add this then save the file and exit:

```
[Service]
ExecStartPre=/bin/sleep 1

```
(And if one second isn't long enough, you could try a larger number.)

The problem with that suggestion is remembering to undo it after the issue is fixed for everyone.

I issued the command. I added the text in question where it should be added. I pressed Ctlr+X and then Enter. It didn't fix the camera issue for me. In order to revert it I did the same thing except of deleting the aforementioned text.

Regards!

---

### Post by jbicha on 2024-04-22
Did you try larger numbers? Upstream suggested 5 instead of 1.

---

### Post by Claus7 on 2024-04-22
Hello,

> **jbicha said:**
> Did you try larger numbers? Upstream suggested 5 instead of 1.
it worked like a charm! (...with 5)

Regards!

---

### Post by Claus7 on 2024-05-02
Hello,

I came across also this: systemctl --user restart pipewire
credits here: [https://ubuntuforums.org/showthread.php?t=2497176](https://ubuntuforums.org/showthread.php?t=2497176)

Regards!

---

### Post by timatgca on 2024-05-09
is there a bug report? I surely created a dup just now.

---

### Post by corradoventu on 2024-05-09
[https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2058131](https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2058131)
[https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2060390](https://bugs.launchpad.net/ubuntu/+source/gnome-snapshot/+bug/2060390)

---

### Post by timatgca on 2024-05-10
thanks.
For me it is fixed in 24.04 after pipewire 1.0.5-1 AND adding my user to group video, exactly as you said.

---

### Post by JcY47EP on 2024-10-30
I had the same problem: "No camera found".
It was solved after adding myself in the **video** group, i.e.

```
sudo usermod -a -G video $USER
```

Note: You have to logout and then login again for the change to take effect.

---

### Post by corradoventu on 2024-10-30
This is an OLD WORKAROUND, the bug is still open.

---

