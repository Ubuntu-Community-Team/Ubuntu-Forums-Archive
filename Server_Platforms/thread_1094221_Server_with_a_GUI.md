---
title: "Server with a GUI"
date: 2009-03-12
forum: Server Platforms
---

### Post by Jimmy9pints on 2009-03-12
Before you ask "WHY?", the answer is simple. I want to run a server, which will be placed in my front room and making it headless would give me a wasted screen. At the same time, I want one of those USB photo frames but they're like $150 for a good one. 

So an idea springs to mind - since the server's running all the time, just connect the screen and have it cycle through our family photos. I could even put a frame around the screen :)

Save money and put an otherwise useless flatscreen to use!

I don't want the GUI for admin, I will use webmin for that and do it remotely. I just want to display pictures and perhaps some other stuff.

It's a bit of an old machine, so I tried installing Ubuntu server, so after installing webmin I looked at the [community docs on low mem systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). Following that advice then:
• installed fluxbox
[LIST]
[*]installed xinit
[/LIST]
• installed xorg
• installed slim
• installed xfce-terminal

Disaster struck because in the newly installed GUI neither the mouse nor keyboard is recognized so I couldn't do a thing. 

I can easily reinstall, but after that, what should I do to get the lightest possible GUI...or is there some other way to show photos (and ideally the weather, news....) in my front room?

Cheers,

James.

---

### Post by BkkBonanza on 2009-03-12
I don't think you need a full gui to just show photos. You should be able to run terminal mode with a vesa video setting that would allow cmd line apps to show jpegs. I haven't tried that but I have used the terminal in vesa mode and seen splash screens and background images.

---

### Post by HermanAB on 2009-03-12
If you want a GUI on a local console, install regular Ubuntu.  If not, install ssh-server and remote in from another machine.

Cheers,

Herman

---

### Post by ptn107 on 2009-03-12
I did a similar thing.  I just installed Ubuntu Server 8.10 x86_64 and installed just X on top of it.  Don't need a desktop environment.
```
sudo apt-get install xserver-xorg xfonts*
```

---

### Post by Iowan on 2009-03-12
[https://help.ubuntu.com/community/ServerGUI]("https://help.ubuntu.com/community/ServerGUI")

---

### Post by Jimmy9pints on 2009-03-12
Thank you everybody!

@BkkBonaza: If I can show photos without a GUI then that's perfect. 

@ptn107: Interesting. Once you are running X can you show photos etc?

---

### Post by BkkBonanza on 2009-03-12
Have a look around for info on a cmd line jpeg viewer. I think you can find something that will work without a gui. I found this link where there are a few suggestions. I haven't tried them - first one is for zgv.

[http://linux.derkeiler.com/Newsgroups/alt.os.linux/2006-02/msg00107.html](http://linux.derkeiler.com/Newsgroups/alt.os.linux/2006-02/msg00107.html)

[http://www.svgalib.org/rus/zgv/](http://www.svgalib.org/rus/zgv/)

I guess what you want is a cmd line slideshow and maybe one of these programs can do that. To just show jpegs in sequence a simple script could be combined with a viewer program. If you configure the boot with a "vesa" mode then the local terminal will be in graphics mode rather than text. But it may be that a jpeg viewer can switch the mode anyway. Not sure.

---

### Post by Jimmy9pints on 2009-03-15
Thank you BkkBonaza!  (How do you add thanks these days? Where's the button gone?)

I had been googling for something like this and drew a blank. 

Now I have got zgv installed. Gonna give it a whiz. 

Cheers,

---

### Post by windependence on 2009-03-15
You can show photos in a web interface very easily without ever loading X. If you just want to serve photos to people, then something like gallery2 or Coppermine comes to mind.

-Tim

---

