---
title: "Murrine adds transperency to GTK"
date: 2007-12-13
forum: The Cafe
---

### Post by shafin on 2007-12-13
[IMG]http://arstechnica.com/journals/linux.media/400/murrine_glass.jpg[/IMG]

[[IMG]http://arstechnica.com/journals/linux.media/460/murrine_rgba.png[/IMG]]("http://arstechnica.com/journals/linux.media/murrine_rgba.png")


> GNOME theme engine designer Andrea Cimitan has implemented support for transparent widgets in the [Murrine GTK theme engine]("http://arstechnica.com/journals/linux.ars/2007/08/21/how-to-make-a-gtk-theme-that-uses-multiple-theme-engines"), bringing Vista-like translucent glass effects to the GNOME desktop. Cimitan used RGBA colormaps to implement the feature and says that, with only 10 or 20 extra lines of code, translucency can easily be added to other theme engines that support RGBA.Source:
[http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine](http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine)


It looks beautiful.:KS

---

### Post by hanzomon4 on 2007-12-13
Simply Immaculate, and[ your link is wrong](http://arstechnica.com/journals/linux.ars/2007/12/12/gnome-theme-engine-designer-adds-transparency-to-gtk?bub)
[IMG]http://arstechnica.com/journals/linux.media/murrine_glass.jpg[/IMG]

---

### Post by shafin on 2007-12-13
My link is right,and so is yours.The news was published in Ars Technica,but the original source is the blog I gave in my post :)

---

### Post by hanzomon4 on 2007-12-13
Ah! I just got it...

---

### Post by PartisanEntity on 2007-12-13
Very cool, thanks for sharing.

---

### Post by klange on 2007-12-13
For lack of a better phrase to express my feelings towards this:
DO WANT.

---

### Post by mcduck on 2007-12-13
Wonderful! This is what I've been waiting for _long_ time!

Now I just need to wait until there's something actually available for users.. It feels even harder to wait for it now that I know there already is some working solution around.. :/

---

### Post by spupy on 2007-12-13
I really hope it would work with xcompmgr, because im not switching away from fluxbox anytime soon... other than that:
YES, PLZ!

---

### Post by ~LoKe on 2007-12-13
True or pseudo?

---

### Post by Steveway on 2007-12-13
> **~LoKe said:**
> True or pseudo?

True of course. Didn't you even read the article?

---

### Post by sloggerkhan on 2007-12-13
Murrine themes have always been my favorites and now they're even better.

---

### Post by ~LoKe on 2007-12-13
> **Steveway said:**
> True of course. Didn't you even read the article?

I wouldn't have asked the question if I had.

---

### Post by bruce89 on 2007-12-13
Does this theme support GTK+ theme colour editing?

---

### Post by aimran on 2007-12-19
Wait, i thought murrine is a theme not an engine. If that's the case, what engine is the default Ubuntu installation using?

---

### Post by ~LoKe on 2007-12-19
> **aimran said:**
> Wait, i thought murrine is a theme not an engine. If that's the case, what engine is the default Ubuntu installation using?

There's the Murrine Engine, then Murrina themes (which run on the Murrine engine, of course).

---

### Post by red_Marvin on 2007-12-19
Looks sweet!

Btw, what is an "engine"? I have gnome, which is a de, running metacity, which is a wm, and ...is clearlooks etc engines? Are engines what govern gtk widget styles and looks?

---

### Post by smartboyathome on 2007-12-20
Engines are basically what you said. Clearlooks, Ubuntulooks (which is a fork of clearlooks), rezlooks, etc are all GTK engines.

---

### Post by wana10 on 2007-12-20
quick mind-fart here, help appreciated, how do i change engines? i used murrine once and now i can't get rid of it, even if i try to use the human theme it has a murrine look...i can't get rid of it, ARRRGHh (help *greatly* appreciated)

---

### Post by smartboyathome on 2007-12-20
If you uninstalled it, then Human isn't using the Murrine engine. The Human theme doesn't use the Murrine engine by default, you have to manually edit the theme's gtk files.

---

### Post by aidanr on 2007-12-20
Looks great =D>

---

### Post by wana10 on 2007-12-20
> **smartboyathome said:**
> If you uninstalled it, then Human isn't using the Murrine engine. The Human theme doesn't use the Murrine engine by default, you have to manually edit the theme's gtk files.

so murrine edited my human theme? darn you murrine! darn you to HECK!!! (for the record i have uninstalled the murrine engine and yet everything still has the striped grey bar from my last used murrine theme under the file, edit, etc.)

oh, and human isn't orange anymore...its grey, how would something like this happen?

EDIT* holy crap i fixed it...i probably used the monkey with a hammer approach but it worked, awesome. i deleted everything in my .themes folder and reinstalled every gtk theme through synaptic. i'm good now, sorry 'bout the freakout

---

### Post by smartboyathome on 2007-12-20
> **wana10 said:**
> so murrine edited my human theme? darn you murrine! darn you to HECK!!! (for the record i have uninstalled the murrine engine and yet everything still has the striped grey bar from my last used murrine theme under the file, edit, etc.)

(oh, and human isn't orange anymore...its grey, how would something like this happen?)

Hm... orange is GRAY? That must mean it isn't human then? i would check your ~/.themes/ directory in order to see if there is a theme which is masking over you default human theme (it would be in a folder called Human). Also, post what you get when you run this command:

gedit /usr/share/themes/Human/gtk-2.0/gtkrc

---

### Post by wana10 on 2007-12-20
too late now...wish i had waited for a response now instead of just blowing it away, heh.

---

### Post by yatt on 2007-12-20
OMG! DO WANT! DO WANT! GIMME NOA!


Its about time. To me transparent Emerald + opaque GTK = tackiness at its best (or worst I guess).

This is a fine development.

---

### Post by ~LoKe on 2007-12-20
> **yatt said:**
> OMG! DO WANT! DO WANT! GIMME NOA!


Its about time. To me transparent Emerald + opaque GTK = tackiness at its best (or worst I guess).

This is a fine development.

If you're already using emerald, then compiz will add transparency...

---

### Post by yatt on 2007-12-20
> **~LoKe said:**
> If you're already using emerald, then compiz will add transparency...
But not the same way as the Murrine engine can. Murrine can have only some widgets transparent with others fully opaque. AFAIK, compiz can only make everything transparent or everything opaque.

I hope one of the Qt Styles strikes back with something similar!

---

### Post by aimran on 2007-12-20
Thanks for the replies =)

I do believe however that xcompmgr and transset is an easier way to achive the above mentioned effects.

---

### Post by MyKal on 2010-02-11
it is so unfortunate that people choose to take part in these conversations without reading any of the material that the conversation is based on 

first of all the transparency in emerald is only for window borders and has nothing to do with this whatsoever 

and neither does transset 

all that program does is make an entire window transparent which for anything other then a stupidly gpu intensive way of identifying which window is active is utterly useless 

this however would allow say the background of a window to be semi transparent while buttons text fields etc are fully opaque 

opening up an endless amount of beautification potential to themers 

again 

this is not simply a way to make a window transparent 

that would be far to mundane to warrant a post 

please read and try to understand the articles before posting and CERTAINLY before correcting others

---

### Post by Skripka on 2010-02-11
Necro!

---

### Post by MyKal on 2010-02-11
feel better?

---

### Post by FuturePilot on 2010-02-11
old thread is old.

---

