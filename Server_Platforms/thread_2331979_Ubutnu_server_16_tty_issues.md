---
title: "Ubutnu server 16 tty issues"
date: 2016-07-27
forum: Server Platforms
---

### Post by steviesomm on 2016-07-27
Hi
I have ubuntu server 16 with xorg installed - how can I completely disable all text output when server is booting?
I need tty to be black screen totally because after completing boot it starts the x server auto'

---

### Post by MAFoElffen on 2016-07-27
Not really an "issue" (problem) with the operation of the server console, but rather a user mod... Because normal *is* for Server Edition is for the boot messages and to boot to console to be present. There are reasons to see those (as a server admin) and security in ... not having a GUI. But no matter.
----------------------------------------------------------

Install and add a Plymouth theme...

After that, edit /etc/default/grub with elevated permissions
```

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
After a write, quit, then 
```

sudo update-grub

```
Then your Server Edition will will be closer to looking like a Desktop Edition. (???) That is wanted you want right?

---

