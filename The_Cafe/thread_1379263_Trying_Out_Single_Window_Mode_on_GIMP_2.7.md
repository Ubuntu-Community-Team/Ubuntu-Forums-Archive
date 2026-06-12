---
title: "Trying Out Single Window Mode on GIMP 2.7"
date: 2010-01-12
forum: The Cafe
---

### Post by Ric_NYC on 2010-01-12
[IMG]http://img189.imageshack.us/img189/3338/gimp27singlewindow.jpg[/IMG]

> The open source image editor known as GIMP doesn't need an introduction. Neither does its multi-window interface.

GIMP is a very powerful image editor, there's no denying that, but no matter how good it is feature-wise, **some people simply don't like, or can't get used to the interface it sports**.

With the new release of GIMP 2.7, that's not an issue anymore. GIMP 2.7 brings various improvements like in every new release, but one of the features that really stands out is the ability to choose the interface mode of your choice.

[B][COLOR="DarkRed"]Upgrading to GIMP 2.7[/COLOR]
[/B]
Before we upgrade to GIMP 2.7, it's important for me to state that GIMP 2.7 is still under development, so do expect for some bugs to pop up.

To upgrade to GIMP 2.7, we will have to add a new PPA. The PPA we're going add is the "mrw-gimp-svn for matthaeus123" PPA. You can add the PPA in Karmic Koala by going to the "Other Software" tab in [System -> Administration -> Software Sources] and adding "**ppa:matthaeus123/mrw-gimp-svn**".

After you have added the PPA and reloaded the software list, go to the "Update Manager" and perform an update. You will see that in the list of updates available there will be an update for GIMP.

**[COLOR="DarkRed"]Switching to single-window mode[/COLOR]**

Once you run GIMP 2.7, you'll notice that it will start up in the traditional multi-window interface. **[COLOR="Navy"]To switch to the single-window interface, go to the "Windows" menu and toggle "Single-window mode"[/COLOR]**.

**Now that GIMP has the window mode of your choice, I hope the multi-window zealots and the single-window lovers can both rejoice about the wonderful change that has been brought to GIMP**.

[IMG]http://img705.imageshack.us/img705/5651/snapshot1v.jpg[/IMG]

[http://www.learningubuntu.com/software/trying-out-single-window-mode-gimp-27](http://www.learningubuntu.com/software/trying-out-single-window-mode-gimp-27)

---

### Post by NoaHall on 2010-01-12
I really wish Paint.net would port to GNU/Linux. Who cares mono isn't ethical? It's better than the Gimp. Still, the Gimp has a few nice features. I prefer the non-single-windows-mode, because I have several monitors, it makes life easier across them.

---

### Post by Queue29 on 2010-01-12
> **NoaHall said:**
> I really wish Paint.net would port to GNU/Linux. Who cares mono isn't ethical? It's better than the Gimp. 

[Tada!]("http://code.google.com/p/paint-mono/")

It seems to be an unfinished/ low priority project, though it was started by Miguel de Icaza himself.

---

### Post by Tibuda on 2010-01-12
> **NoaHall said:**
> Who cares mono isn't ethical?

I care, but Mono IS ethical.

---

### Post by NoaHall on 2010-01-12
> **Queue29 said:**
> [Tada!]("http://code.google.com/p/paint-mono/")

It seems to be an unfinished/ low priority project, though it was started by Miguel de Icaza himself.

That's a old version, and it won't get any updates from the real project, as it(the real project) was forced to become closed source after some people stole the source code and rebranded it as their own, then sold it :/

---

### Post by Uncle Spellbinder on 2010-01-12
There are two PPA repos that include paint-mono (Paint.net). Haven't tried yet. I'm on Windows at work. Ill check them out when I get home tonight.

Hardy/Intrepid/Jaunty: [https://launchpad.net/~xmlich02/+archive/ppa](https://launchpad.net/~xmlich02/+archive/ppa)
Hardy/Jaunty/Karmic: [https://launchpad.net/~zachanimerulz/+archive/ppa](https://launchpad.net/~zachanimerulz/+archive/ppa)

---

### Post by Grenage on 2010-01-12
> GIMP has the window mode of your choice

It's great that they added that feature, now those who want a single window don't need to hack like hell to obtain it.

---

### Post by ssam on 2010-01-12
> **NoaHall said:**
> That's a old version, and it won't get any updates from the real project, as it(the real project) was forced to become closed source after some people stole the source code and rebranded it as their own, then sold it :/

people often try this with gimp. there are plenty of site that have 'gimp pro' or some such for $20. the gimp devs just laugh it off.

---

### Post by mocoloco on 2010-01-12
Whaa!? Finally! I thought the devs had vowed they would never change the interface.  Nice to have the choice of either or, very good news.

> **NoaHall said:**
> That's a old version, and it won't get any updates from the real project, as it(the real project) was forced to become closed source after some people stole the source code and rebranded it as their own, then sold it :/

If the code was open then how could anyone "steal" it?  And rebranding and and selling it are perfectly ethical with free & open source software, as long as they comply with the GPL (eg, 
also release the source).  Was there more to the story, or did the Paint.NET devs not understand the GPL?

---

### Post by Tibuda on 2010-01-12
> **mocoloco said:**
> If the code was open then how could anyone "steal" it?  And rebranding and and selling it are perfectly ethical with free & open source software, as long as they comply with the GPL (eg, 
also release the source).  Was there more to the story, or did the Paint.NET devs not understand the GPL?

I don't think Paint.net was released under GPL when the source was open. I think it was a more permissive license.

---

### Post by mocoloco on 2010-01-12
^^ Ah, gotcha.  My mistake, I shouldn't assume that Open Source = GPL.

---

### Post by NoaHall on 2010-01-12
> **danielrmt said:**
> I don't think Paint.net was released under GPL when the source was open. I think it was a more permissive license.

It was a modified MIT license.

---

### Post by Mr. Picklesworth on 2010-01-12
It isn't as pretty as the amazing mockups yet. Hopefully the GIMP developers were as amazed by those as I was and see reason to get the implementation pixel-perfect, even if it requires toolkit changes :P

In particular, the tabs are currently just tabs (as opposed to detachable / resizeable thumbnails for quick comparisons).

Still, I'm excited by this. Tinkering very happily with the build from the PPA.

(On the topic of prettiness, that ruler looks like something out of an early 90s word processor. There *must* be a better way!).

---

### Post by user1397 on 2010-01-12
so I guess [gimshop]("http://gimpshop.com/") is obsolete

---

### Post by aaaantoine on 2010-01-12
Hm... I didn't complain much about the multi window interface, but it may turn out that I prefer this layout.  We'll see when GIMP 2.8 (e.g. stable version) comes out.

---

### Post by mocoloco on 2010-01-12
> **ubuntuman001 said:**
> so I guess [gimshop]("http://gimpshop.com/") is obsolete

Actually no.  The single-window change of Gimpshop only worked on Windows.  The main changes it makes are to the menus and tools, so that Photoshop veterans are more at home and so that newbs can follow Photoshop guides to some extent using Gimp.

---

### Post by Robertjm on 2010-03-11
I posted my previous comments as a response in the thread and then I see the previous comment. I'm fairly certain I used to run GimpShop on Linux, but again, that was something like 4 or 6 years ago.
-------------- 
There used to be a project called "GimpShop" which was free, that not only arranged the windows into a "single window" but also rearranged the menus to more resemble PhotoShop. Not sure what the status currently is as I gave up on it a LOOONNNNG time ago.

Robert

> **ssam said:**
> people often try this with gimp. there are plenty of site that have 'gimp pro' or some such for $20. the gimp devs just laugh it off.

---

### Post by the yawner on 2010-03-11
OT: [Pinta]("http://pinta-project.com/") - Paint.NET clone. Still at its early stages though :)

---

### Post by phrostbyte on 2010-03-11
> **NoaHall said:**
> That's a old version, and it won't get any updates from the real project, as it(the real project) was forced to become closed source after some people stole the source code and rebranded it as their own, then sold it :/

I always find amusement in this. If software developers have a problem with this 100% legal practice, they shouldn't release their code under the BSD or MIT license.

---

### Post by ssj6akshat on 2010-03-11
[http://www.photo-editor-pro.com/](http://www.photo-editor-pro.com/)

Doesn't this look familiar?

---

### Post by murderslastcrow on 2010-03-11
I love that it's a check-box they put in just the right place. :D

A lot of my friends used to say, "GIMP isn't professional," and I said why, and they would keep saying, "I dunno', just the way the windows float around doesn't look like a Photoshop clone." Then I had to remind them that GIMP is GIMP, and downloaded a lot of copies of GIMPshop for people. Note, this is before I ever used Linux.

You'd be stupid to use Photoshop for anything but professional work that requires a specific integrated Photoshop feature. Otherwise, let's just improve GIMP's PSD support and we're good.

---

### Post by gsmanners on 2010-03-11
The GIMP wasn't all that until about 2006 or so. That's when I feel like its features started to compare with Photoshop. Unfortunately, people can have a lot of inertia in their preference. Plus, it doesn't help that Microsoft has paid off numerous "journalists" to basically advertise Microsoft products and to ridicule everything else.

---

### Post by Tibuda on 2010-03-11
> **gsmanners said:**
> The GIMP wasn't all that until about 2006 or so. That's when I feel like its features started to compare with Photoshop. Unfortunately, people can have a lot of inertia in their preference. Plus, it doesn't help that Microsoft has paid off numerous "journalists" to basically advertise Microsoft products and to ridicule everything else.

Photoshop is not a Microsoft product.

---

### Post by HoboJ on 2010-03-11
Great, now I can get rid of those free floating side panels. That's my only gripe with gimp.

---

### Post by kellemes on 2010-03-11
Very happy with the change.. works much more efficient for me.
Well done to the devs.
Now.. am I blind or can't we make it the default window-mode at startup?

---

### Post by ibuclaw on 2010-03-11
> **kellemes said:**
> Very happy with the change.. works much more efficient for me.
Well done to the devs.
Now.. am I blind or can't we make it the default window-mode at startup?

(bare in mind I don't have gimp installed).

I would suggest:
[LIST]
[*]check ~/.gimp-2.x for any config files that may set this (ie: dialogue controls/layout).
[*]check gconf-editor
[*]check anywhere in Edit->Preferences
[/LIST]


(edit): Perhaps it is not [implemented]("http://ubuntuforums.org/showthread.php?t=1398206") to work yet...

---

### Post by kellemes on 2010-03-14
Well, again.. great to see they've finally listed to there users.
This one I've uninstalled, still a lot of issues with the ui and some other issues that's are not finished yet.
Can't wait until a stable 2.7 is released.

---

### Post by _h_ on 2010-03-14
Really nice. I really hate the Gimp currently with the 3 windows...gets annoying sometimes when I have to constantly move the toolbox out of the way. :(

---

### Post by Robertjm on 2010-03-14
Laughter can be heard this morning in my house. The dude didn't even change the name of the product.

As for the question about Gimp not being professional? I run into things like that a lot. Here's the reasoning:

1 - Its "free isn't it? You get what you pay for."
2 - Its linux (most not to seem to know about the Windows or OSX fersions.
3 - Its not Photoshop (what everyone compares things to these days.

Right now I'm looking forward to the single window, but will need to use it before I'm sold on it. The one example I saw showed the windows just popping together with no control, which makes no sense. Usage will tell.

Robert

> **ssj6akshat said:**
> [http://www.photo-editor-pro.com/](http://www.photo-editor-pro.com/)

Doesn't this look familiar?

---

### Post by Ric_NYC on 2010-03-14
I like the "flexibility" of the new versions.

You can choose what you want.

That's much better than: **"No... you cannot have it in a single window."**

:popcorn:

---

### Post by quinnten83 on 2010-03-16
> **kellemes said:**
> Well, again.. great to see they've finally listed to there users.
This one I've uninstalled, still a lot of issues with the ui and some other issues that's are not finished yet.
Can't wait until a stable 2.7 is released.

The odd numbered ones are never stable. The stable ones get even numbers. So the stable one will be 2.8.

---

### Post by kellemes on 2010-03-16
> **quinnten83 said:**
> The odd numbered ones are never stable. The stable ones get even numbers. So the stable one will be 2.8.

Thanks for the info.

---

