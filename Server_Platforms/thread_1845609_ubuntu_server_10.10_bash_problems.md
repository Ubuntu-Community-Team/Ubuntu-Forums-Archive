---
title: "ubuntu server 10.10 bash problems"
date: 2011-09-17
forum: Server Platforms
---

### Post by Zacariaz on 2011-09-17
Hello all

Small problem here that I'm apparently unable to solve on my own.

I've gotten my own server to play around with, and it's all fine and dandy, except for a minor problem.

I'm logging in via ssh, and when doing so using the root account, then everything look as it should. then I make an account for my self, with home folder, add it to sudoers file and all that, but commandline is just a "$" which isn't of much help and autocomplete doesn't work either.

Please do let me know if you know how to solve this small problem.


Best regards

---

### Post by dave01945 on 2011-09-17
you need to look at the **.bashrc** file in the home folder root uses the system wide file in **/etc/bash.bashrc** but your user should be using their own **.bashrc** in the home folder look through it and in there somewhere are the options for bash completion and the prompt

---

### Post by Zacariaz on 2011-09-17
thanks I'll try that. Did try to copy the bashrc from root, but that didn't make any difference.

By the way, the users I've added have no bashrc in their folder as standard, only the ones I've copied from root.

---

### Post by dave01945 on 2011-09-18
not sure why they wasn't created by default but if it is any use the default file should be in **/etc/skel/** directory

---

