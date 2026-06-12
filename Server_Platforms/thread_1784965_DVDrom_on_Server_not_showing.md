---
title: "DVDrom on Server not showing"
date: 2011-06-17
forum: Server Platforms
---

### Post by Nixforce on 2011-06-17
Hi,

Im setting up a local home server for my development. I have downloaded the wireless card drivers and burnt them to a DVD disc (as dont have any CDs) I have it in the DVD drive on the Server, and i dont know how to access the DVD via the console.

Thanks

---

### Post by CharlesA on 2011-06-17
There should be either a cdrom or dvd entry in /dev/

You'd mount it like so:

```
sudo mount /dev/cdrom /cdrom
```

or

```
sudo mount /dev/dvd /cdrom
```

The device name might be different tho.

---

