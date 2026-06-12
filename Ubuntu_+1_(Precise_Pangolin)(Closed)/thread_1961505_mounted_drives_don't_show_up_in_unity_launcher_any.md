---
title: "mounted drives don't show up in unity launcher anymore"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by DavidSommen on 2012-04-19
Recently, mounted drives (CD-ROM or USB) don't show up in my unity launcher anymore. Is this normal behaviour or a bug? I am running Precise Pangolin Beta 2 up-to-date. The drives mount perfectly and show up in Nautilus, no glitches there. It's just that I'm used to ejecting drives via unity.

---

### Post by mc4man on 2012-04-19
Check & see if you set the option to 'show devices' to never, either in the unity plugin settings or thru this command, if it returns 0 you have
```

gconftool -g /apps/compiz-1/plugins/unityshell/screen0/options/devices_option
```

---

### Post by DavidSommen on 2012-04-19
Thanks, I solved it that way. Has this changed for everybody with updates then?... anyway :)

---

