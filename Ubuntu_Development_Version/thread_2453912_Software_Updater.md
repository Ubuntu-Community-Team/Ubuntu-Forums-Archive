---
title: "Software Updater"
date: 2020-11-19
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-11-19
Software Updater crashes always on my computer.
Any other?
apt update and apt upgrade works OK.

---

### Post by dino99 on 2020-11-19
No problem here on G-S on xorg session.
Do you get an error when you start it from a terminal ?
What happen if you purge it (and all its dependencies) then reinstall it ?

---

### Post by P-I H on 2020-11-19
This is the result when started from the terminal.
```
p-i@pi-TUF-Gaming-B550M:~$ update-manager
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 177, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    return self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1623, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1709, in get_aptdaemon
    return dbus.Interface(bus.get_object("org.debian.apt",
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    return self.ProxyObjectClass(self, bus_name, object_path,
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 250, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 182, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 277, in start_service_by_name
    return (True, self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 177, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    return self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1623, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1709, in get_aptdaemon
    return dbus.Interface(bus.get_object("org.debian.apt",
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    return self.ProxyObjectClass(self, bus_name, object_path,
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 250, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 182, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 277, in start_service_by_name
    return (True, self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 177, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    return self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1594, in on_error
    error.raise_exception()
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 130, in raise_exception
    raise self.value.with_traceback(self.traceback)
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 487, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1623, in _run_transaction_helper
    daemon = get_aptdaemon(self.bus)
  File "/usr/lib/python3/dist-packages/aptdaemon/client.py", line 1709, in get_aptdaemon
    return dbus.Interface(bus.get_object("org.debian.apt",
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    return self.ProxyObjectClass(self, bus_name, object_path,
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 250, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 182, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 277, in start_service_by_name
    return (True, self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 177, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    return self.call_blocking(BUS_DAEMON_NAME, BUS_DAEMON_PATH,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.debian.apt': no such name


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/defer/__init__.py", line 483, in _inline_callbacks
    result = gen.throw(excep)
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 66, in update
    trans = yield self.client.update_cache(defer=True)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
```

Will continue with your other suggestions.

---

### Post by P-I H on 2020-11-19
Not able to purge. One of the dependencies is ubuntu-desktop.
Downloaded today's version via the ISO tracker. Found this bug
 [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1904866](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1904866)
Installed the ISO and got two bugs 1904217 to which I don't have permission to see and reported a new
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1904878](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1904878)

---

### Post by dino99 on 2020-11-19
no problem to remove that meta package: ubuntu-desktop; you will not brake your system :p
simply reinstall it after the software removal/reinstall is done

---

### Post by corradoventu on 2020-11-20
Same problem. I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1904980](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1904980)

---

### Post by Frogs Hair on 2020-11-21
Experienced a crash on 11-20 , but the software updater is running normally since.

---

### Post by P-I H on 2020-11-22
I updated today with sudo apt update, sudo apt upgrade, rebooted and now Software Updater works OK.

---

