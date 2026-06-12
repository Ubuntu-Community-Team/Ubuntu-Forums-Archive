---
title: "Modifications to Jaunty Notifications"
date: 2009-05-21
forum: The Cafe
---

### Post by DivineOmega on 2009-05-21
I've made some modifications to the notify-osd that ships with Ubuntu 9.04. I've packaged a deb and provided the source. Please take a look and tell me what you think.

[http://divineomega.co.uk/ubuntu/modifications-to-the-notification-system-of-ubuntu-904/](http://divineomega.co.uk/ubuntu/modifications-to-the-notification-system-of-ubuntu-904/)

Thanks!

---

### Post by keiichidono on 2009-05-21
I don't like either of those improvements. I would prefer the increased time per line implemented and I would like the no notifications when playing video (including flash) to be enforced because that's untrue for my Ubuntu Jaunty x64 installation. Also, make a version for x64 so I can try it out. I'm being tough on you but as a programmer I expect you to meet my (the users) demands. I must say I appreciate your good work, keep it up.

---

### Post by Mr. Picklesworth on 2009-05-21
Always nice to have alternate approaches out there. You should upload the source as a proper branch of notify-osd. Just go to the project's code page on Launchpad ([https://code.edge.launchpad.net/notify-osd]("https://code.edge.launchpad.net/notify-osd")) and choose to register your branch :)

I definitely agree about removing that 'disable notifications while playing videos' feature. It breaks confirmation bubbles (even though having visual feedback for volume control is quite important while watching a movie!) and means that important messages disappear. Also, what if the video I'm watching is work-related?

---

