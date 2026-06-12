---
title: "ubuntu one can not connect in natty"
date: 2011-04-30
forum: Ubuntu One (CLOSED)
---

### Post by shenme888 on 2011-04-30
output for "u1sdtool -s" command
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE
and log file
    2011-04-30 17:26:33,591 - ubuntuone.SyncDaemon.DBus - WARNING - 'CredentialsError': (dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'DBusException'), dbus.String(u'message'): dbus.String(u'The name org.freedesktop.secrets was not provided by any .service files')}, signature=dbus.Signature('ss')),) {'member': 'CredentialsError'}
2011-04-30 17:26:33,592 - twisted - ERROR - Unhandled error in Deferred:
2011-04-30 17:26:33,592 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.linux.dbus_interface.NoAccessToken: CredentialsError: (dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'DBusException'), dbus.String(u'message'): dbus.String(u'The name org.freedesktop.secrets was not provided by any .service files')}, signature=dbus.Signature('ss')),) {'member': 'CredentialsError'}

---

### Post by gsistare on 2011-04-30
I'm having this issue too on Natty. Nothing happens when I start Ubuntu One from panel our application.

---

### Post by odysseus2k7 on 2011-05-04
> **shenme888 said:**
> output for "u1sdtool -s" command
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE
and log file
    2011-04-30 17:26:33,591 - ubuntuone.SyncDaemon.DBus - WARNING - 'CredentialsError': (dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'DBusException'), dbus.String(u'message'): dbus.String(u'The name org.freedesktop.secrets was not provided by any .service files')}, signature=dbus.Signature('ss')),) {'member': 'CredentialsError'}
2011-04-30 17:26:33,592 - twisted - ERROR - Unhandled error in Deferred:
2011-04-30 17:26:33,592 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.linux.dbus_interface.NoAccessToken: CredentialsError: (dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'DBusException'), dbus.String(u'message'): dbus.String(u'The name org.freedesktop.secrets was not provided by any .service files')}, signature=dbus.Signature('ss')),) {'member': 'CredentialsError'}

I just tried that command and got this:
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

Everything looks fine, but I can't get a connection to the cloud on my netbook.

---

