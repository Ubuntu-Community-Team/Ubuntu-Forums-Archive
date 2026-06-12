---
title: "Ubuntu One in 13.10 Not Honoring Disabling of Notification Display"
date: 2013-12-19
forum: Ubuntu One (CLOSED)
---

### Post by buzzingrobot on 2013-12-19
In 13.10 here, I've deselected the "Allow all notifications to this device" in Ubuntu One -> Settings.

However, it is not persistent. After a reboot or a new login, the option is re-selected and the notifications are displayed.

Is there a fix for this?

---

### Post by Irihapeti on 2013-12-19
I'm not seeing this problem with my own system. I turned it off on my netbook to check, and the settings persist. I'm using 14.04, and haven't used it on 13.10, so I don't know if there's a bug in 13.10 or not.

Another factor might be that I have the netbook set up so that it only syncs when I tell it to, not automatically, though I'm not sure that this should make any difference.

It might be worthwhile looking through your Ubuntu One logs to see if they say anything useful. [https://wiki.edubuntu.org/UbuntuOne/syncdaemon.conf](https://wiki.edubuntu.org/UbuntuOne/syncdaemon.conf) looks as though it could be helpful.

If all else fails, you could try completely removing and reinstalling Ubuntu One, as per [https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/](https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/) If you have a lot of data on the server, I'd recommend NOT renaming the Ubuntu One folder or you end up downloading the whole lot again. When you set up again and choose which folders you want to sync, the system simply takes a few seconds to a minute or so to check that the files are present at both ends.

Otherwise, try contacting Ubuntu One, though I notice that they're not the quickest at answering support requests.

---

### Post by buzzingrobot on 2013-12-19
Thanks for the syncdaemon.conf link.  I found the system syncdaemon.conf in /etc/xdg/ubuntuone.  But, in ~/.config/ubuntuone, I found only syncdaemon.conf.old. It contained the stanza, "show_all_notifications = False", so I renamed the file to syncdaemon.conf, logged out and in, and all seems well.

I do recall that the Ubuntu One setup GUI crashed when I initially set the no-notifications option.  Perhap the original conf file had just been backed up and the revised file was not created.

---

