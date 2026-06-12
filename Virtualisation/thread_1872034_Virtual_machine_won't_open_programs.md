---
title: "Virtual machine won't open programs"
date: 2011-10-29
forum: Virtualisation
---

### Post by geekman2 on 2011-10-29
I recently installed the most recent version of vmware player and created a virtual machine of oneric. It worked initially but when I booted it back up the several days later no programs would run and it is stuck in the "highcontrast" theme.
please help  :confused:

I am running windows 7 64-bit on a custom PC running an core i5 and 4gb of ram

---

### Post by LinuxFan999 on 2011-10-30
How much memory did you allocate to the virtual machine?

---

### Post by geekman2 on 2011-10-30
1 Gb but i've made another with 2 and it had the same problem

---

### Post by geekman2 on 2011-11-01
Help?

---

### Post by Jake.Debord on 2011-11-02
You may need to check your video settings... Does it crash when you try to open programs? How much vram do you have allocated? Can you share any error logs?

---

### Post by geekman2 on 2011-11-03
> **Jake.Debord said:**
> You may need to check your video settings... Does it crash when you try to open programs? How much vram do you have allocated? Can you share any error logs?

What do you mean check my video settings? please clarify. It doesn't crash, in fact it will open some programs and settings but not others. I have 1 Gigabyte of RAM allocated to this machine and there are no error logs hope this info helps

---

### Post by geekman2 on 2011-11-03
when I try to run software center from terminal I get this
:confused:
2011-11-03 12:30:09,521 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 108, '__init_network_state')'
2011-11-03 12:30:09,521 - root - WARNING - failed to init network state watcher 'org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused'
2011-11-03 12:30:09,602 - softwarecenter.ui.gtk3.em - INFO - EM's: 0 0 0
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 243, in __init__
    self.backend = get_install_backend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend.py", line 70, in get_install_backend
    install_backend = AptdaemonBackend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 195, in __init__
    bus = get_dbus_bus()
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 62, in get_dbus_bus
    bus = dbus.SystemBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 202, in __new__
    private=private)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

---

