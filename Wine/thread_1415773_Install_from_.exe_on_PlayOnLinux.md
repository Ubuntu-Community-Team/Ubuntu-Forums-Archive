---
title: "Install from .exe on PlayOnLinux"
date: 2010-02-25
forum: Wine
---

### Post by Kdar on 2010-02-25
I have .exe of one game (trying to install Runes of Magic) and would prefer if I could use that instead of letting PlayOnLinux download it for me (especially since it downloads older version.

Anyone know how I can run .exe on PlayOnLinux?

---

### Post by Kdar on 2010-03-05
Hello?

---

### Post by Bwathke on 2010-03-05
You cannot run a .exe with PlayOnLinux (From what Ive heard) And remember PlayOnLinux uses WINE directly and it wont fix any problems that WINE has (Again from what Ive heard). 

If the game is giving you trouble...

1. Patch WINE to the latest version
2. Run the game in -opengl
3. (Last resort) Run it in Windows partition
Please PM me if you have any problems I run this game using WINE pretty well.

---

### Post by Toffeeapple on 2010-03-06
From the Playonlinux window click on "install" then at the bottom click on "install a .pol package or an unsupported application" then on "manual install" then on "Forward" and from there it should be self explanatory.

Hope that helps

---

### Post by exclinux on 2010-05-17
> **Bwathke said:**
> You cannot run a .exe with PlayOnLinux (From what Ive heard) And remember PlayOnLinux uses WINE directly and it wont fix any problems that WINE has (Again from what Ive heard). 

If the game is giving you trouble...

1. Patch WINE to the latest version
2. Run the game in -opengl
3. (Last resort) Run it in Windows partition
Please PM me if you have any problems I run this game using WINE pretty well.

How to run the game in -opengl...??

---

### Post by Toffeeapple on 2010-05-18
Generally it would be like this..

```
wine PathToWhatEverItIsYouAreTryingToRun/App.exe -opengl
```

But then that would depend on weather that particular app was aware of that switch, I believe WOW is for example.

What are you trying to run?

---

