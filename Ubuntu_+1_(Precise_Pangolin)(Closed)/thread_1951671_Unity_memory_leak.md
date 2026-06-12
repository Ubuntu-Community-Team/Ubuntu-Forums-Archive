---
title: "Unity memory leak"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tehowe on 2012-04-02
Launchpad's choking when I search on Unity so I thought I'd float this here (and remind myself to file a bug later if this is news)

The last while whenever I leave my box running, there seems to be a huge memory leak in Unity/the HUD. Observe:

[IMG]http://i1107.photobucket.com/albums/h395/tehowe42/hud_leak.jpg[/IMG]

So after noting this I restarted and...

[IMG]http://i1107.photobucket.com/albums/h395/tehowe42/hud_fresh.jpg[/IMG]

Has anyone else experienced this??

---

### Post by mcellius on 2012-04-02
I had something similar earlier today with thunderbird-bin.  It didn't last through the reboot, but for awhile I was unable to close it and my system monitor showed both cores in my CPU very active and memory not releasing.  (But I'd like to have your six cores!)

---

### Post by NHclimber on 2012-04-03
That's a pretty big memory leak. Report one against compiz too -- 1G?!

---

### Post by MacUntu on 2012-04-03
Make sure you are using indicator-appmenu 0.3.96-0ubuntu2 or later. That leak has already been fixed.

---

### Post by jbicha on 2012-04-03
Also, are you using any extra indicators? For instance, I've heard indicator-multiload has/had some serious issues.

---

### Post by tehowe on 2012-04-04
> **jbicha said:**
> Also, are you using any extra indicators? For instance, I've heard indicator-multiload has/had some serious issues.

You nailed it. I'm using the System Indicator, yeah. 

Currently it's 0.3-0+66~8~17~precise1

Not sure how that compares with the version mentioned by MacUntu but I'm keeping up to date so I'll assume I won't see the problem when I return to my server later this evening :)

Edit: Oh, different package. indicator-appmenu is at 0.3.96-0ubuntu3

---

### Post by philinux on 2012-04-04
> **jbicha said:**
> Also, are you using any extra indicators? For instance, I've heard indicator-multiload has/had some serious issues.

I've had that running for 2 days and no problems so far.
```
apt-cache policy indicator-multiload
indicator-multiload:
  Installed: 0.2-0ubuntu1

```

---

### Post by grandtoubab on 2012-04-04
Hello 
Having 7.8 GB RAM I will set-up swapiness=0
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I have only 2 GB and it works like a charm
```
@ubuntu-desktop:~$ cat /proc/sys/vm/swappiness
0
```

---

### Post by tehowe on 2012-04-16
> **grandtoubab said:**
> Hello 
Having 7.8 GB RAM I will set-up swapiness=0
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I have only 2 GB and it works like a charm
```
@ubuntu-desktop:~$ cat /proc/sys/vm/swappiness
0
```

I haven't been seeing the issue for a while so I assume it's been addressed.

---

### Post by normcross on 2012-04-19
Hi all,

I've been using Ubuntu 10.10 and four days ago I installed Ubuntu 12.04 64bit on a separate drive. Unfortunately I been noticing this problem.

From a clean boot, opening system monitor and nothing else:-

Unity weighs in at 542 MiB and after five minutes reaches 830 MiB in fifteen minutes it's at 1023 MIB and still rising, but slower.

You mention indicator-appmenu version. Mine is 0.3.97 Oubuntu1


Cheers.

---

### Post by cariboo on 2012-04-19
Open a terminal, and type:

```
top
```

Then type:

```
m
```

This will sort applications by memory usage, it should show you what is causing the problem.

On my system the two big ram users are compiz and Xorg.

---

### Post by normcross on 2012-04-20
Hi,  Did some checking:-            Mem used  Ubuntu startup and using 'top'         911660K After 10 mins idle, stays at about    1027116K  start qnome-system monitor        1060336K After 10 mins idle            1406404K and still rising  close system monitor and after 5 mins    1407528K fairly steady.  Guess I wont be using system monitor for a while  Cheers.

EDIT.. sorry about the formatting, just don't know what happened.

---

### Post by cariboo on 2012-04-20
If you can reliably reproduce the problem using System Monitor, I'd suggest you create a bug report. Use the automagic bug reporting utility:

```
sudo ubuntu-bug gnome-system-monitor 
```

---

### Post by Hanine on 2012-04-21
I noticed this just today!
Unity became slow and it laggs starting a certain time of use!

I filed a bug two weeks ago against zeitgeist which issued a big memory and CPU usage leak.

I am trying to monitor resources and spot where the problem come from...

---

