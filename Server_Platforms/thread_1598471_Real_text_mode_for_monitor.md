---
title: "Real text mode for monitor"
date: 2010-10-16
forum: Server Platforms
---

### Post by narcisgarcia on 2010-10-16
I've installed an Ubuntu GNU/Linux 10.04 Server (Lucid Lynx) in a great computer, but with a small and old CRT monitor, that doesn't support much screen resolutions and frequencies.

How can I do to make the system to use everytime traditional text mode (80x25 characters or compatibles)?

Thanks.

---

### Post by dtfinch on 2010-10-16
I haven't found any explicit working option to turn off graphics mode on Lucid server, like it's almost hardcoded, but you can blacklist the framebuffer driver to make it fail and fall back to using text mode.

Adding "blacklist vga16fb" to "/etc/modprobe.d/blacklist-framebuffer.conf" might do the trick, or at least it does on virtualbox. Maybe blacklist uvesafb as well, though I haven't had to yet. There might be others depending on your video card, but a lot are already blacklisted.

---

### Post by narcisgarcia on 2010-10-17
I'll try the blacklist way, but in an encrypted system the LUKS password is already asked in graphic mode (before mounting /etc)

Any useful kernel parameter?

---

### Post by narcisgarcia on 2010-10-17
I see for Ubuntu 10.04 two things:

- vga=xx parameter doesn't work.
- In some machines (I suppose depending on graphics device, not monitor) boots and stays in simple text mode (80x25), but in some others boots in graphic mode with graphic font.

---

