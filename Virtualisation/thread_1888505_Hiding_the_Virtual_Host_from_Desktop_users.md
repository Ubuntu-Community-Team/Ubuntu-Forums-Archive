---
title: "Hiding the Virtual Host from Desktop users"
date: 2011-11-29
forum: Virtualisation
---

### Post by Iosonos on 2011-11-29
Hey,
 
I have a question about the possibility of setting up a system to automatically boot into a VM without exposing the Linux desktop to a user. I'm considering setting up a VM system for my parents to help me with remote troubleshooting, current plan is to run a Linux host which can take care of making VHD backups as well as giving me a place to remote into under any circumstance other than hardware failure.
 
I'd like to set it up so I can still run a GUI desktop for myself to log into remotely while automatically starting up the Windows VM without my parents really knowing about it. Essentially they're against change, and I'd like to be able to explain that the "penguin in the top corner is just what Windows 7 does now" while it boots. Bash/CLI is fine during startup, but I want to keep from exposing them to the Linux desktop. I'd also like command keys such as ctrl+alt+del to work under the Windows guest. Mounting the .vhd on the Linux desktop to transfer files is required, as well as the usual USB device and optical drive passthrough. 
 
Hopefully this makes sense for everyone. I'm not new to virtualization, but I am new to Linux virtualization, and somewhat to Linux as a whole. I'm also not looking for specific instructions at the moment (though pointers are appreciated), just a general idea of what software/hypervisor will allow these kind of features. Thanks in advance!

---

### Post by CharlesA on 2011-11-30
I suppose you could have it set to autologon and then run a script that starts the VM in full screen mode.

It won't be seemless but it should get it done.

---

