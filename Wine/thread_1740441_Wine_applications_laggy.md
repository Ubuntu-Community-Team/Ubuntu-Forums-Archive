---
title: "Wine applications laggy"
date: 2011-04-27
forum: Wine
---

### Post by darkreaction on 2011-04-27
I'm trying to play Tf2 on steam. I can load the game fine but I get maybe 10-15fps when I get into a game even on low settings. I did everything I could find In the Wine hq tf2 page but nothing helps.

system specs
Athlon 64 X2 2.2ghz
2gb memory
Nvidia Geforce Gt 520

Anything would be helpful.

---

### Post by Soulcage on 2011-04-27
Did you install the video drivers?

---

### Post by darkreaction on 2011-04-27
Yes I did. I used 
```
sudo apt-get install nvidia-current
```
then
```
sudo nvidia-xconfig
```

It is a brand new card to replace my Radeon HD 4670

---

### Post by Soulcage on 2011-04-28
Try adding the ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

---

### Post by darkreaction on 2011-04-28
Nope didn't help. I do keep getting this when I run Winedebug
```

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
```

---

