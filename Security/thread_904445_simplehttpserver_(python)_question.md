---
title: "simplehttpserver (python) question"
date: 2008-08-29
forum: Security
---

### Post by adept_king on 2008-08-29
the other day, a friend of mine told me to start a simpleHTTPserver in Python of my desktop and i did it, thought it was cool to see my desktop in opera, but the command he gave me "control-C" didnt seem to stop it, should i be worried that i permanently created a simpleHTTPserver out of my desktop?  how would i even go about finding out?

---

### Post by rogeriopvl on 2008-08-29
can you paste the code here?

---

### Post by adept_king on 2008-08-29
friend: go to some directory
me: pictures... yeah.
 friend: in a command line.
 me: ok
 friend: now type:
  python -m SimpleHTTPServer
 me: how about my desktop?
 friend: sure!
or just open a terminal and type that phrase.
  the directory's unimportant
 me: did it
 friend: it waits...
  now, in the browser.
  [http://localhost:8000](http://localhost:8000)
 me: thats cool!
friend: yes, a tiny web server in one line.
  SimpleHTTPServer is actually very useful, it doesn't have to be a directory it serves
  [http://xkcd.com/353/](http://xkcd.com/353/)
 me: can you see it too?
friend: only if I knew your IP address.
  however, don't leave it on.
  :-D
  type control-C in the command line.
me: what if i leave it on? is it not safe?
friend: only if you don't want people to see your files.
  and even then, the chance of them finding this is small.
  they can't change your system that way.
 me: control-C closes it or copies it or what?
friend: Control-C is the Unix way of interrupting a process.

---

### Post by cariboo on 2008-08-29
To check if it is still running in a terminal type:

```
ps ax
```

This is just a snippet of the results:

```
 8292 ?        S      0:00 gksu /usr/sbin/synaptic
 8293 ?        Ss     0:03 /usr/sbin/synaptic
 8298 ?        S      0:01 /usr/lib/notification-daemon/notification-daemon
 8308 ?        Sl     3:40 /usr/lib/firefox-3.0.1/firefox
 8438 ?        S      0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp
 8477 ?        Ss     0:00 dhclient eth0
 8554 pts/1    Ss     0:00 bash
 8595 pts/2    Ss+    0:00 bash
 8602 pts/1    R+     0:00 ps ax
```

As you can see in the listing I have synaptic running, if it was misbehaving, to stop it in a terminal:

```
sudo kill 8292
```

The number is the pid or program id number, use it to kill a process.

Jim

---

