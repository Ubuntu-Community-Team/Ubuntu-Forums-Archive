---
title: "sync usb drive on mount?"
date: 2013-07-31
forum: Server Platforms
---

### Post by wlraider70 on 2013-07-31
I have a backup folder on my ubuntu server. I also have a USB drive of the same size. 

Is it possible to make the local backup area auto sync with the USB drive whenever I plug it in?

---

### Post by wlraider70 on 2013-08-02
Bump....




I can auto-mount from fstab.
I sync with rsync.

How do I get the system to recognize the mount and sync as a response?

---

### Post by nerdtron on 2013-08-02
Not really here for a solution but can be a possible option.
Since it can auto mount in fstab and rsync to copy files, why not create a script that will check if a particular device is mounted. Then if is mounted, it will run the specific rsync command you specified.
Add this to the crontab entry make it run the script every minute.

---

### Post by sudodus on 2013-08-03
Maybe ***Incron*** would be an alternative

[http://www.howtoforge.com/triggering-commands-on-file-or-directory-changes-with-incron](http://www.howtoforge.com/triggering-commands-on-file-or-directory-changes-with-incron)

---

### Post by ZippyUbu on 2013-08-04
Hi - I was looking for something similar - Have a look at this: 

[http://superuser.com/questions/246953/trigger-off-rsync-by-just-plugging-in-a-usb-drive](http://superuser.com/questions/246953/trigger-off-rsync-by-just-plugging-in-a-usb-drive) 

Might help with what you need.

--
Zu

---

