---
title: "someone!! help me PLEASE to make 3d games running :(((("
date: 2009-11-07
forum: Wine
---

### Post by WoAnerges on 2009-11-07
radeon x1900xtx
amd phenom ii x4
ubuntu 9.10
wine 1.2
-----------------

when i starting a game it's just loading..and loading..and loading and then process just end :(
-----------------------------
earlier i tried to instal ati drivers from ati site, maybe it's bacause of that?
maybe i need to clear configs and remove drivers but i don't know how to.
anyone help me to solve this :(((
how to reset drivers? or something like that and why gameplay is so unstable 10-99fps in wine (whatever now games just not starting anymore)
also after uninstallation of wine settings not clearing, not removing. how to remove wine completely with all settings and video drivers?

---

### Post by WoAnerges on 2009-11-07
up up up up up up

---

### Post by WoAnerges on 2009-11-07
radeon x1900xtx
amd phenom ii x4
ubuntu 9.10 x64
wine 1.2
-----------------

when i starting a game it's just loading..and loading..and loading and then process just end
-----------------------------
earlier i tried to instal ati drivers from ati site, maybe it's bacause of that?
maybe i need to clear configs and remove drivers but i don't know how to.
anyone help me to solve this ((
how to reset drivers? or something like that and why gameplay is so unstable 10-99fps in wine (whatever now games just not starting anymore)
also after uninstallation of wine settings not clearing, not removing. how to remove wine completely with all settings and video drivers?

---

### Post by WoAnerges on 2009-11-07
radeon x1900xtx
amd phenom ii x4
ubuntu 9.10 x64
wine 1.2
-----------------

when i starting a game it's just loading..and loading..and loading and then process just end
-----------------------------
earlier i tried to instal ati drivers from ati site, maybe it's bacause of that?
maybe i need to clear configs and remove drivers but i don't know how to.
anyone help me to solve this ((
how to reset drivers? or something like that and why gameplay is so unstable 10-99fps in wine (whatever now games just not starting anymore)
also after uninstallation of wine settings not clearing, not removing. how to remove wine completely with all settings and video drivers?

---

### Post by WoAnerges on 2009-11-07
up up up up

---

### Post by WoAnerges on 2009-11-07
up up up up

---

### Post by WoAnerges on 2009-11-07
up up up up

---

### Post by hikaricore on 2009-11-07
> **WoAnerges said:**
> up up up up

In the future you will avoid bumping for 24-48 hours to allow people time to read your posts and reply.
This is not optional.  Best of luck.

---

### Post by overdrank on 2009-11-07
Please do not create multiple threads on the same issue. Also it is polite to bump your thread once a day. Threads merged.

---

### Post by Melcar on 2009-11-07
The latest ATI drivers won't work on that card, and the old 9.3 drivers won't work on releases post 9.04 (could be earlier, I don't remember).  You will have to use the open source driver (radeon) for your card.  The driver should load automatically provided you haven't messed with anything.  Furthermore, while the driver does provide 3D acceleration for your class of card, it can only accelerate up to OpenGL1.3-1.5 in hardware; WINE needs working OpenGL2.0-2.1 hardware acceleration for much of its functionality; some games might work (I can run a few 3D games myself on my laptop's 200M) but many may not.  Compiz, KWIN composition, and most open source games should work fine however, as long as you don't use OpenGL2.x specific features (GLSL in games for example, or bloom/HDR).

---

### Post by WoAnerges on 2009-11-07
> **Melcar said:**
> The latest ATI drivers won't work on that card, and the old 9.3 drivers won't work on releases post 9.04 (could be earlier, I don't remember).  You will have to use the open source driver (radeon) for your card.  The driver should load automatically provided you haven't messed with anything.  Furthermore, while the driver does provide 3D acceleration for your class of card, it can only accelerate up to OpenGL1.3-1.5 in hardware; WINE needs working OpenGL2.0-2.1 hardware acceleration for much of its functionality; some games might work (I can run a few 3D games myself on my laptop's 200M) but many may not.  Compiz, KWIN composition, and most open source games should work fine however, as long as you don't use OpenGL2.x specific features (GLSL in games for example, or bloom/HDR).

but i played CS 1.6 few days ago and now it not starting. and i don't know what to do. why?
how to completely remove drivers from ati sie and how to completely remove wine with allllll configurations and data?

---

### Post by Melcar on 2009-11-07
How did you install the ATI drivers?  Straight from the installer?  If so you need to run the uninstall script:

```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

Once you reboot, the system should load the open source driver on its own.
To remove WINE clean just remove it with Synaptic and delete your .wine folder.

---

### Post by WoAnerges on 2009-11-07
> **Melcar said:**
> How did you install the ATI drivers?  Straight from the installer?  If so you need to run the uninstall script:

```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

Once you reboot, the system should load the open source driver on its own.
To remove WINE clean just remove it with Synaptic and delete your .wine folder.

```
:~$ cd /usr/share/ati
bash: cd: /usr/share/ati: No such file or directory
```
i downloaded installer, than maked ubuntu 9.04 packages and than just ran them.
what to do now?

---

### Post by semitone36 on 2009-11-07
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")

Have fun.

---

### Post by WoAnerges on 2009-11-07
> **semitone36 said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")

Have fun.
my dear friend,
1. there only installation guide i need to clean up.
2. thre only jaunty guide.

guys what to do next? help

---

### Post by semitone36 on 2009-11-07
> **WoAnerges said:**
> my dear friend,
1. there only installation guide i need to clean up.
2. thre only jaunty guide.

guys what to do next? help

1. youll have to try at least a little to use proper english
2. i realize that i gave you a jaunty guide.  youll have to use your judgement and adjust all code lines in the wiki to fit a Karmic install

---

### Post by Melcar on 2009-11-07
If you generated packages just uninstall them with Synaptic.  Do a search for fglrx and remove all the packages named after it (I think there should be 5 or so).

---

### Post by WoAnerges on 2009-11-07
> **semitone36 said:**
> 1. youll have to try at least a little to use proper english
2. i realize that i gave you a jaunty guide.  youll have to use your judgement and adjust all code lines in the wiki to fit a Karmic install

1.akey akey aim sorree may inglish ise no no no vary gud ai knov it. sorree ef theis apset you.

2. ok, but i already tried and after reboot even gui wasn't loading. now i'm affraid that it will happen again :\
can you please help me to fit those codes, you said, with ubuntu 9.10?
---
hmm their page is not loading. perfect! (::

---

