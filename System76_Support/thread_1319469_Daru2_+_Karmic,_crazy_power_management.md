---
title: "Daru2 + Karmic, crazy power management"
date: 2009-11-08
forum: System76 Support
---

### Post by werewolves on 2009-11-08
Well, I had heard this was supposed to be fixed under Karmic, and for the first week it seemed to be, but the flaky power monitoring that used to plague the Daru2 seems to be back.

I will be running along just fine, and the system will decide that I have no battery, and the temp monitor will go crazy.

There used to be a PPA that had a fix, but I believe this was for an older kernel.  So, what should I do now?

Thanks

---

### Post by werewolves on 2009-11-09
Hello System 76... any help would be appreciated.

---

### Post by gaussian on 2009-11-09
Are you sure that you are running a Karmic Kernel? There have been cases of borked upgrades lead to wrong Kernel being default choice under Grub?

If this is a clean install, then never mind.

You can check you kernel version by ```
uname -r
```

---

### Post by werewolves on 2009-11-09
werewolves@loki:~$ uname -r
2.6.31-14-generic

---

### Post by gaussian on 2009-11-09
Well, there goes my theory. You are running the same Karmic kernel as I am. I have not seen any problems yet with my Daru2

---

### Post by werewolves on 2009-11-09
Well, thanks for trying.  Anyone else?

---

### Post by thomasaaron on 2009-11-10
werewolves, did you upgrade to karmic or do a fresh install?
How about you, gaussian?

---

### Post by gaussian on 2009-11-10
> **thomasaaron said:**
> werewolves, did you upgrade to karmic or do a fresh install?
How about you, gaussian?

I have both (32-bit) non-fresh install. Actually, it is as non-fresh as they come, it has been updated from 7.04 to 9.10 incrementally. No problems currently with power management. Suspend obviously does not work.

---

### Post by werewolves on 2009-11-10
I did an upgrade (specifically from Kubuntu 9.04) to Kubuntu 9.10.  Like I said, the first week or so I had NO issues, then all of a sudden it starts acting up again.

---

### Post by thomasaaron on 2009-11-11
We're not really able to support Kubuntu, and I'm wondering if an update hosed it.

I'm *assuming* guassian is using Ubuntu.

Do you know if you have acpi=noirq as a kernel option?

---

### Post by gaussian on 2009-11-11
> **thomasaaron said:**
> We're not really able to support Kubuntu, and I'm wondering if an update hosed it.

I'm *assuming* guassian is using Ubuntu.

Do you know if you have acpi=noirq as a kernel option?

I am using Ubuntu. And I do have acpi=noirq (kills brightness function keys).

---

### Post by thomasaaron on 2009-11-12
Werewolves,

I think the reason guassian doesn't have the problem is that he's carried that acpi=noirq kernel option over through several versions.

Yours may have been lost. Can you see if it is there?

Run...
sudo <whatever text editor you use> /etc/default/grub
...and see if there is a line like this...
GRUB_CMDLINE_LINUX="acpi=noirq"

If there is not, add it, save, and then run...

sudo update-grub

...and then reboot.

---

### Post by werewolves on 2009-11-12
> **thomasaaron said:**
> We're not really able to support Kubuntu, and I'm wondering if an update hosed it.

I'm *assuming* guassian is using Ubuntu.

Do you know if you have acpi=noirq as a kernel option?

I understand that, but I would think power management is the same...

At any rate, I'll check that when I get home, but I don't think so.

Oddly, it has been behaving itself for a couple of days now.  Gremlins.  I'll keep you posted.

---

### Post by thomasaaron on 2009-11-12
> but I would think power management is the same

Probably is under the hood. But they use different power management programs. I doubt that has anything to do with it, though.

---

### Post by werewolves on 2009-11-12
> **thomasaaron said:**
> Werewolves,

I think the reason guassian doesn't have the problem is that he's carried that acpi=noirq kernel option over through several versions.

Yours may have been lost. Can you see if it is there?

Run...
sudo <whatever text editor you use> /etc/default/grub
...and see if there is a line like this...
GRUB_CMDLINE_LINUX="acpi=noirq"

If there is not, add it, save, and then run...

sudo update-grub

...and then reboot.

OK, there was nothing in that file, so I added the line above and rebooted.

So far, so good.  I will watch it for a couple of days, and let you know.

Thank you for the help.

---

### Post by ackey on 2009-11-13
> Run...
sudo <whatever text editor you use> /etc/default/grub
...and see if there is a line like this...
GRUB_CMDLINE_LINUX="acpi=noirq"

If there is not, add it, save, and then run...

sudo update-grub

Should this be for the old grub or grub2?  I didn't upgrade my grub and the /etc/default/grub file doesn't exist, update-grub didn't mention it, and the noirq option hasn't appeared in my menu.lst.

If this is for grub2, what is the best way to do it with the old grub?  I had lost track that this option was still needed.

---

### Post by thomasaaron on 2009-11-16
That's for grub2.

You can update to grub2 (if you're on karmic) by running...

sudo apt-get install grub-pc

---

