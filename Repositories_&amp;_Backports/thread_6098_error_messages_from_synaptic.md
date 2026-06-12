---
title: "error messages from synaptic?"
date: 2004-11-24
forum: Repositories &amp; Backports
---

### Post by senectus on 2004-11-24
Is there some easy to read guide for tracking down error messages fron synaptic?

When ever I install stuff I get this:
Preconfiguring packages ...
(Reading database ... 92497 files and directories currently installed.)
Preparing to replace kismet 2004.04.R1-1.1 (using .../kismet_2004.04.R1-1.1_i386.deb) ...
Unpacking replacement kismet ...
Setting up tpb (0.6.2-1) ...
chown: failed to get attributes of `/dev/nvram': No such file or directory
dpkg: error processing tpb (--configure):
 subprocess post-installation script returned error exit status 1
Setting up kismet (2004.04.R1-1.1) ...
Errors were encountered while processing:
 tpb
E: Sub-process /usr/bin/dpkg returned an error code (1)


It looks to me like its bitching about an application I installed a while ago called "tpb"

---

### Post by thepoch on 2004-11-26
I just replied to another thread regarding getting tpb to work. So you are also using a Thinkpad? What model?

Anyway, I assume you installed tpb because you want on-screen display of your button changes (volume change, brightness change, etc.). If so, then I hope this helps.

The reason for the error is that /dev/nvram doesn't exist. It's because, by default, the nvram module isn't loaded.

First thing to do is to edit /etc/modules
Add the line "nvram" to it. This will allow the module to load on startup.

Next is to edit /etc/udev/permissions.d/udev.permissions
Look for two lines that contain the word "nvram". I'm assuming you know how to grep using whatever text editor you prefer. By default the two lines are:

misc/nvram:root:root:660
nvram:root:root:660

Change them to:

misc/nvram:root:root:666
nvram:root:root:666

This will allow everyone to 'use' /dev/nvram now. You can change this to use whatever user or group you prefer. I've personally set it to root:thinkpad, and added my user to the thinkpad group.

Now to test it. Go to a terminal and type "sudo modprobe nvram". Then type "ls -l /dev/nvram". The left most should say "crw-rw-rw-". Now type "tpb -d". Try out if you now have on screen display when changing your volume, etc.

I hope this helps.

---

### Post by monsieurk9 on 2005-02-13
thanks a lot

now my t42 fn keys work

it rocks ! \\:D/

---

