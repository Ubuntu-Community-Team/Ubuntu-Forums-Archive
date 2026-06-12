---
title: "Cryptkeeper alternative? (graphical encfs manager)"
date: 2013-05-02
forum: Security
---

### Post by FreedomOverdose on 2013-05-02
Hello, 

So apparently Cryptkeeper won't work any time soon in 13.04 because of the changes made regarding tray icons. As I used that extensively, are there any other suggestions for graphilcally managing encfs partitions? 

I tried Gnome Encfs Manager, and not only was it buggy, but it also somehow corrupted my encrypted folder (thank god I have backups to that).

Thanks in advance

---

### Post by Stonecold1995 on 2013-05-03
Well in the meantime, couldn't you just use TrueCrypt?  It's a lot more secure because no information about the filesystem is leaked.

---

### Post by FreedomOverdose on 2013-05-03
Good point, haven't used Truecrypt in quite a while. But I heard that it has the same issue regarding the notification icon though. Can anyone confirm whether it works under 13.04 or not?

---

### Post by Stonecold1995 on 2013-05-03
What problems with the icon?  It looks fine along with all my other icons, at least on KDE.

[img]http://oi39.tinypic.com/sbrifa.jpg[/img]

---

### Post by FreedomOverdose on 2013-05-03
I think notification icons are fine in KDE, not the new unity though... Anyway I'll give it a try and let you guys know :)

---

### Post by Stonecold1995 on 2013-05-04
You can use TrueCrypt through command line only so you won't even need an icon.

```
unset DISPLAY # fools TC into thinking no graphical display is available
sudo truecrypt /path/to/file/or/device
cd /media/truecrypt1
# whatever you want to do in truecrypt
cd -
sudo truecrypt -d /media/truecrypt1
```

---

### Post by markbl on 2013-05-05
I have a really simple encfs UI wrapper which I have used for years. See [https://github.com/bulletmark/encfsui](https://github.com/bulletmark/encfsui).

---

### Post by Soul-Sing on 2013-06-24
sudo add-apt-repository ppa:timekiller/unity-systrayfix
sudo apt-get update
sudo apt-get upgrade

**gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Pidgin', 'Cryptkeeper', 'Skype', 'Upatemanager', 'Truecrypt']"**

reboot

---

### Post by QDR06VV9 on 2013-06-25
> **Soul-Sing said:**
> sudo add-apt-repository ppa:timekiller/unity-systrayfix
sudo apt-get update
sudo apt-get upgrade

**gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Pidgin', 'Cryptkeeper', 'Skype', 'Upatemanager', 'Truecrypt']"**

reboot

This PPA dose not appear to be populated for saucy yet. as of today 6/25/13
Just a FYIF

---

### Post by Soul-Sing on 2013-06-26
[http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html](http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html)

---

### Post by cariboo on 2013-06-26
> **runrickus said:**
> This PPA dose not appear to be populated for saucy yet. as of today 6/25/13
Just a FYIF

The ppa probably won't be updated to Saucy, until after it is released. You can still use Raring without causing any problems.

---

### Post by Soul-Sing on 2013-06-26
> **cariboo907 said:**
> The ppa probably won't be updated to Saucy, until after it is released. You can still use Raring without causing any problems.

It works fine.

---

