---
title: "Can mount cifs shares by IP but unable to ping the same IP?"
date: 2009-11-23
forum: Server Platforms
---

### Post by Wildscot on 2009-11-23
Hi,

I'm having what strikes me as an odd problem, but then I'm no expert so maybe someone can help?

I have a server (Ubuntu 9.10) which mounts a number of windows shares on a lan by ip through fstab with no problems. 

I can browse them, unmount them etc. They mount again with 'sudo mount -a' again no problem. I can also mount the shares manually with 'sudo mount -t cifs -o guest //192.168.1.22/bob /mnt/shares/bob'.

However I can't ping these ip's from the server. Surely if the server can see the shares by ip then it can ping the same ip or am I missing something here?

In case anyone wonders what I'm trying to achieve I'm experimenting with this script ([http://ubuntuforums.org/showthread.php?t=637258](http://ubuntuforums.org/showthread.php?t=637258)) to automatically mount or unmount shares on a network. If anyone knows of a better way to acheive the same thing then I'd be interested in that too.

---

### Post by Wildscot on 2009-11-24
Bah! It was the obvious firewall settings. If in doubt sleep then post.

---

