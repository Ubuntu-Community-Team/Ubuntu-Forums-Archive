---
title: "LXD configuration?"
date: 2015-04-25
forum: Virtualisation
---

### Post by jeffw2 on 2015-04-25
So far, not real impressed with LXD. It's documentation is non-existent and for a small home installation with a couple of virtual machines it seems to provide no additional features than LXC while increasing complexity and confusion.

How do I:
[LIST=1]
[*]Modify the configuration of LXD to bridge containers' eth0 connection with my host's br0 interface? I changed /etc/default/lxc-net to USE_LXC_BRIDGE='false' but I get a lot of

```
Apr 25 14:53:07 nas systemd-udevd[2783]: Could not generate persistent MAC address for vethNJ6IOJ: No such file or directory
Apr 25 14:53:07 nas systemd-udevd[2785]: Could not generate persistent MAC address for vethPVTJAQ: No such file or directory
Apr 25 14:53:07 nas libvirtd[1496]: Failed to open file '/sys/class/net/vethNJ6IOJ/operstate': No such file or directory
Apr 25 14:53:07 nas libvirtd[1496]: unable to read: /sys/class/net/vethNJ6IOJ/operstate: No such file or directory
Apr 25 14:53:07 nas systemd[1]: Started ifup for vethNJ6IOJ.
Apr 25 14:53:07 nas systemd[1]: Starting ifup for vethNJ6IOJ...
Apr 25 14:53:07 nas systemd[1]: Stopping ifup for vethNJ6IOJ...
Apr 25 14:53:07 nas ifdown[2818]: /sbin/ifdown: interface vethNJ6IOJ not configured
Apr 25 14:53:07 nas systemd[1]: Stopped ifup for vethNJ6IOJ.
Apr 25 14:53:07 nas libvirtd[1496]: Failed to open file '/sys/class/net/vethPVTJAQ/operstate': No such file or directory
Apr 25 14:53:07 nas libvirtd[1496]: unable to read: /sys/class/net/vethPVTJAQ/operstate: No such file or directory
Apr 25 14:53:07 nas systemd[1]: Started ifup for vethPVTJAQ.
Apr 25 14:53:07 nas systemd[1]: Starting ifup for vethPVTJAQ...
Apr 25 14:53:07 nas systemd[1]: Stopping ifup for vethPVTJAQ...
Apr 25 14:53:07 nas ifdown[2827]: /sbin/ifdown: interface vethPVTJAQ not configured
Apr 25 14:53:07 nas systemd[1]: Stopped ifup for vethPVTJAQ.

```
[*]Create configuration files specific to a particular LXD container so that I can specify fixed MAC addresses to use?
[*]specify starting a container with a specific configuration file. attempting 'lxc start --config=/path/to/config name" yielded a stupid warning about missing config.yml not being a directory. What is config.yml? I cannot find anything on a search about lxd and yml.
[/LIST]

LXD documentation needs some serious updating. Otherwise it's just a DOA toy to launch a trivial example with and then quickly be apt-get removed because you can't figure out to adjust it to your specific needs.

---

### Post by capscrew on 2015-04-25
> **jeffw2 said:**
> So far, not real impressed with LXD. It's documentation is non-existent and for a small home installation with a couple of virtual machines it seems to provide no additional features than LXC while increasing complexity and confusion.

LXD just manages LXC containers.  It's also pretty new.  Start with reading what the developer, Stephane Graber,  [has to say]("https://www.stgraber.org/2015/04/21/lxd-getting-started/") about the progress.  The entire project is new.  I believe it is only 6 months old.  LXC containers have been around for some time. 
> 

How do I:
[LIST=1]
[*]Modify the configuration of LXD to bridge containers' eth0 connection with my host's br0 interface? I changed /etc/default/lxc-net to USE_LXC_BRIDGE='false' but I get a lot of

```
Apr 25 14:53:07 nas systemd-udevd[2783]: Could not generate persistent MAC address for vethNJ6IOJ: No such file or directory
Apr 25 14:53:07 nas systemd-udevd[2785]: Could not generate persistent MAC address for vethPVTJAQ: No such file or directory
Apr 25 14:53:07 nas libvirtd[1496]: Failed to open file '/sys/class/net/vethNJ6IOJ/operstate': No such file or directory
Apr 25 14:53:07 nas libvirtd[1496]: unable to read: /sys/class/net/vethNJ6IOJ/operstate: No such file or directory
Apr 25 14:53:07 nas systemd[1]: Started ifup for vethNJ6IOJ.
Apr 25 14:53:07 nas systemd[1]: Starting ifup for vethNJ6IOJ...
Apr 25 14:53:07 nas systemd[1]: Stopping ifup for vethNJ6IOJ...
Apr 25 14:53:07 nas ifdown[2818]: /sbin/ifdown: interface vethNJ6IOJ not configured
Apr 25 14:53:07 nas systemd[1]: Stopped ifup for vethNJ6IOJ.
Apr 25 14:53:07 nas libvirtd[1496]: Failed to open file '/sys/class/net/vethPVTJAQ/operstate': No such file or directory
Apr 25 14:53:07 nas libvirtd[1496]: unable to read: /sys/class/net/vethPVTJAQ/operstate: No such file or directory
Apr 25 14:53:07 nas systemd[1]: Started ifup for vethPVTJAQ.
Apr 25 14:53:07 nas systemd[1]: Starting ifup for vethPVTJAQ...
Apr 25 14:53:07 nas systemd[1]: Stopping ifup for vethPVTJAQ...
Apr 25 14:53:07 nas ifdown[2827]: /sbin/ifdown: interface vethPVTJAQ not configured
Apr 25 14:53:07 nas systemd[1]: Stopped ifup for vethPVTJAQ.

```
[*]Create configuration files specific to a particular LXD container so that I can specify fixed MAC addresses to use?
[*]specify starting a container with a specific configuration file. attempting 'lxc start --config=/path/to/config name" yielded a stupid warning about missing config.yml not being a directory. What is config.yml? I cannot find anything on a search about lxd and yml.
[/LIST]

LXD documentation needs some serious updating. Otherwise it's just a DOA toy to launch a trivial example with and then quickly be apt-get removed because you can't figure out to adjust it to your specific needs.

Set the config file correctly.  The veth connector is not finding the other end.

Read the basic LXC configuration documentation.  It's all spelled out there.  Google is your best bet other than Stephane's excellent [LXC how to series]("https://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/"). 

I believe your custom file should be referenced like this ```
lxc start -f /etc/lxc/<some-lxc.conf 
```...rather than your --config=//path/to/config name.  See the man page for lxc-start.

I'm waiting for LXD to become more mature, maybe you should too.

---

### Post by Frogs Hair on 2015-04-25
*Moved to **Visualization ***

---

### Post by minhtran-01 on 2015-06-14
I had probably equal if not more levels of frustration dealing with LXD and the containers created using LXC client vs containers created using lxc-start.  And scouring google posts did not help, as the majority of tutorials deal with using containers via lxc- commands and not this new LXC client.  Introduction to LXD states that this technology isn't a rewrite of LXC, but builds on top of existing LXC technology.  No mention that the containers created via LXC client vs lxc-start are not interchangeable.  One doesn't know about the other.  The LXC client doesn't even appear to create a configuration file for the container when it is first created, unlike containers created using lxc-create.  So everything you find about LXC container configurations being stored at /var/lib/lxc/container/container.conf file doesn't apply.

> **capscrew said:**
> 

I believe your custom file should be referenced like this ```
lxc start -f /etc/lxc/<some-lxc.conf 
```...rather than your --config=//path/to/config name.  See the man page for lxc-start.


if you did have a configuration file to use with the new LXC client the --config option is the correct option to use. Not lxc start -f.  You are incorrectly confusing options based on lxc-start command vs lxc client command.

And I tried using the --config option but got same problem as jeffw2 w/ useless config.yaml errors.


However, I did figure out how to reconfigure the container I created using LXC by running the following command:

```

lxc config set first raw.lxc 'lxc.network.link = br0'

```

Where br0 is a virtual bridge I created so that my containers could obtain DHCP from my real network LAN.

Now I want to figure out how to change global configuration so I don't have to do this on every container I create for my home use.  But again, where can this information be found?  It doesn't exist in the man pages for LXD/LXC.  How does canonical expect users to use this technology without putting out better documentation?

---

### Post by rsommer on 2015-09-04
Add a new profile using:
```
lxc profile create bridged
```

Add your device definition:
```
lxc profile device add bridged eth0 nic nictype=bridged parent=br0
```

Create your new containers using this profile:
```
lxc launch ubuntu/vivid test --profile=bridged
```

If you would like ALL containers to be on the main bridge, just change the default profile.

Hope that helps!

---

