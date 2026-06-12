---
title: "Tree view gone in Nautilus :("
date: 2013-04-07
forum: Ubuntu Development Version
---

### Post by abovett on 2013-04-07
I'm probably late to the party, but I've just loaded the Raring beta and was _very_ disappointed to find that tree view is gone in Nautilus. This means that the file manager can no longer display an  overview of the file hierarchy. It also means that Nautilus is not much use for moving or copying files to multiple disparate folders which don't share a common parent (for example when sorting out and categorising a bunch of files) or tidying up a file system hierarchy. For me these are common use cases. I realise that not everyone uses Tree view, but when you have 1000's of folders, many levels deep, and 10,000's of files I think it's hard to manage the file system without it.

I now understand that this is an upstream Gnome decision (though one I can't begin to comprehend - their reasons make no sense to me). Whilst it's possible to load other file managers such as Nemo they won't integrate as well into the Unity interface as the native one. Does anyone know if the Ubuntu devs are considering how to address this? I regard it as a vary significant regression in functionality and I hope that they will do something about it. 

Regards

Andy

---

### Post by IanW on 2013-04-07
The upstream decision was reversed rather quickly, and tree view returned in version 3.7.90, available in the Gnome3 PPAs.
Sadly, Ubuntu devs have chosen to give us version 3.6.3.

---

### Post by dino99 on 2013-04-07
dconf-tools can change that default choice easily

---

### Post by pfeiffep on 2013-04-07
> [COLOR=#000000]dconf-tools can change that default choice easily[/COLOR]

I'm certainly no expert - I searched dconf and failed to find an option enabling tree view  gnome session fall back on 13.04

Mind elaborating a bit please?

---

### Post by Harry33 on 2013-04-07
> **IanW said:**
> The upstream decision was reversed rather quickly, and tree view returned in version 3.7.90, available in the Gnome3 PPAs.
Sadly, Ubuntu devs have chosen to give us version 3.6.3.

Well I haven't found the way to set the list view into the sidebar and the icon view into the main window.
This was how it used to be the old Nautilus.

It is possible to set the list view into the main window, however.
I am using v. 3.8.

---

### Post by dino99 on 2013-04-07
> **pfeiffep said:**
> I'm certainly no expert - I searched dconf and failed to find an option enabling tree view  gnome session fall back on 13.04

Mind elaborating a bit please?

org.gnome.nautilus.list-view.use-tree-view true

---

### Post by althu on 2013-04-07
> **dino99 said:**
> org.gnome.nautilus.list-view.use-tree-view true

thanks to you I could change the defalut zoom level.
but I could not find the tree-view option you said.

---

### Post by dino99 on 2013-04-07
note: does not know if it makes a difference, but i'm using the gnome3 ppas

---

### Post by jbicha on 2013-04-07
> **IanW said:**
> The upstream decision was reversed rather quickly, and tree view returned in version 3.7.90, available in the Gnome3 PPAs.
Sadly, Ubuntu devs have chosen to give us version 3.6.3.

Well it's slightly different. It's tree view in the main view instead of in the sidebar.

> **dino99 said:**
> org.gnome.nautilus.list-view.use-tree-view true

That will only work with Nautilus 3.7+ but you can also just enable it there in Preferences>Display>Navigate folders in a tree.

---

### Post by pfeiffep on 2013-04-07
>  [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG][COLOR=#000000] Originally Posted by [/COLOR]**dino99**[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12592397#post12592397")
[COLOR=#000000]*org.gnome.nautilus.list-view.use-tree-view true*[/COLOR]


Thanks dino99
I'm using gnome session fallback so I suppose that's why the list view is not present:confused: - I searched the entire gnome section and found nothing regarding tree view...I'll login using Unity and try again

Interesting when using Unity and searching for preferences I found this:
> **[SIZE=4]nautilus crashed with SIGABRT in raise()[/SIZE]**



So [COLOR=#333333][FONT=Ubuntu]**Bug #424956**[/FONT][/COLOR] has been reported to launchpad many times ... I thing I'll stop looking for now. This exercise was just for me to learn some more!

> [COLOR=#000000]That will only work with Nautilus 3.7+ but you can also just enable it there in Preferences>Display>Navigate folders in a tree.[/COLOR]

I tripped on my ignorance since I could not find preferences in unity

---

### Post by jbicha on 2013-04-07
> **pfeiffep said:**
> I tripped on my ignorance since I could not find preferences in unity

I think I phrased my last response badly. Both the gsettings and the preference are only available in Nautilus 3.7 or higher. You can get to preferences by clicking Files in the menu bar at the top left of the screen. That is how the newest GNOME3 apps work.

---

### Post by lapaza on 2013-05-30
[h=1][GET NAUTILUS 3.4 FEATURES BACK IN UBUNTU 13.04 WITH SOLUSOS PATCHED NAUTILUS]("http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html")[/h][http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)

Works like a charm...

---

### Post by cariboo on 2013-05-30
> **lapaza said:**
> [GET NAUTILUS 3.4 FEATURES BACK IN UBUNTU 13.04 WITH SOLUSOS PATCHED NAUTILUS]("http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html")

Works like a charm...

Does it work on Saucy?

---

### Post by hako1 on 2013-06-16
Thank you! that special Nautilus version works in Raring.  After the poor experience of 12.10, and that useless file manager in 13.04, I was already considering to go back to 12.04, which so far seems to be the best Ubuntu available.

---

### Post by undoIT on 2013-10-10
Such a shame when things get dumbed down and useful features are stripped out. Is this Ubuntu or Gnome's fault? I don't see any reason to remove a useful feature like expandable folders when it was already included and easy to turn on or off in the preferences.

---

### Post by cariboo on 2013-10-10
> **undoIT said:**
> Such a shame when things get dumbed down and useful features are stripped out. Is this Ubuntu or Gnome's fault? I don't see any reason to remove a useful feature like expandable folders when it was already included and easy to turn on or off in the preferences.

The features were removed by Gnome, Ubuntu has added back some of the lost functionality.

---

### Post by undoIT on 2013-10-10
> **cariboo907 said:**
> The features were removed by Gnome, Ubuntu has added back some of the lost functionality.

Gnome has been on a long downhill slide into the abyss of dumbness and decreased user functionality since the release of 3.0 :(

---

