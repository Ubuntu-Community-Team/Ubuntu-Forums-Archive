---
title: "After a power outage, server gets hung in GRUB"
date: 2010-02-10
forum: Server Platforms
---

### Post by Sporkman on 2010-02-10
When power was restored after an outage, my server (running Ubuntu server 9.10) started back up & got stuck in the GRUB menu ("Version 1.97~beta 4" I think) - it didn't do that countdown & auto-select the top item like I'm used to. Just stayed there, and since the server is headless, I had to dig out my monitor & hook it up to see what was wrong.

Anybody know how that countdown & auto-select can be restored?

---

### Post by tjvries on 2010-03-24
I had the same problem today. 

grub2 in ubuntu 9.10 server is configured by default with GRUB_HIDDEN_TIMEOUT=0. If there is no keyboard attached (as in my headless setup), this causes grub2 to go to menu and stay there. 
Setting it to -1 gives me the desired sequence of menu, timeout and default choice.

I don't know if this is a grub2 bug or not, but if this is intended grub2 behavior, the default config for a server distro such as ubuntu server (which you would expect to function headless out of the box) should be different.

---

