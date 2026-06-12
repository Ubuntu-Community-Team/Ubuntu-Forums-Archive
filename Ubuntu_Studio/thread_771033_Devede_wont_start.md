---
title: "Devede wont start"
date: 2008-04-27
forum: Ubuntu Studio
---

### Post by bmenge on 2008-04-27
Devede not loading error importing mplayer.  I tried to reinstall mplayer and devded no changes.

This is the code I got;
Traceback (most recent call last):
  File "/usr/local/bin/devede", line 33, in <module>
    import mplayer
ImportError: No module named mplayer

I opened /usr/local/bin/devede and didn't really know what I was looking at but there is a command to import mplayer.  I did notice that I can not open anything with mplayer so I would think that the problem started there but am not sure where to go after that.  

I tried a few searches on this forum and on google, none of which seemed to lead me in the right direction.



Edit: Maybe I should have statred a new thread but I will stick with this for now.

This is what I get when I type mplayer in the command line;
mplayer: error while loading shared libraries: libdirectfb-0.9.so.24: cannot open shared object file: No such file or directory

So it is definitely mplayer not devede with the error.

---

### Post by bmenge on 2008-04-27
ok I am only digging a bigger hole I think.  I did some more searching on google and found that there was a comment somewhere about not being able to use copies of mplayer and I also had gmplayer in my usr/local/bin folder.  I removed the mplayer folder and tried to remove the import mplayer line in the devede file this did not work as it only gave me the same error but with gmplayer.  Gmplayer does work for me so I was hoping this would be an ok fix but it wasn't  I then check to see if I had another copy of mplayer that I was not aware of and when I rand the mplayer command I got an error.  I figured that removing the folder created a problem so it seemed logical to use apt to remove mplayer and reinstall.  This is the error I get know when I try to use mplayer from the command line;


brian@brian-desktop:/usr/share$ mplayer
bash: /usr/local/bin/mplayer: No such file or directory
brian@brian-desktop:/usr/share$ cd /usr/local/bin
brian@brian-desktop:/usr/local/bin$ ls
bungee_gtk  cycas3_verbose  devede~    dvddirdel    gmplayer  mencoder   spumux
cycas3      devede          dvdauthor  dvdunauthor  gpsbabel  mpeg2desc  spuunmux

---

### Post by bmenge on 2008-04-28
ok I got mplayer to run without any errors from the terminal now I am back to just having problems with devede.  I am still getting this error with devede.  Some one has to have an idea

brian@brian-desktop:~$ devede
Traceback (most recent call last):
  File "/usr/local/bin/devede", line 33, in <module>
    import mplayer
ImportError: No module named mplayer

---

### Post by bmenge on 2008-04-29
[http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2](http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2) ok I found the fix  I overlooked this because all the documentation I saw stated poor audio quality.  Audio quality was not my problem so I never thought to try it, maybe someone can use this info in the future.

---

