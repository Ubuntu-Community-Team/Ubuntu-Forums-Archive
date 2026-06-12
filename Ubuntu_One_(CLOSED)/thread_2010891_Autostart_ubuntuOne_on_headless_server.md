---
title: "Autostart ubuntuOne on headless server"
date: 2012-06-26
forum: Ubuntu One (CLOSED)
---

### Post by mbeltoft on 2012-06-26
I've set up UbuntuOne on my headless server using this guide

[https://wiki.ubuntu.com/UbuntuOne/Headless](https://wiki.ubuntu.com/UbuntuOne/Headless)

however i get disconnected every time i log off and I have to connect it manually each time i log into my server.

I want it to autostart and be online all the time even if im not logged into the server.
How do i do that?

---

### Post by thnewguy on 2012-06-26
Have you tried starting the U1 client using a cron job? Run "crontab -e" and create an entry so that it attempts to start One at a given time. An entry like the following in your crontab might do the trick:

0 * * * * u1sdtool --start

I assume that if One is already running the "start" command won't hurt it.

---

### Post by mbeltoft on 2012-06-26
No i haven't tried that but I would rather run it as a service using a init.d script... i just don't know how to make the script

---

### Post by thnewguy on 2012-06-27
You could put an entry in your /etc/rc.local file. Something like this might work:

su -c "u1sdtool --start" your-username

---

### Post by mbeltoft on 2012-06-28
tried to add the line to rc.local but it didn't work

it shows a error about it's unable to start because it need to have X11 running?

```
 File "/usr/bin/u1sdtool", line 44, in <module>
    bus = dbus.SessionBus(mainloop=loop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 211, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: //bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

```

Why do U1 need X just to connect to a online service?

---

### Post by mbeltoft on 2012-07-02
Apparently what it want to do can't be done.
Disappointing that Ubuntu-1 don't fully support their own OS.

My solution was to use dropbox. it can run as a service on a headless server without any problems. However I've never been a fan of dropbox so i hope U1 will be updated so it can be used on all flavors of Ubuntu

---

