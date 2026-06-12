---
title: "[SOLVED] help with falling sand game"
date: 2008-05-16
forum: The Cafe
---

### Post by rugbylg6 on 2008-05-16
I downloaded the linux binary from <http://www.piettes.com/fallingsandgame/download.html> and now I cant figure out how to run it. I'm still pretty new at this, thx.

---

### Post by ibuclaw on 2008-05-16
Downloaded the [fsg-4.4 binary]("http://www.piettes.com/fallingsandgame/fsg-4.4")
Opened a terminal and typed in:
[PHP]
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
sudo ln -s /usr/lib/libexpat.so /usr/lib/libexpat.so.0
[/PHP]

Change the file permissions to be executable on the fsb file.
[PHP]chmod +x fsb-4,4[/PHP]
Then it ran!

Regards
Iain

---

### Post by rugbylg6 on 2008-05-16
I did all that,```
chmod +x /home/alex/Desktop/fsg-4.4
```, thats all I changed. When I ```
exec /home/alex/Desktop/fsg-4.4 
``` the terminal window closes and nothing happens.

---

### Post by ibuclaw on 2008-05-16
Open up a terminal.
Type in:
```

cd ~/Desktop
./fsg-4.4

```
What output does the program bounce back at you?

Regards
Iain

---

### Post by rugbylg6 on 2008-05-16
```
./fsg-4.4: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory
```

---

### Post by ibuclaw on 2008-05-16
Step One, read the instructions! :D

```

gksu ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
gksu ln -s /usr/lib/libexpat.so /usr/lib/libexpat.so.0

```
I've change it to open a gui password prompt.

Copy line one first, then line two.

Regards
Iain

---

### Post by init1 on 2008-05-17
> **rugbylg6 said:**
> ```
./fsg-4.4: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory
```
```

sudo apt-get install libpng3
sudo apt-get install libexpat1
ln -s /usr/lib/libexpat.so.1 /usr/lib/libexpat.so.0

```

---

### Post by init1 on 2008-05-17
> **tinivole said:**
> Step One, read the instructions! :D

```

gksu ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
gksu ln -s /usr/lib/libexpat.so /usr/lib/libexpat.so.0

```
I've change it to open a gui password prompt.

Copy line one first, then line two.

Regards
Iain
That won't work if he doesn't have them to begin with ;)

---

### Post by cardinals_fan on 2008-05-17
Check this out: [http://dan-ball.jp/en/javagame/dust/](http://dan-ball.jp/en/javagame/dust/)

---

### Post by rugbylg6 on 2008-06-12
Done, thanks a lot for your help.

---

