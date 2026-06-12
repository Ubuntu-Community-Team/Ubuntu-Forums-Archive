---
title: "Telenet Connection Refused"
date: 2009-12-13
forum: Server Platforms
---

### Post by Vegan on 2009-12-13
I was wondering, been getting a connection refused problem with TELNET, all other services seem to be working so far.

---

### Post by Iowan on 2009-12-13
I'm sure this is obvious beyond belief, but is **telnet** running (either a service or daemon)? With it's security problems, I doubt it's configured out-of-the-box.

---

### Post by Vegan on 2009-12-13
Seems to be running, I tried a bunch of them. I have my firewall open so the LinkSys box cannot be it.

---

### Post by BkkBonanza on 2009-12-13
Telnet isn't generally used by anyone any more except perhaps for quick tests on some other protocols like POP, HTTP etc. You shouldn't be using it either. Anything you type including login and password are clearly visible to anyone listening.

I'm sure it's no longer installed or enabled (as a service) on any systems now, so any typical firewall configs would be dropping connections.

---

### Post by BkkBonanza on 2009-12-13
Well, just where are you trying to telnet from/to?

---

### Post by Iowan on 2009-12-13
I notice **telnetd** is available in Synaptic on this Hardy machine, as is **telnetd-SSL** (and the client for it).

**sudo ps -ef | grep telnet** reveal anything?
Can **telnet** do something **SSH** cannot?

---

### Post by Vegan on 2009-12-13
I see one line with that ps check. tty1 is the localhost with me logged in.

I wanted to connect from Windows using a VT220 terminal program to the Linux machine.

I can change the terminal emulation to a range of choices up to VT320.

---

### Post by BkkBonanza on 2009-12-13
Ok. So on your Linux machine you need to make sure "telnetd" is running.
Try, "ps afx" and view listing to see if that's running.
Can also use, "netstat -lntp" and make sure telnetd is listening on port 25 (default).
If both those are happening then you likely need to open port 25 on your firewall.
If telnetd isn't running then you likely need to install it. Use Synaptics (as above).

After you mess around with Telnet the best thing to do (really) is install Putty on Windows and use SSH to connect to your Linux machine (and remove telnetd again). SSH has way more cool stuff (proxying, X forwarding) and it's secure so you can use it across the web safely. With ssh and X forwarding you can even have GUI windows from your linux box show up on your Windows desktop.

---

### Post by Vegan on 2009-12-13
excuse me, port 25 is the mail port, 23 is telnet

---

### Post by BkkBonanza on 2009-12-14
Ah, ya, faulty memory!

---

### Post by Vegan on 2009-12-14
I can connect to the mail on port 25 only getting refused on port 23, go figure.

---

