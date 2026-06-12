---
title: "command history (alt+f2"
date: 2017-06-09
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-06-09
Why does gnome-shell keep a history of commands run in the alt+f2 prompt if it provides no means to access those commands from the prompt?

---

### Post by P-I H on 2017-06-10
I think there is a problem with this feature. I checked if there was any information in syslog, after using the feature. Command without sudo e.g "inxi -F",  "sensors" and "uname -r" provides the output in syslog. 
However commands that start an application like "gnome-terminal" and "synaptic" works as expected.

---

### Post by mc4man on 2017-06-15
Actually the alt+f2 command in gnome-shell is just terrible compared to unity's. No history, 'suggested results' based on characters typed or icons associated.
So for someone who uses the run command a lot having to always retype the full command every time isn't suitable at all.

(- the gnome-shell history, (dconf) is also a bit of a joke as it saves each command, so if you type XXX 10 times it saves XXX ten times. Whether there is some time-based or otherwise culling haven't bothered to see. If not then the history could get very large & even more worthless.
Seems designed to at least allow running a command but to discourage using.

---

### Post by robin217 on 2018-04-13
This Gnome Extension adds prefix search to the GNOME Shell Run Command dialog (Alt-F2)

[[COLOR=#1155cc][FONT=Calibri]_[https://github.com/sustmi/gnome-shell-extension-historymanager-prefix-search](https://github.com/sustmi/gnome-shell-extension-historymanager-prefix-search)_[/FONT][/COLOR]]("https://github.com/sustmi/gnome-shell-extension-historymanager-prefix-search")

[COLOR=#000000][FONT=Calibri]Its available at Gnome Extensions:[/FONT][/COLOR]
[[COLOR=#1155cc][FONT=Calibri]_[https://extensions.gnome.org/extension/544/historymanager-prefix-search/](https://extensions.gnome.org/extension/544/historymanager-prefix-search/)_[/FONT][/COLOR]]("https://extensions.gnome.org/extension/544/historymanager-prefix-search/")


I works with Page Up and Page Down keys. I'd prefer if it worked with UP and DOWN arrow keys instead, but not bad.

---

### Post by mc4man on 2018-04-21
No need for an extension, seems to have been recently fixed or added to gnome-shell

---

