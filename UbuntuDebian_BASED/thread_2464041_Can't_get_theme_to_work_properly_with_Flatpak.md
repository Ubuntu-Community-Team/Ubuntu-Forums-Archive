---
title: "Can't get theme to work properly with Flatpak"
date: 2021-06-23
forum: Ubuntu/Debian BASED
---

### Post by sithlord366 on 2021-06-23
Hi, I'm running Pop!_OS 20.04, but this question should go for Ubuntu as well. 

I installed the [Dracula theme]("https://github.com/dracula/gtk") on my system, and since there is not a Flathub package for it, all Flatpak applications default to Adwaita. I somewhat managed to get around this by creating a Flatpak theme for Dracula by using a tool called [pakitheme]("https://github.com/refi64/pakitheme"). However, another problem arose where the close, minimize, and maximize buttons would not render. You could still click them, but they would appear invisible. Do you know of a solution to this problem? I think it has something to do with the animation that happens when the cursor hovers over the buttons. It could be calling some other part of the system for the animations and rendering, but I'm not sure.

Thanks for reading,

SithLord366

---

### Post by QIII on 2021-06-23
Moved to **Ubuntu/Debian BASED**

---

### Post by sithlord366 on 2021-06-24
I figured it out. I added a flatpak override to ~/.themes with this command:

```
sudo flatpak override --filesystem=~/.themes
```

Although I don't think it's the ideal solution, it does serve its purpose. There are still some flatpaks that still don't use the theme, but those aren't as important.

---

