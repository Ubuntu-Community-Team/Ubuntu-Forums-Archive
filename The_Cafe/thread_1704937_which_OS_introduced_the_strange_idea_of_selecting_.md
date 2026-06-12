---
title: "which OS introduced the strange idea of selecting windows by  SMALLER representations"
date: 2011-03-11
forum: The Cafe
---

### Post by Bazon on 2011-03-11
?

Was it Windows 7? Or Mac OSX?
Sorry, I don't know, I really only use ubuntu for quite some time. 

And sorry, I mentioned this before, but Ubuntu going this way in Unity really makes me a little mad. How on earth should one distinguish e.g. Text Documents in DECREASED size? :-(

---

### Post by RiceMonster on 2011-03-11
I assume you mean the idea of only using an icon and no window title in the taskbar/panel? Mac OSX was using only icons before Windows 7 came in the the superbar (no, I'm not saying they're the same thing).

To the second part of your question, Windows 7 displays window title and gives you a preview of the window when you hover of the icon in the task bar, so you can easily distinguish different instances of the same application. It also makes all the other windows transparent so you can see the entire window when you hover over the window preview.

I haven't used Unity, so I can't tell you if it does anything similar.

---

### Post by 3Miro on 2011-03-11
> **Bazon said:**
> ?

Was it Windows 7? Or Mac OSX?
Sorry, I don't know, I really only use ubuntu for quite some time. 

And sorry, I mentioned this before, but Ubuntu going this way in Unity really makes me a little mad. How on earth should one distinguish e.g. Text Documents in DECREASED size? :-(

I saw the feature for the first time in KDE 4.2, although I think Compiz had it for some time before. I believe it is called "windows-thumbnail-preview" The advantage of KDE was that it allowed to preview minimized windows, standard Compiz previews only opened ones. In Unity, it should be easily disabled from Compiz-Config-Settings-Manager.

---

### Post by Bazon on 2011-03-11
> **RiceMonster said:**
> I assume you mean the idea of only using an icon and no window title in the taskbar/panel? 

yes and no:
yes, I blame the strange idea of leaving out the useful information of the window/document title
no, I don't mean the icon, I mean the smaller zoomed window. (see link below)

> **RiceMonster said:**
> I haven't used Unity, so I can't tell you if it does anything similar.

so that's no wonder you haven't seen it. in unity, there isn't a thing like the taskbar/ window switcher any more. you just have the launcher on the left side. when running several windows of one application (e.g. several documents), you have to select the window by a smaller zoomed version of the window, it looks this way:
[http://ubuntuone.com/p/gtO/](http://ubuntuone.com/p/gtO/) (link leads to screenshot)

and really, selecting a text document like that makes me a bit mad....

---

### Post by cchhrriiss121212 on 2011-03-11
I see what you mean, for something like a series of text documents, you really need to be able to see a file name in order to distinguish between them. Photos, on the other hand, benefit from the opposite approach.

---

### Post by Copper Bezel on 2011-03-11
Oh, so you're talking about Compiz Scale. Everyone has an equivalent, but I *think* Compiz got it first, then OSX. 

Unity uses window thumbnail previews too, though, doesn't it? If you hover the icon *without* clicking it, doesn't it give you a captioned list? Everything else does - AWN, KDE, Windows 7's Superbar, etc.

I'm also a bit unversed in Unity, as it's cack in 10.10 and it's far too early to upgrade to Natty for me.

Oh, one last bit - in your Compiz settings, you should be able to set scale to display a caption when you hover a window, which might help a bit.

---

### Post by Bazon on 2011-03-11
> **Copper Bezel said:**
> Unity uses window thumbnail previews too, though, doesn't it? If you hover the icon *without* clicking it, doesn't it give you a captioned list? Everything else does - AWN, KDE, Windows 7's Superbar, etc.

No, it doesn't. The context menu of the launcher is also very...  ..short. (only "keep in launcher" and "quit")

> **Copper Bezel said:**
> Oh, one last bit - in your Compiz settings, you should be able to set scale to display a caption when you hover a window, which might help a bit.

yes, the scale or the expo plugin, they seem to make no difference in unity. and no, unfortunately there is no way of additionally showing the window title in these plugins....

---

### Post by Copper Bezel on 2011-03-11
Huh. Are you on 10.10 or 11.04?

---

### Post by ikt on 2011-03-11
> **Bazon said:**
> 
and really, selecting a text document like that makes me a bit mad....

Don't be mad, if you let yourself get angry and frustrated in a world of FOSS then you don't understand what FOSS is about :p

How did you switch between documents before?

---

### Post by Copper Bezel on 2011-03-11
If he's using Unity, he was probably using Classic Gnome before, so the taskbar would have either a list of buttons with the titlebar labels or (if grouped) a button with a quick menu of titlebar labels.

---

### Post by Bazon on 2011-03-11
> **Copper Bezel said:**
> Huh. Are you on 10.10 or 11.04?

mostly on 10.10, but i'm testing 11.04 right now to see whether I go with the upgrade next month...

---

### Post by Bazon on 2011-03-11
> **ikt said:**
> How did you switch between documents before?

window switcher in gnome panel or cairo/glx dock. (i have several computers...)
both provide window/document titles (glx dock at least if there is more than one window of the application)

---

### Post by ikt on 2011-03-11
> **Copper Bezel said:**
> If he's using Unity, he was probably using Classic Gnome before, so the taskbar would have either a list of buttons with the titlebar labels or (if grouped) a button with a quick menu of titlebar labels.

So then why not just use Gnome classic?

In 11.04 on the login screen, after clicking on your username, down the bottom click on "Ubuntu Classic Desktop" and you will get the same panel configuration in Ubuntu 10.10, which should show you the list of titlebar buttons with the labels of open applications.

---

### Post by BrokenKingpin on 2011-03-11
> **ikt said:**
> So then why not just use Gnome classic?

When Gnome 3 drops you will be able to still run classic Gnome, but there won't be any more support for the old panels and WM, so why use something that is dead and not supported.

---

### Post by Copper Bezel on 2011-03-11
That may or may not be Bazon's concern. It sounds like he needs his labels.

I'm fairly disappointed that Scale can't be configured in Unity, and it's another reason I won't be using it in 11. (AWN and DockbarX are quite a bit more mature at this point.)

> and WM

It's the same WM, because it's all Compiz inheriting Metacity settings. Only the panel is "unsupported" (but still available.)

---

### Post by ikt on 2011-03-11
> **BrokenKingpin said:**
> When Gnome 3 drops you will be able to still run classic Gnome, but there won't be any more support for the old panels and WM, so why use something that is dead and not supported.

There are many improvements and bug fixes coming to the launcher, I'm sure eventually someone will include the ability to select an icon and then a slide out menu will show all the windows currently open by it.

If it is not included by default, it may be an option that libreoffice or openoffice decide to include, as what the menu does when you click on an icon in launcher is customisable by the individual program, you might even be able to write a quick script that does that :)

> **Copper Bezel said:**
> I'm fairly disappointed that Scale can't be configured in Unity

At the moment not much of compiz can be configured at all because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685552](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685552)

Once it is fixed, it looks like it can be configured.

---

### Post by zekopeko on 2011-03-11
> **Copper Bezel said:**
> Oh, so you're talking about Compiz Scale. Everyone has an equivalent, but I *think* Compiz got it first, then OSX.

And you would be wrong. OSX got it in 2003. Compiz in 2006 or 2007.

---

### Post by Copper Bezel on 2011-03-11
I did say "think," and I really was hoping for some clarification, so thank you.

---

### Post by Bazon on 2011-03-12
> **ikt said:**
> So then why not just use Gnome classic?

In 11.04 on the login screen, after clicking on your username, down the bottom click on "Ubuntu Classic Desktop"...


Thanks, I know.
But it's not that I don't like Unity. I like it and I don't like it. 
I looks good, but it lacks of functionality and is not enough customizable. 

And adding functionality to the window selection in the window spread would be relatively easy: Just display the window/document titles in normal size additionally. So you really can distinguish windows.
I think I'll file a bug when I have time....

---

### Post by ugm6hr on 2011-03-12
> **Bazon said:**
> And adding functionality to the window selection in the window spread would be relatively easy: Just display the window/document titles in normal size additionally. So you really can distinguish windows.

I like the Expose / Scale function to select between open windows - I use it on my standard Gnome2 desktop (on my netbook).
However, as you say - it is less helpful when you have multiple instances of the same application. It really only works when all the applications have a tabbed windows option.
As you say - having a list in addition to this is useful at times.

---

### Post by Bazon on 2011-03-13
OK, today I got time, filed a bug:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/734253](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/734253)

---

