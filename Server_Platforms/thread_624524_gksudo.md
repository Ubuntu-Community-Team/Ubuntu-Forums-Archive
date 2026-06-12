---
title: "gksudo"
date: 2007-11-27
forum: Server Platforms
---

### Post by toupeiro on 2007-11-27
is there a mechanism in gksudo like sudo -e <filename>?

---

### Post by rsambuca on 2007-11-27
gksu doesn't really work the same way.  It is giving root permissions to a executable frontend program that runs within the X-Server.

---

### Post by toupeiro on 2007-11-27
So then, it is suceptable to the same vulnerabilities as say: running vi or vim with sudo, and dropping to a root shell, if the gui frontend supported such a function?

:edit: verified, at least with gvim, that this is the case

```
 gksu gvim 
```

based on what I have done, gksu has to be doing a little more than merely elevating a frontend.  the full vi environment is roots environment, as I was able to shell out as root within the GUI application.

which leads me into my next question.  is there anything like gksu that can envoke a hardened graphical editor such as sudo -e does for the CLI?  There are a lot of things graphical that wrap around vi.  sudo -e on most linux and UNIX systems basically envokes vi, but hardened.  If I shell out using sudo -e with vi envoked, I get my shell, not a root shell. in Ubuntu, sudo -e appears to be configured to use nano, which I can verify that as of sudo-1.6.9p2  is not a default behavior for sudo source. So, this is unique to ubuntu's compilation of sudo. I'm just curious if there is any graphical solution for this kind of need?  If I am to explicitly give users access to run certain commands elevated, and if some of those have graphical capabilities, based on what I have seen, gksu is not as sound of a solution as plain sudo in a CLI environment. Unless there are additional elements I can specify in a sudoers file, or something like it, that apply only to gksu?

---

