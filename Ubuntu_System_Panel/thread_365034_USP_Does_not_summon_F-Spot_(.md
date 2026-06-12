---
title: "USP Does not summon F-Spot :("
date: 2007-02-19
forum: Ubuntu System Panel
---

### Post by WinterWeaver on 2007-02-19
HI there!

Just installed and love it!! But I have a slight problem... not really a biggie....

I added F-Spot to the Favorites and when I run it I get a Fatal Error:
```

 An unhandled exception was thrown: Failed to connect to socket /tmp/dbus-pdBCbAIoVX: Connection refused

  at DBus.Bus.GetBus (BusType busType) [0x00000] 
  at DBus.Bus.GetSessionBus () [0x00000] 
  at FSpot.Core.get_Connection () [0x00000] 
  at FSpot.Core.get_Service () [0x00000] 
  at FSpot.Core.AssertOwnership () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 1.1.4322.2032

Assembly Version Information:

System.Data (1.0.5000.0)
Mono.Data.SqliteClient (1.0.5000.0)
gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
dbus-sharp (0.60.0.0)
System (1.0.5000.0)
Mono.Posix (1.0.5000.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.2.1.0)
mscorlib (1.0.5000.0)

Platform Information: Linux 2.6.17-11-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
```

I don't get this error if I, ALT + F2 -> f-spot
or if I run it from the terminal.

I haven't come across any other programs that manifests in this way, yet.
Does someone know how I can fix this?

Thanks,

WW

---

### Post by WinterWeaver on 2007-02-19
ooh... never mind... After a reboot f-spot properly manifested after being summoned by USP.

so disregard previous post please ^_^

---

