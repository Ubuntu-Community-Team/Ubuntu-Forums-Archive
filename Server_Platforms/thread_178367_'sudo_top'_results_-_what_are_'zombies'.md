---
title: "'sudo top' results - what are 'zombies'"
date: 2006-05-17
forum: Server Platforms
---

### Post by Coal on 2006-05-17
Hi could anybody help me in understanding the results of the 'sudo top' command?
In particular I would like to know what those processes listed as 'zombies' (in the 'tasks' line) are. My pc goes now and then up to 100%CPU usage but the 'system monitor' does not list any processes  responsible for it.

THanks a whole lot in advance.

---

### Post by Jason_25 on 2006-05-17
This doesn't belong in the security issues forum.

---

### Post by Coal on 2006-05-17
sorry....I don't know exactly where it belongs, though.

---

### Post by meng on 2006-05-17
Google: [http://www.linuxsa.org.au/tips/zombies.html](http://www.linuxsa.org.au/tips/zombies.html)

---

### Post by stanz on 2006-05-17
Geez...thats a helpful response to a new user... Bad Day?
Even If Thats true Coal... hang tuff... someone will respond- usually  in a most helpful & friendly manner...
Have ya searched wiki ?
even maybe a google... they often are a help...
post your results!! it may help another ! ;)

---

### Post by dumbsnake on 2006-06-03
zombies are threads that have terminated, but their parent thread hasn't yet read their return value.  They have to remain in memory until the parent reads the return value incase that number is relavent to the parent thread for some reason.  If for example you were downloading something in firefox, it might spawn a new thread to perform the download.  When that thread finishes downloading, it probably returns a value telling firfox if there was an error.  If there was, firefox would need to know.  SO when the thread that is downloading a file is done, it stays around as a zombie until firefox reads the value saying that everything went ok.

---

