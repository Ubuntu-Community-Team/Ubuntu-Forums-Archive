---
title: "Tool to maintain init scripts?"
date: 2008-09-11
forum: Server Platforms
---

### Post by Xemanth on 2008-09-11
I've handling problem with init scripts. Is there any advanced graphical (ncurses) tool which would handle all init scripts (dynamically notice new scripts installed by hmm-m like vmware server). It would be much more convenient to disable unneeded service scirpts with tool than manually breaking them.

Features which I would like to have:
- Move scripts from level to other...
- Activate / Disable boot time scripts...
- Start &/ Stop scripts in real time...

I use Ubuntu Intrepid x86 Server version.

---

### Post by cdenley on 2008-09-11
You might want to check out sysvconfig and sysv-rc-conf. I usually just use the "update-rc.d" command.

---

### Post by Xemanth on 2008-10-29
> **cdenley said:**
> You might want to check out sysvconfig and sysv-rc-conf. I usually just use the "update-rc.d" command.

Ah that update-rc.d does the job nicely.

---

