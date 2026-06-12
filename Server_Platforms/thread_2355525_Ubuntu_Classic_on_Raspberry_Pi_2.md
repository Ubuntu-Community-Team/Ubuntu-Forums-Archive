---
title: "Ubuntu Classic on Raspberry Pi 2"
date: 2017-03-13
forum: Server Platforms
---

### Post by arathen on 2017-03-13
Hi all. Im not sure if im posting this in the right place, so please feel free to refer me on. I've just migrated my Raspberry Pi 2 from Raspbian to Ubuntu 16.04 LTS "classic" (not Core and not MATE) from here: [https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)
and for the most part everything seems to be working really well, but I cant find any links or references to a community or forums that deal with that particular platform.

One of the first things I did after install was to move the root filesystem across to an NFS mount, and that mostly also seems to be working great.

However, the problem that i seem to have introduced by doing that, is now my Pi wont reboot. Booting up from a cold start is fine, but a warm reboot hangs indefinitely. If I had to guess, it may be a problem with systemd sequencing the shutdown such that the network stops and the filesystem unmounts are in an order that pulls the rug out from under the OS running on NFS. The last three things on the console before the lockup are:

[ OK ] Stopped target Network.
         Stopping Raise network interfaces...
[ OK ] Stopped Create Volatile Files and Directories.

And thats it until the power gets cycled.

Im not 100% sure this is necessarily an Ubuntu problem, or a Raspberry Pi problem, but it seems it could be more generically related to how systemd works in conjunction with NFS root installs.

Does anybody have any ideas? My systemd skills are ok, but im still learning that particular product.

Many thanks for any help.

---

