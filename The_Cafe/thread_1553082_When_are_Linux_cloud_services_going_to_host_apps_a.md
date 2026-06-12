---
title: "When are Linux cloud services going to host apps and not just files and networking?"
date: 2010-08-14
forum: The Cafe
---

### Post by Nick_Jinn on 2010-08-14
Isnt that the real goal of cloud software? To be able to sell low power netbooks and tablets running cheaper hardware (like ARM processors) and Linux/Android, and out competing the conventional desktop style mobile computing by offering more for less?

Can we already host apps on UbuntuOne and I am just behind the curve again?


What might be cool is to make it really easy (GUI based) to use your own desktop as a cloud server. So you just leave your desktop running and its a cloud provider for your tablet either around the house or when you are out and about...but without being a virtual desktop, just hosting apps and drop box and stuff.

---

### Post by earthpigg on 2010-08-14
hi,

> When are Linux cloud services going to host apps and not just files and networking?

Today.

with ssh and x forwarding, you can run apps from a remote computer on your netbook.

take a look at the picture below.

on the right, openoffice is running on my primary desktop.
on the left, openoffice is running over the lan from my server running ubuntu 9.04 over ssh with x forwarding.

no reason i couldn't do the same thing with my netbook, but the screenshot wouldn't look as nice. :P

with a standard internet connection, however, this really isn't viable if you are on the road. most home internet connections don't have the upstream bandwidth to allow you to run graphical software remotely without it being horribly slow. Great on the LAN, not so great on the road. due to those same limitations, i found it to be non-viable to stream movies from my server in California to me on vacation in Hawaii.... but i ***could*** stream mp3 music to myself in hawaii on my netbook.

note that when i say 'server', i really just mean 'a desktop computer that i never turn off that happens to have sshd installed and configured, in addition to my multimedia library'. 

[this]("http://wiki.archlinux.org/index.php/SSH") is the guide i used to learn ssh. you can replace the pacman stuff with apt-get or synaptic, and you don't need to manually add the sshd daemon to ubuntu's startup (ubuntu does it automatically, arch does not)

---

### Post by Nick_Jinn on 2010-08-14
Yeah, but we are still hosting apps on a home desktop, just steaming app functions rather than an entire remote desktop which is more efficient for ARM based tablets....In my opinion, ARM is going to catch up as it moves into dual and quad core processor schemes...it already offers great CPU power for price and energy consumption but is poor at mult-tasking....a quad core ARM processor might be a decent computing device for the money.

Anyway, I am talking about installing apps to the cloud server...not the servers choice of apps but your own apps that you can tweak and serving to whoever you allow to connect to it.

---

### Post by murderslastcrow on 2010-08-14
I used FreeNX to stream applications from a server directly to my friends' computers, including a Linux, Windows, and OS X desktop (PowerPC). So yeah, I don't see why this wouldn't be possible with something as simple as web applications if it's already possible with Blender over a crappy DSL connection.

Of course, you need client software for that, and it could be made simpler through a web-enabled service.

Don't be surprised if everyone starts running WoW straight from their web browsers in the next five years.

---

