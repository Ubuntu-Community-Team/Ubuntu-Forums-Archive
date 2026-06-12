---
title: "Command Line switch don't want for program to exit"
date: 2007-07-20
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-20
Hi all,

I know this is really simple but for the life of me I cant remember it or find it online.

I want to be able to start a program on the command line and not have to wait for it to exit.

i.e.. I have to start vmware-server in sudo mode (icon on applications doesnt work) so doing this by the command line means I have to have that command window open all the time vm server is on.

thanks for the help

---

### Post by EndPerform on 2007-07-20
Like so:

```
sudo vmware-server &
```

The & sign tells Ubuntu to run the process in the background.

---

### Post by twistedtwig on 2007-07-20
Of course... I remember that now... thank you :)

---

