---
title: "inkscape"
date: 2009-05-21
forum: Ubuntu Studio
---

### Post by bashphoenux on 2009-05-21
i  always get this window
[ATTACH]114519[/ATTACH] when i try saving any art i do in inkscape in .xcf format 
does anyone wat the problem is ???

---

### Post by lukeiamyourfather on 2009-05-21
Looks like one of the Python scripts in the application is a little out of date. Its a Python warning saying that the module used has been replaced by a newer module. Usually its a suggestion for the author to use a more modern way of performing the same task but the script will still function. If it works as expected then disregard the message, and maybe report it as a bug. If it doesn't work at all and you really need it to, then edit the Python script to use a different module for launching a system command (subprocess.Popen() instead). Cheers!

---

