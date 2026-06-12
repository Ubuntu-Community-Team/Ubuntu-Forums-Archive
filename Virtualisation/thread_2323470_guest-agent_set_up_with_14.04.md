---
title: "guest-agent set up with 14.04"
date: 2016-05-05
forum: Virtualisation
---

### Post by Swiftjay on 2016-05-05
I have alot of 14.04 host servers still and I'm trying to configure qemu-guest-agent to work on them I add the channel into the xml file and starting the vm I get this error:

Error starting domain: internal error: process exited while connecting to monitor: qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/testbed.org.qemu.guest_agent.0,server,nowait: Failed to bind socket: Permission denied
qemu-system-x86_64: -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/testbed.org.qemu.guest_agent.0,server,nowait: chardev: opening backend "socket" failed



I've checked /var/lib/libvirt/qemu/channel/target the channel and target folder didn't exist before so I created them, I then chowned them to libvirt-qemu:kvm as that seems to be the group that runs virt sessions but I'm still not getting the guest agent installed.

Is there any particular packages I need to install on the host OS to get this working?

---

### Post by KillerKelvUK on 2016-05-05
Hi, just done this with a pty device and it worked.  Host is 16.04, guest is a 14.04...installed the qemu-guest-agent package and this worked out of the box.  Did this using windows also a while back, see here [http://ubuntuforums.org/showthread.php?t=2289210&p=13338769#post13338769](http://ubuntuforums.org/showthread.php?t=2289210&p=13338769#post13338769).

---

### Post by Swiftjay on 2016-05-05
@killerkelv Thanks for the tip I'll give it a try and see if the pty works instead of unix.

---

### Post by Swiftjay on 2016-05-06
@killerkelv that seems to work great however I'm not realising that domfsfreeze isn't installed by default on virsh? When I run the command virsh domfsfreeze DOMAIN I'm getting an error: 
error: unknown command: 'domfsfreeze'

I would've thought this would exist in 14.04 but maybe I'm wrong?

---

### Post by KillerKelvUK on 2016-05-06
Hey switftjay, stretching my capabilities here as I've never had a practice use case so only got this up and running, never used it in anger.  Checking however you are structuring your commands with the necessary *fluff* the protocol requires?  Also I believe issuing a [COLOR=#000000][FONT=Ubuntu Mono]{"execute": "guest-info"}[/FONT][/COLOR]  should show all the capabilities the guest agent has on the guest aka if 'domfsfreeze' isn't listed then its not supported.

---

