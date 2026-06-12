---
title: "md raid reconstruction fails at boot"
date: 2005-08-19
forum: Server Platforms
---

### Post by ceswiedler on 2005-08-19
I have a Hoary server with md software raid configured. It's been working great since April. Recently I've had a problem with what appears to be a kernel panic. I'm still trying to track that down, but as a result, when I reboot, the md array is out-of-sync. When the arrays are created (by the initrd) it correctly starts to reconstruct the degraded array. 

The problem appears to be that one of the startup scripts tries to kill all processes, and refuses to continue if there are any processes left. The output is something like this:

mdadm starting drive reconstruction...
Stopping all tasks ===
== stopping all tasks failed, 1 task remaining

(I haven't written down the messages word for word, I can reproduce it and post if it will help).

From there it refuses to boot. The reconstruction doesn't appear to be continuing but I'm not 100% sure. Possibly two hours later when the reconstruction finishes it will boot, but I've never waited that long.

Why does ubuntu try to stop all tasks at this point (before init has even started AFAICT)? Is this a known issue?

---

### Post by lee_connell on 2005-08-19
theirs been an issue for me for a while now with kernel panics and software raids, seems like it doesn't configure the new kernel (when i upgrade kernels) properly and possibly doesn't add the right drivers with initrd.

I'm really not sure but hopefully someone else can come up with a better solution for you.

---

### Post by nathan43081 on 2005-08-25
I found a fix earlier on this forum for the same problem you are having. I don't remember the original poster to give them credit.

The fix is to add acpi=off to the end of the boot string. I am not sure all of what this is doing, but it allowes the reconstruction of the array's to continue in the background after the computer finishes booting.

---

