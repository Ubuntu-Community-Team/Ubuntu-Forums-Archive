---
title: "HOWTO: Random Wallpaper and Splash in Xubuntu"
date: 2011-04-15
forum: The Cafe
---

### Post by s7dhansh on 2011-04-15
Here is a script which will randomly select a wallpaper from a folder (recursive) and put it as a splash screen as well, so that when you login, it seems as if the wallpaper has been set immediately before the session loads up. Believe me, it looks awesome!

[http://gist.github.com/921514](http://gist.github.com/921514)

A few requirements:
1. Imagemagick
2. Balou splash screen in xubuntu (installed by default). Go to its settings and change the image file to the splash.jpg created in the script above.
3. Height of xfce panel (bottom one) = 24px. I use only one panel. In case of multiple panels, accordingly the following line in the script can be modified:
convert $TMP_DIR/splash.jpg -gravity south -background black -splice 0x24 $TMP_DIR/wallpaper.jpg

Another addon script you might need is:
[http://gist.github.com/921573]("http://gist.github.com/921573")
What this does is that in case you do not like the current wallpaper, you can delete it using this and go for a new one.

Thats it!

---

