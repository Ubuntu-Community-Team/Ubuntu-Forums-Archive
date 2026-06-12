---
title: "Virtualbox seamless mode not covering all screen"
date: 2010-10-22
forum: Virtualisation
---

### Post by woodyg on 2010-10-22
I've installed virtualbox on my Ubuntu in order to run Windows 7. Everything runs perfect, except one annoying thing... when in seamless mode **the "virtual screen area" doesn't extend all the way to the right hand edge**. There is a small gap, 4-5mm wide, between the edge of any Windows application and the edge of the entire screen. So it is very easy when using the scroll bar for a Windows application, to miss the scroll bar and place the cursor in that gap... and accidentally return to Ubuntu.

How to solve?

---

### Post by JKyleOKC on 2010-10-22
There's a significant difference between the "seamless" and "full screen" modes. Seamless puts the active guest window onto the host desktop so that you can still see other windows on the host, while full screen replaces the host desktop with that of the guest. It sounds as if you are using seamless but expecting the full screen action.

Personally I've found both of these modes to be less easy to work with than simply running vbox as another window on the host desktop, and sizing it to occupy most but not all of the area. This leaves the "Machine" and "Device" menu choices available (they vanish when in either seamless or full screen mode unless you enable the mini-toolbar) while still providing enough real estate in the guest...

---

### Post by woodyg on 2010-10-22
thanks for the reply, but I think you misunderstood the problem. I am aware that the "virtual" screen is not going to go all the way to the top or the bottom. It does however cover the entire screen to the left, but to the right there is a small gap that is just big enough for you to sometimes click on by mistake, rather than the scrollbar you intended.

Have a look at the attached screenshot. The top arrow point at the red close-button in a windows application. It is not positioned at the very right. There is a small gap. The arrow below points at the scroll bar from an Ubuntu application that is positioned below the "virtual" window, which one can just about see because of the gap.

---

### Post by woodyg on 2010-12-30
bump

---

### Post by sokekoke on 2011-01-10
Same problem. Bump (:

---

### Post by tij on 2011-11-25
Having the same problem. Any luck with this?

---

### Post by woodyg on 2011-11-25
> **tij said:**
> Having the same problem. Any luck with this?

I think the problem disappeared after my installation of 11.04, and no sign of it since. Which versions of Ubuntu and Virtualbox are you using? (I'm on 11.10 and 4.1.2-dfsg-1ubuntu1)

---

