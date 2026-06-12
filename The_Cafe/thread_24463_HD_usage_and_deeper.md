---
title: "HD usage and deeper"
date: 2005-04-07
forum: The Cafe
---

### Post by LongTooth on 2005-04-07
My output of df -h on my main Ubuntu box:

longtooth@ubuntu:~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              38G  7.1G   29G  20% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev                   38G  7.1G   29G  20% /.dev
none                  5.0M  2.8M  2.3M  55% /dev
longtooth@ubuntu:~ $


Question:
How would I go about getting a break down of the 7.1G of usage? This seems like a lot of space and I'd like to find out just where it's all at? Thanks.

---

### Post by Juergen on 2005-04-07
try
```
du -hs /*
```

---

### Post by bigzak on 2005-04-07
if you do:
```
ds / | sort -g
``` 
you will get the directories ordered in increasing size. The one at the bottom is the biggest. Note that it doesn't take the hierarchy into account, so if folder /usr is the biggest, and /usr/lib and /usr/include and the 2nd and 3rd respectively, it gives you an insight into why /usr is at the top.

---

### Post by jobezone on 2005-04-07
[QUOTE=LongTooth]My output of df -h on my main Ubuntu box:
Question:
How would I go about getting a break down of the 7.1G of usage? This seems like a lot of space and I'd like to find out just where it's all at? Thanks.[/QUOTE]

Try filelight, it's either in the Main repository or Universe.

More about it at:
[http://www.kde-apps.org/content/show.php?content=9887](http://www.kde-apps.org/content/show.php?content=9887)

Screenshot:
[http://www.kde-apps.org/content/pre1/9887-1.png](http://www.kde-apps.org/content/pre1/9887-1.png)

---

### Post by LongTooth on 2005-04-07
To all, thanks for the tips. They worked as 'advertised'. Bigzak, I used du instead of ds. I figured that's what you meant :)

jobezone, filelight certainly looks like something I would be interested in. Unfortunately, it's a KDE app and I'd like to keep my system as pure Gnome as I can. Love to have something similar for Gnome. Anyone know of anything like that?

---

