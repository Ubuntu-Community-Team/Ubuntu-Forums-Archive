---
title: "RKhunter report - hidden directories"
date: 2008-10-04
forum: Server Platforms
---

### Post by wattaman on 2008-10-04
Hi!
I've just installed rkhunter to help me administer my server (since I'm kind of noob) and the first log file have this warning:
> 
Warning: Hidden directory found: /dev/evms/.nodes
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs

... and, of course, many other warning that I'm aware of.
What I don't know and hope someone more experienced will advice is: are those directories supposed to be hidden in Ubuntu 8.04? They came with the linux distro?

Thank you!

---

### Post by windependence on 2008-10-04
Yes, they are and there are many many more. Hidden directories start with a dot.

Just my opinion, but sometimes n00bs spend more time trying to learn a tool to admin their box than they do admining their box. The best way to do this is with a simple ssh session. There is tons of info out there about how to do this and we can help you here on the forums. 

The other problem with that is what if the tool crashes? Then what are you gonna do? What if you go on another box that doesn't have it loaded? See my point? the very best thing you can do for yourself is to just buckle down and learn the CLI. It's not that hard.....really! There are also command line tools out there like Midnight Commander (file manager) nano (text editor) that run an ncurses GUI, it's like the old DOS GUI, but they can still be run from the CLI. Relying on another application to admin your box is just a crutch and you'll be mad at yourself later on for doing it.

-Tim

---

### Post by ProgramErgoSum on 2008-10-04
I am a *Linux* n00b. What I don't get is, why should files be hidden at all ? Hidden from whom/what ?

---

### Post by wattaman on 2008-10-04
Thanks, windependence.
You're right about what you wrote, however not anyone who uses Ubuntu (or other linux) has the time to learn it. For me, at least, playing the admin is more like a hobby, I barely make enough money to pay the servers rent... is not a business.
So, when I'll quit my job I'll dedicate my time learning the linux and possible growing an internet business. Untill then I'll just depend on this tools and the help of others.
ProgramErgoSum: probably because they're hidden from noobs like us, so we won't delete them or something :D

---

