---
title: "vi display screwy when running in resized gnome-terminal in Ubuntu 14.04.1 as guest"
date: 2015-02-02
forum: Virtualisation
---

### Post by ScottSanbar on 2015-02-02
I am running Ubuntu desktop 14.04.1 as a guest OS on a Windows 8.1 PC.  Using either Hyper-V or VMWare, if I use the following command to start a vi session:

```
gnome-terminal --geometry 156x48+80+50 -e "/usr/bin/vi .bashrc"
```

the text inside the vi window starts at the line below where the text would stop if the file were opened without resizing bash and after the number of lines of text (offset from the top of the file as just indicated) are displayed in vi, the rest of the lines in vi are blank until the bottom of the window.

To fix the problem, I have to scroll down until the text is fully displayed, then I can scroll around and vi works fine.

If I do the exact same thing on my native Ubuntu Desktop 14.0 machine, it works fine.

I would like to file a bug report, but I am not sure which process to file on - bash or vi, or something else that is involved in this, like the virtualized display driver or whatever.

I would like to work on this problem myself as I am a developer who wishes to get into Ubuntu community development, but need a little direction.

Thanks!

---

