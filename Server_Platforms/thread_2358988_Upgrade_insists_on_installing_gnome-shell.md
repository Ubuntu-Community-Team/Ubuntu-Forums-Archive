---
title: "Upgrade insists on installing gnome-shell"
date: 2017-04-19
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2017-04-19
I decided after virtualizing that I'm ok with upgrading my server to 17.04 today. I just did the 16.10 upgrade from 16.04, now im doing 16.10 to 17.04. Is there a reason the upgrade insists on installing the gnome shell and assorted junk? I don't use it, don't have it installed yet it installs it during the upgrade and I have to rip it out afterwards. Why?

---

### Post by TheFu on 2017-04-19
Do you have any gui already installed on this "server"?  Servers don't have any GUI stuff usually.

---

### Post by Tadaen_Sylvermane on 2017-04-19
Sorry, i use server as it rolls off the tongue easier than htpc. It does all server related things on my lan. dns, dhcp, ltsp, backup target, media server, mythtv backend, apt-cache proxy, transmission server, and 4 minecraft servers in lxd containers. Direct boots to Kodi for media center use.

---

### Post by darkod on 2017-04-20
Well, Kodi is a GUI, right? That is probably related to the machine asking to install graphical components.

Plus if you don't want unexpected behavior, stick to LTS releases. :P Maybe this is a feature of 17.04? :)

---

### Post by TheFu on 2017-04-20
```
$ aptitude why {package}
```
can show why a package was installed.

---

### Post by Tadaen_Sylvermane on 2017-04-20
> [COLOR=#000000]Plus if you don't want unexpected behavior, stick to LTS releases. [/COLOR]:razz:[COLOR=#000000] Maybe this is a feature of 17.04? [/COLOR]:smile:

I just got owned... I mainly upgraded to get mergerfs, isn't in ltsp repos, even backports. Should have stuck with mhddfs :P

---

### Post by TheFu on 2017-04-20
**LVM** is what we professionals use for this stuff.  Extremely flexible and extremely well tested, well understood, well used.

We also would ensure that a backup existed prior to doing any apt-get stuff and definitely prior to doing a system version change (I stopped using "upgrade" years ago).

"owned" means your system was cracked and cannot be trusted anymore. Was that your intent?

---

### Post by Tadaen_Sylvermane on 2017-04-20
Tried LVM awhile back on 16.04. Woke up to a crashed system. Reinstalled with the only installer I had handy, Debian Jessie. Installed on LVM was fine till the next day, crashed again. Managed to get my Ubuntu Server installer off the server before and reinstalled on regular partitions. Been going strong ever since. 

I also like the idea of MergerFS because if I lose a disk unexpectedly then I only lose that disk, not the whole volume.

No, means you just owned me by slapping me with the "shoulda stayed on lts" :p

---

