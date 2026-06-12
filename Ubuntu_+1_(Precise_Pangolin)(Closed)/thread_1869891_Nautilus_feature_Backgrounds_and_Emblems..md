---
title: "Nautilus feature: Backgrounds and Emblems."
date: 2011-10-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2011-10-26
Anyone else like to see this back for precise. I used to change the background to slate grey. Much easier on the eye.

Bug has been marked invalid. If more people comment and click Affects me too it might get some attention.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/881864](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/881864)

Another too with more info.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/873788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/873788)
Looks like it's not a bug but those whatsit gnome devs again!!!

---

### Post by madjr on 2011-10-26
looks uglier than before (needs make over) and has less features (for now..), but i hope they bring those back !!!

edit:
seems to be marked as invalid because of upstream...
They need to link the bugs with upstream

---

### Post by philinux on 2011-10-30
Is there a way to modify a css file to do this just for nautilus.

---

### Post by r_mano on 2011-11-30
I have not checked, maybe [http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html) could help. But I suppose that changing the theme default background is not what you want.

Sad, this feature-tossing trend.

---

### Post by vasa1 on 2011-11-30
> **philinux said:**
> Is there a way to modify a css file to do this just for nautilus.

Bit of a late response ... but I haven't found a way to restrict css changes to just one thing like Nautilus or gedit or Movie Player **in 11.10**.

The changes affect all gtk-3.0 stuff (sometimes with unintended effects).

---

### Post by r_mano on 2011-11-30
Hmmm... is there any alternative to nautilus for Gnome? That integrates well?

---

### Post by vasa1 on 2011-11-30
> **philinux said:**
> Is there a way to modify a css file to do this just for nautilus.

What about this file:
/usr/share/themes/Ambiance/gtk-3.0/apps/nautilus.css ???

Edit: just did a little tweak. Works! Now to see whether tweaks to this file are really Nautilus-specific and then make further posts elsewhere since this is a U+1 thread and I'm fiddling with Nautilus in 11.10!

---

### Post by r_mano on 2011-11-30
To have emblems back, you can download [https://github.com/allefant/Nautilus-Emblems-Menu-Extension/blob/master/nautilus_emblems_menu.py](https://github.com/allefant/Nautilus-Emblems-Menu-Extension/blob/master/nautilus_emblems_menu.py) and then drop it in your .local/share/nautilus-python/extensions directory. Create it if it doesn't exist. 

It works, albeit with a simple interface (now I do not know how to create new emblems --- albeit I can use the old ones I created).

Is there somewhere a movement to push to have emblems back? I tested Marlin, no joy...

---

### Post by Harry33 on 2011-11-30
> **vasa1 said:**
> What about this file:
/usr/share/themes/Ambiance/gtk-3.0/apps/nautilus.css ???

Edit: just did a little tweak. Works! Now to see whether tweaks to this file are really Nautilus-specific and then make further posts elsewhere since this is a U+1 thread and I'm fiddling with Nautilus in 11.10!

The drawback with a tweak like that is that it will be overwritten by the next update.
And believe me, there will be updates during any dev (Ubuntu + 1) cycle.
The setting should be located in the home directory.

---

### Post by vasa1 on 2011-11-30
> **Harry33 said:**
> The drawback with a tweak like that is that it will be overwritten by the next update. ...
The setting should be located in the home directory.
Yes, I'm aware of that. I even tried but couldn't manage perhaps because I don't fully understand the interplay of the various elements involved.
The css used here is somewhat different than that of web pages :(

What I'm doing is to record any changes in a text file so that I have something to refer to in case of an update/backport.

---

### Post by r_mano on 2011-12-07
I have opened a widhlist request on gnome bugzilla: 

[https://bugzilla.gnome.org/show_bug.cgi?id=665735](https://bugzilla.gnome.org/show_bug.cgi?id=665735)

If anyone agree with me, please sum yourself to the request. Thanks,

---

### Post by r_mano on 2011-12-07
Ok, don't worry. The bug/request have been closed as WONTFIX, and it seems that the decision is irrevocable.

---

### Post by philinux on 2011-12-07
> **r_mano said:**
> Ok, don't worry. The bug/request have been closed as WONTFIX, and it seems that the decision is irrevocable.

I would not mind if I could just change the background from the glaring white.

---

### Post by r_mano on 2011-12-07
Wild guess: maybe it's just a matter of finding the correct "metadata" to add to the directory. Could you go to a directory with a personalized background (from an older nautilus) and issue:

```
gvfs-info -a  metadata:: .
```

then you can set it with gvfs-set-attribute...

---

### Post by Bowmore on 2011-12-07
Well, a first start is to include this section
```
NautilusWindow .view {
    background-color: #BCBFB8;
    color: #000000;
}
```
in the file /usr/share/themes/Ambiance/gtk-3.0/apps/nautilus.css and restart nautilus.  Then change to the colors of your taste.

However there are other things that need to be changed in nautilus.css to make it complete. But, maybe lucazade that updated Ambiance to gtk3+ can assist and maybe refer to some css-guide for Nautilus.

An example of the Nautilus sidebar you can find at OMGUbuntu:
[http://www.webupd8.org/2011/11/download-ambiance-with-dark-nautilus-3.html](http://www.webupd8.org/2011/11/download-ambiance-with-dark-nautilus-3.html)

---

### Post by ranch hand on 2011-12-07
> **r_mano said:**
> Hmmm... is there any alternative to nautilus for Gnome? That integrates well?
As a guy that has used Gnome from the beginning of my Linux life that has switched to Thunar, I would recommend trying that.

No split screen, no tabs.

Has always had the Open Terminal option by default and it is pretty easy to add Open as Administrator too.

Mine actually says Open as Hephaestus (I am a Blacksmith among other things).

You can't, unfortunately, remove Nautilus even using "aptitude keep-all" first.

---

### Post by cariboo on 2011-12-07
> **r_mano said:**
> Ok, don't worry. The bug/request have been closed as WONTFIX, and it seems that the decision is irrevocable.

Your bug report was pretty sparse on information, you didn't justify why the option should be brought back. I'd suggest you rethink your bug report, add reasons why it would be good for everyone, and provide examples. and screen-shots if possible.

---

### Post by Mr. Picklesworth on 2011-12-08
One of the reasons this feature was removed (and I, for one, am not upset) is because it was pretty poorly implemented. The desire to remove it has been going on for years at this point.

If I recall correctly, the implementation problems were things like these:
 * Emblems in Nautilus didn't carry over to other file managers, or even to the GTK file chooser: they were limited to Nautilus.
 * It wasn't clear why someone would choose emblems over custom icons.
 * There was no rhyme or reason to the set of emblems. They were essentially a bunch of random pictures. Going by memory, but I recall two gear emblems in Ubuntu's default set and a number of "multimedia" emblems.
 * A large number of emblems could be attached to a file icon, but they weren't always visible and there was no way to specify which order they became visible.
 * The file manager itself can add emblems - for example, with the U1 and Dropbox extensions. These used to be presented in the same way as emblems added by the end user. Presentation aside, the code paths for that were weird.

I do miss some of what they did (though I've started using custom folder icons for most of what I used emblems for), but I think - especially at this point - people would be better served by something that isn't the same emblems we had before. If you're particularly interested in seeing these back, I'd suggest that you ponder a way to improve on the idea. The folks who removed emblems can probably give you some really good reasons why they were removed, so they won't be interested in "reinstating" that design. They would probably be thrilled to see something new that has been better thought out.

---

### Post by r_mano on 2011-12-08
Cariboo907, Mr. Picklesworth: you are both obviously right. 

I understand the technical reason very well, and I agree with them. What makes me sorry is that last years Linux development seems a rush to simplification over configure-ability --- and I am quite an old-timer, see my signature. 

This was a minor nuance --- I agree, I can use custom icons to obtain the same use of emblems I had (but now the new icons are invariable, they do not adapt to a change of theme), but I will survive. And beside, I can manage them with gvfs-info and gvfs-set-attribute, so I have a solution.

But there are more examples. For example, the real big problem --- with has made me switch from unity, which otherwise I like, on all my computers minus one(*), is the fact that the global menu is not configurable off, so when you have a big screen, focus-follow-mouse and multiple windows, the system is unusable(**). 

That is --- losing features because somewhere, unidirectionally, someone thought that "this is best for you". Sad. 

Romano 


(*) gnome-shell and ATI fglrx incompatibility.
(**) yes I know, there are ENV tricks and hack to disable it, but they're just that, hacks.

---

### Post by ubuntu27 on 2011-12-08
Check out: [How To Manually Add Emblems In Nautilus 3]("http://www.webupd8.org/2011/12/how-to-manually-add-emblems-in-nautilus.html")

---

### Post by irv on 2011-12-08
> **r_mano said:**
> Cariboo907, Mr. Picklesworth: you are both obviously right. 

I understand the technical reason very well, and I agree with them. What makes me sorry is that last years Linux development seems a rush to simplification over configure-ability --- and I am quite an old-timer, see my signature. 

This was a minor nuance --- I agree, I can use custom icons to obtain the same use of emblems I had (but now the new icons are invariable, they do not adapt to a change of theme), but I will survive. And beside, I can manage them with gvfs-info and gvfs-set-attribute, so I have a solution.

But there are more examples. For example, the real big problem --- with has made me switch from unity, which otherwise I like, on all my computers minus one(*), is the fact that the global menu is not configurable off, so when you have a big screen, focus-follow-mouse and multiple windows, the system is unusable(**). 

That is --- losing features because somewhere, unidirectionally, someone thought that "this is best for you". Sad. 

Romano 


(*) gnome-shell and ATI fglrx incompatibility.
(**) yes I know, there are ENV tricks and hack to disable it, but they're just that, hacks.

I agree with you 100% on this one. I have been a Linux user for many years now. When Ubuntu came along, I gave it a try and could see it was going to go places, which it has. I also find it sad that from some of the older releases much of the customablity as gone. And again I can see some of the changes they made to be OK, but I don't like the fact I have to really hack to change things the way I want them. 

Right now I am testing 12.04 and overall I like the feel and looks, but again I do want to change a few things. Have you notice that there is a lack of Unity Themes and Icons. See this link. [http://techhamlet.com/2011/05/4-unity-themes-and-2-icon-packs-to-decorate-ubuntu-11-04/]("http://techhamlet.com/2011/05/4-unity-themes-and-2-icon-packs-to-decorate-ubuntu-11-04/") A quote from this page said:
> I have seen a lot of themes coming out for Gnome 3, but still Unity is a bit less popular…
I agree that Unity has not taken a real hold on uses yet, but I see it growing as time goes on. (There are things to like and things to dislike), but I believe it is here to stay.

Getting back on subject, I would like to change the background in Nautilus also but this is not an easy thing to do I can change Icons for now, but I do hope a few things will change as time goes on.

---

### Post by philinux on 2011-12-16
Someone has been busy trying to "fix" this and other omissions from nautilus.

[http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html](http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html)

[http://www.omgubuntu.co.uk/2011/12/how-to-add-actions-emblem-support-back-to-nautilus-in-ubuntu-11-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2011/12/how-to-add-actions-emblem-support-back-to-nautilus-in-ubuntu-11-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by irv on 2011-12-16
> **philinux said:**
> Someone has been busy trying to "fix" this and other omissions from nautilus.

[http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html](http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html)

[http://www.omgubuntu.co.uk/2011/12/how-to-add-actions-emblem-support-back-to-nautilus-in-ubuntu-11-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2011/12/how-to-add-actions-emblem-support-back-to-nautilus-in-ubuntu-11-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

The problem in 12.04 Alpha 1 is when I go to install nautilus-actions-extra I get:
> The following packages have unmet dependencies:
 nautilus-actions-extra : Depends: nautilus-gksu but it is not installable
And if I try to install the depended "nautilus-gksu" I get:
> Package nautilus-gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

I may have to wait until the final release of 12.04 to get this problem resolved.

---

### Post by philinux on 2011-12-16
Thats odd. They must have removed nautilus-gksu from the alpha 1.

[edit] just checked it not there.

---

### Post by irv on 2011-12-16
> **philinux said:**
> Thats odd. They must have removed nautilus-gksu from the alpha 1.

[edit] just checked it not there.

You are right, it is not there. I did an update/upgrade this morning I wonder if it was removed this morning? I thought it was there the other day.

---

