---
title: "Headless VirtualBox-VM - start via Putty"
date: 2011-11-05
forum: Server Platforms
---

### Post by anXieTyPB on 2011-11-05
Hi!

I'm having some problems starting a Virtual Machine via

```
VBoxHeadless --startvm "VMName"
```

Starting the machine isnt a problem.

But when i press CTRL+C in Putty, the Machine shuts down immediately. I want to keep the machine running even though the terminal i started it with isnt "connected" anymore.


Any suggestions?

Regards!

---

### Post by CharlesA on 2011-11-05
Easy:

Add a "&" at the end to start it in the background.

```
VBoxHeadless --startvm "VMName" &
```

---

### Post by anXieTyPB on 2011-11-05
Thank you very much!

---

### Post by CharlesA on 2011-11-05
No problem. Don't forgot to mark the thread as solved from thread tools. :)

---

### Post by anXieTyPB on 2011-11-07
Okay, i just realized that the VM does not keep running when i exit the putty session I started it with even though i used the & operator.

When starting it via 

```
VBoxHeadless --startvm "VMName" &
```, the machine can be pinged until I close my session. The VM seems to shut down immediately then and therefore cannot be ping-accessed anymore.


Any solutions to that?

---

### Post by Zeosa on 2011-11-07
Try using 
```

VBoxManage startvm vmname --type vrdp

```

Works for me

---

### Post by CharlesA on 2011-11-07
> **Zeosa said:**
> Try using 
```

VBoxManage startvm vmname --type vrdp

```

Works for me

I use this as well, but the earlier command worked for be prior to switching due to running into a issue with a script I use.

---

### Post by anXieTyPB on 2011-11-07
> **Zeosa said:**
> Try using 
```

VBoxManage startvm vmname --type vrdp

```

Works for me

For me too, ty!

---

