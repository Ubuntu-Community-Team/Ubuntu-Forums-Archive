---
title: "Change gnome scrollbar behavior?"
date: 2015-11-10
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-11-10
I actually noticed this in Wily but was too busy to ask or complain. Can standard scrollbar behavior be restored to GNOME? I've dug thru dconf-editor but can't find anything.

I almost wouldn't mind it but Firefox uses the old scrollbar behavior while other apps use the new scrollbars so the inconsistency looks repulsive.

---

### Post by sgage on 2015-11-10
> **kansasnoob said:**
> I actually noticed this in Wily but was too busy to ask or complain. Can standard scrollbar behavior be restored to GNOME? I've dug thru dconf-editor but can't find anything.

I almost wouldn't mind it but Firefox uses the old scrollbar behavior while other apps use the new scrollbars so the inconsistency looks repulsive.

I consider the Firefox behavior to be new scrollbar behavior, and find it really annoying. If I click in the scrollbar below the 'thumb', it should scroll one screenful, not to the relative position of the thumb in the document. You know, like every GUI since the invention of the GUI.;

I have asked how to fix it many times over the last year or so, but no answers. It would at least be nice to have an option...

I agree, though, the inconsistency is maddening.

---

### Post by sammiev on 2015-11-10
I found if you select Tweak Tools -> Appearance -> GTK+ and select HighContrast or Numix.

FireFox will only scroll up or down one page at a time.

---

### Post by kansasnoob on 2015-11-10
I haven't tried it yet but I found this:

[https://www.reddit.com/r/gnome/comments/37bp1r/how_do_i_disable_316s_overlay_scrollbars/](https://www.reddit.com/r/gnome/comments/37bp1r/how_do_i_disable_316s_overlay_scrollbars/)

So just what would this do:

```
GTK_OVERLAY_SCROLLING=0
```

I always like to look before I leap ................. it's nice to know how to revert any change before you make it ;)

---

### Post by kansasnoob on 2015-11-10
> **sgage said:**
> I consider the Firefox behavior to be new scrollbar behavior, and find it really annoying. If I click in the scrollbar below the 'thumb', it should scroll one screenful, not to the relative position of the thumb in the document. You know, like every GUI since the invention of the GUI.;

I have asked how to fix it many times over the last year or so, but no answers. It would at least be nice to have an option...

I agree, though, the inconsistency is maddening.

I had suspected that once Firefox went gtk+3 things would be consistent but that doesn't seem to be the case.

I actually have a laundry list of things that upstream GNOME has been ignoring, like a buggy gvfs, goofy clock format, etc, etc. Oh, and killing hal before it's time!

---

### Post by ajgreeny on 2015-11-10
Same problem is in Xubuntu 14.04 with the xfce-4.12 ppa enabled.  I can't remember if it was the same with the default xfce-4.10 but I think it was.

I do find it very annoying when I want to scroll one page at a time and forget that placing the cursor and clicking in the scrollbar pulls it all the way from top to bottom or vice-versa.

Who on earth was it who decided that behaviour was a good idea?

I have just tried the solution suggested in that link but it made no difference at all, but I'm just about to install xenial in VBox so I will test things in that and report back.

---

### Post by sgage on 2015-11-10
> **ajgreeny said:**
> I do find it very annoying when I want to scroll one page at a time and forget that placing the cursor and clicking in the scrollbar pulls it all the way from top to bottom or vice-versa.

Who on earth was it who decided that behaviour was a good idea?

No kidding - this has been bugging me for a long time. As alluded to above, it's encoded in the GTK+ theme - if you use, e.g., the Numix theme, for example, it works properly. But if you want to use Adwaita, you will get the bizzarro behavior. As far as I know you can't simply edit the Adwaita theme - it seems to be baked right into Gnome Shell.

---

### Post by kansasnoob on 2015-11-10
> **sammiev said:**
> I found if you select Tweak Tools -> Appearance -> GTK+ and select HighContrast or Numix.

FireFox will only scroll up or down one page at a time.

Yep, things seem to work well in Numix. Things even look good but some apps use the Numix window management buttons while others remain on Ambiance.

But overall scrolling behavior and appearance is good in Numix ATM.

---

### Post by kansasnoob on 2016-02-29
Thought I'd give this a bump. Has anyone found a way to restore plain old fashioned scrollbar behavior with the default themes?

---

### Post by QDR06VV9 on 2016-02-29
@kansasnoob I have not tried this my self but other's in various forums report this to work.
The old behavior can be restored by creating or editing the _~/.config/gtk-3.0/settings.ini_ file and setting the **gtk-primary-button-warps-slider** property to **false** as follows: 
 
[TABLE="width: 90%, align: center"]
[TR]
[TD]> [Settings] 
gtk-primary-button-warps-slider = false 
     [/TD]
[/TR]
[TR]
[TD="class: code"][/TD]
[/TR]
[/TABLE]
To make this change for all users by default, edit _/etc/gtk-3.0/settings.ini_ instead and add the line to the existing [Settings] section. 
Just a heads up some after making the change... gedit gave a 1 time warning.
> (gedit:6094): Gtk-WARNING **: Error setting  gtk-primary-button-warps-slider in /etc/gtk-3.0/settings.ini: Key file  contains key 'gtk-primary-button-warps-slider' which has a value that  cannot be interpreted.
After that first time it will return to normal behaviour..
Hope this is helpful

---

### Post by vasa1 on 2016-03-01
> **ajgreeny said:**
> Same problem is in Xubuntu 14.04 with the xfce-4.12 ppa enabled.  I can't remember if it was the same with the default xfce-4.10 but I think it was.

I do find it very annoying when I want to scroll one page at a time and forget that placing the cursor and clicking in the scrollbar pulls it all the way from top to bottom or vice-versa.

Who on earth was it who decided that behaviour was a good idea?

I have just tried the solution suggested in that link but it made no difference at all, but I'm just about to install xenial in VBox so I will test things in that and report back.

Have you looked at [http://ubuntuforums.org/showthread.php?t=2306485&p=13430990#post13430990?](http://ubuntuforums.org/showthread.php?t=2306485&p=13430990#post13430990?) When I tried the gtk3 version of Firefox I encountered this issue. It's default in all gtk3 apps.

---

