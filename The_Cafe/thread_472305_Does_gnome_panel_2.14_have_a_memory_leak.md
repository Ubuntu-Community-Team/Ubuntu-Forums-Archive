---
title: "Does gnome panel 2.14 have a memory leak?"
date: 2007-06-12
forum: The Cafe
---

### Post by FuturePilot on 2007-06-12
I'm trying to figure this out, I've already filed a bug report but I'm not sure what else to do. It seems as though gnome panel in Gnome 2.14 will start leaking memory if you set a custom image on the panel or you make them transparent.

Once I set a custom image on the panel and a few hours later gnome-panel had consumed over 200 MB of RAM. Now something about that just doesn't seem right. And if you don't catch it, it will bring down your system:o Another thing I noticed is that it seems to use up a lot of memory in the first place. When I first log in gnome-panel is using about 15MB. I've noticed that in 2.16 and 2.18 it's around 4MB.

:-k

---

### Post by slimdog360 on 2007-06-12
im sitting on about 10MB for the panel

---

### Post by tehhaxorr on 2007-06-12
> **FuturePilot said:**
> I'm trying to figure this out, I've already filed a bug report but I'm not sure what else to do. It seems as though gnome panel in Gnome 2.14 will start leaking memory if you set a custom image on the panel or you make them transparent.

Once I set a custom image on the panel and a few hours later gnome-panel had consumed over 200 MB of RAM. Now something about that just doesn't seem right. And if you don't catch it, it will bring down your system:o Another thing I noticed is that it seems to use up a lot of memory in the first place. When I first log in gnome-panel is using about 15MB. I've noticed that in 2.16 and 2.18 it's around 4MB.

:-k

I have that problem on my Fedora Core 5 box with 2.14. I was balooning to over 200mb for the panel too, can be solved by removing gnome base and reinstalling it from the repos.

---

### Post by FuturePilot on 2007-06-12
> **tehhaxorr said:**
>  can be solved by removing gnome base and reinstalling it from the repos.
I don't quite understand.

---

### Post by wolfen69 on 2007-06-13
my gnome has no memory leak, my stuff works perfect. im lucky that way.

---

### Post by FuturePilot on 2007-06-13
Here's the bug report. Seems that it's been marked as fixed since it doesn't affect the more recent versions of Gnome. In fact it would be a non issue for me if I could use Feisty on my laptop, but I can't seeing that it has this nasty little freeze bug somewhere in it.:(

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/118716]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/118716")

---

### Post by EdThaSlayer on 2007-06-13
It's only using around 11.4 mb for me. I also have transparency on 50%. :popcorn:

---

### Post by brim4brim on 2007-06-13
I've had my laptop on for the past 3-4 days and it hasn't had a problem with a custom background.

---

### Post by DC@DR on 2007-06-13
No problem for me at all on Feisty Fawn with 100% transparent panel :-)

---

### Post by FuturePilot on 2007-06-13
> **DC@DR said:**
> No problem for me at all on Feisty Fawn with 100% transparent panel :-)

Yeah, it doesn't have this problem on Edgy or Feisty, only Dapper.

---

### Post by samichx on 2007-07-01
I've got a major problem - appx. 30 mins until 350 just for gnome-panel I'll be trying some solutions. This is from feisty, with beryl... Meh

---

### Post by Tritonio on 2007-09-30
I have gnome-panel 2.18 but I have a similar problem! I left the PC on for 2 days with utorrent running (with wine of course) and when I got back to my house gnome-panel was using about 400MB (some value like X00MB). I had similar problems in the past and I found that Geyes must be leaking memory because their memory usage got really high after one or two days (reaching 100MB and more). What I had notices about Geyes is that when I moved my mouse (so that they followed it) their memory usage was slightly raising. So after lot's of use they consumed the memory I said previously. Now I have removed Geyes from the panel. I only use the following apps on my panel:
[LIST]
[*]Disk Mounter
[*]lots of launchers (for firefox xmoto etc)
[*]Force Quit Button
[*]Show Desktop
[*]Windows list
[*]Log Out button
[*]Keyboard Indicator
[*]Notification Area
[*]System Monitor (monitoring everything:CPU, memory, disk etc)
[*]Menubar
[*]Clock
[/LIST]

:confused:

---

