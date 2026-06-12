---
title: "disable touchpad while typing (set delay)"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-11
[[img]http://www.zimagez.com/miniature/screenshot-10112012-021029pm.php[/img]](http://www.zimagez.com/zimage/screenshot-10112012-021029pm.php)
how do i configure how long to disable the mouse after hitting a key?

---

### Post by mc4man on 2012-10-11
Well I guess you'd need to first see what xubuntu is using to disable, maybe syndaemon like Ubuntu?

To check enable the ' disable touchpad while typing' option in your screen, then in a terminal run
ps aux |grep syndaemon

If syndaemon is being used you'll see it & the command being used. 

(On Ubuntu syndaemon is run thru g-s-d & uses this
syndaemon [COLOR="Blue"]-i 2.0 [/COLOR]-K -R [COLOR="Blue"]-t[/COLOR]

The blue shows a timeout of 2 sec's & only tapping & scrolling disabled, (-t)

So on Ubuntu if I wanted to change I'd either rebuild g-s-d & edit the source or not let g-s-d start syndaemon & instead start it  as a custom startup app with command of choice. 
(one needs to be careful not to have 2 instances of syndaemon running as that will usually cause cursor freeze sooner than later

---

### Post by pqwoerituytrueiwoq on 2012-10-11
```
syndaemon -i 2.0 -K -R
```when it is checked it looks like it uses this command
so if i run ```
syndaemon -i 0.5 -K -R
``` it will do 500ms i assume
edit: i like that -t option :)
```
syndaemon --help
syndaemon: invalid option -- '-'
Usage: syndaemon [-i idle-time] [-m poll-delay] [-d] [-t] [-k]
  -i How many seconds to wait after the last key press before
     enabling the touchpad. (default is 2.0s)
  -m How many milli-seconds to wait until next poll.
     (default is 200ms)
  -d Start as a daemon, i.e. in the background.
  -p Create a pid file with the specified name.
  -t Only disable tapping and scrolling, not mouse movements.
  -k Ignore modifier keys when monitoring keyboard activity.
  -K Like -k but also ignore Modifier+Key combos.
  -R Use the XRecord extension.
  -v Print diagnostic messages.
```

---

### Post by mc4man on 2012-10-11
The -t option became default on Ubuntu (gnome) as a result of an upstream change to the -i (back in 11.10 I think

To accommodate users of large touchpads like on Mac's the previous timeout of 0.5 was upped to 2.0 (syndaemon default

This caused issues with 'normal' users as the cursor would lock for 2 sec's. 
So as a way to benefit all the Ubuntu default is now to leave the timeout at 2 sec but only prevent tap & scroll, cursor can be moved at any time.

historical
[https://bugzilla.gnome.org/show_bug.cgi?id=673055](https://bugzilla.gnome.org/show_bug.cgi?id=673055)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/962958](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/962958)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763)

---

