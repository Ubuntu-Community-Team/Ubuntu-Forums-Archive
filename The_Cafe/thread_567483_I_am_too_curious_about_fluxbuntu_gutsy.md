---
title: "I am too curious about fluxbuntu gutsy"
date: 2007-10-04
forum: The Cafe
---

### Post by Gargamella on 2007-10-04
Everyone is waiting for gutsy to come (except dapper users, LTS rocks, I know).
The biggest thing that makes me mad about this ubuntu release, is the fluxbox version by the fluxbox team:can't wait for it.

There is already the countdown on fluxbuntu.org

I have also a pentium celeron 400 and 64 MB ram PC ready to run it........... CAN'T WAIT MEN TELL ME MORE!!!:lolflag::lolflag::lolflag:

---

### Post by yabbadabbadont on 2007-10-04
Why wait?  Build fluxbox from SVN and have fun.  It isn't difficult and doesn't take very long to build.  (on most machines)

---

### Post by ArtF10 on 2007-10-04
Well fluxbuntu.org appears to have 3 screenshots, that look pretty good and improved.  I beginning to get a bit excited myself.

Were there any specific propblems with Fluxbuntu that will be addressed?

---

### Post by mrgnash on 2007-10-04
It looks pretty. I want it. It's such a shame they don't have the meta-package what not in Gutsy Beta already :(

---

### Post by ArtF10 on 2007-10-04
I have read some stuff and don;t really know if I understood...

Can I change the Fluxbuntu wallpaper and ensure that the NEW wallpaper shows up everytime on startup or does it automatically reset to the default wallpaper?

---

### Post by wana10 on 2007-10-04
you can change wallpaper and ensure it always loads with fluxbox. easiest way to do this is a terminal input of
fbsetbg -f /path/to/wallpaper

i'm definitely going to give fluxbuntu a try, having been using fluxbox on feisty for a while now it seems like the natural progression

---

### Post by ArtF10 on 2007-10-04
when you mean /path/to/wallpaper what does that mean?

say I save the wallpaper on the desktop(hopefully I can do this with FluxWM) would I need to replace 

/path/to/wallpaper

by 

/desktop/wallpaperor is there a / missing?

---

### Post by fwojciec on 2007-10-04
Linux paths are case sensitive.  Desktop is usually **D**esktop, full path to desktop would be>  ~/Desktop or>  /home/[user]/Desktop (where [user] is you user name)

---

### Post by wana10 on 2007-10-04
what fwojciec said
~/Desktop/wallpaper_name.file_type

ex: in my case i use /home/wana10/documents/pictures/wallpaper/gurren-grave.png

now i realize that can be a mouthful (or a terminal full as the case may be) so there is a program to help you, [nitrogen]("http://l3ib.org/nitrogen/"). now i couldn't get this set up, it kept complaining about libc6 but i know others who use it and love it.

edit* scratch that, finally buckled up and installed nitrogen from source. i needed a package called lib-gtkmm-2.4-dev or some such thing...of course i didn't know that till the install barked at me. anyways, now i have it and i concur with the others...it is pretty awesome and easy to use.

---

### Post by ArtF10 on 2007-10-05
> **wana10 said:**
> ...edit* scratch that, finally buckled up and installed nitrogen from source. i needed a package called lib-gtkmm-2.4-dev or some such thing...of course i didn't know that till the install barked at me. anyways, now i have it and i concur with the others...it is pretty awesome and easy to use.

Did you do this in a terminal?  If so, could you post the code?

---

### Post by wana10 on 2007-10-05
> **ArtF10 said:**
> Did you do this in a terminal?  If so, could you post the code?


i have to confess i stole it. go [here]("http://sudan.ubuntuforums.com/showpost.php?p=3073307&postcount=400") and follow the instructions. however instead of sudo make install at the end i used sudo checkinstall. this will create a nitrogen .deb so if you ever feel the need to remove it you can do so easily.

if you want to add nitrogen to your flux menu it installs to /usr/local/bin/nitrogen

---

### Post by Tux Aubrey on 2007-10-05
I may be missing something here, but what's the big deal about setting wallpaper?

Install feh (sudo apt-get install feh)

and use

> session.screen0.rootCommand: fbsetbg -l 

in the ~/.fluxbox/init file.  This will automatically reset the wallpaper to the last one used.

If you are using Rox-filer as your desktop, the wallpaper is sticky anyway.

Fluxbuntu has been way too silent for way too long, IMHO. And I'm not clear on what it is really offering that you can't do manually with Synaptic and a few tweaks.

I now just use the fluxbox in the Feisty repositories and hack away using one of the many great "how-tos", such as [this one]("https://help.ubuntu.com/community/Fluxbox") or [this one]("http://ubuntuforums.org/showthread.php?t=371144").

---

### Post by wana10 on 2007-10-05
> **Tux Aubrey said:**
> I may be missing something here, but what's the big deal about setting wallpaper?

Install feh (sudo apt-get install feh)

and use

```
session.screen0.rootCommand: fbsetbg -l
```

in the ~/.fluxbox/init file.  This will automatically reset the wallpaper to the last one used.

If you are using Rox-filer as your desktop, the wallpaper is sticky anyway.

Fluxbuntu has been way too silent for way too long, IMHO. And I'm not clear on what it is really offering that you can't do manually with Synaptic and a few tweaks.

I now just use the fluxbox in the Feisty repositories and hack away using one of the many great "how-tos", such as [this one]("https://help.ubuntu.com/community/Fluxbox") or [this one]("http://ubuntuforums.org/showthread.php?t=371144").

that will reset wallpaper to last one used, but setting one can sometimes be a piece of work...if you've never done it before. yeah i know about feh and use that command in my flux init file, as well as fbsetbg from terminal, but not everyone wants to do it like that, and if your new to fluxbox you wouldn't have a clue about anything like that.

---

### Post by Gargamella on 2007-10-05
I have a really old machine, I hope they will have an alternative disc too, I had problem with the previous dev release and was too slow for me.
For this reason I don't install an ubuntu release putting in a fluxbox desktop then.

BTW does anyone know which programs will be in fluxbuntu?

---

### Post by Kowalski_GT-R on 2007-10-05
I'm more than curious, i actually b****y NEED it!

Can't wait myself.

ciao,

Andrea


(already tried the Ubuntu minimal installation, but found configuring fluxbox too time-consuming for my needs: Fluxbuntu looks quite polished from the screenshots)

---

### Post by Tux Aubrey on 2007-10-05
You could try Mepis Antix - its a minimal Debian-based install (288MB) with a very functional Fluxbox desktop.

See [THIS LINK]("http://antix.mepis.org/index.php/Main_Page") for info and links to the latest release candidate iso.

---

### Post by Gargamella on 2007-10-05
> (already tried the Ubuntu minimal installation, but found configuring fluxbox too time-consuming for my needs: Fluxbuntu looks quite polished from the screenshots)

exactly the same for me...I will enjoy the finished work ;D

---

### Post by ArtF10 on 2007-10-05
I don;t know for sure but I think that a minimal install using an Ubuntu CD/Alternate CD will give an even more lightweight system than the Fluxbuntu installation.

> **Tux Aubrey said:**
> You could try Mepis Antix - its a minimal Debian-based install (288MB) with a very functional Fluxbox desktop.

See [THIS LINK]("http://antix.mepis.org/index.php/Main_Page") for info and links to the latest release candidate iso.

Does that Conky (or equivalent) thing on the desktop come as part of the distro or is it something that was added?

---

### Post by John.Michael.Kane on 2007-10-05
> **ArtF10 said:**
> I don;t know for sure but I think that a minimal install using an Ubuntu CD/Alternate CD will give an even more lightweight system than the Fluxbuntu installation.



Does that Conky (or equivalent) thing on the desktop come as part of the distro or is it something that was added?

Yes conky is included with antix, and setup with default settings. You will have to adjust the settings to suit your needs.

---

### Post by Incense on 2007-10-05
> **Gargamella said:**
> BTW does anyone know which programs will be in fluxbuntu?

I was wondering this as well.

---

### Post by Sunflower1970 on 2007-10-05
After looking at the homepage for Fluxbuntu, I'm very intrigued. It looks beautiful.  :D

I know I'll be d/l this one for my oldest computer and try it out...

---

