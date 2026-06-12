---
title: "grub-customizer (not a tragedy)"
date: 2023-11-08
forum: Ubuntu, Linux and OS Chat
---

### Post by tea for one on 2023-11-08
Following recent posts, where boot-repair reports have shown the existence of grub proxy files created by grub-customizer, I thought that I would install it and see what happens.
Fortunately, I have a test box so no permanent damage can be done.

Xubuntu 23.10 and Windows 11 Dual Boot on one disk
UEFI mode with one ESP

Grub-customizer 5.2.4 installed via 
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
```
I changed the font colours and added a background.

Three lines were added to /etc/default/grub
```
export GRUB_COLOR_NORMAL="light-red/black"
export GRUB_COLOR_HIGHLIGHT="magenta/black"
export GRUB_MENU_PICTURE="/usr/share/xfce4/backdrops/hummingbird03.png"
```

Two items were added to /etc/grub.d/ 
[LIST]
[*]A backup folder containing 4 items [COLOR="#0000FF"]boot_grub   default_grub   etc_grub_d   RESTORE_INSTRUCTIONS[/COLOR]
[*]An empty file (with hidden attribute) [COLOR="#0000FF"].script_sources.txt[/COLOR]
[/LIST]
I was expecting to see proxy files/scripts but I can't find any.
I was going to remove these proxy files together with grub-customizer and break grub.
I haven't yet managed to break anything yet.

I removed grub-customizer.
I deleted the three added lines from /etc/default/grub
Updated grub and rebooted.

Booted successfully with original plain grub screen.

I can only conclude that grub-customizer version 5.2.4 is markedly different from versions which added a proxified scripts folder.

---

### Post by #&amp;thj^% on 2023-11-08
That might have been a very short run with grub-customizer, most problems come in when it is installed for a couple of months.
This i remember from oldfred:
>  grub 2.06. Typically grub-customizer backed up all the grub scripts and replaced then with proxy files. 
I no longer have those proxy scripts as they were month old and I just removed them all and grub-customizer this version "grub-customizer 5.2.4-1"
So the longer grub-customizer remains on a installed system the higher the chance of grub problems, for newer users.
Thanks tea for one.

---

### Post by Rubi1200 on 2023-11-08
Just to add my 2 cents. I think we have seen over the years that these Grub Customizer problems are often made worse when the user upgrades their system.

Thanks tea for one for testing and reporting the results here, this is important.

---

### Post by tea for one on 2023-11-08
> **1fallen said:**
> That might have been a very short run with grub-customizer, most problems come in when it is installed for a couple of months.
Ah, yes, good point.
I've re-installed it.
I'll let you know when it all goes pear-shaped  ;)
> **Rubi1200 said:**
>  I think we have seen over the years that these Grub Customizer problems are often made worse when the user upgrades their system
Agreed, in-situ upgrades often throw a wobbly.
Next upgrade is 24.04 - this thread, together with my memory, will be lost in the mists of time by then.

---

### Post by oldfred on 2023-11-08
Back in 2015, these were the proxy files:

[https://ubuntuforums.org/showthread.php?t=2279347&page=3](https://ubuntuforums.org/showthread.php?t=2279347&page=3)

Perhaps with grub 2.06, he had to change the way he modified files. 
I know with every grub update, he had to modify his scripts also.
Or maybe only some changes need script changes?

I know beginners like a gui. And have heard that using terminal is difficult.
But how hard is it to copy & paste those three lines into /etc/default/grub?

---

