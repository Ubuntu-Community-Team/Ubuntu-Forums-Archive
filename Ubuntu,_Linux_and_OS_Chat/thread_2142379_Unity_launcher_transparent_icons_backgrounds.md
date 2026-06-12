---
title: "Unity launcher transparent icons backgrounds"
date: 2013-05-05
forum: Ubuntu, Linux and OS Chat
---

### Post by Elline on 2013-05-05
I've created a pack that removes a background frame of each icon, making Unity launcher icons clean, as you can see in the picture. It also alternates the Unity button to look like mobile version. If somebody will be interested, I can put a version with default icon in it.

Here's how it looks like with Faenza:

[IMG]http://ubuntuone.com/7PSb4Z7P2CjLmYFsfG6vZn[/IMG]

**[Download link]("http://ubuntuone.com/2kK0vQRRvaQ389aaqHiY7e")**

[B]Instructions:
[/B]This directions was written for Ubuntu 12.04, and tested only with it. It most probably should work with other versions, too, but please create a backup anyway.

If you have another version of Ubuntu you may have another version of Unity, so the folder number in following instructions will be different. You can see which folder you have by looking in "/usr/share/unity/", in my case it contains folder "5". Substitute your number in the folloving directions.[INDENT]1. Open your file manager as root (gksu nautilus)[/INDENT]
[INDENT]2. Go to /usr/share/unity/ and create a backup of directory "5"[/INDENT]
[INDENT]3. Extract the archive UnityCleanIconsBackground0.1.tar.gz[/INDENT]
[INDENT]3. Copy the folder "5" from within the archive to /usr/share/unity/, overwriting the existing folder.[/INDENT]

Logout and login to see result.

**Approach from the terminal** &#8212; first create a backup (enter your password when prompted):
[I]sudo cp -rv /usr/share/unity/5 /usr/share/unity/5.backup
[/I]
Then unpack the archive:
[I]tar -xvf UnityCleanIconsBackground0.1.tar.gz
[/I]
Go into the folder:
[I]cd UnityCleanIconsBackground/
[/I]
Copy files to Unity folder:
[I]sudo cp -rv ./5 /usr/share/unity/
[/I]
Logout and login to see result.

In order to revert default state, run this:
[I]sudo cp -rv /usr/share/unity/5.backup /usr/share/unity/5

[/I]Feel free to contact me via PM or this thread.

---

### Post by DMGrier on 2013-05-05
Awesome man looks really cool. Will give it a try in  a bit and through some feed back your way.

---

### Post by ikt on 2013-05-05
Looks really good! Giving it a crack now :D

---

