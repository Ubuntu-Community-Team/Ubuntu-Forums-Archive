---
title: "Compressing are avatars! what do others think?"
date: 2006-01-18
forum: The Cafe
---

### Post by Omnios on 2006-01-18
UI played around with my avatar and managed to shrink it down from 10.4k to 3k and it still looks ok. I probably could have compressed a png then saves it as a gif for a 4KB. file. Anyways I want to start a discusion on this ans see what everyone thinks. I also make a small how tothread in Forum discussion. 

 [http://ubuntuforums.org/showthread.php?p=667779&posted=1#post667779]("http://ubuntuforums.org/showthread.php?p=667779&posted=1#post667779")

 Right now im testing out a 4k compressed png saved to a gif

---

### Post by gord on 2006-01-18
compressing to one format and then to another won't give you any more compression, infact if you use lossy compression techniques like jpeg there is a good chance you will decrease the ammount of compression.

just compress avitars with png if you want them to be clear/alpha transparent and with jpeg if they are more of a photo type avitar. don't bother with gif, png gives better compression than gif.

---

### Post by Omnios on 2006-01-18
I started with 28k png compressed to 10.1 compressed .png and then saved it to gif which saved the transparency that ended up being 4k and it will blow up to 300% without loss of quality

---

### Post by Lovechild on 2006-01-18
remind me is gif still evil in some parts of the world or was it freed globally?

---

### Post by BWF89 on 2006-01-19
[QUOTE=Lovechild]remind me is gif still evil in some parts of the world or was it freed globally?[/QUOTE]
The FSF still used PNG for their images but I think that GIF has been freed.

---

### Post by ssam on 2006-01-19
png is a better format than gif.
gif mostly works by using reducing the number of colours used to as small a number as possible, can be as low as 2 if you only have 2 colours in the image. then it uses a lossless compression (LWZ, which was patented).

png is lots fancier, you can keep all the colours, and have alpha transparency. it uses a lossless compression

see the [wikipedia article on png]("http://en.wikipedia.org/wiki/Png").

recompressing an image from one format to another will not make the file smaller, unless you are loosing quality in the process and there is less information for the second algorithm to compress. if you want to try a few different formats make each one from the original uncompressed version.

ps: mine is 2.7 k png from an 18.1 k svg

---

### Post by Mr_J_ on 2006-01-19
I think it can be a good idea as a prefered way to put your avatars.
I believe that I can see a bit of a diference, but could you try to see if the result of changing an uncompressed png to gif as better results than the one you have currently?

---

### Post by psychicdragon on 2006-01-19
I think it's a good idea. If everyone's avatar could be redused in size (bytes) by about 50%, or more, the net savings in bandwidth would probably be quite substantial. Considering the size (pixels) of the images a loss in quaility isn't really noticable anyway.

What software did you use to compress your avatar? I don't really want to have to install the gimp or similar to compress mine...

---

### Post by Omnios on 2006-01-19
8.8k .gif also a 2.3 and 2.8 jpg

---

### Post by Omnios on 2006-01-19
[QUOTE=Mr_J_]I think it can be a good idea as a prefered way to put your avatars.
I believe that I can see a bit of a diference, but could you try to see if the result of changing an uncompressed png to gif as better results than the one you have currently?[/QUOTE]

 A 8.5K  png and a 6.2K  gif personaly the gif looses a tad little.

---

### Post by chiefofthejojos on 2006-01-19
I never realized that it would make a difference!  I've compressed mine from 15k to 3k.

---

### Post by majikstreet on 2006-01-19
compressed looks bad to me, btw.

---

### Post by Malphas on 2006-01-19
If saving the server's bandwidth is the goal here it would make more sense to simply link to offsite images, if you don't have your own webspace you can just use a free service such as Photobucket  (however the administrators have disabled this option so it would seem that avatar filesize isn't that much of an issue for them).  If the issue is forum speed you can simply go to UserCP > Options and disable the "Show Avatars" option.

---

### Post by imagine on 2006-01-19
It doesn't really matter if GIF is free or not, because it is inferior to PNG in every way but one:
PNG pictures cannot be animated. There is MNG but most browsers don't support that, so it's no good idea to use it on the web.


And as a sidenote, because it is done wrong so often, even by people who are supposed to have a good knowledge about computers in general: Don't save screenshots of applications, menus, consoles, etc in JPEG. They are big *and* look crappy, compared to PNG or even GIF.
[http://www.r1ch.net/img-formats/](http://www.r1ch.net/img-formats/)

---

### Post by wmcbrine on 2006-01-20
Omnios, the reason you get a smaller image after you convert it to GIF is that you're palettizing it: throwing away colors. GIF can only handle up to 256 colors per image.

You can do the same thing in PNG, but PNG *allows* more colors, so it doesn't happen automatically. But converting a true-color image to GIF always entails palettizing as the first step. (I don't know what you're using to convert, but that step also throws up a warning prompt in most programs.)

---

