---
title: "dbus"
date: 2009-09-23
forum: Server Platforms
---

### Post by newsen on 2009-09-23
Hi,
I am trying to connect to navit from the apache server.When i run the php program in terminal i am not getting any errors.But when i run it from the server.I am getting errors like:
failed to auto launch dbus..X11 initialization failed..How to run it from the server.
Here is my php code.
[php]
$type = DBUS_BUS_SESSION;
$dbus = dbus_bus_get($type);
$m=new DBusMessage(DBUS_MESSAGE_TYPE_METHOD_CALL);
$m->setPath('/org/navit_project/navit/navit/0');
$m->setDestination('org.navit_project.navit');
$m->setInterface('org.navit_project.navit.navit');
$m->setMember('zoom');
$zoom = 3;
$m->appendArgs($zoom);
$r=$dbus->send($m);
[/php]Thanks..

---

