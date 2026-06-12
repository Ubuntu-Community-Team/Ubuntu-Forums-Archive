---
title: "Less colorfull Quick settings panel"
date: 2024-09-16
forum: Ubuntu, Linux and OS Chat
---

### Post by hever2 on 2024-09-16
Hi, I upgraded to Ubuntu 24.04 with Gnome 46. Everything is great, but I really dont like new quick settings menu. For my eye it is too much colorfull. I only needed to change this and leave everything else as it is. But I couldn't find any ready-made way to do this, so I made my own. Simple way.

Before:
[IMG]https://hev.cz/up/gnome-46-quick-settings-default.png[/IMG]

After:
[IMG]https://hev.cz/up/gnome-46-quick-settings-modify.png[/IMG]

How to:
1. Install extension [https://extensions.gnome.org/extension/3414/user-stylesheet-font/](https://extensions.gnome.org/extension/3414/user-stylesheet-font/)

2. And put into ~/.config/gnome-shell/gnome-shell.css:
```

.quick-toggle-arrow:checked, .quick-toggle:checked {
  background-color:#c8c8c8;
  color: #3D3D3D; }
.quick-toggle-arrow:checked:hover, .quick-toggle:checked:hover {
  background-color:#aaaaaa; }
.quick-menu-toggle .quick-toggle-arrow:checked {
  border-color: #999999; }
.quick-toggle, .quick-menu-toggle {
  border-radius: 8px; }
.quick-menu-toggle .quick-toggle:ltr {
  border-radius: 8px 0 0 8px; }
.quick-menu-toggle .quick-toggle-arrow:ltr {
   border-radius: 0 8px 8px 0; }
.quick-menu-toggle .quick-toggle:ltr:last-child {
  border-radius: 8px; }

```

---

