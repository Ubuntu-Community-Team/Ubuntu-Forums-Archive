---
title: "visudo"
date: 2009-09-16
forum: Security
---

### Post by easoukenka on 2009-09-16
For some reason my ability to sudo without password for some commands has quit working.  It appears to be after the update last night that had me reboot but I am not certain.  


Thank you in advance for any assistance.  

root@asoukenka:/home/asoukenka# visudo


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#


Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL
%admin ALL=(ALL) ALL
#asoukenka ALL=NOPASSWD: /usr/sbin/bandwidthd, /sbin/swapoff, /sbin/swapon
asoukenka ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL



asoukenka@asoukenka:~$ sudo /usr/sbin/bandwidthd 
[sudo] password for asoukenka:

---

### Post by Lars Noodén on 2009-09-16
> **easoukenka said:**
> 
#asoukenka ALL=NOPASSWD: /usr/sbin/bandwidthd, /sbin/swapoff, /sbin/swapon


Can't say the reason the sudoers file got that way, but if those are the programs you wish to run with sudo but without a password, then uncomment the line.
Right now it's the same as not being there.

---

### Post by easoukenka on 2009-09-16
While testing i removed that line and added

asoukenka ALL=(ALL) ALL

Which means allow all programs.  I did this just for testing because the other line was not working either all of the sudden

---

### Post by bodhi.zazen on 2009-09-16
You do not have any user or group configured to sudo without a password currently.

---

### Post by easoukenka on 2009-09-17
Ok I understand what you are saying the line I added was incorrect.  However the line that was commented was my origonal line that stopped working.  However after a reboot now the old line is working now.

I'm not crazy though the only reason I modified this file was some scripts stopped running that have always run so I just tryed that other line for testing.  

Thank you all for your support

---

### Post by bodhi.zazen on 2009-09-17
Strange things happen if a user is specified more then once in /etc/sudoers

So you specified your user once, I assume, as your user is in the admin group

and a second time by user name :(

In theory , the FIRST instance is applied to your user (%admin) , and the second is ignored.

---

