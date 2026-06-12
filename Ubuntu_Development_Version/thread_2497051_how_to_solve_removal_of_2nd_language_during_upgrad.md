---
title: "how to solve removal of 2nd language during upgrade"
date: 2024-04-21
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-04-21
Hello,

today I attempted an upgrade from 23.10 to 24.04d. One of the things I noticed is that the hellenic (greek) language was completely removed from my system meaning that I couldn't switch to it, yet under settings->keyboard->input sources it was there. I removed it and add it back again and things are working as normal.

In the meantime in order to restore the Alt+Shift keystroke language change instead of using Super+Space I had to issue the commands:
```
gsettings set org.gnome.desktop.wm.keybindings switch-input-source "['<Shift>Alt_L']"
gsettings set org.gnome.desktop.wm.keybindings switch-input-source-backward "['<Alt>Shift_L']"
```

Regards!

---

### Post by jbicha on 2024-04-21
Could you file a bug about the translation removal issue? That sounds very unexpected.

For the keyboard shortcuts, open Settings > Keyboard > View and Customize Shortcuts. You can search in this popup window, but the settings you want are in the Typing category.

---

### Post by Claus7 on 2024-04-22
Hello,

> **jbicha said:**
> Could you file a bug about the translation removal issue? That sounds very unexpected.

I have it here: [https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-el/+bug/2063138](https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-el/+bug/2063138)

> **jbicha said:**
> 
For the keyboard shortcuts, open Settings > Keyboard > View and Customize Shortcuts. You can search in this popup window, but the settings you want are in the Typing category.

Thank you for your suggestion, alas this is not working: indeed in order to add a keyboard shortcut in order to switch input sources (languages) is to use the Super key combined only with other ones. Yet I cannot add any other shortcut, since it is not recognized. Only issuing the command above adds another shortcut that does't use the super key. This isn't noble specific though. I do not remember exactly the time it has appeared.

Regards!

---

### Post by jbicha on 2024-04-22
There is another way then.

GNOME Tweaks app > Keyboard > Additional Layout Options > Switching to another layout

---

### Post by Claus7 on 2024-04-22
Hello,

> **jbicha said:**
> There is another way then.

GNOME Tweaks app > Keyboard > Additional Layout Options > Switching to another layout

thank you for that as well, yet it is not working. At least it stopped working some time ago: [https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1967563](https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1967563)

The only way I have figured out to make it work and switch between languages is the way mentioned above with the aforementioned commands.

Regards!

---

### Post by Claus7 on 2024-07-10
Hello,

just to add that doing the above, the switch is working fine, yet it is somehow slow. There is an extension that accelerates the switching of langues which is this one:
[https://extensions.gnome.org/extension/4559/quick-lang-switch/](https://extensions.gnome.org/extension/4559/quick-lang-switch/)

Regards!

---

