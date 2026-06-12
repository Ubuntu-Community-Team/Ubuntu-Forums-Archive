---
title: "TV tuner card on server - is this possible?"
date: 2014-03-15
forum: Server Platforms
---

### Post by david_brown on 2014-03-15
Hi, I am not sure if this is possible or not so some input would be appreciated.

I have a headless server running 12.04 at home. Got it to do backups and run Plex media server so far. I'm wondering if it's possible to add a USB tv card to the server and control it by a web interface?

I already have a USB tuner - not sure of the make though.

I appreciate that this might be impossible / very difficult but would like to know if there is an easy way to accomplish this.

Thanks

---

### Post by cariboo on 2014-03-16
TO find out if there are drivers fro your device, plug it in, and run:

```
lsusb
```

The output should be similar to this:

```
 lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Once you have determined which device is the tuner card, do a search using your favorite search engine of the ID number. It should look similar to this:

```
045e:00db
```

---

