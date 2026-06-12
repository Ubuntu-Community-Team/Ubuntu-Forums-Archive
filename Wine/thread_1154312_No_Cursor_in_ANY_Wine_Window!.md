---
title: "No Cursor in ANY Wine Window!"
date: 2009-05-09
forum: Wine
---

### Post by Ant59 on 2009-05-09
I have tried EVERYTHING on the internet to solve this problem, but nothing works.

Regardless of the progaram, the cursor disappears when roling over any wine window.

I have tried all of the following:
[LIST]
[*]Turning off compiz
[*]Reverting to older Wine version
[*]SWCursor and HWCursor in xorg.config
[*]Changing to a single monitor configuration
[*]Uninstalling and reinstalling Wine
[*]Just about everything else I could find on the net...
[/LIST]

Please help me someone!

---

### Post by NightMKoder on 2009-05-09
Does the cursor show up in winecfg? If you don't have any programs installed, you can try removing your prefix (rm -Rf ~/.wine), and then trying to run winecfg again.

---

### Post by Ant59 on 2009-05-10
No the cursor doesn't show in winecfg. Not even after running "rm -Rf ~/.wine".

---

### Post by Ant59 on 2009-05-10
If it helps, this is the terminal output after completely re-installing wine:

```

antony@Ant-PC:~$ winecfg
wine: created the configuration directory '/home/antony/.wine'
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
Could not load Mozilla. HTML rendering will be disabled.
err:local:LOCAL_GetBlock Local heap not found
err:menu:MENU_GetSysMenu failed to load system menu!
wine: configuration in '/home/antony/.wine' has been updated.
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer

```

---

### Post by Ant59 on 2009-05-11
- Bump -

Can noone answer this???

---

### Post by Ant59 on 2009-05-11
- Bump -

---

