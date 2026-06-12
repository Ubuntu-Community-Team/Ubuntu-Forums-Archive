---
title: "Before I dive into virtualization, a few questions."
date: 2009-10-12
forum: Virtualisation
---

### Post by lavadisco on 2009-10-12
- Can a guest OS access my USB ports and CDROM drive? From what I have read here, USB looks to be possible although I've seen nothing about CDROM drive support.

- Can I access the internet via the guest OS? According to one of the Stickies in this forum, wireless networking is not supported in Virtualbox?

- Can the guest OS access files on the host OS? If so, does that mean that a virus that has infected a WinXP guest OS can then damage files on an Ubuntu host?

- Regarding pro audio: How well do pro audio applications run on the guest OS? Can I use my USB audio interface with an ASIO driver like I normally would in Windows? This is probably the most important thing that I will do in my guest OS. That being the case, which virtualization will give me the fastest performance?

---

### Post by tuxxy on 2009-10-12
> **lavadisco said:**
> - Can a guest OS access my USB ports and CDROM drive? From what I have read here, USB looks to be possible although I've seen nothing about CDROM drive support.

- Can I access the internet via the guest OS? According to one of the Stickies in this forum, wireless networking is not supported in Virtualbox?

- Can the guest OS access files on the host OS? If so, does that mean that a virus that has infected a WinXP guest OS can then damage files on an Ubuntu host?

- Regarding pro audio: How well do pro audio applications run on the guest OS? Can I use my USB audio interface with an ASIO driver like I normally would in Windows? This is probably the most important thing that I will do in my guest OS. That being the case, which virtualization will give me the fastest performance?

Yes of course you can mount the CDROM in the VM configs.  Also USB access is possible.

You can access the Internet fine just as normal, and can access files on the host OS by creating a shared folder.

You should be able to run the audio,  aslong as your USB is working should be fine.

---

### Post by lavadisco on 2009-10-12
Thanks!

Is there any VM in particular that might give me the fastest performance, or might be particularly suited for pro audio work (or processor intensive tasks of that type)?

---

### Post by thisllub on 2009-10-13
> **lavadisco said:**
> Thanks!

Is there any VM in particular that might  be particularly suited for pro audio work (or processor intensive tasks of that type)?

No.

For audio you need the whole machine.

---

### Post by lavadisco on 2009-10-13
> **thisllub said:**
> No.

For audio you need the whole machine.

Thanks! Could you perhaps elaborate on your experience running audio in a VM?

---

### Post by Capt. Blackwood on 2009-10-15
It's a bit slower than by doing it via wine. I've tried FL Studio's Latest release and have had lag and buffer issues. That's the only thing I can think of at the moment. Lag and Buffer sizes.

---

