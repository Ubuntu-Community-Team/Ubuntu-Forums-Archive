---
title: "Shutdown problem"
date: 2011-09-24
forum: Server Platforms
---

### Post by Demaki on 2011-09-24
Hi, I'm using Ubuntu server 10.10 (2.6.35-30-server) on a Atom D525 PC.

At shutdown I usually get the message **mount: / is busy**
This message goes away when I shutdown mysql before I shutdown the PC, so my best guess is mysql is not finished when the system tries to unmount the root folder.

I looked into the services which are started/stopped during boot and shutdown and found out that mysql is stopped by an upstart script:
```
stop on runlevel [016]
```The unmounting of the filesystems is default:
```
S31umountnfs.sh
S40umountfs
S60umountroot
```For now I added a **S26shutdowndelay** which make the shutdown process sleep for ten seconds. This seems to work, but this is not safe nor elegant.

If you have any ideas on how to fix this properly, please let me know.

Thanks in advance!

---

### Post by Kelketek on 2011-09-27
The MySQL script makes a PID file used for getting its process ID to check if the server is running. You can also run a loop that checks to see if the process is down yet before continuing the shut down.

```

while [ "$(pidof process_name)" ] 
    sleep 1
done

```

You may be able to put `cat /path/to/PIDfile` where the PID should be so that its output is used. Note that those are backticks and not single quotes.

I haven't tested that, but try that in your shutdown delay script. This should make sure that the shutdown always waits for MySQL to finish up cleanly before going the rest of the way down.

---

