---
title: "AIDE syntax error"
date: 2007-11-20
forum: Server Platforms
---

### Post by GabFromDenver on 2007-11-20
Hi all, 

I recently installed AIDE on Gutsy, using synaptic, and found out that I couldn't create the initial database, because it would fail with a syntax error. It took me a little man-reading to figure out the issue. The problem is that there are 2 kind of files in the aide.conf.d folder: "aide rule files" and shell scripts. The shell scripts needs to be executable, so that AIDE knows it's a script. 

So to fix this, you can either look into each file of the folder and determine whether this is a script or not. Or you could run in the /etc/aide/aide.conf.d folder the following command (as root): 
```

for i in `grep '/bin/' * | awk '{split($1, tokens, ":"); print tokens[1]}'`; do chmod +x $i; done
```

It's pretty straight forward: the "grep...|awk ..." generates the list of the files that need to be exectuable. The rest of the command loops through this list and adds the execution right.

Hope this helps.

Gabriel

---

### Post by beazer on 2007-12-05
Thanks Gabriel

That was a good help :-)

---

### Post by cbobb@alinean.com on 2008-04-24
Thanks that script helped, all is good now!

---

