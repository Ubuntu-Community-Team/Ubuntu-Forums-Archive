---
title: "avgscan nautilus script"
date: 2009-07-09
forum: Security
---

### Post by SteveG on 2009-07-09
I put together this nautilus script to scan files with avg linux.
Download the avg deb linux from here: [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)
Install it.

I use the following script and place it in ./gnome2/nautilus-scripts.
Make it executable.

-----------------------------
#!/bin/bash
#avgscan.sh
# scans selected files or directory for viruses
xterm -T "AVG Virus Scanning $*" -e "pv -ptre "$*" | avgscan --heur --arc --report ./avgscanlog-"$*" $*" &
-----------------------------------------

I would like to have the xterm not auto close after the scan completes, but at least you can see the scan results in the current folder.
You then select your file & right click to access nautilus script and execute it.
This is a work in progress, so anyone please help to improve.

cheers
SteveG

---

### Post by jpeddicord on 2009-07-11
Moved to Security Discussions; to fit in the Tutorials & Tips criteria this must consist of more than a script. :)

Jacob

---

### Post by juancarlospaco on 2009-07-12
**+hold**
parameter for xterm.

---

