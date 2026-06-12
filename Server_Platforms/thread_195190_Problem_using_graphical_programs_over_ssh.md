---
title: "Problem using graphical programs over ssh"
date: 2006-06-12
forum: Server Platforms
---

### Post by Hanj on 2006-06-12
I do all my maintenance of my server via ssh, but now I ran into a problem where I needed a graphical web browser. So I installed Xorg and Window Maker with apt-get and tried to re-login with "ssh -X myip", but when I try to start something that requires X I get this message: "Error: Can't open display:".
I don't know whether the problem lies in the ssh connection or in the X server. Perhaps someone can help me on where to start looking for the problem?

---

### Post by dochood on 2006-06-22
Try this on your local box:

```
xhost +
```

(or: xhost [ip address of remote machine])

That tells X to allow remote "clients" (terminology is backwards in X... your local machine is the "graphics server" and the remote machine is the "client" that wants to be "served" graphics) to display their apps on your local machine.


dochood

---

### Post by ape on 2006-06-22
Also, after ssh'ing into your machine, echo the $DISPLAY variable and see where it's pointing to.  It should be set to point back to the machine's display you are ssh'ing FROM.

---

