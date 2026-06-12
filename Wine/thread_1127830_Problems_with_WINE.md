---
title: "Problems with WINE"
date: 2009-04-16
forum: Wine
---

### Post by stevetsr on 2009-04-16
I have recently reinstalled WINE on the 8.10 version and when I try to configure WINE the window has no text on any of the tabs or buttons. I just received an update for WINE but that has not fixed the problem. I am also having this same problem with other programs such as Open Office, can someone please give me some suggestions. I am still pretty new to Linux so you may have to dumb it down for me.

Thanx

---

### Post by crismdq on 2009-04-16
I think i have the same problem. Still cant find how to fix it. My wine apps looks like this

[[IMG]http://www.imagenserver.com.ar/out.php/i5072_notepad2.png[/IMG]](http://www.imagenserver.com.ar/show.php/5072_notepad2.png.html)

Regards

---

### Post by stevetsr on 2009-04-16
I don't even get that much, I would post a picture of what I am seeing but haven't figured out how to insert the screen shot. It also will not allow me to install any windows apps. I have tried just a couple but it will not allow me to install them I just get an error message that says "Cannot find the auto run program". I have also tried exploring the disk and clicking on the setup.exe file and get the same message.


[IMG]http://ubuntuforums.org/album.php?albumid=1041[/IMG]

---

### Post by J-Rod on 2009-04-17
I can confirm the exact same graphical glitch with the text is happening to me after wine upgrade. I also had gone from Hardy to Intrepid though, so I was a bit lost as to where to begin to find a solution.

---

### Post by adamitj on 2009-04-17
> **J-Rod said:**
> I can confirm the exact same graphical glitch with the text is happening to me after wine upgrade. I also had gone from Hardy to Intrepid though, so I was a bit lost as to where to begin to find a solution.

I couldn't reproduce this error, but if these problems happens only on text, did you installed the MS fonts?

```
sudo apt-get install msttcorefonts
```

---

### Post by J-Rod on 2009-04-18
> **adamitj said:**
> I couldn't reproduce this error, but if these problems happens only on text, did you installed the MS fonts?

```
sudo apt-get install msttcorefonts
```

I checked the fonts, yes they are still installed. Here's a cap of what mine looks like on trying to do a wineconfig.

---

### Post by Mze on 2009-04-18
Check this [thread]("http://ubuntuforums.org/showthread.php?p=6667437#post6667437") out for a possible solution.

---

### Post by J-Rod on 2009-04-18
> **Mze said:**
> Check this [thread]("http://ubuntuforums.org/showthread.php?p=6667437#post6667437") out for a possible solution.

Very nice, that worked for me. This is the kind of thing that drives me nuts, I love the community support but I feel like such a dunce that this was easy for someone else. :)

---

### Post by crismdq on 2009-04-18
works for me too, thank you very much!

---

### Post by hikaricore on 2009-04-18
In the future please make all WINE related posts in our WINE forum: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by bapoumba on 2009-04-18
So moved :)

---

