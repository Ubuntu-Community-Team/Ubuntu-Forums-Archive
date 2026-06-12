---
title: "Need some education/links wrt splash screens."
date: 2012-08-09
forum: The Cafe
---

### Post by mips on 2012-08-09
Feeling lazy not in the mood to sift through google results.

Currently very happy with my setup except I have a mismatch of splash screen in my custum ubuntu 12.04 xfce 4.10 setup.

Grub2 uses a ugly debian background image
Plymouth uses the default Xubuntu 12.04 images
LightDm just has garbage on the screen
Logoff/shutdown just shows text.
XScreensaver default out of the box

I would like to get a seamless/consistent greyish theme across all these apps going. Also want a nice simple progress indicator for plymouth & loggoff/shutdown.

Does anyone have any links that are easy to follow on how to implement this for all the above.

Are there any good utils that could automate this for all or single instances of the above?

I suck at gfx artwork so if anyone knows of any existing plain grey themes that I could just change the colour of it would be great.

Last question, what are the max resolutions supported by all the above? I have a 1920x1080 lcd and the current plymouth slpash does not fill the entire screen and grub is very low res for example.

Just feel it's time to 'fix' all these things after so many months of just living with the current setup.

---

### Post by Jakin on 2012-08-09
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

Will let you put whatever as the grub2 background

---------------------------------

[http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html](http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html)

might this work for your splash? i dont have a resolution that big, so i can't really help there..

Pretty sure ubuntu tweak will allow you to change the lightDM background, as well.

---

### Post by mips on 2012-08-09
Ignore my fist post for now. I will ask more specific questions from here onwards.

I managed to get a consistent theme going from grub all the way to lightdm. I just edited the existing xbuntu theme background.

From boot until the lightdm screen (about when nvidia driver loads) I do not have full screen coverage, everything from the bios screen up to and including plymouth has a black border around the entire image. I've set the lcd (samsung syncmaster p2350 & nvidia 9600gt) to auto adjust but that does not help.

Any ideas on how to fix the above problem?

Second issue I have is that I don't know how to change the colours of the existing xubuntu logos and progress indicator in gimp/pinta, using FILL just creates a big blotch of colour all over the show. I would like to change these logos from white to grey.

---

### Post by Jakin on 2012-08-09
well if you are using gimp, could try the "colorize" function, sorry i still dunno how to help with the resolution issue..

Best way to do it is select the bit with the logo- and work with it in a different window, find the hex color of the background best you can and then make that color transparent ( layer- transpareny- color to alpha)

then "semi-flatten" and use colorize to make it the shade of gray (or whatever color)you want, paste the edited logo back onto the original image.

EDIT: or even easier- find a png image of the xubuntu logo somewhere, colorize it and paste over- ontop the image you wanted to edit [https://www.google.com/search?client=ubuntu&channel=cs&q=xubuntu+logo&um=1&ie=UTF-8&hl=en&tbm=isch&source=og&sa=N&tab=wi&ei=OaQjUOCoCqT30gH3wICwBQ&biw=1366&bih=606&sei=O6QjUKTJFemO0QHW54GwDw](https://www.google.com/search?client=ubuntu&channel=cs&q=xubuntu+logo&um=1&ie=UTF-8&hl=en&tbm=isch&source=og&sa=N&tab=wi&ei=OaQjUOCoCqT30gH3wICwBQ&biw=1366&bih=606&sei=O6QjUKTJFemO0QHW54GwDw) one that alreadh has transpancy in a png is best.

---

### Post by mips on 2012-08-09
I managed to invert the white logo colours to black and the coloured progress bar background I changed to B&W via the Adjustments menu in Pinta which was really easy to do.

The black on dark grey looks really good! Only problem is in black the resolution looks a bit low as opposed to when it was in white. Sigh, I suck at artwork :biggrin:

---

### Post by Jakin on 2012-08-09
Glad you figured something out :D

---

