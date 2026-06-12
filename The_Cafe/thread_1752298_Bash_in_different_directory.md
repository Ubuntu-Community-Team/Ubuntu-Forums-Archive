---
title: "Bash in different directory"
date: 2011-05-07
forum: The Cafe
---

### Post by LewisGNoa on 2011-05-07
I would like to install bash in a different directory. I have two questions: how to do this succefully and how to make the shell scripts that look for /bin/sh and /bin/bash in my own directory (like, id dont know, /tools or /sys maybe) without making changes to the script and without posting a symlink to /bin



Seems like cafe is the best way to post this.

---

### Post by red_Marvin on 2011-05-07
If your script asks for #!/bin/bash that is what it is going to get unless you change the source of the script or the currently running shell.

---

