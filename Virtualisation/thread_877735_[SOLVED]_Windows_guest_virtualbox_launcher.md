---
title: "[SOLVED] Windows guest virtualbox launcher"
date: 2008-08-02
forum: Virtualisation
---

### Post by methodmarvel on 2008-08-02
I'd like to make a launcher which when I click it my windows xp guest loads up and the "virtualbox ose" window doesn't.

I'd basically like a more direct way to get to this machine.
 
I'm on ubuntu (gnome) if that makes any difference. I know you can right click the panel and select "add to panel" then "custom application launcher" but as for what you fill in the command section I am lost.

**Update**
So I found this site: [http://blogs.tech-recipes.com/shamanstears/2008/02/01/ubuntu-easily-add-desktop-launcher-for-virtualbox-virtual-machine-2/]("http://blogs.tech-recipes.com/shamanstears/2008/02/01/ubuntu-easily-add-desktop-launcher-for-virtualbox-virtual-machine-2/")

which says to use the command:

VBoxManage startvm WindowsXP

and that worked. I had to rename my machine "WindowsXP" rather than "Windows XP" because I couldn't work out the space. I probably only needed to put it in "" now I think about it - but oh well.

---

