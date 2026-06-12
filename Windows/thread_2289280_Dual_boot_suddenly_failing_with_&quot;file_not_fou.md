---
title: "Dual boot suddenly failing with &quot;file not found&quot; and &quot;unaligned pointer&quot;"
date: 2015-08-02
forum: Windows
---

### Post by Bob_Reinke on 2015-08-02
I have a Dell XPS 8700 which I have been successfully running dual-boot with Ubuntu and Windows 8.1 for months.  Last week, I left the machine asleep on the Windows side for a few days, and when I went to reboot into Ubuntu I got the following on selecting Ubuntu from the grub menu:
error: file '/vmlinuz-3.13.05.57-generic.efi.signed' not found
unaligned pointer 0xc9bb7bd8
Aborted. Press any key to continue.

When I press a key it boots into some Windows start-up mode I haven't seen before (asking me to select a keyboard, then booting into Windows).

This happens no matter which of the 4 ubuntu versions on my disk I select.

I have tried boot-repair and it hangs (unending progress bar at the "copying kernel" stage).  I had boot-repair copy data to here: [http://past](http://past)e.ubuntu.com/11977280.

I'm guessing that some Windows update has scrogged my system.  Help on how to get out of this appreciated. 

Regards,

Bob Reinke

---

