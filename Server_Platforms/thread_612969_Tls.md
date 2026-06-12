---
title: "Tls"
date: 2007-11-14
forum: Server Platforms
---

### Post by bigdaddyweed on 2007-11-14
I am setting up a mail server following the howto [here]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5") and can't seem to get past the part about the TLS setup. I have double and triple checked everything to no avail. when i restart postfix i get this message

"/etc/init.d/saslauthd: line 8: NAME: command not found"

When i check line 8 in that file it is edited exactly as described in the howto and if I connect via telnet to check it out everything seems to work.

Any ideas anyone??

---

### Post by MJN on 2007-11-14
Post your config as without it we'd be guessing.

Incidentally, you cannot test TLS connections with telnet as it doesn't support the encryption.

Mathew

---

### Post by bigdaddyweed on 2007-11-15
What part of my config?

Here is a snippet from the code where the error is coming from. 

/etc/rc2.d/S20saslauthd

#!/bin/sh -3

NAME=saslauthd
DAEMON="/usr/sbin/${NAME}"
DESC="SASL Authentication Daemon"
DEFAULTS=/etc/default/saslauthd
PWDIR=/var/run/saslauthd
PIDFILE="/var/spool/postfix/var/run/$(NAME)/saslauthd.pid"

....

Hope someone can help

---

### Post by MJN on 2007-11-15
You need to use curly brackets around NAME e.g. {NAME} and not (NAME) (just like in the DAEMON line).

Mathew

---

### Post by bigdaddyweed on 2007-11-15
Funny because as I was typing it in the window (which I do to catch things like that) i thought something was weird with the code but couldn't think just what.

Thanks a bunch now how do i mark this as an Answered Thread??

---

### Post by MJN on 2007-11-15
Not being able to see the wood for the trees is an all too common position to be in once you stare at config for too long - another pair of eyes is always worth it (hence why posting *your* config is essential when you've followed a HowTo and it doesn't work as expected).

Glad to hear you're sorted (I assume it's working now) - you can mark the thread as solved by editing your original post (using the Advanced editing mode).

Mathew

---

