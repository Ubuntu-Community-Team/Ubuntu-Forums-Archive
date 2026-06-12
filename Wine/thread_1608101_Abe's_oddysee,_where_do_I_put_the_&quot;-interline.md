---
title: "Abe's oddysee, where do I put the &quot;-interline&quot; command?"
date: 2010-10-28
forum: Wine
---

### Post by EarthBoundFan on 2010-10-28
I installed wine and Abe's Oddysee running in Win95 mode (it is compatible), but the videos obviously aren't working, the Wine website gives me the code, but where am I supposed to put it? I'd like it in the "Other" menu, I've tried to put it in the .xml cache in different positions, but it doesn't do anything after saving it as root. Any help?

Here's the code

```
</menu>
    <menu name="Other" icon="applications-other">
        <app name="Abe&apos;s Oddysee" cmd="env WINEPREFIX=&quot;/home/xubuntu/.wine&quot; wine &quot;C:\\Program Files\\Abe&apos;s Oddysee\\ABEWIN.EXE&quot;" icon="039f_abewin.0" term="false" snotify="false" /> -interline
        <app name="Notepad" cmd="notepad" icon="wine-notepad" term="false" snotify="false" />
        <app name="Read Me" cmd="env WINEPREFIX=&quot;/home/xubuntu/.wine&quot; wine &quot;C:\\windows\\system32\\NOTEPAD.EXE&quot; C:\\PROG~FBU\\ABE&apos;~FCL\\README.TXT" icon="3550_notepad" term="false" snotify="false" />
    </menu>
```

---

