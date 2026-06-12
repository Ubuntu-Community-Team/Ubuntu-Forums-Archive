---
title: "No audio VMware server"
date: 2007-12-27
forum: Virtualisation
---

### Post by tajreed on 2007-12-27
Using VMware server and Gutsy. And XP as a guest. Under settings, I am unable to add the sound function, both the add and remove functions are grayed out. Any ideas?

---

### Post by obrient on 2007-12-27
I had the same problem when I was first using VMWare. Since the sound card I believe is owned by the root user you need to run VMWare as root once to fix this. I found the [fix]("http://mazimi.wordpress.com/2007/06/26/enabling-audio-in-vmware-server/") here. This was easy to do with the directions.

---

### Post by tajreed on 2007-12-28
Tried that fix, but no luck.

---

### Post by tajreed on 2007-12-28
Virtual Machine must be off before enabling audio

---

### Post by purefan on 2008-09-29
had my machine shut down but still got this message:
> 
Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected.


Even though no sound was audible from my host OS, any clue?

---

