---
title: "WoW permission troubles"
date: 2010-03-08
forum: Wine
---

### Post by Sparkfist on 2010-03-08
Hello,

I'm trying to get World of Warcraft setup on my desktop. I've got it installed, and can get the launcher to come up no problem. But when I try to run the game to test things out it always crashes, because the folder in the wine "Programs Files" keeps going back to an access denied status.

I've tried changing permissions with;

```
 sudo chmod 775 /home/kohler/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
```

as well;

```
 sudo chown kohler /home/kohler/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
```

But neither has worked.

Could someone please tell me what I'm not doing or am doing wrong. Thank you.

-Nick

P.S.I have everything else, graphics drives installed, WoW client up-to-date, ect. The only thing not done is the setting in config.wtf for opengl.

---

### Post by [Shadow] on 2010-03-08
When you use sudo chmod you are changing permissions for the World of Warcraft folder but not the files or folders under that.

Try using the recursive operator -R in that statement to also change the permissions of the subfolders and files as well

Ex.

sudo chown kohler /home/kohler/.wine/drive_c/Program\ Files/World\ of\ Warcraft/ -R
Hope that works!

---

### Post by Sparkfist on 2010-03-08
Just tried it, and doesn't make any difference. Every time I start the launcher it locks the World of Warcraft directory. I went even so far as to change owner of everything under /.wine/ to kohler and still it doesn't want to play nice.

Any other ideas?

-Nick

---

### Post by [Shadow] on 2010-03-08
hmm that is strange. Have you tried running the launcher as root?

You can either use 

```
su 
```or 
```
sudo
```

---

### Post by Sparkfist on 2010-03-08
I tried sudo and still the same. When I used the su command to be root I get an error message saying "You are not the owner", and for some reason shortly after I can't login via the console to root. Every time I type "su" or "su -" I get an "Authentication failed" message.

-Nick

---

### Post by [Shadow] on 2010-03-08
Strange... the only other thing i can think of on hand would be to change the permissions to be for everyone to access.

```
sudo chown 777 /home/kohler/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
```

other than that i really dont know =(

---

### Post by [Shadow] on 2010-03-08
Found a helpful thread where a guy had the same problem

[http://ubuntuforums.org/showthread.php?t=1343520&highlight=WoW+permissions+wine](http://ubuntuforums.org/showthread.php?t=1343520&highlight=WoW+permissions+wine)

---

### Post by Sparkfist on 2010-03-11
I'm starting to think that the problem is more to do with Wine then with WoW. I checked out the thread and tried what they had in there, that I hadn't tried yet. Unfortunately no fix. I even tried running WoW from a copy I have saved on an external hard drive, copied from a Windows install. Same problem.

The odd thing is my monitor goes blank... actually no signal at all when WoW starts. But I am still able to make my system go into a restart by hitting ctrl, alt & delete.

If anyone has any knowledge about nVidia graphics cards, I think that might be what's wrong.

-Nick

---

### Post by [Shadow] on 2010-03-11
After Searching Around I stumbled upon these

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

Theyre written for older versions but maybe one will be useful.

:-|

---

