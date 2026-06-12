---
title: "Precise won't start with wallpaper in sub-folder in Pictures"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by madeinfamous on 2012-04-16
#ubuntu #precisepangolin #beta2 #unitygreeter #bug

imagine we have an image in an folder located in the Downloads folder and we select it as a wallpaper on our pc. Then we move this folder to the Pictures folder, and finally, we restart the pc.

When we return to the login screen, unity-greeter can not find the picture, and when we enter our password... we are screwed, we wait long for nothing since it will not open our session!

I needed to "ctrl / alt F1" to move the file to its original place to remedy the situation and then "ctrl / alt F7" to finally see how I'm smart!

I have no idea how to list this bug, so I rely on you to do so! thank you!

&#12471;

---

### Post by cariboo on 2012-04-16
This doesn't follow the criteria of the folder it was in. Moved to a thread of it's own.

---

### Post by alphacrucis2 on 2012-04-16
> **madeinfamous said:**
> #ubuntu #precisepangolin #beta2 #unitygreeter #bug

imagine we have an image in an folder located in the Downloads folder and we select it as a wallpaper on our pc. Then we move this folder to the Pictures folder, and finally, we restart the pc.

When we return to the login screen, unity-greeter can not find the picture, and when we enter our password... we are screwed, we wait long for nothing since it will not open our session!

I needed to "ctrl / alt F1" to move the file to its original place to remedy the situation and then "ctrl / alt F7" to finally see how I'm smart!

I have no idea how to list this bug, so I rely on you to do so! thank you!

&#12471;

I guess the sensible thing would be for it to just display a uniform colour if the wallpaper cannot be found. ```
ubuntu-bug unity-greeter
``` would be the deal.

---

### Post by mc4man on 2012-04-16
If I do that the greeter uses the default warty & the desktop is a solid color. No hang up at all

---

### Post by alphacrucis2 on 2012-04-16
> **Isabel57 said:**
> [IMG]http://www.infoocean.info/avatar3.jpg[/IMG]I have no idea how to list this bug, so I rely on you to do so! thank you!

There is no point us reporting it as we can't reproduce your issue. It must be something specific to your configuration. If you report it yourself using the command I gave then apport should collect the relevant information.

---

