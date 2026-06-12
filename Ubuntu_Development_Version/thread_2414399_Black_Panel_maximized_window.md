---
title: "Black Panel maximized window"
date: 2019-03-09
forum: Ubuntu Development Version
---

### Post by paulycalvin on 2019-03-09
I have noticed that the transition from transparent Top Bar to black Top Bar when a window is maximized is not working. Is this functionality being removed? I really prefer it.

---

### Post by paulycalvin on 2019-03-09
This is the piece of code I am talking about. From the shell theme and the Top bar. It doesn't work anymore?

/* TOP BAR */
#panel {
  background-color: transparent;
    /* transition from solid to transparent */
  transition-duration: 250ms;

---

### Post by MyMurry on 2019-03-10
I have the same issue. Also the extension pixelsaver dosen't work.

---

### Post by dino99 on 2019-03-10
The 'extensions' are not yet ready for GS 3.32, and so does not work as expected, or simply fail; except ubuntu-dock recently upgraded.

I am waiting for system-monitor for example. :(

---

### Post by paulycalvin on 2019-03-10
Well the transition to a black top bar from transparent when a window is maximized is not an extension. I hope this is just a bug and not removed functionality.

---

### Post by mc4man on 2019-03-11
From what I remember Gnome is getting rid of the [translucent  panel]("https://gitlab.gnome.org/GNOME/gnome-shell/merge_requests/376") altogether. 
What Ubuntu's plans are concerning this I've no idea, maybe you're seeing what now or maybe not..

---

### Post by paulycalvin on 2019-03-11
Yes that is my fear. I downloaded the latest gnome-shell default theme and I examined the code and I believe it has been removed. Still hoping this will be solved in Ubuntu.

---

### Post by mc4man on 2019-03-13
By now you should see the end result, both the panel and ubuntu's launcher a solid color.

---

### Post by paulycalvin on 2019-03-13
Yes now that the default themes don't use transparency the transition isn't necessary. So it's a loss of functionality for 3rd party themes. For now I am using hide top bar until I can find a solution.

---

### Post by paulycalvin on 2019-03-13
If you are using a theme that has transparency. It looks like crap when you have a window maximized and you have this transparent space at the top of the screen or bottom for that matter. I liked it when the theme transitioned to an opaque panel when windows were maximized.

---

