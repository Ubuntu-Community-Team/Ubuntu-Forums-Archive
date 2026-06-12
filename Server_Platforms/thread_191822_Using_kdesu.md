---
title: "Using kdesu"
date: 2006-06-08
forum: Server Platforms
---

### Post by Raezel on 2006-06-08
I started using Kubuntu 6.06 recently, without much prior Linux experience and have gotten around quite nicely, but one thing that started to concern me is  using kdesu. When I kdesu it prompts for my password as expected, but accepts any given password, even a blank one. Thist doesn't happen when using sudo. I don't know if this is relevant to the issue, but I just updated my KDE to 3.5.3. 

Is this a bug, or have I messed something up? Any help appreciated.

---

### Post by aysiu on 2006-06-08
That's not normal behavior.

---

### Post by Raezel on 2006-06-08
I kind of figured it's not, but the real question is, can I do something about it, and should I report it as a bug to Malone? Or is it something I might have caused myself. I haven't really done nothing but installed, updated KDE to 3.5.3 and installed a few programs.

---

### Post by aysiu on 2006-06-08
Can you type this and see if it matches with the code below? ```
sudo visudo
```

Code to compare to: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
``` If it *does* match, consider filing that bug report.

---

### Post by Raezel on 2006-06-08
Thanks, I'll check that once I get back to my Kubuntu machine.

---

### Post by xenblend on 2006-06-08
well i have the exact opposite problem: no matter how carefully I enter my passwds into kdesu I cant log in.  Maybe we should swap?  :)

---

