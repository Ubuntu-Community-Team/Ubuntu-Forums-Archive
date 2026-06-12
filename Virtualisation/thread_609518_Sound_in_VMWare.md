---
title: "Sound in VMWare"
date: 2007-11-11
forum: Virtualisation
---

### Post by Excalibre on 2007-11-11
VMWare doesn't play nice in regard to sound. When I run a VM, I have to have no other sounds playing in order for a guest OS to make noise - it seems to want exclusive control over the sound system.

Anyone else experienced this? It's not a huge deal but it would be nice if it worked.

---

### Post by hungle0 on 2007-11-11
Are you using VMware player or server? After a bit of search through posts, there is a sound workaround for the server and workstation edition. For some reason, it doesn't work with the standalone player version.

Here is a copy and paste of what others have written. (search the forums if you want more details).

For vmware server or workstation only!

   1. Install a package called "alsa-oss" either by using Synaptic or maybe "sudo aptitude install alsa-oss"
   2. sudo chmod +s /usr/lib/libaoss.so.*
   3. cd /usr/lib/vmware/bin
   4. sudo mv vmware-vmx vmware-vmx.real
   5. sudo vim vware-vmx
(then copy and paste the following into the file)

	#!/bin/bash
	LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"


(save the file and exit vim)

   6. sudo chmod +x vmware-vmx

I think that's it.

---

### Post by Excalibre on 2007-11-11
So I tried this, but no dice. When I tried running vmware-vmx from the console, it said this:
```
ERROR: ld.so: object 'libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
```
So I'm not sure what that's about.

---

### Post by hungle0 on 2007-11-11
Hmm... my knowledge with linux is nothing to boast about, but I will take a stab at it ...

Please check to make sure that you did install "**alsa-oss**" correctly. This is another version of alsa, it is different from the one that came with Ubuntu.

Therefore, either the script (vmware-vmx) is not finding the file or the **permissions** of the files are incorrect.

Please double check that you have **chmod** all the necessary parts correctly. Steps #2 and #6.

---

