---
title: "Grub Startup Manger not working in 11.04"
date: 2011-05-16
forum: Ubuntu Studio
---

### Post by jflesher on 2011-05-16
This is a fresh install of Ubuntu Studio 11.04, I installed startupmanager
sudo aptitude install -y startupmanager

I've done the update 
sudo update-grub2
not sure it matters if I do it this way
sudo update-grub
seems to be a link to grub-mkconfig

# grub-install -v
grub-install (GRUB) 1.99~rc1-13ubuntu3

Yet on reboot; the menu is updated, but does not pick the right boot up item; that is, I chose a different version to boot up; and it doesn't even show in the new menu; which is what I think the problem is; it show previous version; which then hides the actual version I want to run; this idea of hiding previous versions may sound like a good idea, and it might be a good idea normally; but in my case its a bad idea.

My question is, is there a way to turn off this new feature?

---

