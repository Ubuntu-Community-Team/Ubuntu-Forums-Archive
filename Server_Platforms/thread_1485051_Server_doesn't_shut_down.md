---
title: "Server doesn't shut down"
date: 2010-05-16
forum: Server Platforms
---

### Post by awacs on 2010-05-16
I inherited a SuperMicro 2-way Xeon beast. It's really fascinating - *six* fans, for instance - but I have a problem - can't reboot the computer.

Init 0 or Init 6, just makes the server run through shutdown stuff, the screen disappears, the server stops responding to pings, and - that's it. The fans keep turning, the power stays on, and I have to push the power button.

Am I missing something on the software side? I installed acpi and turned on and off BIOS power management, didn't help.

Thanks!

---

### Post by Bachstelze on 2010-05-16
Have you tried just [font=monospace]sudo reboot[/font]? You shouldn't normally call init directly.

---

### Post by NullHead on 2010-05-16
That, or "sudo shutdown -r now".

Still, quite odd that it doesn't fully reboot. You might try a [Magic SysRq](http://en.wikipedia.org/wiki/Magic_SysRq_key#Magic_commands) command if you've got a keyboard on the server. 

Note: If you actually call a SysRq force reboot, the filesystems aren't synced. If the system is responsive, you might try SysRq s to try to sync the filesystems first. 

That's all assuming you've got a keyboard handy.

---

### Post by awacs on 2010-05-16
Thanks for the replies. I've narrowed it down to BIND - unable to state my feelings about this program on forum! - not dying gracefully.

Big help for me: editing /etc/default/grub to remove the string "quiet splash", and # update-grub.

---

