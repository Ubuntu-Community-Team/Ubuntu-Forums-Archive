---
title: "Xen on 64 bit Gutsy &amp; Feisty"
date: 2007-12-18
forum: Virtualisation
---

### Post by asteffes on 2007-12-18
I have been trying to get Xen to work with 64 bit Gutsy on Intel hardware. While xen-create-image will indeed create a guest VM using the 64 bit (x86_64) Gutsy distro, it will only start that VM exactly once. If that VM is rebooted or restarted via 'xm', it 'xm' thinks it's running but there is no way to reach it over the network.

However, I tried something a bit non-standard to see if it would work. I told my Gutsy 64 bit host to create a 64 bit, x86_64 Feisty VM using the 2.6.22-14-xen kernel included in the 7.10 host. It works! I can create, teardown and restart the "Feisty" VMs (which are running the Gutsy kernel) to my heart's content.

Thing is, I'm not sure how or why this works. Has anyone used 7.10/x86_64 guests under 7.10? If so, how did you make it work?

---

### Post by listerthrawn on 2008-01-03
I know exactly what your problem is.  It's to do with udev.

start your gutsy vm with xm create -c vm.cfg

When you log on to the console, go to /etc/udev/rules.d and look at 70-persistant-net.rules

You'll see udev is creating different 'network cards' each time you reboot because Xen is giving it a random MAC each time.

To make it work, clear out all the entries out of that file except the eth0 one and note down the MAC address.  Now shutdown the VM (either with halt or xm shutdown, your choice)

Now edit the vm's config file in the /etc/xen/ directory and look for the line that starts vif.  Make it look like this:-

vif      = [ 'mac=00:16:3E:45:7A:38,ip=192.168.1.2' ]

Use your MAC and IP obviously, and don't copy and paste what I've done because the formatting will be wrong.

Start the VM with xm create <config file> and voila your network is restored.

Hopefully this will work for you.

Listerthrawn

---

