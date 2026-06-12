---
title: "Ubuntu Studio Repositories?"
date: 2007-05-19
forum: The Cafe
---

### Post by jclmusic on 2007-05-19
couldn't find any posts about this in a search. are there any repos for ubuntu studio so i can install some of it's programs on my ubuntu without re-installing?

---

### Post by xyz on 2007-05-19
Synaptic > Search > Ubuntustudio
I installed it that way and as a fresh install,too. Worked both ways for me.

---

### Post by jclmusic on 2007-05-19
cool, thanks!¬ i didn't know it waas supported in the nnormal repos :)

---

### Post by xyz on 2007-05-19
No problem...it just asks you to insert Feisty CD once in a while.

PS: Haven't had time to listen to your album on Jamendo...but soon will do!

---

### Post by jariku on 2007-05-19
Here's how to add Ubuntu Studio repositories:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by John.Michael.Kane on 2007-05-19
You can search for the files/metapackages you want with this method.

[how to upgrade from feisty to ubuntu-studio using the repos]("http://ubuntuforums.org/showpost.php?p=2637807&postcount=93")

Or

Command one:
```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
```

Command Two:
```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Install it all at one time
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video ubuntustudio-artwork ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-session-splashes ubuntustudio-sounds ubuntustudio-screensaver ubuntustudio-theme ubuntustudio-wallpapers usplash-theme-ubuntustudio wired
```

If you have an nvidia card
```
sudo aptitude install linux-restricted-modules-2.6.20-15-lowlatency
```

---

### Post by jclmusic on 2007-05-19
i don't want to upgrade, i just wanted some of the music packages. thanks anyway, though. :) the kernel does sound nice though, i think i might upgrade that.

---

