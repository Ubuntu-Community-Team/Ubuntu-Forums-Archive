---
title: "Yet Another VirtualBox Question...."
date: 2008-03-01
forum: Virtualisation
---

### Post by Recked on 2008-03-01
Hello,

I just downloaded the 64 bit version to install on my machine and it installed fine and I see myself being added to the proper group etc. but when I try to start the virtual machine I get the attached error.

New to VirtualBox so my apologies if this is something simple or has been asked over and over again.

thank you

---

### Post by cszikszoy on 2008-03-03
What happens when you try?
```
sudo -u [your_user_name] VirtualBox
```
ie: I would use
```
sudo -u chris VirtualBox
```

If that fixes the problem go back to the users and groups window, scroll down the the vboxusers group and check the box next to your name.

---

