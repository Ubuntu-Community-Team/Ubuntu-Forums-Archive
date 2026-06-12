---
title: "Vmware closes host windows on button press"
date: 2008-09-15
forum: Virtualisation
---

### Post by mindfields83 on 2008-09-15
Well this is highly annoying,

I have tried both vmware server 1.0.6 and 1.0.7 on ubuntu 8.04. When the vmware server console is started it's cool. I can open programs on the host. When I boot up a windows xp guest it goes to pot.

It boots fine and works but when I switch back to the host and open any window/program (cmd promt, vlc, calc etc) and press any button the window closes?

I should add thats it's only windows that I open after vmware that close. The ones that were open beforehand accept me pressing buttons.

So basically I can't use any programs that require keyboard input after using vmware, they just close. It doesn't matter if I power off the vm and exit vmware server console. 

The only way stop it happening is to log off and back on.

Anybody any ideas? Or can anybody tell me what log files to check for errors?

Thank You

---

### Post by mindfields83 on 2008-09-16
I've discovered that just booting the virtual machine does not cause this. It's only when I go in and use it then press ctl-alt to come back out it happens.

---

### Post by mindfields83 on 2008-09-16
Found this [http://ubuntuforums.org/showthread.php?t=775563](http://ubuntuforums.org/showthread.php?t=775563)

Don't think I'm going to get an answer

---

### Post by summerspittman on 2008-10-10
Running setxkbmap clears this up for me.  I even have a quicklaunch button for it.

---

### Post by lwb1086y on 2008-10-11
[size=2]Nice topic,up up up.[/size]------------------------------------------------------------------------------------------------------------------------------[img]http://www.qzone.la/img/userup/0808/2GU30U016.jpg[/img]Welcome to our wow power leveling site:[wow power leveling](http://www.wow-powerleveler.com/),[wow powerleveling](http://www.toppowerlevel.net/),cheap [world of warcraft gold](http://www.yoyo-power-leveling.com/buy_wow_gold.php),[world of warcraft powerleveling](http://www.toppowerlevel.net/),[wow gold](http://www.swow-power-leveling.com/buy_wow_gold.php)

---

