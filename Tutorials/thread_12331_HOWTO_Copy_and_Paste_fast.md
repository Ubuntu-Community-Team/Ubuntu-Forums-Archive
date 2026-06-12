---
title: "HOWTO: Copy and Paste fast"
date: 2005-01-23
forum: Tutorials
---

### Post by apoc on 2005-01-23
Taken from page 21 [ftp://www6.software.ibm.com/software/developer/library/l-faq.pdf](ftp://www6.software.ibm.com/software/developer/library/l-faq.pdf)

Often when you follow howto you have to copy and paste alot of text into your command promt, and for some reason CTRL+V wont paste into the promt, but right click and select paste works, however page 21 of the above mentioned pdf file mentions an even faster way then the typical CTRL+C -> CTRL+V that even works.

You highlight the text you wish to copy, and press the middle mouse butten (useally the weel) then paste it into the promt or other document with another click on the middle mouse button.

I hope it helps someone  :D

---

### Post by piedamaro on 2005-01-23
Yep, it's the X clipboard :)

---

### Post by pseudonym on 2005-01-24
On my machine all I have to do is highlight the text, and this alone seems to perform the copy operation. Then I paste it with one click of the 'Thumb Button' (on a LOgitech Mouseman Wheel, which I used as a double-click button in windows). I would never have guessed! :)

---

### Post by wallijonn on 2005-02-21
That's good Trick / tip.

---

### Post by JmSchanck on 2005-02-21
[QUOTE=pseudonym]On my machine all I have to do is highlight the text, and this alone seems to perform the copy operation. Then I paste it with one click of the 'Thumb Button' (on a LOgitech Mouseman Wheel, which I used as a double-click button in windows). I would never have guessed! :)[/QUOTE]

Yeah i noticed this too with my logitech MX 310, the "Thumb button" is just another button 3 and the "Pinky button" on the opposite side acts as another right click. By the way if anyone can tell me a way to reprogram these it would be great.

And about pasting into the prompt CTRL+SHIFT+V works as well.

---

### Post by DownloadTHIS on 2005-03-02
[QUOTE=JmSchanck]Yeah i noticed this too with my logitech MX 310, the "Thumb button" is just another button 3 and the "Pinky button" on the opposite side acts as another right click. By the way if anyone can tell me a way to reprogram these it would be great.

And about pasting into the prompt CTRL+SHIFT+V works as well.[/QUOTE]

I had the same problem with my mouse.

sudo gedit /etc/X11/XF86Config-4
Find the line that says:	Option		"Emulate3Buttons"		"True
Replace that line with:         Option		"Buttons"		"7"

---

### Post by ixus_123 on 2005-03-03
Wow - I didn't know that.  Thanks :)  

It will save me a few keystrokes

---

### Post by hesjnet on 2009-01-08
Thanks alot for this! You wouldn't belive the time savings this trick does for me:D Thanks!

---

### Post by reptile83 on 2010-09-15
For those who still care about this document it can be found here: [http://adsl.cutw.net/l-faq.pdf](http://adsl.cutw.net/l-faq.pdf)

---

### Post by v1ad on 2010-09-15
can't access document ..

---

### Post by v1ad on 2010-09-15
tx great document.

---

### Post by utnubuuser on 2010-09-16
For those who don't know yet, there is also a great app/extension called klipper (kde), and/or glipper (gnome) that extends the clipboard functionality to include "actions" and multiple "saved" clippings. - Awesome app.
> [http://sazeit.com/articles/klipper-in-ubuntu-gnome]("http://sazeit.com/articles/klipper-in-ubuntu-gnome")

---

### Post by codecentral on 2012-08-06
If you can spare some mouse buttons, give this a try too:

[http://thecodecentral.com/2012/07/27/use-mouse-buttons-to-perform-copy-paste-in-ubuntu](http://thecodecentral.com/2012/07/27/use-mouse-buttons-to-perform-copy-paste-in-ubuntu)

---

