---
title: "2 simultaneous logins problems"
date: 2009-01-04
forum: Security
---

### Post by vace117 on 2009-01-04
Hello, Ubuntu users. 

I have recently installed Intrepid Ibex and I am generally very happy with it, save for a few security issues I would like some advice on.

First, a little info about my setup. btw, please tell me if you know of an easier way to do this. 

Most of the time my computer is hooked up to two monitors, which is my work configuration. However, when I want to use my computer as a movie player, I switch the second VGA output to my projector. I don't want to restart my work X server when I switch over to the projector (different xorg.conf file), so I run two X servers simultaneously and login as two different users. Using a separate user for the projector has an added advantage of using a different UI theme and different config files for various movie players, so this setup used to work great in Slackware for me.

With Ibex it also works, but with some severe limitations, which to me appear to have to do with security.

Issue #1: There are problems with ALSA. If I log in as 'valprj' and use sound for a bit, then log in as 'val' on the other X server and try to use the digital output on the card (spdif), I get this:
```

val@boss:/mnt/datahost/music/5.1$ alsaplayer -dspdif Prelude.wav 
snd_pcm_open: Device or resource busy (spdif)

```
This error also happens when I switch back to valprj X server. 

As soon as I log out one of the users, the sound starts working for the other user. I checked for obvious stuff such as making sure that files under /dev/snd/* are not being used by some process and they are not. What could be locking the device?


Issue #2: Let's say we are logged in as 'val'. If I try:
```

val@boss:~$ xhost +
val@boss:~$ su valprj
valprj@boss:~$ nautilus
** (nautilus:17467): WARNING **: Owner of /tmp/orbit-val is not the current user


(nautilus:17467): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

(nautilus:17467): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```

This error repeats for a while, nautilus starts, but crashes pretty soon. Same goes for other apps that use gconf, I presume. Evolution can't even find the profile for the user. Firefox starts and works, but with the same errors in the beginning. In Slackware I was doing this sort of thing all the time w/o any issues. Could someone please explain to me the nature of these errors?


Thank you very much,



Val

---

