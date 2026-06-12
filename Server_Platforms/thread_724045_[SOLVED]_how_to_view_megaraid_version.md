---
title: "[SOLVED] how to view megaraid version?"
date: 2008-03-14
forum: Server Platforms
---

### Post by gtdaqua on 2008-03-14
quick one: 

i have a 64bit gutsy server running on dell pe 1950.

how to view the megaraid_sas version by command line?

typing "lsmod | grep megaraid_sas" give this:

```

$ lsmod | grep megaraid_sas
megaraid_sas           46012  5
scsi_mod              179896  6 usb_storage,sr_mod,sd_mod,sg,libata,megaraid_sas

```

---

### Post by gtdaqua on 2008-03-15
no answer???

---

### Post by gtdaqua on 2008-03-17
and the answer is:

```

dmesg | grep megasas

```

Thank you, Petersonz!

---

### Post by diegoramos on 2008-05-12
modinfo megaraid_sas

---

### Post by gtdaqua on 2008-05-13
> **diegoramos said:**
> modinfo megaraid_sas

This is really better than the dmesg command.

Thank you.

---

