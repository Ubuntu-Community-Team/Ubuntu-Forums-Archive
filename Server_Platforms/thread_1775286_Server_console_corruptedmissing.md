---
title: "Server console corrupted/missing"
date: 2011-06-04
forum: Server Platforms
---

### Post by isecore on 2011-06-04
So the other day I upgraded my server from Maverick to Natty. All went fine with no errors reported. It's originally a Karmic that got upgraded to Lucid and then to Maverick, if that's any clue. It's the 32-bit installation since the CPU in the machine doesn't have the 64-bit extensions.

This is what the console looks like after upgrade.

During boot:

[IMG]http://www.isecore.net/boot.jpg[/IMG]

After boot is done:

[IMG]http://www.isecore.net/normal.jpg[/IMG]

SSH to the machine works just fine, so I can control it through that - but I would VERY much like to have proper consoles back in case of network problems. Accessing a machine physically is always a good redundancy.

So, does anyone have any idea how to fix this?

---

### Post by Joe of loath on 2011-06-04
I suspect that may be a graphics card issue. Do you have a spare you could try?

---

### Post by ian dobson on 2011-06-04
Hi,

Could well be a graphic card/driver problem. It could well be that the console is trying to use a framebuffer but it's not being setup correctly.

Try deinstalling/blacklisting all the video/framebuffer drivers.

ps. What graphic card is in the box?

Regards
Ian Dobson

---

### Post by isecore on 2011-06-04
I doubt it's related to the card since it worked fine before the upgrade. The card in question is an old PCI-based Mach64 that has worked without problems for years. I will try to find a newer card and see if that makes any difference although I doubt it.

Why are we enabling framebuffers on servers? All I want is a regular old text-console, nothing fancy.

---

### Post by isecore on 2011-06-04
Solved it. The problem apparently lied in the driver/kernel module for the frambuffer it wanted to use, so I figured out which one it was (efifb in my case) and the blacklisted that in /etc/modprobe.d/blacklist-framebuffer.

I also uncommented the GRUB_TERMINAL=console in /etc/default/grub although I'm not sure if it made any difference.

Now I have a nice, pure text-only console running on the server.

---

### Post by ian dobson on 2011-06-05
Hi,

So it was the framebuffer, and disabling is solved the problem.

Maybe mark the tread as solved.

Regards
Ian Dobson

---

