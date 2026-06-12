---
title: "bluescanner??"
date: 2009-12-23
forum: Security
---

### Post by Trisket on 2009-12-23
Does any one know of  a Linux compatible, bluetooth security analysis tool kit like bluescanner for xp??

---

### Post by sgosnell on 2009-12-23
15 seconds with Google came up with [Bluescanner .deb for Linux](http://sourceforge.net/projects/bluescanner/files/bluescanner/BlueScan%201.0.6/bluescan_1.0.6.deb/download).

---

### Post by Trisket on 2009-12-23
thats awesome...however its in spanish

---

### Post by rookcifer on 2009-12-23
```
sudo apt-cache search bluetooth
```

This is a command you can use to search the package repositories for keywords so that you might find packages you need.  Using this command, I came across **btscanner**.  I then googled it, and found out that it's one of the more popular bluetooth scanners for Linux (Linux has had bluetooth scanning for years now, longer than Windows).

So, you can try installing it:

```
sudo apt-get install btscanner
```

Or, if you want, you can download [BackTrac]("http://www.remote-exploit.org/backtrack.html")k, which is a LiveCD specially designed for pen testing.  It is based off Ubuntu.  It has all the tools you could possibly need for any kind of "pen testing."  BackTrack would probably be the easiest route since it is designed for this type of thing.

---

### Post by sgosnell on 2009-12-24
That's the first sourceforge project I've seen entirely in Spanish.

Linux has bluetooth tools built in.  If you just want to scan for bluetooth devices, enter ```
hcitool scan
``` in a terminal, and you'll get the name and MAC address of every bluetooth device available.  The man page for hcitool will give you all the commands and capabilities.  There really is no big need for a separate program, because you can write scripts that will do everything necessary.  If you just want to do a scan for bluetooth devices, write a script that just has 'hcitool scan', and send the output to wherever you want it to go.

---

