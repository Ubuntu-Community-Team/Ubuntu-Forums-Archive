---
title: "Why is Firefox doing this to me?"
date: 2010-08-01
forum: Security
---

### Post by pepsifx357 on 2010-08-01
Every time I open firefox, or at random times, it keeps giving me a login pop up.

```
A username and password are being requested by http://localhost:42344. The site says: "administrator"
```

What the hell is this?  What uses port number 42344?

---

### Post by FuturePilot on 2010-08-01
All I can tell you is that this is related to CouchDB and Firefox bookmark syncing. I don't know enough about it to tell you why it is prompting you because it shouldn't be. Surely someone else knows.

---

### Post by Samana on 2010-08-01
That message is telling you that you have a web server on your computer and it is asking for an admin password.  Do you have any Cisco Network monitoring tools installed or any netowrk monitoring tool at all installed?  You might try to see what is running by pointing your web browser to [http://127.0.0.1:42344/](http://127.0.0.1:42344/)

---

### Post by cdenley on 2010-08-02
```

sudo lsof -i :42344

```

---

### Post by pepsifx357 on 2010-08-02
The Port number has changed.  Here's what output I got...

```
ben@ben-laptop:~$ sudo lsof -i :50509
[sudo] password for ben: 
COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
beam.smp  10916  ben   16u  IPv4 114327      0t0  TCP localhost:50509 (LISTEN)
desktopco 10936  ben   14u  IPv4 114371      0t0  TCP localhost:54827->localhost:50509 (CLOSE_WAIT)
desktopco 10936  ben   15u  IPv4 114402      0t0  TCP localhost:54829->localhost:50509 (CLOSE_WAIT)
```

---

### Post by Samana on 2010-08-02
> **pepsifx357 said:**
> The Port number has changed.  Here's what output I got...

```
ben@ben-laptop:~$ sudo lsof -i :50509
[sudo] password for ben: 
COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
beam.smp  10916  ben   16u  IPv4 114327      0t0  TCP localhost:50509 (LISTEN)
desktopco 10936  ben   14u  IPv4 114371      0t0  TCP localhost:54827->localhost:50509 (CLOSE_WAIT)
desktopco 10936  ben   15u  IPv4 114402      0t0  TCP localhost:54829->localhost:50509 (CLOSE_WAIT)
```


Yup, that is from an application that is using CouchDB. Do a google search for beam.smp but it sounds like something related to something displaying something on your desktop(?)

---

