---
title: "Server install with vbox but no mouse"
date: 2009-04-09
forum: Server Platforms
---

### Post by rikhard.fsoss on 2009-04-09
hi all,

i have done a  lot of search first, but i was unable to find a solution for my problem

i'm studying GNU/Linux so, i installed a minimal and now a server ubuntu 8.10 using virtualbox last release (sun not ose) everything goes fine.

the cli install is ok, i play with the system, but now i want to install xorg and fluxbox so that i can have more xterm's to play with.

i do an $sudo -s

#apt-get install xorg fluxbox xterm

evrything goes well, but than i startx, x runs but i can't have my mouse working

the xorg.conf is clean when i install xorg, there is this file but empty, x runs but without mouse working

then i do #dpkg-reconfigure -plow xserver-xorg

but the config tool does not question about videocard, resolution, mouse, only keyboard.

am i doing something wrong?

thanks in advance

rj

---

