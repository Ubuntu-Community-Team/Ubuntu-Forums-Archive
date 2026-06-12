---
title: "Kerberos Admin Svrs - wait for 5 characters on startup"
date: 2007-01-15
forum: Server Platforms
---

### Post by charlie. on 2007-01-15
I've installed the Kerberos 5 KDC packages along with the Kerberos administration services. When my box starts up, the startup log reads:

* Starting kernel log...
* Starting domain name service...
Starting Kerberos Administration Servers: 

It sits there until I enter exactly five characters from the keyboard. I can enter any characters that I like, but it won't continue until I enter five.

After I've hit five keys, it appends "kadmind." to the end of that line and the startup continues. The remainder of the startup is almost instant.

EDIT: I'm running Ubuntu 6.06.1 LTS (32-bit) in command-line mode only. (Alt. CD - Install a Command Line System)

This is weird.
Any suggestions would be great, thanks.

---

### Post by charlie. on 2007-01-18
I am still suffering from this problem, but I am no longer sure that it waits for exactly 5 characters. All I know is that it does wait for SOME characters. I have seen it proceed after 3 sometimes. I've also seen it wait for 6.

Either way, unless you type some stuff, it does not continue to boot.

---

