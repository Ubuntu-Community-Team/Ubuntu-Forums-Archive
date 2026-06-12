---
title: "System getting hanged"
date: 2011-05-09
forum: Ubuntu One (CLOSED)
---

### Post by sudhakar_282003 on 2011-05-09
Hi All,

I am a new user for ubuntu, recently i have updated to 11.04 version last week. When i kept my desktop idle for long time, the system goes down and it didn't wake up at all. I didnt change in the setting for screen saver and power management still. It is system default.

I didnt face this problem when i use version 10. Only the new version i am facing this.

Any solution for this?

Thanks

Sudhakar

---

### Post by ivanovnegro on 2011-05-09
Maybe you should change your energy settings, seems something is not compatible with your hardware or the default settings are not good enough in your case.
Maybe try to disable suspend mode from the energy settings or similar things.
Suspend things are always a bit problematic on some machines.

---

### Post by sudhakar_282003 on 2011-05-09
What kind of setting change i need to do?

---

### Post by madjr on 2011-05-09
> **sudhakar_282003 said:**
> What kind of setting change i need to do?

maybe disable suspend for now

---

### Post by ivanovnegro on 2011-05-09
I meant the power management settings.
Go to System Settings-> Power Management and disable e.g. suspend after x minutes/hours, I think the suspend mode is the problem. When you disable it your computer will run without to go into suspend mode and this way it wont hang if this happens. Its just a workaround.
Maybe you have to find later why in your case its not working.

A question now, have you made a Swap partition, that is needed normally for suspend mode, but like I said, even if you did it what I think because this happens with the default installation method, it could just not work in your case or you made the Swap space too small?

---

### Post by sudhakar_282003 on 2011-05-09
Thanks for help , i have made the disable the "Put computer to sleep when it is idle for : " to never now. Let see how it works. 

I didnt do any swap partition. Do you mean i need to re install is again with swap partition ? What is the size which i need to give?

My system specification is :
2G Ram, 500GB HDD,

---

### Post by ivanovnegro on 2011-05-09
> **sudhakar_282003 said:**
> Thanks for help , i have made the disable the "Put computer to sleep when it is idle for : " to never now. Let see how it works. 

I didnt do any swap partition. Do you mean i need to re install is again with swap partition ? What is the size which i need to give?

My system specification is :
2G Ram, 500GB HDD,

Are you sure? Normally the Swap is the same as your RAM.
You could look in the system monitor if you have any Swap space in use.

---

### Post by sudhakar_282003 on 2011-05-09
My system swap space is 5.9GB

---

### Post by ivanovnegro on 2011-05-09
> **sudhakar_282003 said:**
> My system swap space is 5.9GB

Ok, then everything is in order, seems to be a hardware issue. I think with the disabled suspend mode you wont have again freezes.

---

### Post by sudhakar_282003 on 2011-05-09
Let me monitor this for some days and i will let you know

---

