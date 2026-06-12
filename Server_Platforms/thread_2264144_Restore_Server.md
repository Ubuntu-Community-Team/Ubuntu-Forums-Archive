---
title: "Restore Server"
date: 2015-02-05
forum: Server Platforms
---

### Post by scott.bouch on 2015-02-05
Hi all, not a good day today...

Well, today I remotely over SSH gave my server (14.04) an **apt-get update**, **upgrade** and **dist-upgrade**. It threw some errors, but overall seemed to do it's job.

I then gave it a **reboot** and waited patiently to re-connect over SSH and wait I did...

After giving up, I went and plugged in a monitor - I saw it was hung up at GRUB. I then plugged in a keyboard, pressed enter and got it logged in.

So,  I then did some research into GRUB causing this issue, and thought I'd try uncommenting **GRUB_DISABLE_RECOVERY="true"** in the config file (/etc/default/grub) and restarted GRUB.

I then gave it another **reboot** and it got stuck at GRUB again, so ok, I thought that didn't work, I'll reset it and try something else. SO after pressing enter again, I got a bigger kick where it hurts.. It is now hanging in the boot sequence here:

[ATTACH=CONFIG]259736[/ATTACH] Is this a BIOS or Ubuntu boot screen?

Any ideas? Any way to recover my server? I've not made a recovery CD (can you make such things in Ubuntu as in Windows?)

I know I can get to my files using a live CD, but can I patch up my boot sequence using it? I guess it may help me to recover some log files to share here to help diagnose the fault?

Once it's fixed, I want to take an image of my HDD, as I've done loads of configuring on it...

Thanks, Scott.

---

### Post by lisati on 2015-02-05
That looks more like a kernel panic (or some such problem) to me than either grub or BIOS. Are you able to boot your server using an older kernel?

---

### Post by scott.bouch on 2015-02-05
Hi Lisati,

Thanks for taking a look, I can try, but have no idea how... I'm quite new to this... Any pointers?

Thanks, Scott.

---

### Post by lisati on 2015-02-05
Starting with an older kernel is usually done when Grub has control, in a similar fashion to selecting recovery mode when starting up. You migt need to do something like holding down the left shift key when booting to get a list of choices.

---

### Post by scott.bouch on 2015-02-05
Bingo! Thanks! :p

I just figured out that the Advanced Ubuntu Options gives you the different kernel versions...

It failed to boot on:
Ubuntu, with Linux 3.13.0-45-generic
Ubuntu, with Linux 3.13.0-45-generic

But it succeeded with:
Ubuntu, with Linux 3.13.0-43-generic

Thanks for your pointer, now I've just got to look into my GRUB settings to force it to use this kernel version each time.

Should the newer versions just work? Is there any detriment in using an older kernel? - Such as security issues?

Thanks again, Scott.

---

