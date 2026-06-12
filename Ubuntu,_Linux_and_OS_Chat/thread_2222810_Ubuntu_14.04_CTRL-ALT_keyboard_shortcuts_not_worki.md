---
title: "Ubuntu 14.04 CTRL-ALT keyboard shortcuts not working (again)"
date: 2014-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by ele2 on 2014-05-08
Hi,

i installed Ubuntu 14.04 in VirtualBox. I have Qt Creator installed. I cannot use the Ctrl-Alt-Up and Ctrl-Alt-Down shortcuts (nothing happens). I know that the keyboard management really sucks in Ubuntu since the competing management tools (e.g. [COLOR=#000000]ccsm,[/COLOR][COLOR=#000000] gconf-editor,[/COLOR][COLOR=#000000] system settings, unity-tweak-tool etc etc.) [/COLOR]all override each other and it is a big mess. 

I remember having the same issue in 10.04 or 11.04. Is there a uberglobal setting that would override all the rest? Where to begin finding out who is eating up my keyboard shortcut?

Regards

---

### Post by russomarco on 2014-05-20
[COLOR=#333333][FONT=monospace]Try upgrading Gnome by adding the official gnome3 ppa:
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update && sudo apt-get dist-upgrade

```
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]Reboot and check if it works.[/FONT][/COLOR]

---

