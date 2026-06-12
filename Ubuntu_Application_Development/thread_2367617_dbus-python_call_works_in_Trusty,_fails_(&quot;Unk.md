---
title: "dbus-python call works in Trusty, fails (&quot;UnknownMethod&quot;) in Xenial (16.04)"
date: 2017-08-01
forum: Ubuntu Application Development
---

### Post by skierstead-t on 2017-08-01
I am porting some code from **Trusty (14.04)** to **Xenial**** (16.04)** and having trouble with a method that uses **dbus** to ask **NetworkManager** for the MAC address of a network interface. The original code is in another language (scala) but I've isolated and reproduced the problem in a simple(ish) python program that does the same query.

When I run this test program on Trusty, it works fine. But when I try it on Xenial, it throws an **UnknownMethod** exception:
```
[dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: No such interface '(null)' on object at path /org/freedesktop/NetworkManager
```

The code tries to get the MAC address for the "eth0" interface (yes, I've set things up in the kernel command line to revert to old interface naming (as [described here]("https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/")), and verified with "ifconfig" that it works. The "eth0" interface is there and working. Plus, I've become convinced that the problem is not about "eth0", but rather something more general.).

The interesting (i.e., broken) behavior is in the [FONT=courier new]getMac()[/FONT] method below:

```
    def getMac(self):
        logger.info("...get the MAC address")
        logger.info(self._proxy_obj)
        devIntf = self._proxy_obj.GetDeviceByIpIface("eth0")
        logger.info(devIntf)
        # NOTE: devIntf is a string, the path to the device.  E.g., "/org/freedesktop/NetworkManager/Devices/0"
        # Now, how to get the Properties of that device?
        dev_proxy = self._bus.get_object(self._dbusName, devIntf)
        dev_prop_iface = dbus.Interface(dev_proxy, "org.freedesktop.DBus.Properties")
        mac = dev_prop_iface.Get("org.freedesktop.NetworkManager.Device.Wired", "HwAddress")
        return mac
```

Again, this code works on Trusty but fails on Xenial with the following error output:

```
Traceback (most recent call last):
  File "./getMacAddress.py", line 233, in <module>
    main()
  File "./getMacAddress.py", line 229, in main
    mac = NetManagerProxy.getMac()
  File "./getMacAddress.py", line 160, in getMac
    devIntf = self._proxy_obj.GetDeviceByIpIface("eth0")
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: No such interface '(null)' on object at path /org/freedesktop/NetworkManager
```

The error output suggests to me that [FONT=courier new]_proxy_obj[/FONT] has no [FONT=courier new]GetDeviceByIpIface()[/FONT] method (or, based on other tests, any methods at all!). But it has methods in Trusty, so what's up?

Any thoughts on what's going wrong, and how I might repair it?

Thank you.

Steve

----

If it helps, here's the entire python program:

```
#!/usr/bin/env python


from dbus.mainloop.glib import DBusGMainLoop
from gi.repository import GLib
import dbus
import dbus.service
import os, sys
import argparse
import logging
import logging.config
import datetime
import time


ContentManager = None
ContentPackages = None


NETMANAGER_NAME = "org.freedesktop.NetworkManager"
NETMANAGER_INTF = NETMANAGER_NAME
NETMANAGER_PATH = "/" + NETMANAGER_INTF.replace(".", "/")


DBUS_ITSELF_NAME = "org.freedesktop.DBus"
DBUS_ITSELF_INTF = "org.freedesktop.DBus"
DBUS_ITSELF_PATH = "/" + DBUS_ITSELF_INTF.replace(".", "/")


DBusGMainLoop(set_as_default=True)
logger = logging.getLogger('renderer_agent')


# ======================================================
# Here's a class for watching DBus itself, to become aware when the other
# processes we want to watch come alive or go away.
class CDBusWatcher(object):


    def __init__(self, bus=dbus.SystemBus()):


        self._bus = bus
        self._proxy_obj = self._bus.get_object(DBUS_ITSELF_NAME, DBUS_ITSELF_PATH)
        self._proxy_intf = dbus.Interface(self._proxy_obj, dbus_interface=DBUS_ITSELF_INTF)
        # Set up a callback when the 'NameOwnerChanged' signal arrives.
        # To clear the callback, set the callback to None.
        self._proxy_intf.connect_to_signal("NameOwnerChanged", self.onNameOwnerChanged)
        self._namesToWatch = dict()


    def watchNameChanges(self, name, proxy):
        logger.info("Watch for dbus name ownership changes for \"{}\"".format(name))
        self._namesToWatch[name] = proxy


    def onNameOwnerChanged(self, dbusConnName, prevOwner, newOwner):
        # The 'NameOwnerChanged' signal is emitted when the name is given
        # up and when it is claimed.  When it is given up, 'newOwner' will
        # be None, and we want to cancel our callbacks.  When it is claimed,
        # newOwner is non-empty and we want to (re)establish our callbacks.


        # logger.info("onNameOwnerChanged(): dbusConnName=\"{}\", owner: {} => {}".format(dbusConnName, prevOwner, newOwner))
        if dbusConnName in self._namesToWatch:
            proxy = self._namesToWatch[dbusConnName]


            if newOwner:
                logger.info("...DBus name \"{}\" claimed".format(dbusConnName))
                if proxy:
                    proxy.tryConnect()
            else:
                logger.info("...DBus name \"{}\" released".format(dbusConnName))
                if proxy:
                    proxy.disconnect()


DBusWatcher = CDBusWatcher()


# ======================================================
# We want to set up dbus proxy connections to a number of other processes.
# Each has a unique set of methods and/or signals, but there are things
# that all of the connections have in common.  This class captures the
# common attributes.  You'll see specific proxy classes below derived
# from this one.
#    This class also tells the DBusWatcher to watch for changes in
# the ownership of the interface name, so if the process being watched
# restarts, we will re-connect when it re-acquires the interface name
# (the DBusWatcher calls our disconnect() method when the connection
# goes away, and calls out tryConnect() method to re-establish the
# connection when it comes back).
class CTapDBusProxy(object):


    def __init__(self, dbusBus, dbusName, dbusPath, dbusIntf, callbacks):
        '''
            dbusBus is the bus itself (e.g., dbus.SystemBus())
            dbusName, dbusPath and dbusIntf are the attributes of the dbus
                peer to which we are to connect
            callbacks is a dict mapping dbus signal names to the callbacks
                to be called when they are emitted
        '''
        self._bus = dbusBus
        self._dbusName = dbusName
        self._dbusPath = dbusPath
        self._dbusIntf = dbusIntf
        self._callbacks = callbacks
        self._connectionUp = False
        DBusWatcher.watchNameChanges(dbusName, self)


    def connectionUp(self):
        return self._connectionUp


    def tryConnect(self):
        logger.info("enter CTapDBusProxy.tryConnect()")
        rval = False
        try:
            self._proxy_obj = self._bus.get_object(self._dbusName, self._dbusPath)
            logger.info(self._proxy_obj)
            self._proxy_intf = dbus.Interface(self._proxy_obj, dbus_interface=self._dbusIntf)
            # Set up a callback for each signal name in self._callbacks.
            # To clear the callback, set the callback to None.
            for signame, cb in self._callbacks.items():
                self._proxy_intf.connect_to_signal(signame, cb)
            rval = True
        except Exception as e:
            logger.error("Exception trying to connect to {}".format(self._dbusName))
            logger.error("Exception {}".format(str(e)))


        logger.info("tryConnect({}) returns {}".format(self._dbusName, rval))
        self._connectionUp = rval
        return rval


    def disconnect(self):
        logger.info("enter CTapDBusProxy.disconnect()")
        if (self._connectionUp):
            for signame, cb in self._callbacks.items():
                self._proxy_intf.connect_to_signal(signame, None)
        else:
            logger.error("call to disconnect() when already disconnected")


        self._connectionUp = False


# ======================================================
class CNetManagerProxy(CTapDBusProxy):


    def __init__(self):
        callbacks = {
            "TapMusicNowPlayingStart": self.onNowPlayingStart,
            "TapMusicNowPlayingStop": self.onNowPlayingStop
        }
        callbacks = {}
        super(CNetManagerProxy, self).__init__(dbus.SystemBus(), NETMANAGER_NAME, NETMANAGER_PATH, NETMANAGER_INTF, callbacks)


    def onNowPlayingStart(self, songId, title, album, artist, mediaFormat, imagePath):
        CachedNowPlayingInfo.update(songId, title, album, artist, mediaFormat, imagePath)
        logger.info("CNetManagerProxy.onNowPlayingStart(): Here's the updated info: {}".format(CachedNowPlayingInfo.get()))
        # Emit the "Playing" signal to send out the update
        AgentDbusIntf.emitPlaying()


    def onNowPlayingStop(self, id):
        logger.info ("CNetManagerProxy.onNowPlayingStop(id={})".format(id))
        playingID = str(CachedNowPlayingInfo.get_datum(NOW_PLAYING_FLD_ID))
        if (playingID == str(id)):
            logging.info("Clear the cached song data")
            CachedNowPlayingInfo.clear()
        else:
            logging.warn("NowPlayingStop for song we didn't think was playing ({} != {})".format(id, playingID))


    def getMac(self):
        logger.info("...get the MAC address")
        logger.info(self._proxy_obj)
        devIntf = self._proxy_obj.GetDeviceByIpIface("eth0")
        logger.info(devIntf)
        # NOTE: devIntf is a string, the path to the device.  E.g., /org/freedesktop/NetworkManager/Devices/0
        # Now, how to get the Properties of that device?
        dev_proxy = self._bus.get_object(self._dbusName, devIntf)
        dev_prop_iface = dbus.Interface(dev_proxy, "org.freedesktop.DBus.Properties")
        mac = dev_prop_iface.Get("org.freedesktop.NetworkManager.Device.Wired", "HwAddress")
        return mac


NetManagerProxy = None


# ======================================================
def main():
    parser = argparse.ArgumentParser()
    args = parser.parse_args()


    # Set up logging, with rotation
    logfile = "mactest.log"
    LOGGING = {
        'version': 1,
        'formatters': {
            'detailed': {
                'format': '%(asctime)s %(levelname)s:%(threadName)s: %(funcName)s:%(lineno)s: %(message)s',
                'datefmt': '%a, %d %b %Y %H:%M:%S',
            }
        },
        'handlers': {
            'file': {
                'level': 'DEBUG',
                'class': 'logging.handlers.RotatingFileHandler',
                'filename': logfile,
                'maxBytes': 5242880,
                'backupCount': 10,
                'formatter': 'detailed'
            },
            'console': {
                'level': 'DEBUG',
                'class': 'logging.StreamHandler',
                'formatter': 'detailed'
            }
        },
        'root': {
            'level': 'DEBUG',
            'handlers': ['console']
        }


    }
    logging.config.dictConfig(LOGGING)
    global logger
    logger = logging.getLogger(__name__)


    starttext = ("======== Start renderer agent")
    print (starttext) # this goes to the /var/log/upstart log file
    print (datetime.datetime.now().ctime() + ": See log messages in " + logfile)
    logger.info(starttext) # this goes to the log file in /scratch/amivideo/logs


    global TheMainLoop
    TheMainLoop = GLib.MainLoop()


    # Create an object to watch for the DBus signals that come when the
    # Jukebox comes online.
    global DBusWatcher
    DBusWatcher = CDBusWatcher()


    # Create the TapMusic proxy (and try to connect to the real channel)
    global NetManagerProxy
    NetManagerProxy = CNetManagerProxy()
    NetManagerProxy.tryConnect()
    if NetManagerProxy.connectionUp():
        mac = NetManagerProxy.getMac()
        logger.info("MAC address is {}".format(mac))


if __name__ == "__main__":
    main()
```

---

### Post by skierstead-t on 2017-08-04
**Update**:

I switched to a different python dbus binding and now it works. That is, I switched from [dbus]("https://dbus.freedesktop.org/doc/dbus-python/")[-]("https://dbus.freedesktop.org/doc/dbus-python/")[python]("https://dbus.freedesktop.org/doc/dbus-python/") to [pydbus]("https://github.com/LEW21/pydbus") and found success.

**So my trouble would appear to be in ****dbus****-python**.  Can anyone tell me what might have caused the breakage?

For the record, here's my python script that uses pydbus to do the query. It works on both Trusty and Xenial:

```

#!/usr/bin/env python


import argparse
import logging
import logging.config
import datetime
import time
from pydbus import SystemBus


NETMANAGER_NAME = "org.freedesktop.NetworkManager"
NETMANAGER_INTF = NETMANAGER_NAME
NETMANAGER_PATH = "/" + NETMANAGER_INTF.replace(".", "/")


logger = logging.getLogger('renderer_agent')


# ======================================================
def getMac(ifname):
    bus = SystemBus()


    # First find the device path for the passed-in ifname
    remote_object = bus.get(NETMANAGER_NAME, NETMANAGER_PATH)
    device_path = remote_object.GetDeviceByIpIface(ifname)
    logger.info (device_path)


    # Now get its "HwAddress" property
    dev_proxy = bus.get(NETMANAGER_NAME, device_path)
    mac = dev_proxy.Get("org.freedesktop.NetworkManager.Device.Wired", "HwAddress")


    return mac


def main():
    parser = argparse.ArgumentParser()
    args = parser.parse_args()


    # Set up logging, with rotation
    logfile = "kier.log"
    LOGGING = {
        'version': 1,
        'formatters': {
            'detailed': {
                'format': '%(asctime)s %(levelname)s:%(threadName)s: %(funcName)s:%(lineno)s: %(message)s',
                'datefmt': '%a, %d %b %Y %H:%M:%S',
            }
        },
        'handlers': {
            'file': {
                'level': 'DEBUG',
                'class': 'logging.handlers.RotatingFileHandler',
                'filename': logfile,
                'maxBytes': 5242880,
                'backupCount': 10,
                'formatter': 'detailed'
            },
            'console': {
                'level': 'DEBUG',
                'class': 'logging.StreamHandler',
                'formatter': 'detailed'
            }
        },
        'root': {
            'level': 'DEBUG',
            'handlers': ['console']
        }


    }
    logging.config.dictConfig(LOGGING)
    global logger
    logger = logging.getLogger(__name__)


    starttext = ("======== Start tool")
    print starttext # this goes to the /var/log/upstart log file
    print datetime.datetime.now().ctime() + ": See log messages in " + logfile
    logger.info(starttext) # this goes to the log file in /scratch/amivideo/logs


    mac = getMac("eth1")


    logger.info("MAC = {}".format(mac))


if __name__ == "__main__":
    main()
```

---

