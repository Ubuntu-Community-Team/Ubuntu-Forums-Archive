---
title: "Wine shuts down"
date: 2010-07-30
forum: Wine
---

### Post by Pollewoppetje on 2010-07-30
Hey all, 

After searching the internet and your forum, I post my question here, since I've been unable to fix my problem. 

When I run a program through Wine, after 1 second, the program shuts down. I'm now unable to use any windows program/game whatsoever. 

Here's the error I got when I ran the program in the terminal: 

```
xxxxxx@xxxxx-laptop:~/.wine/dosdevices/c:/Program Files$ wine VirtualDj/virtualdj.exe
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13f8f0,0x13f878): stub
fixme:time:GetSystemTimes (0x32f7f8,0x32f7f0,0x32f7e8): Stub!
Unsupported color conversion request
```

I see there's a "fixme" in this error, but how do I do that?

I'm running ubuntu Lucid 64-bit and I've updated everything.


Many thanks!

---

### Post by Pollewoppetje on 2010-07-30
Bump!

Please mind that this error doesn't only occur with Virtual DJ, but with every program I run!

Thanks!

---

### Post by asdfoo on 2010-07-30
which video card and drivers are you using? it sounds like you might not have the correct one.

---

### Post by Pollewoppetje on 2010-07-31
I have an 

Nvidia geforce 9500M GS, with
Nvidia driver version 195.36.24

This is what I get when I open the program "NVIDIA X Server settings"

---

### Post by ronnielsen1 on 2010-07-31
You don't say what version of virtual dj you're trying to run. I got the 6.1 trial to run on my box but it made my computer slow to a crawl
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1704](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1704)

From googling this seems to be an issue. May I recommend an alternative

[http://www.ultramixer.com/](http://www.ultramixer.com/)
> **UltraMixer 2.4 (Pro Demo, Basic, Home, Free)**

          [IMG]http://www.ultramixer.com/download/res/pics/logo_linux_large.png[/IMG]
                                                            Version:                     UltraMixer 2.4                                                       System:                     Linux SuSE (10.0 or higher)                                                                        Format:                     JAR (Java based Installer)                                                       Size:                     24 MB[http://www.ultramixer.com/download.html](http://www.ultramixer.com/download.html)
It says suse but it's java based so it works

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-UltraMixerProfessionalDEMO-V240.png[/IMG]


Excuse the black on the bottom. I had issues with my nvidia after an update and I haven't fixed it yet

---

### Post by Pollewoppetje on 2010-07-31
@Ron nielsen:
> **Pollewoppetje said:**
> Bump!

Please mind that this error doesn't only occur with Virtual DJ, but with every program I run!

Thanks!

---

### Post by Pollewoppetje on 2010-08-01
To give a little update, I've had both the regular version and a beta release installed. However, after reinstalling just the regular version, I still get the same "unsupported color conversion request".

I've installed the latest graphic drivers properly. Can anyone please help me with this? I am very new to Ubuntu!

---

### Post by ydeardorff on 2011-12-17
I too have had wine installed for more than a year, and am unable to use it.
I have tried lowering the screen res, to even trying every compatibility setting win 98 through win7 with no luck.
Wine starts, sits for about a second, then shuts itself back down.
This is religious with every program I'm trying to use with it.

I tried to run terminal on it like this person did and it say no such directory.

Any help here?

---

