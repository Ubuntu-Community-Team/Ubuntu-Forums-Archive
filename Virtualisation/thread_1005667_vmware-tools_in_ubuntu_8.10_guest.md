---
title: "vmware-tools in ubuntu 8.10 guest"
date: 2008-12-08
forum: Virtualisation
---

### Post by oxsyn on 2008-12-08
I'm running vista x 64 on my desktop.  I've got a ubuntu 8.10 guest.  I installed vmware-tools w/o any errors, but when I resize the vmware window, the ubuntu guest won't dynamically resize it's resolution to fill the window.

Any suggestions?

---

### Post by dcstar on 2008-12-10
> **F4RR4R said:**
> I'm running vista x 64 on my desktop.  I've got a ubuntu 8.10 guest.  I installed vmware-tools w/o any errors, but when I resize the vmware window, the ubuntu guest won't dynamically resize it's resolution to fill the window.

Any suggestions?

Is vmware-tools **running** in the Ubuntu guest?

---

### Post by Dedoimedo on 2008-12-10
Hello,

Start vmware tools by running vmware-toolbox from the command line. If you want it to start in the background, run vmware-toolbox &.

You can also add it to startup sessions, so you have the tools always when you boot into your session.

Dedoimedo

---

### Post by bodhi.zazen on 2008-12-10
I start vmware-tools with nohup so I may close the terminal.

```
nohup vmware-tools &
```

---

