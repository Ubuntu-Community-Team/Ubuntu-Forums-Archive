---
title: "I'm looking to make the top bar transparent"
date: 2022-07-11
forum: Ubuntu, Linux and OS Chat
---

### Post by mikber18 on 2022-07-11
Hi Guys, 

There is one thing that I really want to achieve and not sure how. The Gnome-Shell extension does not seem to work. I'm running Gnome 42.2. 

I'm looking to make this top bar transparent. Ironically I've achieved this effect with the overview view (pressing Super) but not on my default desktop view. 

Please see the screenshots below:

I want the default desktop top bar (i.e. not in overview) to also show a transparent bar and I'm not sure what I need to do to make it happen.

---

### Post by Perfect Storm on 2022-07-11
Probably some .css hacking should do it if the Gnome Team haven't disabled transparency yet.

Try add:

```
#panel {
color: rgba(0, 0, 0, 0.5);
}

```

---

### Post by Dennis N on 2022-07-11
You don't say what your gnome-shell theme is, but the extension "Transparent Top Bar (Adjustable Transparency)" does work with the Yaru gnome-shell themes in Ubuntu 22.04 as well as the "default", so stick with those.

---

### Post by VMC on 2022-07-11
Go here and add the extension then to the top right click "on":
[https://extensions.gnome.org/extension/3960/transparent-top-bar-adjustable-transparency/](https://extensions.gnome.org/extension/3960/transparent-top-bar-adjustable-transparency/)

---

