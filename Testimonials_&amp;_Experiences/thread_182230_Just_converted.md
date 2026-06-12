---
title: "Just converted"
date: 2006-05-25
forum: Testimonials &amp; Experiences
---

### Post by UbuntuniX on 2006-05-25
Installed ubuntu linux after trying live CD,
I love it :D

My graphics hardware seems to have problems with it but I'll fix it probably...

So is there any software to run windows programs and games?

---

### Post by bruce89 on 2006-05-25
Wine, but which applications would you need?

**edit** - beat me to it again!

---

### Post by aysiu on 2006-05-25
[QUOTE=cyberphr]So is there any software to run windows programs and games?[/QUOTE] Wine, Crossover Office, Cedega.

---

### Post by UbuntuniX on 2006-05-26
Ok thanks guys :)

What about an ftp client?

---

### Post by aysiu on 2006-05-26
[QUOTE=cyberphr]Ok thanks guys :)

What about an ftp client?[/QUOTE] I'd recommend in this order:

Firefox's FireFTP extension
KFTPGrabber
FileZilla (run in Wine)
gFTP

---

### Post by henriquemaia on 2006-05-26
FTP client: **konqueror**. Specially good if you're a KDE user.

---

### Post by UbuntuniX on 2006-05-26
umm the add apps window froze lol how do I get like task manager or w/e?

---

### Post by henriquemaia on 2006-05-26
[quote=cyberphr]umm the add apps window froze lol how do I get like task manager or w/e?[/quote]

Maybe there is a better way to get it through a shortcut, but I don't know it. This way works.

Go to 
Applications --> Accessories --> Terminal

In the terminal, type:

gnome-system-monitor

---

### Post by aysiu on 2006-05-26
Press Alt-F2 and type ```
xkill
```

---

### Post by henriquemaia on 2006-05-26
[quote=aysiu]Press Alt-F2 and type ```
xkill
```[/quote] 
And take care not to click on the wrong window... it will close it :-D

---

### Post by UbuntuniX on 2006-05-26
Still won't close guess I'll just boot lol

---

### Post by henriquemaia on 2006-05-26
[quote=cyberphr]Still won't close guess I'll just boot lol[/quote] 
That happens because the window is being runned by the administrator. You have to close it with administrator rights also.

Try this on the terminal:

sudo gnome-system-monitor


this way, if you select an app to stop, it will most certainly close it.

ps: reboot can solve that, but that's not the Linux's way of doing things.

---

### Post by UbuntuniX on 2006-05-26
Thanks dude it worked :)

So moving on...

Best music player?

---

### Post by henriquemaia on 2006-05-26
[quote=cyberphr]Thanks dude it worked :)

So moving on...

Best music player?[/quote]

Tricky one :)

I will say **Amarok**. But, again, this is a best option if you are a KDE user. I run Gnome, but other players just lack a proper notification area support.

---

### Post by UbuntuniX on 2006-05-26
I'll try it man thanks :D

---

### Post by UbuntuniX on 2006-05-26
What program do I use to extract/open 7-zip files?

(Sorry if I seem n00by, just so used to windows ;) )

---

### Post by 3rdalbum on 2006-05-27
It's a good question. I opened up Synaptic Package Manager and did a search, and it came up with p7zip. I don't know if it can unzip as well, but I assume it does. (I didn't try it, because it's over a megabyte and my internet connection is slow ATM)

---

### Post by Sef on 2006-05-27
> So is there any software to run windows programs and games?

[http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

