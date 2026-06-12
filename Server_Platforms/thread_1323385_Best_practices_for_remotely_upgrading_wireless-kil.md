---
title: "Best practices for remotely upgrading wireless-killing packages?"
date: 2009-11-11
forum: Server Platforms
---

### Post by shaggy999 on 2009-11-11
I was wondering what the best practices are for running upgrades remotely that kill wireless or even wired connections. There are many times using the desktop version that an upgrade kills my internet connection and I have to reboot. That's pretty simple when I have direct access to a machine, but maintaining a machine remotely seems like another ball of yarn entirely. The only thing I can think to do is to issue a reboot command to occur immediately afterward like this:

```

sudo apt-get -y dist-upgrade && sudo shutdown -r now

```

But that kind of kills the whole idea of never needing to reboot your server except for kernel upgrades. I would think to issue something like 'ifup/down' but in my experience working with the desktop version it seems like my internet setup gets completely borked -- like it can't see my wireless card anymore or something.

Also, is there a way to predict what packages might result in needing to reset network connections? I ask this because I'll update a package that seems innocuous, like 'udev', which is hardware-related but since it's just an event-managing package I wouldn't think it would take down the network, but it does.

edit: I should mention that my issues on the desktop version occur with a completely 100% in-kernel-supported wireless driver.

---

