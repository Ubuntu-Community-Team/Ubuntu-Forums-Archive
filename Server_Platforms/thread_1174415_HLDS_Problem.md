---
title: "HLDS Problem"
date: 2009-05-30
forum: Server Platforms
---

### Post by user328 on 2009-05-30
When i try to install hlds (Half Life dedicated server) i go through this process:
make a directory called "hlds_1"
[SIZE=3]cd hlds_l
wget [http://www.japje.nl/wp-content/steam/steam.tar.gz](http://www.japje.nl/wp-content/steam/steam.tar.gz)
tar -zxvf steam.tar.gz
chmod +x steam
[/SIZE][SIZE=3]./steam

When i type "./steam" i get this:
-bash: ./steam: No such file or directory

Maybe i am doing something wrong? Have any ideas?
Thanks[/SIZE]

---

### Post by user328 on 2009-05-31
anyone knows?

---

### Post by Invader Amoto on 2009-05-31
I had this problem. It turns out that the steam executable is 32-bit and I was running a 64-bit system without the compatibility packages.
If you are running a 64-bit version, then get the compatibility packages. I'm sorry that I don't know them off the top of my head, though I'm sure someone else knows them.

---

### Post by user328 on 2009-05-31
Yeah i am running the 64 bit version. So do i need to install the 32 bit version?

---

### Post by xKU5Hx on 2009-05-31
this might help [http://forums.steampowered.com/forums/forumdisplay.php?f=45](http://forums.steampowered.com/forums/forumdisplay.php?f=45)

---

