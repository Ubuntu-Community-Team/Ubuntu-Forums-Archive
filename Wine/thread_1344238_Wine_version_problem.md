---
title: "Wine version problem"
date: 2009-12-02
forum: Wine
---

### Post by afrodeity on 2009-12-02
Synaptic says I have wine-1.2 installed but winecfg says I have wine1.1.33. This is very weird. I think it has something to do with Wine-doors which downloaded an earlier version of wine for some reason, but for the life of me I can't see how Synaptic is out. I tried reinstalling, but still same version problem.

---

### Post by 8Kuula on 2009-12-02
[http://wiki.winehq.org/WineReleaseCriteria](http://wiki.winehq.org/WineReleaseCriteria)
> 
Branching

Wine now uses a stable/unstable branch model. Even-numbered releases (eg 1.0.x) will be stable, with only minimal changes merged in. Development will continue on the 1.1.x branch until we stabilize it for the 1.2.0 release, after which 1.3 will become the new development branch. When asked whether the 1.1.x branch can be considered "alpha" or "beta", Alexandre responded that it is the "development branch" -- for end user purposes, this means alpha (and thus prone to regressions) until we freeze for 1.2.

---

### Post by afrodeity on 2009-12-02
So the fix would be to remove the wine ppa. The 1.2 version would be in the ubuntu repo, and I've gone and installed directly from the wine repo. Thanks for reminding me.:)

---

### Post by 8Kuula on 2009-12-02
You can have wine's own repo still, I think new development version is faster there than in ubuntu repo, but its only a feeling :)

---

### Post by afrodeity on 2009-12-03
Guess it is faster. But there's an app (Digital Space Traveller ) that won't start-up in this version. Keeps saying "unable to load olsdk2.dll". I've tried making this dll native, also tried downloading a fresh one but no go.

UPDATE: Recently tried to run this programme again in Wine 1.3.7 but still crashes, if posted the error output [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=21871&iTestingId=58526")

```

wine traveler.exe 
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub! 
fixme:storage:create_storagefile Storage share mode not implemented. 
err:heap:GlobalFree (0x82): Page fault occurred ! Caused by bug ? 
```

---

