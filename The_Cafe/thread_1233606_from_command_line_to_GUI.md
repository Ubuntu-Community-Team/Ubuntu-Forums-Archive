---
title: "from command line to GUI"
date: 2009-08-06
forum: The Cafe
---

### Post by windows-killer on 2009-08-06
Lets do this, post a command and beside it write the GUI way of accomplishing that same task. here is an example:

       


[COLOR="Blue"]**T**[/COLOR]ask-[COLOR="Blue"]**C**[/COLOR]ommand [COLOR="Blue"]**L**[/COLOR]ine-**[COLOR="Blue"]GUI[/COLOR]** way
 
([COLOR="Blue"]**T**[/COLOR]) check for updates ([COLOR="Blue"]**CL**[/COLOR]) sudo apt-get update ([COLOR="Blue"]**GUI**[/COLOR]) System > administration > update manager > check for updates

for your convenience, copy the example and replace the words with the appropriate ones.


have fun:)

---

### Post by Skripka on 2009-08-06
The reason why terminal commands are given in lieu of GUI instructions is that there are 4 or 5 major desktop environments, there are roughly 20 or so window managers...and potentially 25+ ways of accomplishing any one terminal command depending on which specific GUI tool you choose to use instead of the terminal.

Terminal commands are for the most part, distro and GUI agnostic.

---

### Post by windows-killer on 2009-08-06
ok, so lets stick with ubuntu gnome commands

---

### Post by Tibuda on 2009-08-07
You should check this thread: [http://ubuntuforums.org/showthread.php?t=898328](http://ubuntuforums.org/showthread.php?t=898328)

---

### Post by wojox on 2009-08-07
(T) Go to root (CL) cd /. (GUI) Places > Computer > Filesystem (Double Click)

---

### Post by RiceMonster on 2009-08-07
How to open a terminal the GUI way in GNOME

Applications > Accessories > Terminal

Or, you can go to  Preferences > Keyboard shortcuts, and make a custom keyboard shortcut to open a terminal. Mine is Alt-F1.

---

### Post by chriskin on 2009-08-07
i would be more interested in why the OP thinks that open source is dictatorship than expressing my love for the command line way

---

### Post by koenn on 2009-08-07
> **chriskin said:**
> i would be more interested in why the op thinks that open source is dictatorship than expressing my love for the command line way

+1

---

### Post by mcduck on 2009-08-07
([COLOR="Blue"]T[/COLOR]) Resize 100 images and compress them for use in web pages.

([COLOR="Blue"]CLI[/COLOR])
```
for i in *.jpg; convert $i -resize 800 -strip -quality 86 small-$i; done
```

([COLOR="Blue"]GUI[/COLOR])
1. Go to Applications/Graphics/Gimp
2. Go to File/Open
3. Browse to find your image file, and click "Open"
4. Go to Image/Scale Image
5. Set the image width & height and click "Scale"
6. Go to File/Save As
7. type new name for your image and click "Save"
8. Adjust the Quality-scale to 85
9. Click "Advanced Options"
10. Enable "Optimize, and disable "Save thumbnail"
11. Click "Save"
12. Close the image.
13. Go to File/Open
14. Browse to find your next image file, and click "Open"
15. Go to Image/Scale Image
16. Set the image width & height and click "Scale"
17. Go to File/Save As
18. type new name for your image and click "Save"
19. Adjust the Quality-scale to 85
20. Click "Advanced Options"
21. Enable "Optimize, and disable "Save thumbnail"
22. Click "Save"
23. Close the image.
24. Go to File/Open
25. Browse to find your next image file, and click "Open"
.
.
repeat until you decide that actually posting uncompressed 6000x4000 images to web is quite fine and you didn't really want to resize your images anyway.

---

### Post by chriskin on 2009-08-07
there is also a nautilus script that you just choose all the images you want to resize, right click on one ---> resize images , choose what you want and press ok :)

---

### Post by mcduck on 2009-08-07
> **chriskin said:**
> there is also a nautilus script that you just choose all the images you want to resize, right click on one ---> resize images , choose what you want and press ok :)

Yes, and several other batch image converters. Still, none of them provides the same amount of functionality and options you get with Gimp or Imagemagick. (for example nautilus-image.-converter doesn't have same kinds of options for resizing by using max size limits while maintaining aspect ratio, and it doesn't support stripping metadata from images.) And that was just an example of simplest possible image processing..

Of course there's also a Gimp plugin for batch processing, but you'll still end doing quite many steps to create your batch process, compared to single command in CLI.

edit: Besides, I was easily able to type the CLI command from memory, while the GUI process required me to open Gimp and check the options and menu items etc step-by-step while writing the instructions.

---

### Post by chriskin on 2009-08-07
true :) i just mentioned an alternative

---

