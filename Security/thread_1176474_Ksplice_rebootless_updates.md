---
title: "Ksplice rebootless updates"
date: 2009-06-02
forum: Security
---

### Post by dhughes on 2009-06-02
Ksplice [http://www.ksplice.com/](http://www.ksplice.com/) is an app that allows "rebootless updates" any updates that required a reboot no longer need a reboot using Ksplice.

 Interesting idea, download it here (no .debs) [http://www.ksplice.com/software](http://www.ksplice.com/software)

 Has anyone tried it yet?

edit: I just installed it but now I need to install something that used to require a reboot.

---

### Post by cariboo on 2009-06-02
THe only update that needs a reboot, is when you update the kernel, all other services can be restarted with out rebooting.

---

### Post by dhughes on 2009-06-04
Doesn't that involve logging out, stopping the GUI, becoming root, going to runlevel 1 and then back to runlevel 2? Or something like that.

 I figured Ksplice was easier with fewer steps.

 I haven't successfully done either.

---

### Post by cariboo on 2009-06-04
I would say most services can be restarted from the commaand line. Just open a terminal and type for example:

```
sudo /etc/init.d/networking restart
```

For most desktop programs, network manager for example, just log out and then back in again. In many cases, if a service needs to restart after installing a package, the install script usually takes care of it.

---

