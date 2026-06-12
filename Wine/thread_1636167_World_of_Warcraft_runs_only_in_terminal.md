---
title: "World of Warcraft runs only in terminal"
date: 2010-12-02
forum: Wine
---

### Post by Starmartyr on 2010-12-02
I have tried to get World of Warcraft to run using a panel launcher but have no clue how to do this, or it's just not letting me.  This is what works for me in terminal:

padsp wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl

So, I actually created an app launcher and added this in, but it doesn't work.  How, if at all possible, can I make this work?

Also, I kept running into that error #134 and also Launcher.exe not having read/access error messages when I did try the other methods.

Thanks

10.10 Mav

---

### Post by cwwilson721 on 2010-12-03
A few questions:

[LIST]
[*]Where do you ACTUALLY have WoW installed? (For example, my WoW install is in /home/<USER>/.wine-wow/drive_c/Program Files/World of Warcraft), and my launcher uses ```
env WINEPREFIX="/home/<USER>/.wine-wow" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```
Note the quotes


[*]Why do you aadd the 'padsp' to the front of the command? I don't and sound is fine. Try removing, and changing the wine run to use XP
[/LIST]

---

### Post by Starmartyr on 2010-12-08
I finally got one working.  I still have to do the padsp for my sound to work, though.

```
padsp env WINEPREFIX="/home/<user>/.wine" wine "C:\Program Files\World ofWarcraft\Launcher.exe" -opengl
```

I actually now get no errors but Wine shows that it failed to load with an error message.  It loads one second later than the error message.  Weird.

---

