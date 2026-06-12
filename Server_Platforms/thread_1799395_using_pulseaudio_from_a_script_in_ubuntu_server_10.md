---
title: "using pulseaudio from a script in ubuntu server 10.10"
date: 2011-07-07
forum: Server Platforms
---

### Post by Effcook on 2011-07-07
Hi, I'm working on a server who's job is to record audio on a
scheduled basis.  I'm trying to get this working under Ubuntu Server
10.10 and am having difficulty with pulseaudio.

I've added the user account to groups audio and pulse* and
have installed the pulseaudio and associated library packages.

Here's the problem:

If I have a user session logged in, everything works just fine
but when I start my program from rc.local (su'ed to a regular user, not root), pulseaudio doesn't start correctly.

My startup script attempts to start pulseaudio with:
/usr/bin/pulseaudio --start --log-level=3

but syslog shows this:
pulseaudio[1045]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.Spawn.ExecFailed: /bin/dbus-launch terminated abnormally without any error message

/bin/dbus-launch does not exist on this system, but dbus is there
and running.

I run ps ax > /tmp/psout from the startup script and dbus appears
to be running before I log into the user account:
grep dbus /tmp/psout
  551 ?        Ss     0:00 dbus-daemon --system --fork

My system works just fine if I leave a user logged in, but
it doesn't work after a reboot with no user logged in.

Any ideas what's going on here?

---

### Post by Effcook on 2011-07-12
I managed to get my automatic audio recording system to work.  After
trying a bunch of stuff to get pulseaudio to work in user mode,
I finally decided to ignore the documentation warnings about
pulseaudio in system mode and was able to get things going that way.

I put the following into /etc/rc.local:
/usr/bin/pulseaudio --system --disallow-module-loading --disallow-exit 
  --log-level=2 --log-target=syslog &

su - cook /home/cook/SatRec/start_SatRec >
  /var/www/log/start_SatRec.log 2>&1


And a deprecation warning message was fixed by
editing /etc/pulse/system.pa to change the load-module line:

#load-module module-detect
load-module module-udev-detect

Now my software works as it should.

Incidentally, in user mode, this build of pulseaudio complains about
being unable to find /bin/dbus-launch, that file does not exist on
this system.  That seems to be a non-fatal error, but it may need to
be fixed anyway.

---

