---
title: "New Linux user, No sound settings in Ubuntu Studio?"
date: 2016-12-08
forum: Ubuntu Studio
---

### Post by sterlinglee38 on 2016-12-08
I am a recent Windows 10 refugee who has hopefully found a new land in Linux. I'm surprised with all my years of computer use, that haven't been here sooner 

I just wiped my Toshiba laptop and installed Ubuntu Studio. I'm a musician and love to mess with other arts, so thought it would be a good fit for me. I have started with one issue though. I can't seem to find any kind of place to adjust audio settings. I have included some screenshots as proof of my search. How I came upon this issue is I can't get sound from the tv when I attach my tv through the HDMI out. There is sound on the laptop, but it should switch to the tv when the cable is attached to the laptop. I was searching for some answers, and most started with adjustments to the sound settings, and so here I am. So can anyone help me with this? Is this a setting somewhere I have missed or what? Thanks so much for any help you can give me. 

[http://i628.photobucket.com/albums/uu5/sterlinglee38/Screenshot_2016-12-08_21-45-02_zpstp4ol68w.png](http://i628.photobucket.com/albums/uu5/sterlinglee38/Screenshot_2016-12-08_21-45-02_zpstp4ol68w.png)
[http://i628.photobucket.com/albums/uu5/sterlinglee38/Screenshot_2016-12-08_21-42-55_zps3owd9thj.png](http://i628.photobucket.com/albums/uu5/sterlinglee38/Screenshot_2016-12-08_21-42-55_zps3owd9thj.png)
[http://i628.photobucket.com/albums/uu5/sterlinglee38/Screenshot_2016-12-08_21-44-08_zpsyunkasbq.png](http://i628.photobucket.com/albums/uu5/sterlinglee38/Screenshot_2016-12-08_21-44-08_zpsyunkasbq.png)

Thanks,
Lee

PS edit: I noticed also that the option to mirror the monitor image when I plug in the hdmi is not available, it's there but greyed out.  Not sure if related or not

---

### Post by marseille2 on 2016-12-09
You probably need to switch "sinks" (kind of like another word for audio port). Others may have a different method but IMO, the easiest way to do it is to install the program "[pasystray]("https://launchpad.net/ubuntu/+source/pasystray/0.5.2-1ubuntu1")" (from your package manager or software center).  Pasystray will let you switch between your audio cards (sink) and your mics (source).

---

### Post by sterlinglee38 on 2016-12-09
This "fixed" my problem. Thanks so much Marseille2! Now I just have to figure out how to get a mirrored image, if possible, when I plug in the hdmi. I can work around that though. Thanks again!!!

---

### Post by marseille2 on 2016-12-11
Glad to hear it:)

BTW... If you mean the projection display (on pc and tv) RE: "mirrored image" ... I think it's [xrandr]("https://www.x.org/releases/X11R7.5/doc/man/man1/xrandr.1.html") that takes care of it. It's probably already installed but don't quote me. You can always check to see where it is at the command line like this:

```
$ which xrandr
```

If it's installed you should get some feedback telling you the directory it's located in. ... There might be a GUI program(s) in the package manager too, but I don't use it so I'm not sure. 

If it's gets any tougher than messing around with xrandr, you might want to look up your video card's specs.

---

