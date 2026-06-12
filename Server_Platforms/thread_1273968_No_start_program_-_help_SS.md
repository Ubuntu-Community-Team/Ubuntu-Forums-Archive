---
title: "No start program - help :S:S"
date: 2009-09-24
forum: Server Platforms
---

### Post by alanfake on 2009-09-24
root@mr-desktop:~# sudo start-stop-daemon --start --exec /home/mr/pvpgn/sbin --chuid bnetd
start-stop-daemon: Unable to start /home/mr/pvpgn/sbin: Permission denied (Permission denied)

---

### Post by Lars Noodén on 2009-09-24
> **alanfake said:**
> root@mr-desktop:~# sudo start-stop-daemon --start --exec /home/mr/pvpgn/sbin --chuid bnetd
start-stop-daemon: Unable to start /home/mr/pvpgn/sbin: Permission denied (Permission denied)

It looks like you might have plucked a line out of context from the systemv init scripts in /etc/init.d

Your one-line script is missing the function start-stop-daemon.  It and a few others are stored in this file:

/lib/lsb/init-functions

take a look at the file /etc/init.d/skeleton
or the man page for update-rc.d(8&#41;

If you are planning on writing your own startup script, then you might look ahead to 'upstart'

---

### Post by koenn on 2009-09-24
> **Lars Noodén said:**
> 
Your one-line script is missing the function start-stop-daemon. 

hm, to me it looks like 'start-stop-daemon' executes ok, but can't do the requested '--exec /home/mr/pvpgn/sbin' : it fails with a permission error - possibly that file should be set executable (chmod +x)

but you're right that if the OP is looking to run a service, he'd better look in to init scripts and upstart.

---

