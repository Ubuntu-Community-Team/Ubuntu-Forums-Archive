---
title: "Ristretto, Thunar for Picture-viewing"
date: 2007-09-18
forum: The Cafe
---

### Post by Steveway on 2007-09-18
Everyone should know the awesome thunar filemanager.
It's fast, powerfull and looks hot.
XFCE has many nice applications.
The pretty new Squeeze is a very fast archivemanager: [http://squeeze.xfce.org/](http://squeeze.xfce.org/)
There are many more nice apps for XFCE but today I want to talk about Ristretto.
Ristretto is like thunar for photoviewing.
It's fast, powerfull and looks very nice.
[http://goodies.xfce.org/projects/applications/ristretto](http://goodies.xfce.org/projects/applications/ristretto)
A few weeks ago, when I tried 0.0.4 it wouldn't show pictures, only the thumbnails worked.
But I tried it again today, running ristretto 0.0.6-svn-r03234, compiled it myself, it works and it is really awesome.
I can upload a .deb I made with ceckinstall, but it will remove /usr/local/share/icons/hicolor/icon-theme.cache , so you'll have to force-install it.
It shouldn't be a problem if that get's overwritten, AFAIK, and I dunno why ristretto wants to overwrite it.
The easiest way is to compile it yourself from SVN, 
```
svn co http://svn.xfce.org/svn/goodies/ristretto/trunk ristretto
cd ristretto
./autogen.sh
make
sudo make install
or 
sudo checkinstall
```
You need of course the needed development-files from the repos.
And here a screenshot from it's site:
[IMG]http://goodies.xfce.org/_media/projects/applications/ristretto-screenshot.png[/IMG]

---

### Post by fuscia on 2007-09-18
is there a way to load a wallpaper from ristretto?

---

### Post by Steveway on 2007-09-18
Not that I know of, but a way to set the xfdesktop wallpaper with it would be nice.
It shouldn't be to hard to implement.
I'm pretty new to C but I'll take a look into it.
And if I can't figure it out, then I'll forward it to Stephan.
EDIT: Damn you buggy aiptek-driver! I just managed to add a button to the edit-menu with the label "Set as Wallpaper".
Then I surfed a bit to find out how to make xfdesktop change to a picture, I checked back, looked a bit in main.c, when suddenly Gedit just closed itself.
Well it didn't close itself but the buggy aiptek-driver killed it together with what I reached.
I'll just mail Stephan, he'll sure be able to do it.

---

### Post by kadath on 2007-09-19
I might have to compile this and try it out.

If you set it to be the default app for viewing images, when you click on an image in Thunar, does Ristretto open the image full size, while resizing the window to fit?

---

### Post by Steveway on 2007-09-19
> **kadath said:**
> I might have to compile this and try it out.

If you set it to be the default app for viewing images, when you click on an image in Thunar, does Ristretto open the image full size, while resizing the window to fit?

Well it seems to remember the size of the window it last had and fits the picture into it.

I mailed Stephan and he said that he really wants to implement this, but xfdesktop needs to be fixed a little bit for it, so other apps can easily change the wallpaper with a command.
I'll just quote him:
> Therefore, for me to add
this feature to ristretto I need to either patch xfdesktop 4.4 (a
patch which won't get accepted if it changes the strings in the
translations), or write a patch for trunk, in which case it will work
with xfce 4.6.

Right now I am still working on some stability and performance issues
with ristretto, (it is by far not as stable as it should be) but when
that is done, I will discuss the feature with the xfdesktop
maintainer.
So lets wait for XFCE4.6, wich should be an awesome release.

---

### Post by kadath on 2007-09-19
> **Steveway said:**
> Well it seems to remember the size of the window it last had and fits the picture into it.

I mailed Stephan and he said that he really wants to implement this, but xfdesktop needs to be fixed a little bit for it, so other apps can easily change the wallpaper with a command.
I'll just quote him:

So lets wait for XFCE4.6, wich should be an awesome release.

Awesome. I can't wait for Xfce 4.6 too :)

---

