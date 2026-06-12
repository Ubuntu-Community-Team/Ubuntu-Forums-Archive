---
title: "LTSP, Rdesktop and hair pulling."
date: 2011-09-30
forum: Virtualisation
---

### Post by SpruceNZ on 2011-09-30
Hi everyone,

First post to these forums, I'm starting to go mad and have probably broken google by now looking for answers. I'm hoping someone here will be able to help.

The system is as follows, I have Ubuntu with LTSP up and running, everything there is running smooth. I also have KVM configured and have several VM's running all at once. The thin clients boot perfectly into LTSP and I can RDP into the VM's without issue whatsoever. The issue starts when I want to initiate Rdesktop at boot. 

Problem #1 For the LIFE of me, I simply CANNOT get rdesktop to launch with the "ltsp-localapps" command. Firefox launches, exterm launches, but not rdesktop. Launching it normally as per "redesktop -u example -p example etc etc" works perfectly. However I do think that this isn't running locally on the thin clients, defeating the purpose. (Running an image within an image) It becomes laggy. What on earth do I need to do to get this to run with the localapps command?

Problem #2 Having temporarily been resigned to my fate in terms of not being able to use the localapps command, I proceeded to setup a regular startup script using rdesktop. On boot up, this works to a degree. The thin client boots, logs directly into the VM, remains in the VM for about 4 seconds and then GNOME takes back over. However the VM is still running in the background. (Damn you GNOME!) On a different thin client, it logs in and STAYS in the VM, however I can still see the lower and top bars in GNOME, same problem but to a different degree.

My theory on #2 is that it's booting up rdesktop too fast, then gnome loads secondary and takes priority over the VM. Could someone guide me in terms of writing a small script to delay the startup of rdesktop on boot? I'd also like it if the thin client would shut down if the rdesktop session is logged out. I once found a script for this but I have since lost it. I am relatively new to Linux.

Or can I disable gnome altogether and just have rdesktop run?

What to do?! I think you can all see what my desired goal here is, for the end user to not be aware they are actually using a Linux machine, (aside from boot screens of course)

I'm currently using Ubuntu 10.10 (Desktop). I've downgraded from 11.04 due to a few errors with LTSP, in a hope that an older build might be a bit more  stable. So far I've had less errors, but I still keep coming back to one  problem. The above problems existed in 11.04 as well and if I can solve them, I'd happily upgrade again.

Hoping someone out there could help!!! Thanks in advance!!

---

### Post by SpruceNZ on 2011-10-01
Could anyone out there help me?!

---

