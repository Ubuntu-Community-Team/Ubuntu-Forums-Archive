---
title: "Download flash or use synaptic?"
date: 2010-08-14
forum: System76 Support
---

### Post by japhyr on 2010-08-14
Hi everyone,

I just got around to installing 64-bit 10.04 on my panp5 last week.  Can anyone suggest whether I should install the plugin for flash through synaptic, or download it from adobe's site?

---

### Post by howefield on 2010-08-14
Either way, you'll want 32 bit flash, as 64 bit is temporarily unavailable (following a critical vulnerability in it).

Easier to get it from Synaptic.

---

### Post by japhyr on 2010-08-14
Thanks, I used flashplugin-installer, restarted, and it works.

---

### Post by howefield on 2010-08-14
Thanks for the update, some people have had problems with the buttons when using 32 bit flash in a 64 bit system, if this is the case for you, perhaps the following fix might help.

Open a terminal and type

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

press enter, and place the following on a new line before the last line.

```
export GDK_NATIVE_WINDOWS=1
```

---

