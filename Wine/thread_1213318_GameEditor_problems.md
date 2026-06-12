---
title: "GameEditor problems"
date: 2009-07-14
forum: Wine
---

### Post by Tclarkie on 2009-07-14
Because of exportation limitations on "GameEditor", i was forced to install the windows version of the application, this proved a problem. After installation i booted it and every time it informed me "Not enough memory".
Can anyone help

---

### Post by afroman10496 on 2009-08-01
Can you boot into Grub?

---

### Post by afroman10496 on 2009-08-01
Press the ESC button at the 3-second timeout, and select the current kernel's recovery mode. Then, drop down to the "Drop to root shell prompt" menu, an type:
```
aptitude remove wine
apt-get update
```
That should remove Wine and remove the app that is hogging your memory. Hope it helps! You can re-install Wine, but you might not want to install that program again:D

---

### Post by Tclarkie on 2009-08-01
No, the problem is not ubuntu having enough memory, its wine that doesn't have enough memory

---

### Post by afroman10496 on 2009-08-01
Oh... sorry:D. How much RAM do you have anyway, and how much swap space?

---

### Post by Tclarkie on 2009-08-01
i have 512mb (i know, not much) and this is going to sound really nooby bu i think im missing some icons in system, where do i find my swap

---

### Post by afroman10496 on 2009-08-01
One way to do it is:
```
sudo apt-get install gparted
```and then:
```
sudo gparted
```
Then, look for a reddish square box, and right to it "Linux swap". Then, to the right of that, it will show the disk space for it. The nice thing about it is that you can modify the space with gparted.

---

### Post by NightMKoder on 2009-08-02
That's probably just the wrong error message. What's the terminal output?

---

