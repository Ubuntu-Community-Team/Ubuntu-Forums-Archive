---
title: "set irq priorities?"
date: 2011-10-14
forum: Ubuntu Studio
---

### Post by drumbug1 on 2011-10-14
According to [https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes:](https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes:)

> 
Currently, Ubuntu Studio is shipping the -generic kernel. Excitingly, this kernel should **allow users to set irq priorities**, which means a real time kernel is no longer required for this task! Firewire users should be excited about this. 


I've been google-ing for this - how exactly do you set your IRQ priorities in Ubuntu 11.10?

---

### Post by sgx on 2011-10-15
[http://manpages.ubuntu.com/manpages/dapper/man8/irqtune.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/irqtune.8.html)

This might help!
Cheers

---

### Post by drumbug1 on 2011-10-15
I saw that, but it appears it's no longer in the repositories. That link you posted is from dapper drake- 5 and a half years old.

---

### Post by dawiba on 2011-10-15
Open Software Centre, search for and install rtirq or...

```
sudo apt-get install rtirq-init
```

Then go to [Ubuntu Firewire]("https://help.ubuntu.com/community/FireWire") and follow the instructions from Step 5 onwards

---

