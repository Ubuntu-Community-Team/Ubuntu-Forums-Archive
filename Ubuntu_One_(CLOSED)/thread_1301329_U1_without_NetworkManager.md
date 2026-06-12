---
title: "U1 without NetworkManager?"
date: 2009-10-25
forum: Ubuntu One (CLOSED)
---

### Post by RavanH on 2009-10-25
Hi,

I am using Wicd (because of slow connection with my RT2500 based wifi card with Network Manager) as an alternative Connection Manager. Now I see in the syncdaemon-exceptions.log file 
```
2009-10-26 03:05:36,133 - dbus.proxies - ERROR - Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
2009-10-26 03:05:36,143 - ubuntuone.SyncDaemon.DBus - ERROR - Error while getting the NetworkManager state org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
```

Can this become a problem?

---

### Post by joshuahoover on 2009-10-26
> **RavanH said:**
> Hi,

I am using Wicd (because of slow connection with my RT2500 based wifi card with Network Manager) as an alternative Connection Manager. Now I see in the syncdaemon-exceptions.log file 
```
2009-10-26 03:05:36,133 - dbus.proxies - ERROR - Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
2009-10-26 03:05:36,143 - ubuntuone.SyncDaemon.DBus - ERROR - Error while getting the NetworkManager state org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
```Can this become a problem?

Yes, it can be a problem if you're not using NetworkManager. However, we'd like to get more information on exactly what is going on with these types of NetworkManager related errors.

If you can file a bug report by right-clicking on Ubuntu One client and selecting "Report a Problem", it would be greatly appreciated. In addition to that, can you run the following at a terminal session and report the output in a comment to the bug?

wget -q [http://launchpadlibrarian.net/34282008/nm-checker](http://launchpadlibrarian.net/34282008/nm-checker) && chmod 755 nm-checker && ./nm-checker

This downloads a small python script (that collects information about the state of NetworkManager on your computer), sets it to executable, and runs the script. If you want to check the script first, please open the URL in your browser first before running the command. :-)

Thank you,

Joshua

---

### Post by djaquay on 2009-11-07
I too am trying to get U1 to work, and am not running Network Manager due to wanting to run Wicd due to a wireless card.  I ran nm-checker, and got the following:

```

ERROR:dbus.proxies:Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files

```

I files bug #477700 on this.

Dave

---

### Post by trundlenut on 2009-11-07
same problem here, bug report filed.

---

### Post by RavanH on 2009-11-08
There is a 7 months old bug report about it on [https://bugs.launchpad.net/ubuntuone-client/+bug/357395](https://bugs.launchpad.net/ubuntuone-client/+bug/357395) but nothing seems to be done... Is there any work going on with this?

Joshua, will it help if I use your nm-cheker and attach it to the above bug report or should I file a new bug report? 

I'd really like to help with this because I and so many other users can no longer use Ubuntu One :(

---

### Post by joshuahoover on 2009-11-09
> **RavanH said:**
> There is a 7 months old bug report about it on [https://bugs.launchpad.net/ubuntuone-client/+bug/357395](https://bugs.launchpad.net/ubuntuone-client/+bug/357395) but nothing seems to be done... Is there any work going on with this?

Joshua, will it help if I use your nm-cheker and attach it to the above bug report or should I file a new bug report? 

I'd really like to help with this because I and so many other users can no longer use Ubuntu One :(

This is the bug we're using to eliminate needing Network Manager. You'll notice we have some branches that are being worked on. One of the developers working on this was out for about a week, but is back this week so we should see some progress on this soon. If you're interested in the progress of this bug, please subscribe to it.

Also, yes, attaching the results of the nm-checker script to bug 357395 would be helpful. Just be sure that you reference what the output is from (nm-checker script). :-)

Thank you,

Joshua

---

