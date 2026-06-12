---
title: "Trying LXC. Need some help."
date: 2010-05-15
forum: Virtualisation
---

### Post by tnek on 2010-05-15
Hi!

I'm about to try LXC. I have Googled and read a lot of information, but I still have some steps before I can try it.

What I have done is:

[LIST=1]
[*]Installed a Server with Ubuntu Server 10.04
[*]Installed the usermode tools for LXC:
sudo apt-get install lxc
[*]Installed the bridge-utils:
sudo apt-get install bridge-utils
[*]Added a bridge br0 with uses DHCP and has one bridge port, eth0
[*]Installed debootstrap to download Lucid for my container:
sudo apt-get install debootstrap
[*]Used debootstrap to setup a root filesystem in ./minubuntu containing Ubuntu Lucid for AMD64 architecture:
sudo debootstrap --arch amd64 lucid ./minubuntu [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
[/LIST]
I want to use LXC to run the lucid system I got through debootstrap. I want the systems to be as separate as possible. I want to create a few systems like this one for running different services, separated.

What should I do next? Also, the minubuntu directory is around 250MB, is it possible to get something a bit more slim?

---

### Post by dsylexic on 2010-05-27
Hi,

Have you succeeded in starting up the container yet?  There's a fair bit of setup that needs to be done after debootstrap (deleting unused devices, modifying init scripts, etc.).  This thread: [http://ubuntuforums.org/showthread.php?t=1382823](http://ubuntuforums.org/showthread.php?t=1382823) has some good information and links, or you could use something like the lxc-ubuntu script in [http://github.com/phbaer/lxc-tools](http://github.com/phbaer/lxc-tools), which does almost everything for you.

To save space, you could bind-mount parts of your host filesystem (like /bin, /sbin, etc.) in the guest via the lxc.mount option, so as not to need a duplicate copy of those files in every container.  **However**, this is a bad idea if you want isolation, because Lucid's LXC currently contains a bug that grants all containers write access to filesystems shared with the host--even if you mount them ro.

---

