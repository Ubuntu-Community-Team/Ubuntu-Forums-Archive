---
title: "gthumb configuration."
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2014-04-03
Can anyone tell me how to get to any configuration dialogue for the version of gthumb in 14.04.  There is no menubar, no way to change the horrible look of the icons in the edit image window or add any text labels to the icons and there is no way that I can find to set preferences such as the placement of the thumbnails when using the viewer, nor the folder I wish the application to use at startup.

This all seems to be a very retrograde step, dumbing it down and removing a useful way of setting preferences, unless I am simply not seeing something obvious.  Is this an upstream gnome decision about which ubuntu can do very little?  I have been using gthumb for a very long time and it had become my favourite picture and photo organiser; now I'm not so sure.

---

### Post by slickymaster on 2014-04-03
I think that you won't be pleased to know that it has been voted by the [Xubuntu Team]("https://launchpad.net/~xubuntu-team"), on [2014-02-13]("http://ubottu.com/meetingology/logs/xubuntu-devel/2014/xubuntu-devel.2014-02-13-19.01.log.html"), that from Trusty Tahr on, gThumb is dropped and removed from the seed, so it won't be shipped with Xubuntu anymore.

Starting in Trusty, Xubuntu will only ship Ristretto as Image-viewer for the Xfce Desktop Environment.

---

### Post by ajgreeny on 2014-04-03
But it is still in the repos so that does not really matter, and ristretto is not and will never be an application to manage and edit photos etc as gthumb is.

Is it even possible to get the menubar back and set preferences as was possible in previous versions, eg 3.1.2, or has that option disappeared for ever, never to return?

---

### Post by slickymaster on 2014-04-04
You can always [file a bug report upstream]("https://bugzilla.gnome.org/enter_bug.cgi?product=gthumb"), requesting that feature.

---

### Post by philinux on 2014-04-04
> **ajgreeny said:**
> Can anyone tell me how to get to any configuration dialogue for the version of gthumb in 14.04.  There is no menubar, no way to change the horrible look of the icons in the edit image window or add any text labels to the icons and there is no way that I can find to set preferences such as the placement of the thumbnails when using the viewer, nor the folder I wish the application to use at startup.

This all seems to be a very retrograde step, dumbing it down and removing a useful way of setting preferences, unless I am simply not seeing something obvious.  Is this an upstream gnome decision about which ubuntu can do very little?  I have been using gthumb for a very long time and it had become my favourite picture and photo organiser; now I'm not so sure.

Mouse up to top left you'll see the only menu option there which is also called gthumb. Click that to get the preferences window.

Not as good an app as it used to be.

---

### Post by ajgreeny on 2014-04-04
> **philinux said:**
> Mouse up to top left you'll see the only menu option there which is also called gthumb. Click that to get the preferences window.

Not as good an app as it used to be.
I can't find any menu on my gthumb by mousing to top left.  Here's my gthumb window from trusty Xubuntu.  Where does the mouse go to find a menu like the one you show; I have put it everywhere and nothing appears when clicked.

---

### Post by 23dornot23d on 2014-04-04
I just had a quick look - and activated it from clicking a picture and choosing gthumb as the default application.

A few more menus were visible - but still not sure how to get to do what you want and add text change icons etc.

Video here of the quick test I did with it ........... [http://youtu.be/KCND4z5RS2A](http://youtu.be/KCND4z5RS2A)

---

### Post by alan-pater on 2014-04-04
Upstream bug report is here: [https://bugzilla.gnome.org/show_bug.cgi?id=724238](https://bugzilla.gnome.org/show_bug.cgi?id=724238)

And a suggestion to revert to version 3.2.6 until that gets fixed: [https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/1290691](https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/1290691)

It appears that gthumb version 3.3 is optimized for a Gnome Desktop, and that results in some missing functions on other desktops.

---

### Post by mc4man on 2014-04-04
While you're waiting a fix, if there is one, you could just try using the version of gthumb in 13.10. You'd need to replace 2 packages - 
gthumb
gthumb-data
If inclined go here  for data package, (used in both i386 & amd64
[http://packages.ubuntu.com/saucy/gthumb-data](http://packages.ubuntu.com/saucy/gthumb-data)
And then here, pick arch, dl package
[http://packages.ubuntu.com/saucy/gnome/gthumb](http://packages.ubuntu.com/saucy/gnome/gthumb)

Stick them both in an empty folder, cd to folder in terminal & run
```
sudo dpkg -i *.deb
```

Maybe it works ok, maybe not. If not then just upgrade back or remove altogether

---

### Post by ajgreeny on 2014-04-05
For the time being I have installed the debs of 3.2.6 which were available from [http://launchpadlibrarian.net/162929872/gthumb-data_3.2.6-1ubuntu2_all.deb](http://launchpadlibrarian.net/162929872/gthumb-data_3.2.6-1ubuntu2_all.deb) and [http://launchpadlibrarian.net/162929685/gthumb_3.2.6-1ubuntu2_amd64.deb](http://launchpadlibrarian.net/162929685/gthumb_3.2.6-1ubuntu2_amd64.deb), and that gives me back a sensible GUI again, so I have now locked the versions in synaptic to avoid them being upgraded in normal updates.

I will keep looking for the proper version to be made more usable in other than gnome-shell DEs and upgrade to that when it becomes available.

These two .debs are more recent versions than the saucy version, and were originally the proposed versions for trusty before the disaster of 3.3.1 came along.

---

### Post by philinux on 2014-04-05
> **ajgreeny said:**
> I can't find any menu on my gthumb by mousing to top left.  Here's my gthumb window from trusty Xubuntu.  Where does the mouse go to find a menu like the one you show; I have put it everywhere and nothing appears when clicked.

Dang was on smart phone. Did not see xubuntu. I'm using unity. But that preferences menu should be somewhere. It's the same app.

---

### Post by mc4man on 2014-04-05
Unfortunately Gnome seems to never enable an accel for a gnome app's preferences menu. When the app uses an accels file it can be user added (ex. nautilus), but gthumb doesn't.

---

### Post by ajgreeny on 2014-04-05
It does seem strange, and very disappointing, that the gthumb version that was chosen for the whole *ubuntu family of 14.04 systems is one that will not display properly on the DEs that are most popular and one of which must probably be used in 90% of the *ubuntu systems installed, ie unity, xfce, lxde, kde? (not sure about kde, as I've not tried it).

I've not used gnome-shell and have no intention of doing so at the moment, but I imagine there are fewer users of that in *ubuntu than any of the other DEs.

Thank goodness for version 3.2.6!

---

### Post by alan-pater on 2014-04-08
gthumb 3.2.7 is now the default version in trusty. The package maintainer, Jackson Doak, was kind enough to revert to the 3.2 series.

---

### Post by ajgreeny on 2014-04-08
Oh WOW!

Thank-you so much to Jackson Doak for that.

I think gthumb is one of the best photo organisers available; it avoids all the annoying bloat of applications like shotwell or f-spot, etc etc, which I never bother to use as I much prefer simplicity and to import my photos into my own personally organised folders, not allow some grand arrangement of them all by an application that may tag them so they have tags unreadable by all other applications.

---

