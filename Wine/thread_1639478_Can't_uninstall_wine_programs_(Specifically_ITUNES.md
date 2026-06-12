---
title: "Can't uninstall wine programs? (Specifically ITUNES!!)"
date: 2010-12-06
forum: Wine
---

### Post by academicboosters on 2010-12-06
Okay, so today, my ipod (which turned on magically after a year !!!:)) was working, so over the summer, i switched to ubuntu. I tried to download itunes on it, but it didn't work, so i tried to uninstall it from the computer, to try it again, but it wont. Also, i have other programs like quicktime player and weird itunes stuff, so please help!
and step by step please, i dont even know how to work this ubuntu linux at all- i don't even know what people mean when they say home/<wine> okay? so please go eassy :D

---

### Post by marl30 on 2010-12-07
First of all, you don't really need to install itune to get your ipod to work with Ubuntu. I don't own an ipod, but I see threads quite often on this forum that said there are apps in the Software Center that will help you to manage your ipod in Ubuntu. I believe RhythmBox also has ipod support. Type ipod in Software Center and check out the softwares that are there. Always try to find good Linux alternatives before trying to install Windows programs. Here's a site to help you find great Linux alternatives for any Windows program you use to use: [http://alternativeto.net/software/?profile=linux](http://alternativeto.net/software/?profile=linux)

To remove hard to remove software from Wine, I always use this free Uninstaller called: Revo uninstaller:[http://download.cnet.com/Revo-Uninstaller/3000-2096_4-10687648.html](http://download.cnet.com/Revo-Uninstaller/3000-2096_4-10687648.html)

---

### Post by Soulcage on 2010-12-07
If you want to return wine back to a fresh install then copy this whole thing ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
``` then run winecfg.

---

