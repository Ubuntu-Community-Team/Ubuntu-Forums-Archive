---
title: "Compiz/Unity: The next coming huge task"
date: 2012-02-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-02-04
Precise use compiz via unity for its default frontend; but it seems that some hard times are coming:

[http://smspillaz.wordpress.com/2011/12/25/apology-2/](http://smspillaz.wordpress.com/2011/12/25/apology-2/)
[http://www.phoronix.com/scan.php?page=news_item&px=MTA1Mjc](http://www.phoronix.com/scan.php?page=news_item&px=MTA1Mjc)
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=compiz&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=compiz&search=Search+Bug+Reports&field.scope=all&field.scope.target=)
( so long list :()
[http://www.phoronix.com/scan.php?page=news_item&px=MTA1MjU](http://www.phoronix.com/scan.php?page=news_item&px=MTA1MjU)

So the questions are:
- is canonical will fix compiz alone ?
- is unity will have to choose gnome3 API instead of compiz one for future, meaning a complete rewrite :( ?

Too much bad design choices for a long life, and scary for a LTS.

---

### Post by effenberg0x0 on 2012-02-04
> **dino99 said:**
> Precise use compiz via unity for its default frontend; but it seems that some hard times are coming:

[http://smspillaz.wordpress.com/2011/12/25/apology-2/](http://smspillaz.wordpress.com/2011/12/25/apology-2/)
[http://www.phoronix.com/scan.php?page=news_item&px=MTA1Mjc](http://www.phoronix.com/scan.php?page=news_item&px=MTA1Mjc)
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=compiz&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=compiz&search=Search+Bug+Reports&field.scope=all&field.scope.target=)
( so long list :()
[http://www.phoronix.com/scan.php?page=news_item&px=MTA1MjU](http://www.phoronix.com/scan.php?page=news_item&px=MTA1MjU)

So the questions are:
- is canonical will fix compiz alone ?
- is unity will have to choose gnome3 API instead of compiz one for future, meaning a complete rewrite :( ?

Too much bad design choices for a long life, and scary for a LTS.

Last I read somewhere, they were already cutting it in half, so it could work on wayland. Other recent news had something about wayland having reached a stable 1.0, usable, release.
I will bet on compiz, as it is now, being dropped soon by most distros as unmaintained code. And on compiz for Wayland, or whatever name they choose for it, receiving focus/investment by Canonical. And, of course, nothing of that is possible for this release. I'm not even sure about PP+1.

---

### Post by grahammechanical on 2012-02-04
At least the guy himself is still around. Sam Spilsbury has today blogged a thank you for all the support.

And we did get a Compiz update the other day. I do not know how much needs fixing or how badly it needs fixing but it seems unthinkable to switch compositing managers part way through a 5 years support promise. If it could be done without the user noticing anything, well then it would be a different matter.

I have found this, which clears things up a bit.

[http://en.wikipedia.org/wiki/Wayland_(display_server_protocol)]("http://en.wikipedia.org/wiki/Wayland_(display_server_protocol)")

> Wayland provides a method for compositing window managers to communicate directly with applications and to communicate directly with video and input hardware. Applications render graphics to their own buffers, and the window manager becomes the display server, compositing those buffers to form the on-screen display of application windows. This is a simpler and more efficient approach than using a compositing window manager with the X Window System.

> Canonical Ltd., owner of Ubuntu, hired Sam Spilsbury, primary Compiz developer. He has been moving Compiz dependencies on X into a plugin. This will make it easier to enable Compiz to become a Wayland display server. Canonical is planning to help port Compiz to OpenGL ES, currently a requirement for Wayland display servers.

Something else has just come to mind from reading the links in the first post - FUD

Regards.

---

### Post by dino99 on 2012-02-04
> **effenberg0x0 said:**
> Last I read somewhere, they were already cutting it in half, so it could work on wayland. Other recent news had something about wayland having reached a stable 1.0, usable, release.
I will bet on compiz, as it is now, being dropped soon by most distros as unmaintained code. And on compiz for Wayland, or whatever name they choose for it, receiving focus/investment by Canonical. And, of course, nothing of that is possible for this release. I'm not even sure about PP+1.

I'm thinking the same way too; but Canonical will probably rewrite some part of Unity as this LTS will be used 5 years, even after frozen calendar; or wait for 12.10 then backport the main changes. Anyway, there is some kind of urgency.

---

### Post by dino99 on 2012-02-04
> **grahammechanical said:**
> At least the guy himself is still around. Sam Spilsbury has today blogged a thank you for all the support.

And we did get a Compiz update the other day. I do not know how much needs fixing or how badly it needs fixing but it seems unthinkable to switch compositing managers part way through a 5 years support promise. If it could be done without the user noticing anything, well then it would be a different matter.

Regards.

Sure, but it needs help as himself cant makes the needed fixes on such short time before Precise release. Hopes that some skilled devs will make a pool to work with him :)

---

### Post by lucazade on 2012-02-04
good thread Dino..
I would bet on Unity 2D.. great performances thanks to the marvelous QT4 toolkit, OpenGL/ES backends for desktop and mobiles, great IDE like QtCreator to develop rich apps and good perspectives for future toolkit releases (QT5).
No compiz in my box.. they just need to purge metacity and provide a decent window manager.

---

### Post by effenberg0x0 on 2012-02-04
Have you guys tried Wayland? There was a thread in the Cafe about someone making a Wayland Test Live CD. I'm curious but really short on time to play.

Regards,
EFfenberg

---

### Post by t1497f35 on 2012-02-04
> **effenberg0x0 said:**
> Have you guys tried Wayland? There was a thread in the Cafe about someone making a Wayland Test Live CD. I'm curious but really short on time to play.

Regards,
EFfenberg
This sunday at fosdem 2012 will be announced that the Wayland devs plan to do a 1.0 release - but it could take like 2 months until they actually release it (cause right now Wayland is still buggy). Plus the Gtk+/Qt toolkits do support Wayland but there's a pile of issues yet to be solved, not to mention that LibreOffice etc use their own tookits which aren't supported at all.
So while Wayland is doing great progress - don't expect a usable desktop on top of Wayland this year.

---

### Post by jfernyhough on 2012-02-04
I'm sure I saw a YouTube clip that demoed Wayland and showed it running a nested X session for an xterm. This might mean we end up with X running in Wayland for "legacy" apps.

---

### Post by ronacc on 2012-02-04
> **effenberg0x0 said:**
> Have you guys tried Wayland? There was a thread in the Cafe about someone making a Wayland Test Live CD. I'm curious but really short on time to play.

Regards,
EFfenberg

got the dvd comming down now , will report when I test it .

---

### Post by keithpeter on 2012-02-04
> **lucazade said:**
> good thread Dino..
I would bet on Unity 2D.. 

Hello Dino, lucazade and all

Yes, where is Unity 2d going? (I've invested some time in 2d, see sig)

HUD appears to be Unity only. Shuttleworth appears to have 'pivoted' HUD from an optional component for power users into a core Unity affordance. Is there a plan?

PS: I'm glad Mr Spilsbury has resumed his posts, and I hope he has had a good rest, and gets some structured support from Canonical as Compiz seems central to Unity on 12.04 and perhaps 12.10

Cheers

---

### Post by BwackNinja on 2012-02-04
Whether it is dying on its own, or the world is killing it, Compiz is dying.

The only major distro that I see that still supports Compiz is Ubuntu, and it is at the point where it has to because of Unity. The closest thing to support from even Arch Linux is the old 0.8.x compiz in the Community repo, and git versions in AUR. There is no bzr version in AUR despite the fact that compiz no longer does development in git.

We have the great window decorator Emerald, which is no longer supported and has left hobbling along despite bugs.

It doesn't support the new antialiased window decorations you can use with Mutter although there was previous work towards that.

The only real new plugin we've got is Unity, everything else (while better structured and full of technical advantages) at best is at feature-parity with the 0.8.x series.

We've got people trying to kill Compizconfig-Settings-Manager, something that **defines** what Compiz is by exposing its plugin system. Without that, the modularity is only there for cleanness of code.

The cube, a **core** plugin has been unusable for a long time now, and there used to be visible work trying to fix it, but now I don't see anything.

At the very best, I'd say that all we've got left is "Unity Window Manager." That in itself is a lot for Ubuntu to be handling on its own, on top of all the changes to especially upstream Gnome that makes Unity too much of a pain to package. Like this, Ubuntu will be a project with only increasing maintainance burden.

The only real hope for Compiz as a project is probably the possibility of a Wayland port. This would allow a lot of the project to be rewritten, especially the currently problematic and complex parts that deal with X, which is one of the reasons why there aren't more developers working on it.

The only reasons for people being so supportive of Sam are because he seems to really be trying his best and cares about the project himself, while nobody wants to see Compiz disappear. Unfortunately we can't just call Compiz stable because of effort, it has to be because of success.

There is no replacement for Compiz. There are no window managers as ambitious as Compiz. Desktop-agnistic, OpenGL accelerated, compositing window manager (and it actually doesn't even *need* OpenGL or compositing, there are just not enough plugins that work without those). KWin is the closest thing there is to Compiz at the moment, but it is missing the desktop-agnostic part. It is so tied to KDE and leverages that power well, but that also means that it isn't Compiz. There is no other window manager to turn to, at best there are projects that we call "good enough."

---

### Post by ronacc on 2012-02-04
and they didn't think of this before they tied unity to compiz ???

---

### Post by dino99 on 2012-02-04
Well i hope that the compiz dev really get help in the coming days/weeks (and a bunch of support as Precise rely on it) to get a stable Precise. Then some backports could reach the archives.
For Precise+1, there is more time to choose the good design and may be rewrite some parts (of course Qt is stable/strong & so fine, but wayland will find its place too, and maybe something else too).
Anyway unity is not the only Precise choice, the ubuntu family is quite large. But maybe the installer (ubiquity) could give the choice of frontends when installing instead of setting compiz/unity by default. Myself does not really worry about unity, its not my choice on desktop/laptop, but i understand that tablet/mobile are good supports for it.

---

### Post by ronacc on 2012-02-04
@ effenberg0x0  tried the wayland live cd (dvd) , it booted but defaulted to xorg , wayland wouldn't run , libEGL problem .

---

### Post by effenberg0x0 on 2012-02-04
> **ronacc said:**
> @ effenberg0x0  tried the wayland live cd (dvd) , it booted but defaulted to xorg , wayland wouldn't run , libEGL problem .

Thank you for trying Ronacc. Maybe all the talk we see here and there about people running it with some stability are nothing but rumors..

---

### Post by ronacc on 2012-02-04
> **effenberg0x0 said:**
> Thank you for trying Ronacc. Maybe all the talk we see here and there about people running it with some stability are nothing but rumors..

I just did a quick try , I'll give it a little more time later . It booted to desktop ok but when I clicked the wayland icon nothing happened , investigating with top showed xorg running but not wayland , calling it from term gave an undefined symbol error in libEGL .

---

### Post by effenberg0x0 on 2012-02-04
> **ronacc said:**
> I just did a quick try , I'll give it a little more time later . It booted to desktop ok but when I clicked the wayland icon nothing happened , investigating with top showed xorg running but not wayland , calling it from term gave an undefined symbol error in libEGL .

I'm gonna see if I can try it this week.Which live cd did you download?

---

### Post by exploder on 2012-02-04
I see no problems with using compiz for this release. Wayland will come into future releases, right now it is not mature and compiz seems fine for now.

---

### Post by Mr. Picklesworth on 2012-02-04
> **BwackNinja said:**
> There is no replacement for Compiz. There are no window managers as ambitious as Compiz. Desktop-agnistic, OpenGL accelerated, compositing window manager (and it actually doesn't even *need* OpenGL or compositing, there are just not enough plugins that work without those). KWin is the closest thing there is to Compiz at the moment, but it is missing the desktop-agnostic part. It is so tied to KDE and leverages that power well, but that also means that it isn't Compiz. There is no other window manager to turn to, at best there are projects that we call "good enough."

I don't understand why we *need* a desktop-agnostic window manager. Okay, Mutter depends on GObject and all that jazz, but XFCE and Unity both happily depend on that as well.
Granted, XFCE is still on Gtk2, but that won't be forever.
(And besides, xfce has xfwm).

Off the top of my head, I can't think of a single desktop environment that doesn't have its own window manager. Most of the other things that are kind of like desktop environments call themselves window managers, anyway, much like Unity and Gnome Shell are today.

If it's about visual effects, I'd argue that many years of Compiz quite clearly demonstrate: a pretty window manager does not make a pretty desktop environment. (Remember the brown theme?). You can have windows wobble and explode all you like, but if the contents of those windows are as grey and lifeless as before, you haven't gotten anywhere. The only way to solve *that* is at the level of each application: have a good set of APIs (like the web, Qt 4, Gtk3(ish), Clutter) that make it really obvious for developers to create applications that look and feel good.

Sure, you can paint over the problem in an agnostic way (and Compiz has done that amazingly well), but it's a pretty thin layer of paint. The problem is very, very big and it cannot be solved without digging in and touching those dependencies and *changing things*.

And that is my over-dramatic opinion :)

---

### Post by ronacc on 2012-02-04
> **effenberg0x0 said:**
> Thank you for trying Ronacc. Maybe all the talk we see here and there about people running it with some stability are nothing but rumors..

I used the one from this thread , [http://ubuntuforums.org/showthread.php?t=1906762](http://ubuntuforums.org/showthread.php?t=1906762) , I didn't read the thread just saw the link and followed it . Had I been smart enough to read before clicking I would have seen that you have to run ```
 sudo bash 
``` then in the root term that opens run ```
 weston 
``` to get it to run . The window that opens is garbage on my sys , see SS . Maybe you'll have better luck .

---

### Post by effenberg0x0 on 2012-02-04
> **ronacc said:**
> I used the one from this thread , [http://ubuntuforums.org/showthread.php?t=1906762](http://ubuntuforums.org/showthread.php?t=1906762) , I didn't read the thread just saw the link and followed it . Had I been smart enough to read before clicking I would have seen that you have to run ```
 sudo bash 
``` then in the root term that opens run ```
 weston 
``` to get it to run . The window that opens is garbage on my sys , see SS. Maybe you'll have better luck .

Thanks a lot for the info Ronacc! I'll give it a try. We know wayland won't happen for 12.04 (and who knows if it will be ready for the next one)... but it's nice to test new stuff. 

On an side note (considering your wallpaper): I do wonder sometimes [http://www.whichseatcanitake.com/](http://www.whichseatcanitake.com/) .

Regards,
Effenberg

---

### Post by kyleabaker on 2012-02-04
> **effenberg0x0 said:**
> On an side note (considering your wallpaper): I do wonder sometimes [http://www.whichseatcanitake.com/](http://www.whichseatcanitake.com/) .

Thanks for that. Just had a 20 minute laugh with my roommates. :D

---

### Post by ronacc on 2012-02-04
> **effenberg0x0 said:**
> 
On an side note (considering your wallpaper): I do wonder sometimes [http://www.whichseatcanitake.com/](http://www.whichseatcanitake.com/) .

Regards,
Effenberg

I can't take credit for that , remember it was a live cd .:lolflag:
see ss for a samole of mine .

---

### Post by effenberg0x0 on 2012-02-04
> **ronacc said:**
> I can't take credit for that , remember it was a live cd .:lolflag:
see ss for a samole of mine .
Ah, now I got it lol... I thought that was incredibly awkward :) 
Romulan design, much better... Some of my wallpapers are BSG  (Cylon Raiders).
EDIT: Thinking about it a little, why humans never get to have the best taste for design (not only StarTrek, BSG, etc). Ok, no more OT.

---

### Post by BwackNinja on 2012-02-04
> **Mr. Picklesworth said:**
> I don't understand why we *need* a desktop-agnostic window manager. Okay, Mutter depends on GObject and all that jazz, but XFCE and Unity both happily depend on that as well.
Granted, XFCE is still on Gtk2, but that won't be forever.
(And besides, xfce has xfwm).

Off the top of my head, I can't think of a single desktop environment that doesn't have its own window manager. Most of the other things that are kind of like desktop environments call themselves window managers, anyway, much like Unity and Gnome Shell are today.

If it's about visual effects, I'd argue that many years of Compiz quite clearly demonstrate: a pretty window manager does not make a pretty desktop environment. (Remember the brown theme?). You can have windows wobble and explode all you like, but if the contents of those windows are as grey and lifeless as before, you haven't gotten anywhere. The only way to solve *that* is at the level of each application: have a good set of APIs (like the web, Qt 4, Gtk3(ish), Clutter) that make it really obvious for developers to create applications that look and feel good.

Sure, you can paint over the problem in an agnostic way (and Compiz has done that amazingly well), but it's a pretty thin layer of paint. The problem is very, very big and it cannot be solved without digging in and touching those dependencies and *changing things*.

And that is my over-dramatic opinion :)

We *don't* need a desktop-agnostic window manager. However, its an ideal. Rather than fit well just in some scenarios, it fits well in all of them. Compiz managed to be **beyond** desktop-agnostic. It is meant not only to work well outside of any specific desktop environment (hence the term "Compiz Standalone" thrown around) but also **integrate** into desktop environments. Its a powerful message to send if a project is able to do that properly. Qt3, Qt4, Gtk2, Gtk3, FLTK, whatever, Compiz has always been there for us integrating well and looking good. Ironically, the easiest window manager to compare it to is Openbox. You can use it in Gnome or KDE or XFCE or LXDE or whatever, and it is right at home. What you're referencing more than anything is a homogenous desktop, one that would pick either GTK or Qt, ignoring that the other even exists. Its hard to call Mutter a good fit for a KDE desktop just as its hard to call Kwin a good fit for a Gnome desktop. Compiz manages to do both.

You start well with your argument, but then you stray beyond the realm of a window manager just like people saying that Ubuntu should spend less time working on looks and more time fixing bugs. Compiz, nor any other window manager is meant to just bring the focus away from the toolkit and the applications, but rather make them easier to use together and switch between. It can't fix GTK or Qt theming or the APIs used to make applications. That's a separate issue. GTK has managed to tackle that now with CSS, but Compiz puts such high-level dependencies in their place. GTK and Qt are at the decoration level, not at the window management level where things **are** desktop-agnostic.

Compiz **isn't** a specific desktop environment's window manager, it is a suitable candidate for any desktop environment. It is just being locked out of major desktop environments because of the ties to the shell that environments are now having, even Unity.

Compiz has moved from a common denominator to a niche, and its not even its own fault.

---

### Post by cariboo on 2012-02-04
I actually think compiz died more than two years ago when all the other developers quit, leaving Sam holding the stick. His plan at the start of Maverick development was to drop any new development, and start creating plugins for mutter, then Canonical came along and hired him to start development again.

My feeling is that most of the extra plugins should be dropped, or made optional components, thereby taking some of the pressure off, and letting him concentrate on making compiz as good as it can be.

---

### Post by kyleabaker on 2012-02-04
> **cariboo907 said:**
> My feeling is that most of the extra plugins should be dropped, or made optional components, thereby taking some of the pressure off, and letting him concentrate on making compiz as good as it can be.

That is precisely what I was thinking as well.

---

### Post by dino99 on 2012-02-05
> **BwackNinja said:**
> We *don't* need a desktop-agnostic window manager. However, its an ideal. Rather than fit well just in some scenarios, it fits well in all of them. Compiz managed to be **beyond** desktop-agnostic. It is meant not only to work well outside of any specific desktop environment (hence the term "Compiz Standalone" thrown around) but also **integrate** into desktop environments. Its a powerful message to send if a project is able to do that properly. Qt3, Qt4, Gtk2, Gtk3, FLTK, whatever, Compiz has always been there for us integrating well and looking good. Ironically, the easiest window manager to compare it to is Openbox. You can use it in Gnome or KDE or XFCE or LXDE or whatever, and it is right at home. What you're referencing more than anything is a homogenous desktop, one that would pick either GTK or Qt, ignoring that the other even exists. Its hard to call Mutter a good fit for a KDE desktop just as its hard to call Kwin a good fit for a Gnome desktop. Compiz manages to do both.

You start well with your argument, but then you stray beyond the realm of a window manager just like people saying that Ubuntu should spend less time working on looks and more time fixing bugs. Compiz, nor any other window manager is meant to just bring the focus away from the toolkit and the applications, but rather make them easier to use together and switch between. It can't fix GTK or Qt theming or the APIs used to make applications. That's a separate issue. GTK has managed to tackle that now with CSS, but Compiz puts such high-level dependencies in their place. GTK and Qt are at the decoration level, not at the window management level where things **are** desktop-agnostic.

Compiz **isn't** a specific desktop environment's window manager, it is a suitable candidate for any desktop environment. It is just being locked out of major desktop environments because of the ties to the shell that environments are now having, even Unity.

Compiz has moved from a common denominator to a niche, and its not even its own fault.

Thanks for such explanations & classifications, it really help to sort some confused ideas around :)

---

### Post by dino99 on 2012-02-05
Sam appreciate the feedback and the debate:

[http://smspillaz.wordpress.com/2012/02/04/thanks/#comments](http://smspillaz.wordpress.com/2012/02/04/thanks/#comments)
[http://smspillaz.wordpress.com/compiz-stuff/](http://smspillaz.wordpress.com/compiz-stuff/)

---

### Post by t1497f35 on 2012-02-05
> **cariboo907 said:**
> I actually think compiz died more than two years ago when all the other developers quit, leaving Sam holding the stick. His plan at the start of Maverick development was to drop any new development, and start creating plugins for mutter, then Canonical came along and hired him to start development again.

My feeling is that most of the extra plugins should be dropped, or made optional components, thereby taking some of the pressure off, and letting him concentrate on making compiz as good as it can be.
Agree, plus it took too much time rewriting it to C++ which kinda reminds me of Netscape when they decided to rewrite their browser and ultimately lost grip.

Also, I think Compiz should be simplified and like 3/4 functionality thrown off until great graphics drivers are available, without them so many sophisticated options just can't work together on a most hw. Only most useful functionality must be present.

---

### Post by MacUntu on 2012-02-05
Compiz is dead? Again? :D

---

### Post by VMC on 2012-02-05
> **MacUntu said:**
> Compiz is dead? Again? :D

Like a zombie, it never dies - walks funny, tattered clothes and sounds strange.

I keep hearing it's dead, no its still alive, no its dead again. This is worse than a Steven King movie.

---

### Post by lucazade on 2012-02-05
it is time for a new beryl :)

---

### Post by ronacc on 2012-02-05
drive a stake through its heart ! oops wrong creature , that won't kill a zombie .

---

### Post by dino99 on 2012-02-05
sudo compiz --stay-alive  -:)

---

### Post by EgoGratis on 2012-02-06
I think now is the time for precision in Precise Pangolin but after this is done i think is the time for serious talks. Common composition manager for Gnome/KDE/Unity... should be the outcome and it should be better then all the ones we have now.

---

### Post by EgoGratis on 2012-02-06
Word about Compiz compositor. I tried to use Unity 2D a lot of times and i read a lot how something like Compiz is not technically needed but why in the end i always end up in Unity 3D?

---

### Post by jerrylamos on 2012-02-07
> **lucazade said:**
> good thread Dino..
I would bet on Unity 2D.. great performances thanks to the marvelous QT4 toolkit, OpenGL/ES backends for desktop and mobiles, great IDE like QtCreator to develop rich apps and good perspectives for future toolkit releases (QT5).
No compiz in my box.. they just need to purge metacity and provide a decent window manager.

Unity-2D running great here! on pc's that will support -3 D (with its big fuzzy hard to read images and constant compiz overhead) as well as my quick thinkpad T40 that won't do pae.  (Somebody, what advantage is pae now?)

Hoping Unity-2D will stay in the mix.  I've tried HUD, got a bug, and it's not working on updated precise pangolin now.

Jerry

---

### Post by cariboo on 2012-02-07
> **jerrylamos said:**
> Unity-2D running great here! on pc's that will support -3 D (with its big fuzzy hard to read images and constant compiz overhead) as well as my quick thinkpad T40 that won't do pae.  (Somebody, what advantage is pae now?)

Hoping Unity-2D will stay in the mix.  I've tried HUD, got a bug, and it's not working on updated precise pangolin now.

Jerry

This is so far of topic, but, a pae kernel will allow i386 processors to access 64GiB of ram which your non-pae cpu will never be able to do.

Back on topic, if you are running Unity 5.2 there are no big fuzzy icons any more. See the screenshot. As far as compiz using a lot of resources check the second screenshot, on my system is using 1% of cpu resources.

---

### Post by ventrical on 2012-02-07
> **cariboo907 said:**
> This is so far of topic, but, a pae kernel will allow i386 processors to access 64GiB of ram which your non-pae cpu will never be able to do.

Back on topic, if you are running Unity 5.2 there are no big fuzzy icons any more. See the screenshot. As far as compiz using a lot of resources check the second screenshot, on my system is using 1% of cpu resources.

 Thanks a million cariboo907.  All my compiz /ccsm installs work great also. Low resource, great animation.

regards,

ventrical

---

