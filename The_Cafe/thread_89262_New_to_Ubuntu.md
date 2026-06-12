---
title: "New to Ubuntu"
date: 2005-11-12
forum: The Cafe
---

### Post by Chandu on 2005-11-12
Hi All,

First of all I would like to congratulate the Ubuntu team for getting their first certification from IBM DB2.

I am new to Ubuntu.

Just got my CDs yesterday. Planning to install this weekend.

Can I install it on an existing partition. The writeup on CD says that, by default it wipes all data on disk, however there is a manual install procedure also availble.

Someone guide me in... I have Windows XP installed on my machine and all my partitions have some data but having free space of arounf 5 GB. Can I utilize the existing partition or I need to create a different...

Thanks
Chandu

---

### Post by Haegin on 2005-11-12
You will need sperate partitions for windows and ubuntu but as far as I know you can install ubuntu on 5GB. You can do this from within the installer but the partitioning tool isn't the greatest available and you should definatly take care. It isnt a step where you can go back and change it later if it goes wrong and you could end up losing Windows (hmm... now I would say thats a good thing :))

Be careful and it will be fine. You will also want to check out the dual boot howto on the wiki ([https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)) (You can ignore the "you need at least 10 GB", its best to have about that much (or more) but by no means neccessary - my sister was running hoary on a 4Gb hard drive perfectly happily (normal install - nothing special or odd))

As I said, be careful and if you need more help just ask.

---

### Post by Chandu on 2005-11-13
Thanks for the info.

I have successfully installed the Ubuntu on my Windows XP machine and both are working fine.

I have choose the 'expert' option at the startup and done the installation.

The only problem I am getting in with the GUI the 'X' is not starting. It didn't ask me to choose the graphics adapter while installing, I think it proceeded with some default config and the X Server is not starting.

Can you guide me how to change the Adapter configuration so that I will be able to use the GUI.

-Chandu

---

### Post by quietglow on 2005-11-13
To rerun the xorg config utility you'll want to

```
sudo dpkg-reconfigure xserver-xorg
```

If you want to back up your config file when doing this (don't know why in this case, but if you want to tweak once its working) 

```
cp /etc/X11/xorg.conf /etc/X11/xorg.confbackup
```

Good luck! You're almost there!

---

