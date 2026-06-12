---
title: "Xubuntu Spotify crashing on start"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rogerdean on 2012-03-10
Hello all
I have Xubuntu Precise B1 and Spotify (unlimited account) from its repository. On each launch attempt I get no Spotify and -

```
roger@roger-ThinkPad-X60s:~$ spotify
18:53:43.119 I [breakpad.cpp:36] Registered Breakpad for product: spotify

18:53:43.119 I [translate.cpp:123] Reloading all languages
18:53:43.164 I [breakpad.cpp:94] Searching for crashdumps: /home/roger/.cache/spotify/*.dmp

18:53:45.406 I [breakpad.cpp:105] Not allowed to upload file

QDBusArgument: write from a read-only object
18:53:46.076 I [ap:1754] Connecting to AP C8.spotify.com:4070
18:53:46.131 I [offline-mgr:2146] Storage has been cleaned
18:53:46.326 I [ap:1212] Connected to AP: 78.31.8.14:4070
18:53:46.494 I [user_cache:138] UserCache::initiateGetUsers() will query for 1 users
18:53:46.495 I [gui-model:2549] Login Code: 0

Gdk-CRITICAL **: IA__gdk_window_set_back_pixmap: assertion `GDK_IS_WINDOW (window)' failed

Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault (core dumped)
roger@roger-ThinkPad-X60s:~$ 

```

Can anyone help me troubleshoot this? Am loving Xubuntu so really want this to work out

Cheers
Roger

---

### Post by thelinuxkid on 2012-03-10
So there is some problem where something in the cache seems to break after you have started up spotify for the first time. I have had that issue as well.

> Searching for crashdumps: /home/roger/.cache/spotify/*.dmp

Go to your home directory here and delete /home/roger/.cache/spotify and try again. I believe it will work then. Unfortunately you have to do that on each startup :-(

---

### Post by paul_in_london on 2012-03-10
> **rogerdean said:**
> Hello all
I have Xubuntu Precise B1 and Spotify (unlimited account) from its repository. On each launch attempt I get no Spotify and -

```
roger@roger-ThinkPad-X60s:~$ spotify
18:53:43.119 I [breakpad.cpp:36] Registered Breakpad for product: spotify

18:53:43.119 I [translate.cpp:123] Reloading all languages
18:53:43.164 I [breakpad.cpp:94] Searching for crashdumps: /home/roger/.cache/spotify/*.dmp

18:53:45.406 I [breakpad.cpp:105] Not allowed to upload file

QDBusArgument: write from a read-only object
18:53:46.076 I [ap:1754] Connecting to AP C8.spotify.com:4070
18:53:46.131 I [offline-mgr:2146] Storage has been cleaned
18:53:46.326 I [ap:1212] Connected to AP: 78.31.8.14:4070
18:53:46.494 I [user_cache:138] UserCache::initiateGetUsers() will query for 1 users
18:53:46.495 I [gui-model:2549] Login Code: 0

Gdk-CRITICAL **: IA__gdk_window_set_back_pixmap: assertion `GDK_IS_WINDOW (window)' failed

Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault (core dumped)
roger@roger-ThinkPad-X60s:~$ 

```

Can anyone help me troubleshoot this? Am loving Xubuntu so really want this to work out

Cheers
Roger

Have a butcher's at this page:

[http://benjaminkerensa.com/2012/02/15/spotify-bash-script-for-improved-stability](http://benjaminkerensa.com/2012/02/15/spotify-bash-script-for-improved-stability)

---

### Post by rogerdean on 2012-03-11
Magnificent, many thanks both. Shame it means I have to log in each time, but that's the way it goes...
Cheers
Roger

---

### Post by rogerdean on 2012-03-11
Actually I find I can change the script to delete .cache/spotify but not .config/spotify. It starts cleanly and also remembers my login...
Cheers

---

