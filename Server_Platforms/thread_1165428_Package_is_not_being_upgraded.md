---
title: "Package is not being upgraded"
date: 2009-05-20
forum: Server Platforms
---

### Post by supanatral on 2009-05-20
I followed a tutorial on how to create a network boot server and add the windows xp cd to it so that I can boot off the network and install XP off of there. Here is the link: [Click Here]("http://sourceforge.net/forum/message.php?msg_id=6140494")

After you "patch" tftp, it says the following:
> Now tell Apt not upgrade this package, so you don't lose your patched package 
echo "tftpd-hpa hold" | dpkg --set-selections 


How can I reverse what I did so that it upgrades again since I removed the XP install feature?

---

### Post by adaniels on 2009-05-20
I think you should do `echo "tftpd-hpa install" | dpkg --set-selections`.

BTW I recommend not using set-selections in the future, but use /etc/apt/prefrences instead. [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by supanatral on 2009-05-21
Awesome! that worked. Thanks

---

