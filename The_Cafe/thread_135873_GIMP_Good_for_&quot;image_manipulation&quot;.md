---
title: "GIMP? Good for &quot;image manipulation&quot;?"
date: 2006-02-24
forum: The Cafe
---

### Post by giddy1945 on 2006-02-24
If I copy & paste a small image from the internet to a folder and open it with a jpg type image viewer, the image, naturally, becomes distorted because of the lack of pixcels.  I was wondering if Gnu Image Manipulation Program (GIMP) would be the one to use to enhance the image.  I have played with it a little, but maybe someone could point me in a better direction.  I have absolutely no idea what I am doing, so please advise me as you would a brand newbie.  Thank you in advance. : )

---

### Post by niviche on 2006-02-24
I am not sure that I understand what you want to do, and what the problem is. What do you mean by "lack of pixels"?

Web images are usually saved with a resolution of 72 dpi (dots per inch). If you open them in an image viewer (Gwenview or whatever), they should appear at the same size as in your browser. But if you zoom in, they will get all pixel-ized, of course.

---

### Post by giddy1945 on 2006-02-24
Yes! Pixel-ized.  I want to be able to copy a very little image from a webpage that will not allow me to view the image "up close".  I then want to paste it to a folder and then open it with "image viewer".  When I enlarge the image, I want to be able to "clear it up" I guess are the words I am looking for.  You know?  Make the distortion less noticeable.  Is that even possible, or have I been whatching too much TV?

---

### Post by Iandefor on 2006-02-24
[quote=giddy1945]Yes! Pixel-ized. I want to be able to copy a very little image from a webpage that will not allow me to view the image "up close". I then want to paste it to a folder and then open it with "image viewer". When I enlarge the image, I want to be able to "clear it up" I guess are the words I am looking for. You know? Make the distortion less noticeable. Is that even possible, or have I been whatching too much TV?[/quote]I think you've been watching too much tv :). The image is composed of an array of pixels- if you get a small image, it will be composed of a small array of pixels. Zooming in to look closer won't help resolution, it'll just make the individual pixels look bigger.

---

### Post by giddy1945 on 2006-02-24
Thanks anyway.

---

### Post by cdhotfire on 2006-02-24
You might want to try sharping it, from "Filter->Sharpen->Sharpen".  But you gotta realize that what you want is creating more pixels that are not even there, all it does when you enlarge it is, enlarges the smaller pixels.

Good luck. :)

---

### Post by giddy1945 on 2006-02-27
ok. I'll try that and get back with you.

---

### Post by eriqk on 2006-02-28
There are some scripts that will help you with what you want, but as already explained, don't expect too much in the way of quality.
There's a script that will blow up the image in steps (which is moderately better than doing it in one go) and there are some interesting unsharp-masking/sharpening scripts. Check the Gimp plugin page and have fun!

Groet, Erik

---

### Post by mostwanted on 2006-02-28
[QUOTE=Iandefor]I think you've been watching too much tv :). The image is composed of an array of pixels- if you get a small image, it will be composed of a small array of pixels. Zooming in to look closer won't help resolution, it'll just make the individual pixels look bigger.[/QUOTE]

Actually, I think the GIMP was used in an episode of 24 or something for just that purpose. Read it in a Gnome developer's blog post some time back. Pretty humorous :)

---

### Post by Brunellus on 2006-02-28
[QUOTE=mostwanted]Actually, I think the GIMP was used in an episode of 24 or something for just that purpose. Read it in a Gnome developer's blog post some time back. Pretty humorous :)[/QUOTE]
wow, they´ve ported the GIMP to MovieOS!

---

### Post by Minyaliel on 2006-02-28
I use GIMP for everything, including fixing pixelized images. (I seldomly grab mine from the Net, though, prefer making'em myself :P ) It's easily done by just playing around with various brushes and the scripts mentioned above.

---

### Post by eriqk on 2006-02-28
[QUOTE=Brunellus]wow, they´ve ported the GIMP to MovieOS![/QUOTE]

Ah, good old MovieOS. I loved the old versions where letters printed to the screen would sound like a daisywheel printer. 

Groet, Erik

---

