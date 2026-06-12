---
title: "Dual Boot games on Steam"
date: 2011-03-26
forum: Wine
---

### Post by ColourblindKid on 2011-03-26
Hi, I am currently dual-booting windows vista and ubuntu 10.04, ubuntu is the OS I usually use but Windows still has all of my games on it.

Personally I hate windows, so I downloaded Steam through Wine to try and play the two games I have on it, Medieval II Total War and the Kingdoms expansion pack. I found this page:
[http://developer.valvesoftware.com/wiki/Steam_under_Linux#Save_space_on_dual-boot_machines](http://developer.valvesoftware.com/wiki/Steam_under_Linux#Save_space_on_dual-boot_machines) and was wondering if this would be a good idea as the games take up a lot of space.

However, I tried putting that in the terminal but the second line returned the error message 
> mv: cannot stat `steamapps': No such file or directory
I looked up 'steamapps.bak' and found it was just a folder. Does anyone have any suggestions on where I should go from here?

Thanks in advance and please forgive my lack of technical knowledge

---

### Post by cogadh on 2011-03-26
The steamapps directory is only created when you install games, so if you haven't installed any Steam games within Wine, you are going to get that error. You can ignore it and move on to the rest of it.

---

