---
title: "Snap apps use"
date: 2016-10-13
forum: Ubuntu Development Version
---

### Post by krishnan t s on 2016-10-13
Well its not really an issue. More like a clarification. I'm using the development release of ubuntu 16.10(to be released today). I have set up a separate /home partition and store all my data on that so i can upgrade my distribution without the theoretical fear of loss of data(Still maintain weekly backups just in case). I have installed a few applications in the snap package format. Though its limited, the basic functionality is good and un-installing is no longer a PITA. Plus there is no dependency hell!! The main problem i have is how do i access files through the snap packages located in my separate /home directory? For example, i use the vlc snap package to play videos. However, as i cant access /home through the installed snap, i cant play any video located in /home. Is there any work around or is it going to be solved in the future releases?

---

### Post by dino99 on 2016-10-13
snap is a "work in progress" in its early days, and is by no means ready to be used. Only testing for the curious/tester/aventurous is proposed. Some wiki/howto are also maintained as progress is made/changes done.

---

### Post by mc4man on 2016-10-13
It may be about permissions, (snaps aren't exactly transparent so require greater security.
In any event atm you could - 
```
sudo snap remove vlc
```
```
sudo snap install --devmode vlc
```
That will allow the file browser to go out further..

---

### Post by P-I H on 2016-10-30
I have problems with the snap version of VLC.
I can't install by use of Software Center. There is a bug about this [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943)
to install with ```
[COLOR=#000000][FONT=&amp]sudo snap install --devmode vlc[/FONT][/COLOR]
``` works fine.
It manage to play my flac files and also video files. To play video files I have to change Output in Video Preferences to** X11 video output (XCB)** from** Automatic**. This might be because of my DRM driver amdgpu-pro.
The snap version is not recognized when you right click a folder in Natilus. This makes the no snap VLC version easier to use.

---

