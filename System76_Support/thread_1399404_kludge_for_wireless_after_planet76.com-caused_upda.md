---
title: "kludge for wireless after planet76.com-caused update failure: boot older kernel"
date: 2010-02-05
forum: System76 Support
---

### Post by tlroche on 2010-02-05
I'm now able to wireless again on a starling running karmic/9.10 which had its kernel update broken by the [planet76.com downtime]("http://ubuntuforums.org/showthread.php?t=1399130"). Short answer: boot to previous kernel. Long answer:

When I exited Update Manager after it timed out, and tried to reconnect my home wireless, I got the Black Screen of Death (i.e. black screen, unblinking text cursor in upper-left, immobile mouse cursor in center). I then rebooted and was unable to reconnect my wireless, or detect any networks. As this is my girlfriend's box, this was bad :-(

The starling had a fresh install of karmic/9.10. As noted at the [GRUB 2 guide]("http://ubuntuforums.org/showthread.php?t=1195275")

[QUOTE="http://ubuntuforums.org/showthread.php?t=1195275"]
> Grub 2 will be the default in Ubuntu 9.10, Karmic Koala but the plan
> is not to convert over previous Grub legacy installations to Grub 2.
...
> [to] confirm the version of Grub you are using [run]
> $ grub-install -v
[/QUOTE]

This produced

```
grub-install (GNU GRUB 1.97~beta4) 
```

which despite the number indicates GRUB 2. This means

[QUOTE="http://ubuntuforums.org/showthread.php?t=1195275"]
> [With] a clean install of Ubuntu 9.10 with no other installed
> operating system [GRUB 2] will boot directly to the login prompt or
> Desktop without displaying a menu. Other major differences:

> * No ''/boot/grub/menu.lst''. It has been replaced by ''/boot/grub/grub.cfg''.

> * Hold down SHIFT to display the hidden menu during boot (formerly
>   ESC is GRUB legacy).

> * There is no "find /boot/grub/stage1" at the grub prompt. Stage 1.5
>   has also been eliminated.

> * The main menu file, ''/boot/grub/grub.cfg'' is not meant to be
>   edited, even by 'root'.

> * ''grub.cfg'' is overwritten anytime there is a update, a kernel is
>   added/removed or the user runs `update-grub`

...

> * No changes made in the configuration files will take effect until
>   the `update-grub` command is also run.
[/QUOTE]

So I kludged the wireless by

[LIST=1]
[*]"Open" /etc/default/grub in an editor, e.g.: ```
sudo emacs /etc/default/grub &
```
[*]Comment out the line beginning "GRUB_HIDDEN_TIMEOUT=", i.e. by placing '#' at the beginning of the line.
[*]I kept the line ```
GRUB_TIMEOUT="10"
``` but feel free to change the value to some other positive integer (number of seconds to display the menu before automatic selection) or "-1" to wait for the user to press ENTER (no timeout).
[*]"Save" the file and exit the editor. **Note the contents are not actually changed until you ...**
[*]Update grub ```
sudo update-grub
``` which generates grub.cfg and finds a bunch of kernel images
[*]shutdown/restart
[*]On boot, choose a previous/unbroken kernel from the GRUB menu. Using the arrow keys, I chose kernel=
```
Ubuntu, Linux 2.6.31-17-generic
```
because it was the first previous kernel to 
```
Ubuntu, Linux 2.6.31-19-generic
```
[*]Hit Enter to boot that
[/LIST]

Upon booting that, Network Manager connects to my home wireless!

This is however obviously a just a kludge; have [queried separately regarding fixing the broken kernel update]("http://ubuntuforums.org/showthread.php?t=1399413").

---

### Post by samalex on 2010-02-05
I'd never heard the term *kludge* before and had to look it up:
[http://en.wikipedia.org/wiki/Kludge](http://en.wikipedia.org/wiki/Kludge)

Learn something new everyday :)

Sam

---

### Post by thomasaaron on 2010-02-08
You should be able to go to Synaptic package manager, search for the hosed kernel, and re-install it. That should also cause the wireless fix to automatically applied. (But if not, running the System76 Driver and rebooting should do the trick.)

---

