---
title: "Vbox rdesktop-vrdp sound"
date: 2011-10-24
forum: Virtualisation
---

### Post by dhysk on 2011-10-24
ok...

Host = Desktop running Ubuntu 11.10 and VirtualBox 4.1 from repos
Vmachine = windows XP

remoteTerminal = laptop running VirtualBoxe's 4.1.4 from their website so I could get rdesktop-vrdp for USB support.  Works great remote USB works like a charm.

Problem is I can not get sound to work remotely using 'rdesktop-vrdp'.  Sound does work from the laptop using the default sound options in 'rdesktop' that comes with ubuntu.

error messag...
```

WARNING: Remote desktop changed from 800x600 to 1024x768.
/dev/dsp: No such file or directory
WARNING: no working audio-driver found
```

any ideas.. I'm not sure how to find the sound device and put it in the format they want.

```
'-r sound:[local[:driver[:device]]|off|remote]': enable sound redirection
                     remote would leave sound on server
                     available drivers for 'local':
                     oss:	OSS output driver, default device: /dev/dsp or $AUDIODEV

```

---

### Post by dhysk on 2011-10-24
ok looks like oracle didn't update their rdesktop-vrdp when rdesktop updated their sound.

so anyway long story short to get sound to work add padsp as a workaround.

```
padsp rdesktop-vrdp -r usb -r sound -r clipboard -N yourIP:port &
```

sweet now I have sound and USB capability for my VM no matter ware I go... HOW AWESOME IS THAT :)..

---

