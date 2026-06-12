---
title: "MATE 20.04 - error:0 in libdvdnav.so.4.2.0"
date: 2020-04-06
forum: Ubuntu Development Version
---

### Post by josephdcooper on 2020-04-06
Recently did a fresh install of Ubuntu MATE 20.04 and things were working great until I did... *something*... what I don't know, but I could really use your help so I don't have to reformat.


When i try to play a DVD it crashes immediately. In syslog I get this message:
kernel: [ 6686.109226] traps: vlc[18479] general protection fault ip:7f1a3750ed74 sp:7f1a0431aeb0 error:0 in libdvdnav.so.4.2.0[7f1a37505000+d000]


It works fine in the snap version of VLC, but I'd prefer for my use-cases to use the non-snap version.


Based on my bash history it started when I tried to install handbrake


```
271 apt-cache policy handbrake
272 apt-cache madison handbrake
273 sudo apt install handbrake
274 handbrake
275 sudo apt install libdvdread
276 sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg
277 sudo dpkg-reconfigure libdvd-pkg
278 handbrake
279 sudo apt update && sudo apt upgrade
280 sudo apt purge handbrake
281 sudo apt update && sudo apt upgrade
282 vlc -vvv
283 sudo apt install ubuntu-restricted-extras
284 vlc -vvv
285 sudo apt install libdvdcss2
286 vlc -vvv
287 sudo apt install libdvdnav4
288 sudo apt install libdvdnav
289 sudo apt autoremove libdvdnav4
290 sudo apt update --fix-missing
291 handbrake
292 sudo apt install handbrake
293 handbrake
294 which libdvdread
295 sudo apt install libdvdnav-dev
296 sudo apt remove libdvdnav4
297 sudo apt install --reinstall libdvdnav4
298 vlc -vvv
299 sudo apt-get install ubuntu-restricted-extras
300 tail -f /var/log/syslog
```




I've since purged vlc and deleted ~/.cache and ~/.config and even manually removed the links and files in /usr/lib/x86_64-linux.gnu/ for the below, but still no luck.
```
lrwxrwxrwx 1 root root 18 Nov 28 03:49 libdvdnav.so.4 -> libdvdnav.so.4.2.0
-rw-r--r-- 1 root root 88136 Nov 28 03:49 libdvdnav.so.4.2.0
lrwxrwxrwx 1 root root 19 Mar 29 10:33 libdvdread.so.7 -> libdvdread.so.7.1.0
-rw-r--r-- 1 root root 133112 Mar 29 10:33 libdvdread.so.7.1.0
```




What can I do to get VLC reading DVDs again? It reads BluRays just fine, but not DVDs due to the libdvdnav issue.

---

### Post by alezflute on 2020-04-06
I had the same problem on regular Ubuntu and can confirm dvd reading works with the snap so I guess we need an update on the libdvdnav packages from Ubuntu devs.

---

### Post by josephdcooper on 2020-04-06
I just set up a VM to see what the diff would be in the libdvd* files. After fresh install and installing updates, then installing vlc, it crashes when playing a DVD with the same error.
I also (since it is a VM) installed the nightly VLC - it makes it further, but stops at 

```
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed (spu)
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed (spu)
[00007fae88001bd0] dvdnav access warning: cannot get next block (Error reading from DVD.)
[000055d2a3a7ea40] qt interface debug: on_player_error_changed
[000055d2a3a7ea40] qt interface debug: on_player_state_changed
[00007fae88001bd0] main access debug: removing module "dvdnav"
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed
[000055d2a3a7ea40] qt interface debug: on_player_program_list_changed
[000055d2a3a7ea40] qt interface debug: on_player_item_epg_changed
[000055d2a3a7ea40] qt interface debug: on_player_title_array_changed
[000055d2a3a7ea40] qt interface debug: on_player_state_changed VLC_PLAYER_STATE_STOPPING
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed (spu)
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed (spu)
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed (spu)
[000055d2a3a7ea40] qt interface debug: on_player_track_list_changed (spu)
[000055d2a3a7ea40] qt interface debug: on_player_state_changed
[000055d2a3a7ea40] qt interface debug: on_player_state_changed VLC_PLAYER_STATE_STOPPED
```

So, is the issue VLC or Ubuntu? Should I open a bug report with VLC?

---

### Post by alezflute on 2020-04-07
Since the bug also appears with handbrake, I guess it's a libdvdnav issue and not a VLC issue

---

### Post by josephdcooper on 2020-04-08
Checked for updates today, tried the disk again, and it all works!
I did nothing else from my side.

---

