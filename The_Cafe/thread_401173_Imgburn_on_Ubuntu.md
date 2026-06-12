---
title: "Imgburn on Ubuntu"
date: 2007-04-04
forum: The Cafe
---

### Post by gvzfs1972 on 2007-04-04
Hi all! I am new, may be posting the wrong place too, bear with me, I am keen to get it right. I want to get Imgburn working under wine and so far the install worked fine, now for the devices, the do not show and all I can find is that this program workes for other users on the net. But How do I configure so that Imgburn finds the dvd drives?

[IMG]http://www.flickr.com/photos/gvzfs/446083874/[/IMG]
[http://www.flickr.com/photos/gvzfs/446083874/](http://www.flickr.com/photos/gvzfs/446083874/)  Screenshot

Please help.

[email]gvzfs@yahoo.dk[/email]

---

### Post by maniacmusician on 2007-04-04
> **gvzfs1972 said:**
> Hi all! I am new, may be posting the wrong place too, bear with me, I am keen to get it right. I want to get Imgburn working under wine and so far the install worked fine, now for the devices, the do not show and all I can find is that this program workes for other users on the net. But How do I configure so that Imgburn finds the dvd drives?

[IMG]http://www.flickr.com/photos/gvzfs/446083874/[/IMG]
[http://www.flickr.com/photos/gvzfs/446083874/](http://www.flickr.com/photos/gvzfs/446083874/)  Screenshot

Please help.

[email]gvzfs@yahoo.dk[/email]
why are you trying to use a windows cd burning program on Linux? Why not just use one of the great ones that Linux already has? The two most popular ones are Brasero and K3B. I recommend K3B.

---

### Post by gvzfs1972 on 2007-04-04
Oh but no. It is a windows dvddecrypter in it&#347; newest form.

---

### Post by EdThaSlayer on 2007-04-04
> **gvzfs1972 said:**
> Oh but no. It is a windows dvddecrypter in it&#347; newest form.

Why don't you just use Thoggen DVD Ripper? Or one of those other dvd decrypter's that GNU/Linux has, native program always run faster.

---

### Post by Gutsy Guy on 2008-01-26
To answer your original post, I was having the same problem and I just tweaked some configurations within imgburn. First make sure your wine config is set to Windows 2000. Then open imgburn with wine. Open the Tools menu and then goto Settings. The Settings window will open and then click the I/O Tab. Under Interface there is several different options, the default is SPTI - Microsoft(Bad), the working one for me was ASPI - WNASPI32.DLL. Try playing around with these and see if it works.

Good Luck

---

### Post by Tekovro on 2008-08-02
Thank you Gutsy guy.. that worked.. very helpful :)

---

### Post by mnavasuk on 2008-08-08
Thanks Gutsy guy, just the answer we needed, also to the other members who gave us alternatives.

---

### Post by stinger30au on 2008-08-08
> **gvzfs1972 said:**
> Oh but no. It is a windows dvddecrypter in it&#347; newest form.

why bother.

you can use dvdfab free for this under wine as well

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

---

