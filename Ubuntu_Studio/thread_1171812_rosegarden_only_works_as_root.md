---
title: "rosegarden only works as root"
date: 2009-05-27
forum: Ubuntu Studio
---

### Post by paul_r on 2009-05-27
got my usb midi device working with rosegarden today, though it will only start as root giving this error:

```
paul@ubuntu:~$ rosegarden
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/share: Permission denied
trying to create local folder /home/paul/.kde/socket-ubuntu: Permission denied
trying to create local folder /home/paul/.kde/socket-ubuntu: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/paul/.kde/socket-ubuntu/kdeinit__0'

```

viewing permissions on ~paul, user can create/delete to it, my user's group and others can just access it. I tried setting group and other access to create/delete though still the error

only other post on the forums close to this, has to do with realtime processing not working unless as root, though this is different, thanks

---

### Post by kayosiii on 2009-05-27
That certainly is odd....
try the following and see if it fixes the problem....

sudo chown -R [username].[groupname] .kde

where [username] is your username and [groupname] is probably also your username.

using the terminal application in your home folder.

---

