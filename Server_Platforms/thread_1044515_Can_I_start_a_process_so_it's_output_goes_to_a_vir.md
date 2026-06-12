---
title: "Can I start a process so it's output goes to a virtual terminal?"
date: 2009-01-19
forum: Server Platforms
---

### Post by paul2110 on 2009-01-19
Please Help!

I have Ubuntu Server 6.06.1 running Asterisk PBX and a custom Java application.

Both Asterisk and the Java app are started in /etc/inittab on run level 2 so they're both running once Ubuntu has booted up.

However, both apps send very verbose information to the main console and I was wondering if it's possible to start each process in a separate terminal so I can switch to the terminals to see the console output (using Ctrl+Alt+F1, F2 etc.) For example I could start Asterisk in Terminal #2 and the Java app in Terminal #3...

Is there any way to do this using either inittab or a standard script?

---

