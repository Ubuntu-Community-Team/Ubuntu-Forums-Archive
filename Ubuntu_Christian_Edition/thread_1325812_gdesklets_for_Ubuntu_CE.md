---
title: "gdesklets for Ubuntu CE"
date: 2009-11-13
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-11-13
Gdesklets was broken in jaunty so as I do not included it. But in karmic, it works again. Anyhow, I still do not know how to put it in metapackage so as to install it automatically. What you could do is to install it manually, below is the steps:

[COLOR="Red"]WARNING: DO NOT DO IT IN JAUNTY, THIS IS FOR KARMIC ONLY[/COLOR]

1. sudo apt-get install gdesklets 
2. wget [http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/bible-rss.tar.gz](http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/bible-rss.tar.gz)
3. Launch gdesklet (applications > accesories > gdesklets)
4. On gdesklets Shell, install bible-rss.tar.gz (File > Install Package > and then locate bible-rss.tar.gz )

The gdesklet give a warning that the lines in border could not be remove satisfactorily, but actually it could be removed. Here is the steps:

On configuration windows, uncheck all borders and background options.

DK

---

