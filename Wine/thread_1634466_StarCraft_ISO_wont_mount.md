---
title: "StarCraft ISO wont mount"
date: 2010-11-30
forum: Wine
---

### Post by budman10 on 2010-11-30
New to Linux. I have searched around and found how to install SC on linux but I cannot even get to that point. I have tried to mount the image with Fusion, Gmount and the native mounter that came with Ubuntu. Every time I go to the folder where it is mounted it is empty. Any tips?

---

### Post by NightwishFan on 2010-11-30
Ensure you use a blank folder to mount to. You can test if the .iso will mount using this command:
```
sudo mount -o loop -t iso9660 **/path/to/iso** **/path/to/mountpoint**
```

Replace the bold text with the required information.


To be honest, I am not sure why gmount-iso does not work for you. It works fine here.

---

### Post by budman10 on 2010-11-30
found the answer....

[URL="http://ubuntuforums.org/showthread.php?t=1392169&page=2"]http://ubuntuforums.org/showpost.php?p=9819185&postcount=15
[/URL]

---

### Post by budman10 on 2010-12-01
So I have another issue. I cannot get my saved games to show up. I have even tried loading after starting a game and it completely freezes and crashes. I have only found two instances when it crashes, if I hit single player on the main menu screen or if I try to load a game mid game (when i hit load button it crashes). I have the game mounted. If you need anymore info let me know, but this is god awful annoying.

---

### Post by NightwishFan on 2010-12-02
Hmm, seems like you are having way more issues than is normal. To be honest I am not a Wine dev and the only answer I can give you is try a different version of wine. Wine 1.0 usually works best, and is in the repositories.

---

### Post by budman10 on 2010-12-02
Right now I am using 1.3.7 I tried an uninstall also, same problem. Are you running SC2 on Wine 1.0 no problems?
 
 I notice the post got moved from the gaming forum to here, my bad on wrong forum.

---

### Post by NightwishFan on 2010-12-02
You meant Starcraft 2? I have no experience with that my apologies. I am certain you should probably use Wine 1.2 at the least. Also, Sc1 you are allowed to play without the cd, though SC2 I doubt it. It will probably work better with the packaged DVD.

Check here as well:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

---

### Post by budman10 on 2010-12-02
No worries man.

For others:

How can I permanently mount the image? If I shut down or restart the file where I mounted it to is empty. I have read that people have got it running successfully. When I play i disconnect from the Internet. I cant find anyone that has this problem. Maybe this thread will get more response in video game forum?

---

### Post by NightwishFan on 2010-12-02
No, wine forum is the correct place. I hope you get some attention to the problem. I only use SC1.

---

### Post by budman10 on 2010-12-02
Do you think its wine or something with my mounting issue. I have to remount everytime I restart or boot. The mount folder is empty.

---

### Post by NightwishFan on 2010-12-02
That's the default behaviour. You might have to add a line to /etc/fstab to mount it on every boot. It seems a bit out of the way to be honest. I am not entire sure how you could do this, certainly it needs to be mounted as a loop device.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by budman10 on 2010-12-02
how do i change the title of post

---

### Post by budman10 on 2010-12-06
bump

---

### Post by budman10 on 2010-12-17
Has anyone else tried to play starcraft 2 from an ISO and had this problem?

---

### Post by tgm4883 on 2010-12-17
> **budman10 said:**
> how do i change the title of post

You edit the first post. I'm not sure if it will allow you to still do that since it's been so long.

---

