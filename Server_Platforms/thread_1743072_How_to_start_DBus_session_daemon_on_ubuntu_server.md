---
title: "How to start DBus session daemon on ubuntu server?"
date: 2011-04-29
forum: Server Platforms
---

### Post by saepia on 2011-04-29
Hi,

I am developing an application that uses DBus to perform inter-process communication.

It works perfecly on ubuntu studio, but it is intended to work on servers.

When I install dbus package, system bus works perfectly. But I encounter problems when I try to start session bus. 

Manually launching dbus-daemon --session does not help. No other DBus process see bus launched in this way.

Any ideas?

---

### Post by saepia on 2011-04-30
I've finally found the method.

dbus-launch prints in the console something like that:


DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-RKvgH2uzDI,guid=37cfdf614fe9c896cc8790160018b974
DBUS_SESSION_BUS_PID=18717

you need to export this as environment variables

---

