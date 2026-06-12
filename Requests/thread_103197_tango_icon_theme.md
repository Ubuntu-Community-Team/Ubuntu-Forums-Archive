---
title: "tango icon theme"
date: 2005-12-13
forum: Requests
---

### Post by sect2k on 2005-12-13
I wish for tango icon theme 0.6.1 to be backported to breezy.

I know the dapper package works fine, but having it in backports woulde just be more convenient.

Cheers,
/me

---

### Post by arpunk on 2005-12-13
You can easily download the unofficial tango icons from art.gnome.org, or better, with the *art manager* in *System*, *Preferences* if you have it installed.

---

### Post by sect2k on 2005-12-14
I installed the dapper package just fine using dpkg, but as I said, having tango in backports would be so much more convenient.

And since it has no dependencies, I would imagine this would be one of the easiest backports ever.

Cheers,
/me

---

### Post by jdong on 2005-12-14
There is actually one build dep on icon-naming-utils that'll need backporting. I need to investigate this a bit more.

---

### Post by benplaut on 2005-12-19
[QUOTE=jdong]There is actually one build dep on icon-naming-utils that'll need backporting. I need to investigate this a bit more.[/QUOTE]

it would be nice for tango to be backported... convenience :)

btw, jdong - you have an awesome sig!!

---

### Post by SpEcIeS on 2005-12-19
[QUOTE=arpunk]You can easily download the unofficial tango icons from art.gnome.org, or better, with the *art manager* in *System*, *Preferences* if you have it installed.[/QUOTE]
Never knew about that one. Nice tool and a must have in the install. :)

---

### Post by Joao_a on 2006-02-05
I'm using Kubuntu with KDE 3.5 and here is how i did tu use the tango icons:
(after reading this [http://www.kde-look.org/content/show.php?content=32288]("http://www.kde-look.org/content/show.php?content=32288") )


**1--** In a terminal type:

```

$ sudo apt-get install checkinstall

$ sudo apt-get build-dep icon-naming-utils tango-icon-theme

$ sudo apt-get remove icon-naming-utils tango-icon-theme

```

**2--** Download the latest icon-naming-utils and tango-icon-theme archives.
[http://tango-project.org/Tango_Icon_Library#Download]("http://tango-project.org/Tango_Icon_Library#Download")

**3--** Decompress those archives.

**4--** Go to the "icon-naming-utils" folder, open a terminal and type:

```

$ ./configure --prefix=`kde-config --prefix`

$ make

$ sudo checkinstall

```

**5.1--** Go to the "tango-icon-theme" folder, open a terminal and type:

```

$ ./configure --prefix=`kde-config --prefix` --enable-png-creation

$ make

```

**5.2--** Open the "index.theme" file (located on the "tango-icon-theme" folder):
[LIST]
[*]replace all the "Context=..." by "Context=FileSystems"
[*]save and exit
[/LIST]

**5.3--** Return to the terminal (on the "tango-icon-theme" folder) and type:
```

$ sudo checkinstall

```


You should now by able to select the Tango Icon Theme on KControl!
(i hope it works!)

---

### Post by Moises Cabello on 2006-02-05
[QUOTE=Joao_a]
You should now by able to select the Tango Icon Theme on KControl!
(i hope it works!)[/QUOTE]

All ok, but the folders still are the original kde ones :cry:

---

### Post by niviche on 2006-02-08
[QUOTE=Joao_a]You should now by able to select the Tango Icon Theme on KControl!
(i hope it works!)[/QUOTE]

Thanks a lot, I had been looking for this for a long time. I like KDE a lot, but never found any good icon set for it.
Your method works fine, congratulations. However, I guess there is some problem with the way some icons are used in KDE (something to do with the SVG conversion, maybe), as my icons are somehow slightly different than the screenshots, with blunter, darker shadows. The folders icons are also weirdly blue and white, unlike anything I have seen from Tango so far.

---

### Post by Joao_a on 2006-02-09
First of all, it's not my method: i just applied what superiodico said on kde-look.org ([http://www.kde-look.org/content/show.php?content=32288]("http://www.kde-look.org/content/show.php?content=32288"))

**to Moises Cabello:**
> All ok, but the folders still are the original kde ones
Did you replace all the "Context=..." by "Context=FileSystems" in index.theme *before* doing the checkinstall? I forgot to do this once and i got the original folder icon...

**to niviche:**
> However, I guess there is some problem with the way some icons are used in KDE (something to do with the SVG conversion, maybe), (...)
It did the same to me.

I looked in [http://tango-project.org/Installation]("http://tango-project.org/Installation") and they say librsvg does a better job than ksvgtopng.
I searched in ubuntu archive with adept and find a few packages "librsvg".
I didn't kown wich one to install so i installed all of them! (not the best method to find out wich one is really needed -- if someone has more patience and knowledge than i do...)
The fact is ./configure now doesn't choose ksvgtopng anymore, and the icons are better rendered.

---

### Post by Moises Cabello on 2006-02-14
That was, thanks.

Btw, here is a nice .png tango icon for konqueror. 

[img]http://ramnet.se/~nisse/blog/images/konqueror.png[/img]

The svg source file is [here](http://ramnet.se/~nisse/blog/images/konqueror.svg).

---

