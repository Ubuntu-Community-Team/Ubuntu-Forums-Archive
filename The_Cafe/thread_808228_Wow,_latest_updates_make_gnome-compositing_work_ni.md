---
title: "Wow, latest updates make gnome-compositing work nicely"
date: 2008-05-26
forum: The Cafe
---

### Post by Npl on 2008-05-26
Dunno whats responsible, but last time I tried, I experienced severe slowdowns. No such things so far.. should it continue to work without problems I will keep it :)

The only thing thats missing is Vsync for videos.

---

### Post by madjr on 2008-05-26
i think it were the new nvidia drivers

---

### Post by Bungo Pony on 2008-05-26
I take this is an update released today?

PLEASE GOD let it fix my random freezing problem.

---

### Post by dasunst3r on 2008-05-26
I'm still seeing 169.12 on the nVidia web site.  Am I missing something here?  Also, exactly what is gnome-compositing?  I've heard of Compiz Fusion, but where do you get this gnome-compositing?

---

### Post by kevin11951 on 2008-05-26
> **dasunst3r said:**
> I'm still seeing 169.12 on the nVidia web site.  Am I missing something here?  Also, exactly what is gnome-compositing?  I've heard of Compiz Fusion, but where do you get this gnome-compositing?

the newest gnome (the one in hardy) has a built it composite manager,it has none of the cool effects of compiz, but it does allow things like live thumbnails, and transparencies.

---

### Post by Npl on 2008-05-26
Im using same NV-Drivers as before, no idea what update is responsible for compositing working nicely now (maybe kernel-scheduling?)

And the right term is metacity-compositing, unlike compiz this is done right in gnomes default window-manager, so no ackward differences in UI-Handling, and both lighter and much more stable.

To enable (you should disable compiz-compositing before - do so in the "Appearance" GUI ):
```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true
```

To disable:
```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager false
```

or run gconf-editor and navigate to the key manually

---

### Post by Joeb454 on 2008-05-26
The metacity compositor has always worked well for me (I have an Intel onboard graphics card) :)

---

