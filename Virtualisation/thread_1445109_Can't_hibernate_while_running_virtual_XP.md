---
title: "Can't hibernate while running virtual XP"
date: 2010-04-02
forum: Virtualisation
---

### Post by nerdtron on 2010-04-02
I pause the running guest Windows XP and then when I try to hibernate my PC (without closing virtual box), it goes to a black screen, the cursors blinks and then after several seconds, goes back to the log-in screen. But if I close the running virtual machine, I can successfully put the PC to hibernate.

Why can't I put it to hibernate while the virtual machine is running? I hate to start the virtual machine each time I restart the PC. Is there a way to do this? I'm running Ubuntu 9.10 and using Virtualbox 3.1.6 PUEL version.

---

### Post by jfparis on 2010-04-02
Did you try putting the windows XP VM on pause?

You can do that through the "Machine" menu

---

### Post by nerdtron on 2010-04-02
Yes, i pause it first then go to hibernate and it still fails..

---

### Post by JustinR on 2010-04-03
Hi,

You can always do this to replace hibernate:

on VirtualBox go to Machine>Close

And click the checkbox called "Save Machine State".

It basically the same as hibernate but going through VirtualBox instead.

Hope this works for you.

---

### Post by dcstar on 2010-04-04
> **nerdtron said:**
> I pause the running guest Windows XP and then when I try to hibernate my PC (without closing virtual box), it goes to a black screen, the cursors blinks and then after several seconds, goes back to the log-in screen. But if I close the running virtual machine, I can successfully put the PC to hibernate.

Why can't I put it to hibernate while the virtual machine is running? I hate to start the virtual machine each time I restart the PC. Is there a way to do this? I'm running Ubuntu 9.10 and using Virtualbox 3.1.6 PUEL version.

How much RAM and Swap space do you have?

---

### Post by nerdtron on 2010-04-06
> **dcstar said:**
> How much RAM and Swap space do you have?

Thanks for the reply:
I'm running VirtualBox right now and System Monitor shows 1.2GB is used out of 1.7GB RAM and 227.4MB out of 3.8GB of Swap.
Is there any problem with these?

---

### Post by julianb on 2010-04-06
> I'm running VirtualBox right now and System Monitor shows 1.2GB is used out of 1.7GB RAM and 227.4MB out of 3.8GB of Swap.
Is there any problem with these?

Given those numbers, your problem is not a shortage of swap space. It must be something else.

---

### Post by nerdtron on 2010-04-09
Uhmmm...bump?
Has anyone tried this yet? Or maybe there is a setting in virtual box or on virtualXP that prevents the system from hibernating?

---

### Post by dcstar on 2010-04-10
> **nerdtron said:**
> Uhmmm...bump?
Has anyone tried this yet? Or maybe there is a setting in virtual box or on virtualXP that prevents the system from hibernating?

You may want to try out a 10.04 beta CD and see if the hibernation works, I know that is is more reliable on my hardware than previous releases.

---

### Post by nerdtron on 2010-04-10
> **dcstar said:**
> You may want to try out a 10.04 beta CD and see if the hibernation works, I know that is is more reliable on my hardware than previous releases.

OK..but I'll wait for the final release. Thanks for all your replies everyone

---

### Post by davidsarah on 2011-03-23
Looks to be the same bug: [http://www.virtualbox.org/ticket/7716](http://www.virtualbox.org/ticket/7716)

---

