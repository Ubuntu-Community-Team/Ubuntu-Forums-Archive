---
title: "Consolekit issues"
date: 2012-03-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by teeedubb on 2012-03-22
Ive just upgraded my ubuntu x64 install from 11.10 to 12.04 and am  noticing something strange with consolekit which never occurred using  11.10. Its a htpc and auto logged in using mingetty, x is launched from  .bash_profile and xbmc is started with .xinitrc. On a fresh boot there  is no audio (aplay -l shows no soundcards) and no options to  shutdown/suspend/reboot, but if I exit xbmc (which from my understanding  restarts the whole login/process process again) sound and shutdown  options works as should. apt-cache shows consolekit to be version  0.4.5-2.

```
cat /etc/init/tty2.conf
# tty2 – getty
#
# This service maintains a getty on tty2 from the point the system is
# started until it is shut down again.
 start on runlevel [23]
stop on runlevel [!23]
 #respawn
#exec /sbin/getty -8 38400 tty2
 respawn
exec /sbin/mingetty --autologin=xbmc tty2

``````
cat ~/.bash_profile
if [[ ! $DISPLAY && ! -e /tmp/.X11-unix/X0 ]] && (( EUID )); then
  exec xinit — /usr/bin/X  #startx
fi

``````
cat ~/.xinitrc
 exec ck-launch-session xbmc

``````
ck-list-sessions
Session1:
        unix-user = '1000'
        realname = 'xbmc'
        seat = 'Seat1'
        session-type = ''
        active = FALSE
        x11-display = ''
        x11-display-device = ''
        display-device = '/dev/tty2'
        remote-host-name = ''
        is-local = TRUE
        on-since = '2012-03-23T01:51:45.280408Z'
        login-session-id = '4294967295'
        idle-since-hint = '2012-03-23T01:52:15.165039Z'
Session2:
        unix-user = '1000'
        realname = 'xbmc'
        seat = 'Seat2'
        session-type = ''
        active = FALSE
        x11-display = ':0'
        x11-display-device = ''
        display-device = '/dev/tty2'
        remote-host-name = ''
        is-local = TRUE
        on-since = '2012-03-23T01:51:46.798630Z'
        login-session-id = '4294967295'
Session3:
        unix-user = '1000'
        realname = 'xbmc'
        seat = 'Seat3'
        session-type = ''
        active = FALSE
        x11-display = ''
        x11-display-device = ''
        display-device = '/dev/ssh'
        remote-host-name = 'bumblebee.billion.7800n'
        is-local = FALSE
        on-since = '2012-03-23T01:53:00.571348Z'
        login-session-id = '4294967295'

```ck-list-sessions after exiting xbmc or killing x


```

Session4:
        unix-user = '1000'
        realname = 'xbmc'
        seat = 'Seat1'
        session-type = ''
        active = FALSE
        x11-display = ''
        x11-display-device = ''
        display-device = '/dev/tty2'
        remote-host-name = ''
        is-local = TRUE
        on-since = '2012-03-23T02:14:08.571713Z'
        login-session-id = '4294967295'
        idle-since-hint = '2012-03-23T02:14:39.165082Z'
Session5:
        unix-user = '1000'
        realname = 'xbmc'
        seat = 'Seat1'
        session-type = ''
        active = TRUE
        x11-display = ':0'
        x11-display-device = '/dev/tty3'
        display-device = '/dev/tty2'
        remote-host-name = ''
        is-local = TRUE
        on-since = '2012-03-23T02:14:09.936782Z'
        login-session-id = '4294967295'
Session3:
        unix-user = '1000'
        realname = 'xbmc'
        seat = 'Seat3'
        session-type = ''
        active = FALSE
        x11-display = ''
        x11-display-device = ''
        display-device = '/dev/ssh'
        remote-host-name = 'bumblebee.billion.7800n'
        is-local = FALSE
        on-since = '2012-03-23T01:53:00.571348Z'

```Session 5 is marked as ACTIVE after restarting x and has a x11-display-device value.

/var/log/Consolekit/history  [http://pastebin.com/b8cc9dNH](http://pastebin.com/b8cc9dNH)

Ive tried different .bash_profiles and various .xinitrc's (no  ck-launch-session, with dbus-launch etc) to no avail.  This has me  stumped and I cant seem to find much info about it. At this stage im not  sure if its a config error, consolekit change or a bug....
 Any suggestions?

---

