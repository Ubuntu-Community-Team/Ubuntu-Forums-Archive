---
title: "Hangs forever after login..."
date: 2012-09-29
forum: Ubuntu One (CLOSED)
---

### Post by 3vi1 on 2012-09-29
On two of my 7 machines, U1 just does *not* want to work.

I've tried all the standards:  kill the processes, remove *all* the local files (in .config, .cache, .local/share), remove the machine from the account, plus remove the password from seahorse.  And it still fails to work.

After I do all that stuff, and log in with it, it showing the "Getting information..." loop forever after login, and never proceeds.

The status just seems to indicate that it's not connected.  I'm not using wicd or anything on this machine; I'm using network manager.  I may have had wicd on the machine several upgrades back, though.  I even tried ending the network-manager service to see if it would proceed... but I have no evidence that it's not proceeding because of the network connectivity (with which no other app has an issue).

evil@jupiter:~$ u1sdtool --status
State: INIT
    connection: Not User With Network
    description: just initialized
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING

I don't think that the other machine, which shows the exact same symptoms as far as I can tell, ever had any other network-manager on it.

---

### Post by mparillo on 2012-09-30
Is there a next button showing in the bottom right, even though it shows Getting Information at the top center?

I think I recall this, and just clicked next, and if your use case, like mine, is the simple one (all you want to sync is your U1 directory and below), it worked.

---

### Post by 3vi1 on 2012-10-01
I can click next to proceed, but the service continually says "File Sync starting..." at the top right and not a single byte of the 600MB in my ~/Ubuntu One folder ever gets pulled down to the machine.

u1sdtool continues to show a status of "INIT" with all the 'is' questions saying False.  I don't know why it wouldn't be connected.  I'm accessing these systems over a wireless network, so I know they are connected.

---

### Post by 3vi1 on 2012-10-01
I figured it out.

The solution was to:

   sudo apt-get install gir1.2-syncmenu-0.1

This was caused by this bug:

[https://bugs.launchpad.net/ubuntuone-client/+bug/1053775](https://bugs.launchpad.net/ubuntuone-client/+bug/1053775)

---

### Post by Zomgrick on 2012-10-01
[FONT="Tahoma"][SIZE="2"]I've had this problem, restarting my computer solved it tho. You probably tried that but if you didn't, do it. :) 

EDIT: You solved it, sorry.[/SIZE][/FONT]

---

### Post by 3vi1 on 2012-10-01
Yes, I tried restarting many times after cleaning up.

In addition to the installation fix above, I found I had to do one more thing on both boxes - delete the old dbus session entries.

Until I did that, I kept getting:

```

dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-GitKDdcsz0: Connection refused
```

from anything that tried to import dbus.

So, here's the complete solution just in case anyone else runs into this frustrating problem:

```
sudo apt-get install gir1.2-syncmenu-0.1
sudo service dbus stop
sudo rm .dbus/session-bus/*
sudo service dbus start

```

I only rarely used the two machines that were having the problem, but when I upgrade them I tend to upgrade them both at the same time.  It sounds like I had unfortunately upgraded them both at a point in time where the upgrade process was semi-borked.

---

