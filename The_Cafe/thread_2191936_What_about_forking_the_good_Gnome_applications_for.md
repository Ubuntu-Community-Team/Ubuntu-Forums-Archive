---
title: "What about forking the good Gnome applications for Unity?"
date: 2013-12-05
forum: The Cafe
---

### Post by lads on 2013-12-05
In the past one of the strengths of Gnome was the quality of its applications: Nautilus, GEdit, Evince, EoG, Terminal, etc. This was actually one of the reasons behind the success with Unity, with all these great applications behind the user experience improved considerably.

Unfortunately Gnome has diverged from the desktop in recent years, producing an environment with different (and unclear) goals. This has been having a negative impact on its applications, notably on Nautilus, but the side effects go beyond that. One of the consequences of this degradation in Gnome applications is their lack of integration with Unity. [I just found out]("http://ubuntuforums.org/showthread.php?t=2191641") that Evince is no longer accessible from the HUD, apparently as a pure design option. Going forward I expect this sort of issues to become more serious and eventually affect all Gnome applications.

Just as the Mint folk forked Nautilus when its usability started to be visibly degraded, I feel that all these once good Gnome applications should be forked for Unity. 

What do you think? Would this be something useful? Would it square with the long term path Ubuntu is taking?

I am quite willing to contribute to such a project, although I may be missing some of the knowledge at the moment. If other folk are willing to join this can become way easier.

---

### Post by monkeybrain20122 on 2013-12-05
Yeah, first I notice that with Nautilus all the buttons are fixed on the right along with other things. It is going to happen with with all other gnome-applications too eventually. I found a patched version of Nautilus that restores some kind of consistency with Unity (no HUD doesn't work) 
[https://launchpad.net/~mc3man/+archive/sacy-tests](https://launchpad.net/~mc3man/+archive/sacy-tests)  Never mind forking, something like this is probably the minimal that needs to be done eventually if they stick with gnome.

Don't know if they need to do this on a per app basis (which would be horrible) or if they can just apply a single fix to all of them..

---

### Post by QDR06VV9 on 2013-12-05
> **lads said:**
> I This has been having a negative impact on its applications, _[COLOR=#ff0000]notably on Nautilus[/COLOR]_, but the side effects go beyond that. One of the consequences of this degradation in Gnome applications is their lack of integration with Unity. [I just found out]("http://ubuntuforums.org/showthread.php?t=2191641") that Evince is no longer accessible from the HUD, apparently as a pure design option. Going forward I expect this sort of issues to become more serious and eventually affect all Gnome applications.

Just as the Mint folk forked Nautilus when its usability started to be visibly degraded, I feel that all these once good Gnome applications should be forked for Unity. 



Could not agree more! I almost scraped gnome for KDE which has found a warm place in my heart.
Have you tried Nemo on gnome? It has brought enough form and function back at least for me, I enjoy gnome much more now.:)
Regards
[h=2]Nemo ppa for Trusty available now. With Unity patches and no cinnamon dependencies.[/h][http://www.webupd8.org/2013/10/insta...tches-and.html](http://www.webupd8.org/2013/10/insta...tches-and.html)

---

### Post by monkeybrain20122 on 2013-12-05
First of all installing nemo brings in a lot of dependencies, secondly (and more important) it doesn't replace Nautilus, but co-exists with it that means there will be conflicts about which control what. I tested it briefly in 13.04, don't remember the details now, except that somethings behaved really strangely or not working. tried to fix them for a few days without sucess. I concluded that the cure was worse than than the disease and removed nemo after that. The only workable alternative was a patched version of Nautilus 3.4 by solusOS which actually replaced the default version and took over, but of course solusoS is gone now.

Some people suggest Marlin, but it is even more stripped down and unusable than Nautilus IMO (and there are suggestions for pcmanfm and thunar but  aside from the problem of two file managers co-existing both are lacking in functions and even more annoying to use than Nautilus in my experience,--especially thunar)

---

### Post by philinux on 2013-12-05
If you want nemo without all the deps look here.

[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

---

### Post by lykwydchykyn on 2013-12-05
With Unity being rewritten in Qt/QML, I kind of wonder what is the long-term future of Gnome applications in Ubuntu.  Seems to me they could as well pull applications from any desktop environment or write their own in QML using the same underlying libraries (gvfs, e.g.).

---

### Post by QDR06VV9 on 2013-12-05
> **monkeybrain20122 said:**
> First of all installing nemo brings in a lot of dependencies, secondly (and more important) it doesn't replace Nautilus, but co-exists with it that means there will be conflicts about which control what.
Well most non-native file mangers bring in extra packages or dependencies, and since you haven't tested it since 13.04 you probably have not experienced the changes in Nemo.
But hey to each there own.;) For me it is a game changer it is a work flow much like the gnome of old IMHO. Its a Keeper for Me.:)
Did you even read the links Me and philunux provided, It is very stable and smooth works a treat!
Regards

---

### Post by monkeybrain20122 on 2013-12-05
> **runrickus said:**
> Well most non-native file mangers bring in extra packages or dependencies, and since you haven't tested it since 13.04 you probably have not experienced the changes in Nemo.
But hey to each there own.;) For me it is a game changer it is a work flow much like the gnome of old IMHO. Its a Keeper for Me.:)
Did you even read the links Me and philunux provided, It is very stable and smooth works a treat!
Regards

It is not so much the extra packages, but the conflicts between two co-existing file managers. I just read the webupd8 link and the long list of problems that this patched version has supposedly overcome is exactly why I thought nemo was a worse cure than the disease when I tried it in 13.04. This new patched version does look promising if the issues on that list are resolved. I will test it out in a few days and report back.

Now what to do with evince? :)

---

### Post by RichardET on 2013-12-06
> **monkeybrain20122 said:**
> Yeah, first I notice that with Nautilus all the buttons are fixed on the right along with other things. It is going to happen with with all other gnome-applications too eventually. I found a patched version of Nautilus that restores some kind of consistency with Unity (no HUD doesn't work) 
[https://launchpad.net/~mc3man/+archive/sacy-tests](https://launchpad.net/~mc3man/+archive/sacy-tests)  Never mind forking, something like this is probably the minimal that needs to be done eventually if they stick with gnome.

Don't know if they need to do this on a per app basis (which would be horrible) or if they can just apply a single fix to all of them..

Do you use Ubuntu exclusively, or are you using other distributions as well?

---

### Post by monkeybrain20122 on 2013-12-06
> **RichardET said:**
> Do you use Ubuntu exclusively, or are you using other distributions as well?

Mostly Ubuntu and for some things Fedora (gshell). I keep a third distro just for experimenting, first Debian sid, now Manjaro and will switch that to Arch once I get more comfortable. I find Ubuntu most polished and always reliable overall. while Fedora is good, I find sound and graphics doesn't work as well as Ubuntu on my hardware and it doesn't have software support as good as Ubuntu's. I really like Unity, which works only on Ubuntu (gshell is nice, but it feels claustrophobic and less fluid comparing to Unity, I don't really like kde)

---

