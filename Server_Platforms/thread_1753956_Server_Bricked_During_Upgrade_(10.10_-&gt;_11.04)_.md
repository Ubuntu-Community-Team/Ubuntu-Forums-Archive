---
title: "Server Bricked During Upgrade (10.10 -&gt; 11.04) &quot;The disk drive for / is not ready&quot;"
date: 2011-05-09
forum: Server Platforms
---

### Post by NessDan on 2011-05-09
So today I decided to go ahead and do-release-upgrade on my home server. I was doing this over SSH.

The installation for the most part took care of itself. It notified me that some services needed to be restarted and I okayed that message twice. The problem arose when it said that my Samba configuration file was different then the upgrade's. I was shown a number of options and although I don't remember the exact wording, I chose the option that was along the lines of "Show the differences side-by-side." I scrolled through the file and saw the differences. The problem was that there was an Ok button to exit, but I couldn't get my cursor on it.

In the end, I semi-panicked and thought, "CTRL+C will get me back to the installation!"

The installation stopped and everything looked pretty normal so I rebooted. Then I noticed I could no longer log in via SSH so I hooked my server up to a monitor and was presented with "GNU GRUB" giving me choices for bootup (I chose Ubuntu, with Linux 2.6.35-28-generic-pae). After selecting that, I get some more information:

```
init: udevtrigger main process terminated with status 1
init: udevtrigger post-stop process terminated with status 1
init: udevmonitor main process terminated with status 1
The disk drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
```

The manual recovery lets me go around in root. Is there a way to finish the installation, get the computer to boot normally, while not deleting everything on the server? (I made backups already but it'd be a bother to re-do everything.)

---

### Post by dtfinch on 2011-05-09
The error alone doesn't help much.

If you can get it mounted, it'd help to see /etc/fstab. A live cd might be useful for this. Or at least describe your disk setup, like whether you're using an md raid, bios/fakeraid, lvm, etc.

---

### Post by NessDan on 2011-05-09
I'm new to the world of servers and my server isn't really server-material.

I assume the disk was mounted since when I was in recovery mode, I could explore all the directories but my disk setup is very simple (it's just an old machine that I use for hosting my web work and Minecraft.): I installed the server on the entire disk.

I'll get the info from fstab and post it as soon as I can. I'm using a Live CD to try a couple of things.

---

### Post by NessDan on 2011-05-09
Here's what I have in my /etc/fstab file:

```
proc    /proc    proc    nodev,noexec,nosuid    0    0
# / was on /dev/sda1 during installation
UUID=4cd9b904...    /    ext4    errors=remount-ro   0    1
# swap was on /dev/sda5 during installation
UUID=17796db5...    none    swap    sw    0    0
```

---

### Post by Gerbiler on 2011-06-16
I have this exact problem. I started the update, interrupted it, and now  I can't get in due to the exact same error. Did you find the problem  Nessdan?

---

### Post by Gerbiler on 2011-06-18
I managed to fix it!  Basically all I did was download the latest ubuntu server edition. Then I booted into it and chose the rescue broken system option. Then I selected the correct hard drive, and all the options. Then I just ran dpkg --configure a. And voila it worked! So that was it.

---

