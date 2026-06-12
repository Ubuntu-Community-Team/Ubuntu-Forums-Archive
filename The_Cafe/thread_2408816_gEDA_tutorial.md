---
title: "gEDA tutorial"
date: 2018-12-23
forum: The Cafe
---

### Post by torbentf on 2018-12-23
Hi,
I am running the Bill Wilson gEDA tutorial and I have got to the point where I have entered "pcbboard pcbpcb" and have got the screen "Unnamed (board.pcb) - PCB": I have entered "File - Import schematics" and I have imported one.sch and two.sch.
The problem is, that in both cases I get only part of the items on screen - some are missing.  
I can't figure out what I am missing/doing wrong.
Can anyone help?
best regards
torben

---

### Post by torbentf on 2018-12-24
Hi,
The tutorial suggested that I gave the two OPAMPS in one.sch the same number U101, therefore they turned up as one. If I give them the numbers U101 and U102, they turn up as two - OK, but it does not tally with the instructions

The transistor does not turn up in two.sch and the log gives:

File 'board.pcb' has no font information, using default font
Can't change working directory to
   '/usr/local/pcb-elements'
chdir() returned: 'No such file or directory'
Can't change working directory to
   'packages'
chdir() returned: 'No such file or directory'
Note:  home directory is "/home/torben"
Loading menus from /usr/share/pcb/gpcb-menu.res
Unable to load footprint CONNECTOR 2 1
Cannot change attribute of CONN201 - element not found
Cannot change attribute of CONN201 - element not found
Cannot change attribute of CONN201 - element not found
Cannot change attribute of CONN201 - element not found
Cannot change attribute of CONN201 - element not found
Can't find CONN201 pin 2 called for in netlist.
Can't find CONN201 pin 1 called for in netlist.
Warning! Net "unnamed_net1" is shorted to net "vmixer"
Warning! Net "vmixer" is shorted to net "unnamed_net1"

I think that I have loaded footprint CONNECTOR 2 1 as instructed in the tutorial correctly, so what is wrong?
torben

---

### Post by torbentf on 2018-12-26
Hi,
Solved.
best regards.
torben

---

