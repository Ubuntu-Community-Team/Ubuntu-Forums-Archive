---
title: "Start Liferay at Boot"
date: 2010-08-20
forum: Server Platforms
---

### Post by trippinnik on 2010-08-20
I know Ubuntu has changed the startup system in 10.04 and I am wondering how to go about starting my liferay server at boot (instead of starting manually).

There's already a startup script, can I setup a symlink to somewhere to have it start automatically?

I've tried searching through documentation and google but most of it applies to older versions of Ubuntu.  It could be that I'm not using the right vocabulary, but I would appreciate some help here.

---

### Post by ajgreeny on 2010-08-20
What command do you use at the moment to start it, and does it need sudo?

You can probably simply write a shell script with that command in it and add that shell script to your startup applications list if it does not need sudo to start, or perhaps add the command without the sudo to the **/etc/rc.local** file, just above the "exit 0" line.

It is possible that an init.d script may work as you suggest, but some things no longer work using init.d

---

### Post by trippinnik on 2010-08-20
That worked thanks. [SOLVED]

---

### Post by ajgreeny on 2010-08-20
> **trippinnik said:**
> That worked thanks. [SOLVED]
For future reference, which one of my suggestions was it that worked?

---

