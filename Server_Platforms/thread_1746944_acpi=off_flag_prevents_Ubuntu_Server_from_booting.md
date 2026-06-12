---
title: "acpi=off flag prevents Ubuntu Server from booting"
date: 2011-05-02
forum: Server Platforms
---

### Post by SwordRaven on 2011-05-02
Hi All,

I'm running Ubuntu Server 11.04 on a home PC as a local-only file and web server for some private projects.

After a few minutes Ubuntu will stop responding to the network and a cold reboot is required to re-enable the NIC.

I've been able to stop the above occurring with a user logged in and constantly pinging the gateway, although this is obviously undesirable.

I read here and elsewhere that a fix is to set acpi=off in grub. I have done this but now instead Ubuntu will not boot and shows the message:

[B]do_IRQ: 1.55 No irq handle for vector (irq -1)
Disabling IRQ #34[/B]

and hangs there indefinitely. The system will boot fine if I revert the changes but obviously the sleep problem remains.

The BIOS does not have an option to disable ACPI, just select S1 or S3.

Is there anything else I should be looking for in order to disable sleep? Otherwise the system is working fine, and when it's awake I haven't had any other trouble.

Thanks.

---

### Post by volkswagner on 2011-05-02
Perhaps a work around would be to have something like [ntp update]("https://help.ubuntu.com/community/UbuntuTime") to keep the card awake.

Try leaving acpi active but install ntp update and have it run every five minutes or so.  This will not use much resources, but may be enough to keep the machine/card from sleeping.

---

### Post by SwordRaven on 2011-05-02
> **volkswagner said:**
> Perhaps a work around would be to have something like [ntp update]("https://help.ubuntu.com/community/UbuntuTime") to keep the card awake.

Try leaving acpi active but install ntp update and have it run every five minutes or so.  This will not use much resources, but may be enough to keep the machine/card from sleeping.

Thanks for the reply,

Would you recommend using ntpd or does this not do quite what I want? Or should I just cron ntpdate for a more regular interval?

---

### Post by volkswagner on 2011-05-02
> **SwordRaven said:**
> Thanks for the reply,

Would you recommend using ntpd or does this not do quite what I want? Or should I just cron ntpdate for a more regular interval?

I would use ntpd, I believe the default is to run every five min.

---

### Post by matt_symes on 2011-05-02
Hi

Just out of interest, what card is it ? Wired or wireless ?

```
sudo lshw -C network
```

Kind regards

---

### Post by SwordRaven on 2011-05-02
Hi, sorry I left that out, it's an onboard Wired NIC.

I've just halted the server because the nic is asleep at the moment so I can't try out the ntp thing either... this is frustrating. I'll find out what it is in a sec.

edit: Sometimes the NIC refuses to work unless I unplug the power cord physically after a shutdown and wait about 20-30 mins before it will initialise properly again. This exact hardware was previously my Ubuntu Desktop for 2 years and I never had any problems with the networking of it at all.

---

### Post by SwordRaven on 2011-05-02
> **matt_symes said:**
> Hi

Just out of interest, what card is it ? Wired or wireless ?

```
sudo lshw -C network
```

Kind regards

I've found CK804 Ethernet Controller nVidia eth0 on irq 24

```

sudo ifdown eth0
sudo ifup eth0
``` 

Claims that it is up and running but I can't ping out anymore... I don't know why this has suddenly happened. It used to work if I connected on boot and set my pinguser to work!

---

### Post by SwordRaven on 2011-05-02
I'm leaning towards thinking that the NIC has given up the ghost. This is most distressing. It doesn't work for the server installer CD anymore or a 9.10 live CD I found.

Thanks for the advice though chaps. I'll keep it in mind.

Edit: not really solved, but there's no 'It's not Ubuntu's fault' option!

---

### Post by SwordRaven on 2011-05-03
Just to confirm, the NIC was at fault. I've added a PCI card and enabled it and the server is working fine. Not had any sleep problems since either.

Thanks for your help.

---

### Post by matt_symes on 2011-05-03
Hi

Thanks for the follow up.

Kind regards

---

