---
title: "even.d initctl script how?"
date: 2008-09-16
forum: Server Platforms
---

### Post by kaltsi on 2008-09-16
I woud like run a application by initctl.
I wrote the next scipt:
/etc/even.d/mnt

# MNT runner
#

start on runlevel 2

stop on shutdown

respawn

script

exec su -s /bin/bash -c "/home/tech/mnt/mntII /home/tech/mnt/live.cfg >> /home/tech/mnt/mnt.log 2>&1" mnt

end script

If I use the "sudo initctl stop mnt" command, the state will be stoped, but a mntII process runs forward.

How can I run an application with different user such as root?

---

