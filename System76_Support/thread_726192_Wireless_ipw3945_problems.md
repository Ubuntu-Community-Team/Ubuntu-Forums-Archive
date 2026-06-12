---
title: "Wireless ipw3945 problems"
date: 2008-03-16
forum: System76 Support
---

### Post by kuzew on 2008-03-16
Hello,

Within the last few months, my wireless drivers for the integrated wireless chipset 'Intel  PRO/Wireless 3945ABG' has been acting a bit odd, resulting in the connection dropping out and the wireless drivers going into an unresponsive state; which is fixed by rebooting. This happens with no warning and is completely random (anywhere between 20 minutes to +24 hours).

**Symptoms: **

[LIST]
[*]Process 'ipw3945d-2.6.22-14-generic' or '[ipw3945/1]' uses up to ~50% total processor usage and system load increases to ~24.00.

[*]Networking tools (ifconfig) and wireless tools (iwconfig) freeze up when executed, as well as launching another xterm or any other application within X, though can change VTs and log on.

[*]Can't unload kernel module 'ipw3945', it sits there and returns nothing.

[*]nm-applet and Network Monitor within GNOME go into a unresponsive state.

[*]Nothing odd with the output from 'dmesg'.

[*]System, overall, becomes unstable.

[*]After a reboot (shutdown now -r), system doesn't come back normally, BIOS splash screen has this 'melting' effect, where the grey turns slowly into black. This is fixed with a hard reboot.
[/LIST].

I am running kernel version 2.6.22-14-generic, SMP enabled. Kernel is the stock kernel from the Ubuntu repositories.
System76 model is serp3.

Anyone have a solution to this problem?

Thank you for your time.

Cheers,
kuzew

---

### Post by thomasaaron on 2008-03-17
I've seen it a few times. I believe it is a problem with the drivers. Try switching to the iwl drivers. That should fix it.

echo blacklist ipw3945 | sudo tee -a /etc/modprobe.d/blacklist
echo iwl3945 | sudo tee -a /etc/modules

---

### Post by kuzew on 2008-03-17
Ah, thank you thomasaaron... I will give that a go right away. I figured it had to be something driver related, just wasn't sure how to go about doing it.

Thanks again, I'll report back if there are any problems.

Cheers,
kuzew

---

### Post by kuzew on 2008-03-17
Well, everything seems _much_ more stable in terms of Signal to Noise Ratio (SNR) using the application 'wavemon'. The SNR is at a constant level and not bouncing around like with the other drivers (not normal). Hopefully this should solve this issue, we shall see... but it looks promising already. Thank you once again thomasaaron for your help.

---

### Post by Royal_Pwner on 2008-03-25
I have had EXACTLY the same problem.

However, I can't even do a normal shutdown, because my panel menu breaks. I didn't even try command line (terminal? are they the same thing?).

Thanks for the help thomasaaron, you godly tech-support man.
Srsly. You solve all my problems.

Also, my problem is exacerbated by large bandwidth usage. (Torrents, big downloads more than a gig or so, etc.)

I will try the switch-fix soon.

---

### Post by imhavoc on 2008-03-25
FYI:

I applied this fix 8 days ago (17.Mar.2008). So far, I haven't had any trouble with the wireless, but I wasn't having the level of troubles you were having at the time. Several months ago the wireless would drop randomly -- sometimes 2-3 times per day, sometimes not for a week or more at a time. I've been letting the machine run longer hours lately, and I've not had the wireless card go down since making this change.

Thanks, Tom!

---

### Post by Royal_Pwner on 2008-03-30
Works like a charm. Thanks!

---

