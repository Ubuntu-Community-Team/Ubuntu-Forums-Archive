---
title: "OS UI (themes, icons, Cerebere process) set and stuck to default, cannot be changed"
date: 2015-06-10
forum: Ubuntu/Debian BASED
---

### Post by Jrme_B on 2015-06-10
Hi there,

This is my first post, most often I manage to find the solutions of my linux problems but this time I cannot figure it out.

I use Elementary OS 0.3 Freya and I have messed up something, breaking the OS UI behavior. Here are the list of things that don't work anymore (non exhaustive):

- Wallpaper is the elementaryos-default.jpg from /usr/share/backgrounds/ and cannot be changed
- Metacity and GTK themes as well as Icons are default and cannot be changed
- List of process launched at startup with Cerbere (elementary-tweaks) is resetted to default everytime and cannot be changed (all my custom plank docks are gone)
- Nothing can be done to change them. The config files are correctly set up as well as dconf entries, but it's like the OS only wants to use default configuration.

I'm quite a newbie in Linux so I have no clue how to fix that. I don't know what caused that since I've made several modifications before rebooting and getting this issue. It could be new installed packages, maybe activating the numlock at startup with numlockx, maybe a bug with wine which changed the screen resolution before I rebooted. I really don't know.

I would be very grateful if you can help me on this one. Tell me what additionnal informations I can give you.
Thank you very much.

---

### Post by Jrme_B on 2015-06-11
Fixed !

With a little search I found out the solution. 

By trying to apply a theme with terminal I got this message "Using the 'memory' GSettings backend. Your settings will not be saved or shared with other applications."

Then I found the solution here : [https://askubuntu.com/questions/558446/my-dconf-gsettings-installation-is-broken-how-can-i-fix-it-without-ubuntu-reins](https://askubuntu.com/questions/558446/my-dconf-gsettings-installation-is-broken-how-can-i-fix-it-without-ubuntu-reins)
I also resintalled dconf and dconf-tools.

Good to have my Linux back. See you guys !

---

