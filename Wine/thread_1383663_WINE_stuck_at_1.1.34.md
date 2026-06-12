---
title: "WINE stuck at 1.1.34"
date: 2010-01-17
forum: Wine
---

### Post by spoons on 2010-01-17
Okay, so I had 1.1.34 installed, updated to 1.1.36, and although that's what package manager shows as the version notepad and winecfg still say they are 1.1.34? :s

I tried completely removing wine and reinstalling it but it still thinks it's 1.1.34, and even when it's not installed according to Synaptic windows apps such as COD2 still run?!?! I find this all rather odd!

I'm on Ubuntu 9.10 x86_64, thanks for any advice given.

---

### Post by hikaricore on 2010-01-17
> wine --version

^

---

### Post by spoons on 2010-01-18
> **hikaricore said:**
> ^

Terminal reports 1.1.34.

I don't understand, Synaptic says it has installed 1.1.36 and removing Wine doesn't actually remove it at all?!?

Thanks for the help so far,
Chris.

---

### Post by rocky5051 on 2010-01-19
```
sudo apt-get purge wine && sudo apt-get install wine
```

After you've done that, restart your computer. Sometimes you get two different versions of wineserver running at once for the old and new versions of Wine, and you end up with problems like that. A reboot usually clears it up.

---

### Post by beastrace91 on 2010-01-19
Why reboot to clear wine server?... Just do - ```
killall wineserver
```

This is Linux - we only reboot for hardware installs and kernel updates :P (and even then you don't always have to lol)

~Jeff

---

### Post by rocky5051 on 2010-01-20
Because it could clean up any other pending issues that may have arisen since his last reboot.

Linux may be stable, but nothing clears up issues on a computer better than a reboot, and I'll always stand by that. \\:D/

---

### Post by hikaricore on 2010-01-21
> **rocky5051 said:**
> Because it could clean up any other pending issues that may have arisen since his last reboot.

Linux may be stable, but nothing clears up issues on a computer better than a reboot, and I'll always stand by that. \\:D/

Sorry but this is nonsense and a very windowsy way of thinking.
The worst you should ever have to do is restart gdm/kdm a far cry from a complete reboot.

---

### Post by rocky5051 on 2010-01-21
No, I disagree. This is a user friendly way of thinking of things. The average user, which due to the fact Windows happens to appeal to the greatest number of them last time I checked (I'm not bashing Ubuntu, I'm just stating things how they are), don't understand, nor want to understand, how to perform the alternatives to rebooting because they're too complex for the average user. The average user isn't going to want to Google how to restart the desktop environment or any other component because they are lazy and there isn't a button in a drop down menu, or right on the desktop itself, that says "restart kdm" or gdm or really any other component that may need to be restarted.

I said I stand by restarting because it is the lazy way out, not because it's a Windowsy way of thinking.

I'm not the average user, but when I tell an average user to restart a component individually or a number of them, they ask me why should they and why they can't restart almost every time.

EDIT:I'm not going to (nor was I in the first place) argue about this and hijack this thread over it. It's a matter of tastes from a power user perspective versus a lazy/average/lazy power user perspective.

EDIT:WAIT! I reread my post and I see where my generalization of the matter made me wrong, but I still stand by my argument about rebooting.

---

