---
title: "[Quantal Quetzal - 12.10] Update Manager not launching"
date: 2012-08-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Kelvari on 2012-08-31
Marked [SOLVED] because an OS is only as good as the hard drive that it's installed on. See final post.

I'm currently running Ubuntu 12.10, and my Update Manager hasn't been working for the better part of a week, at least. I've been doing manual updates, hoping that they fix the problem, but have not yet had any relief from this situation. [This thread](http://ubuntuforums.org/showthread.php?t=1940459) has the same symptoms of what I am experiencing, but the solution for their problem - launching the updater manually - has not resolved my situation.

I don't know if this is a problem with Update Manager, or a problem with Python. Below is the output I get when I try to launch Update Manager manually.
```
$ ubuntu-bug update-manager
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 16, in <module>
    from gi.repository import GObject, GLib, Wnck, GdkX11, Gdk
ImportError: No module named gi.repository
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
ImportError: No module named apt

Original exception was:
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 16, in <module>
    from gi.repository import GObject, GLib, Wnck, GdkX11, Gdk
ImportError: No module named gi.repository

```

---

### Post by Kelvari on 2012-08-31
Well, I followed the cookie-trail through the errors, and wound up roughly running this bit of code (pieced together via trial-and-error)

```
sudo apt-get install --reinstall python3-update-manager python3-apt python3-gi update-manager python3-dbus python3-aptdaemon aptdaemon lsb-release python3-defer python3-aptdaemon.gtk3widgets python3-dbus

```

This has left me with the following```
$ update-manager 
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    's', (bus_name,), **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1624, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1698, in get_aptdaemon
    False),
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    's', (bus_name,), **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1624, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1698, in get_aptdaemon
    False),
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    's', (bus_name,), **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1595, in on_error
    error.raise_exception()
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 130, in raise_exception
    raise self.value.with_traceback(self.traceback)
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1624, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1698, in get_aptdaemon
    False),
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Fontconfig warning: "/etc/fonts/conf.d/69-language-selector-ja-jp.conf", line 141: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/69-language-selector-zh-tw.conf", line 79: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    's', (bus_name,), **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 483, in _inline_callbacks
    result = gen.throw(excep)
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 60, in update
    trans = yield self.client.update_cache(defer=True)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
```

---

### Post by dcstar on 2012-08-31
> **Kelvari said:**
> I'm currently running Ubuntu 12.10
.......

Do not post issues with Development software in General Support, no one here at all runs this software and therefore no one knows anything at all about it.

Post in the Development Forum as you are specifically told to do when you use Development versions.

---

### Post by sffvba[e0rt on 2012-09-01
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*


404

---

### Post by Kelvari on 2012-09-01
Thank you, nf, and my apologies dc

---

### Post by jerrylamos on 2012-09-01
Not a problem for me.  First thing I do on an install is run either sudo synaptic or sudo software-repositories-gtk, turn "ubuntu partners" on, update manager as far off as possible, also "unsupported updates" off.

Update Manager loves to come unexpectedly crashing in to whatever I'm doing, if it does run, interferes with any setup I'm doing, kills my install with partial updates, general pain to me. Your experience may vary.

Usually daily when doing Alpha, Beta, release candidate, I do sudo apt-get update, sudo apt-get dist-upgrade when I want to - after checking the development forum if the day's update is causing problems.  I don't need Update Manager installing a broken update on me.

For general users on released code update manager is set to run.  As a tester I don't use it.  My choice, no problem.

Jerry

---

### Post by cariboo on 2012-09-01
Out of curiosity, as I don't get the same errors as the op, what mirror are you using as a package source?

---

### Post by Kelvari on 2012-09-02
I should be using the default US mirrors. I'll have to double-check and will edit this post (assuming no others post between now and then) or post a reply with the mirror(s) that I'm using.

Edit: Seems I'm having more than just minor OS issues. Ubuntu told me that I had errors on / and /home, but when I went to try to fix them, after the reboot, I got a notice about hd0 being out of disk and got thrown into a GRUB recovery shell. I'm able to access my /home directory well enough, but I can't do anything with the / partition. SMART full-test is hanging at 10% remaining; short test is failing almost immediately. SMART says the disk is good, but it's got 661 bad sectors and a G-sense Error Rate of 975 (I did get this laptop used, though). Reallocation count of 338 with 51 pending. Sounds like I know where the problem is now, at least.

If I end up having issues with this again after I get a new drive, then I'll let you guys know for sure and actually post in the right place.

---

