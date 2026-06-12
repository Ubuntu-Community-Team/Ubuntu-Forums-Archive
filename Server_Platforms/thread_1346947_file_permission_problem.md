---
title: "file permission problem"
date: 2009-12-05
forum: Server Platforms
---

### Post by GradaL on 2009-12-05
Hi,

I am using 9.10. I changed the file permission of all filesystem to 755 and ownership to root for some stupid reason. The code was


sudo chown -R root /
sudo chmod -R 755 /


I didn't backup, and now, i need to reset the file permissions. Is there any short way to do this exept to fix all file one by one?

Thanks..

---

### Post by brettg on 2009-12-05
Normally, I would not bother with a "I don't know how to do that" post, but in this case there have been quite a few views and no answers.

As far as I know, there is no way to easily fix what you have done.

You have two options as far as I can tell. 

1) Manually change everything back 

or 

2) Backup all your user data and config files and then reinstall.

Sorry

---

### Post by BkkBonanza on 2009-12-06
Wow. What a nightmare!

I can think of various convoluted ways you may fix this involving a second install and copying permissions but really nothing is going to work as well as a re-install. Hopefully you don't have too much customization.

Next time you feel the urge to get wild and crazy with commands like this I'd suggest installing VirtualBox and creating a guest OS that you can play in with no danger of nuking your main desktop. [www.virtualbox.org](www.virtualbox.org)

With a guest OS under VBox you can use snapshotting to revert to a saved state, or you can just delete the test system and start again.

---

