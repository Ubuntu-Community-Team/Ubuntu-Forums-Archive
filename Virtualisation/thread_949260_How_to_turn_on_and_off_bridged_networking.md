---
title: "How to turn on and off bridged networking?"
date: 2008-10-16
forum: Virtualisation
---

### Post by winrowc on 2008-10-16
I have Virtualbox working great with virtual networking, but unfortunatly it doesnt remain under restart,and I can't use my host computers networking even with wifi which is a different card. This means that everytime I want to use my virtual machine with the internet, I need to type in 8 lines in the terminal which is tiring (sudo tunctl -t tap1 -u .... sudo chmod 0666 /dev/net/tun) Then when i turn off my virtualmachine, my host machine naturally still has the networking bridged, so I need to restart my machine to get internet back. Is there a way to make this more seemless? Id rather not have to enter in 8 lines in the terminal every time I want to just turn on my virtualbox's internet, and restart everytime I want to switch it back.

---

### Post by b0b138 on 2008-10-16
Not sure which 8 lines your using, as I've seen a few that are slightly different, but get the same result.

Check out this page [http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/](http://spinczyk.net/blog/2008/03/05/setting-up-a-bridged-network-for-virtualbox-on-ubuntu-linux/)

It shows to setup (in its way) your 8 lines to get the host networking in a script that you save. This way, all you have to do is run that script, and its setup. You could also just put the commands you are currently using in a script and use that. I'm not sure why you have to reboot to get your internet back, haven't had that problem.

You will also have the option once you get a working script, to have it run at system boot, that way the bridging is always setup.

---

### Post by winrowc on 2008-10-19
Thanks the script worked perfectly.

---

