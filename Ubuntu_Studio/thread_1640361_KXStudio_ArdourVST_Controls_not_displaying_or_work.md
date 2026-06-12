---
title: "KXStudio ArdourVST Controls not displaying or working"
date: 2010-12-07
forum: Ubuntu Studio
---

### Post by grolling on 2010-12-07
Hello all,

I'm a long-time lurker, first-time poster.  Recently installed KXStudio 10.04.2 after Ubustu.  

When I add a VST plugin to a track in ArdourVST, I'm able to view the properties, but they are nonsense characters and I'm unable to modify any of the settings.  I've been googling this a bit and think maybe I'm just not using the correct terminology or something because I'm not coming up with anything.  Could anyone point me in a good direction to resolve this?

Thanks for all your help and wisdom...
--Greg

---

### Post by falkTX on 2010-12-12
> **grolling said:**
> Hello all,

I'm a long-time lurker, first-time poster.  Recently installed KXStudio 10.04.2 after Ubustu.  

When I add a VST plugin to a track in ArdourVST, I'm able to view the properties, but they are nonsense characters and I'm unable to modify any of the settings.  I've been googling this a bit and think maybe I'm just not using the correct terminology or something because I'm not coming up with anything.  Could anyone point me in a good direction to resolve this?

Thanks for all your help and wisdom...
--Greg

ArdourVST can't handle GUI-less plugins very well...

To use plugins with no GUI, you can try the dssi-vst ladspa extension though. Look:
[http://kxstudio.sourceforge.net/screenshots/ardourvst.png](http://kxstudio.sourceforge.net/screenshots/ardourvst.png)

---

### Post by sgx on 2010-12-13
> **grolling said:**
> Hello all,

I'm a long-time lurker, first-time poster.  Recently installed KXStudio 10.04.2 after Ubustu.  

When I add a VST plugin to a track in ArdourVST, I'm able to view the properties, but they are nonsense characters and I'm unable to modify any of the settings.  I've been googling this a bit and think maybe I'm just not using the correct terminology or something because I'm not coming up with anything.  Could anyone point me in a good direction to resolve this?

Thanks for all your help and wisdom...
--Greg
Hi, use Reaper to host windows vsts, using wineasio, and choose that in the Reaper preferences, and then have Reaper scan your .wine folder for
plugins, kept in

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins

Tons of Reaper vids/tips on google/youtube.

The output of Reaper can be routed to Ardour using qjackctl, if desired, and it has its own facilities for rendering/recording, and includes a
sizeable selection of its own plugins.

Some vsts will load using festige, the fst command, and lmms, I've not
tried windows plugins in Ardour. If you are also using linux plugins,
let people know which ones, and the rest of your hardware and software setup.

Cheers

---

