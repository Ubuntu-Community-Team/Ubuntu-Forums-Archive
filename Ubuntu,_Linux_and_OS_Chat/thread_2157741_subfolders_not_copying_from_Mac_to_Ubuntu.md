---
title: "subfolders not copying from Mac to Ubuntu"
date: 2013-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by labman365 on 2013-06-26
When I copy a folder that contains sub-folders from Mac 10.6 to Ubuntu 10.04.4 the sub-folders don't get populated with any files.

---

### Post by cariboo on 2013-06-26
If you are using the command line, you the recursive option when copying several directories that have sub-directories eg:

```
cp -R /home/$USER/Videos /media
```

When using command line utilities, the man command is your friend.

---

### Post by montag dp on 2013-06-26
You need to provide a little more information, as it's not quite clear what you are trying to do.  Are you dual booting, and trying to copy files from one partition to the other?  Are you trying to use the command line, or a file manager (the GUI)?  If the latter, which file manager are you using?  The Mac OS one (not sure what it's called)?  The default Ubuntu one (Nautilus)?

As cariboo said, if nothing else than at least the command line utility should work with the recursive option.

---

