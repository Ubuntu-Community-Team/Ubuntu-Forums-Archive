---
title: "What would Gnome be like if it was written/used QT?"
date: 2008-12-15
forum: The Cafe
---

### Post by master5o1 on 2008-12-15
Wild speculation thread :)

I wonder what Gnome would be if it were rewritten using QT but still in keeping with very Gnomish principles.

---

### Post by Giant Speck on 2008-12-15
Kde 3.5?

---

### Post by Sand &amp; Mercury on 2008-12-15
It would mean that KDE and (new) GNOME apps could live in peace and harmony! It would also mean me using the wonderful Oxygen theme. :KS

---

### Post by GeneralZod on 2008-12-15
Not very different from current GNOME, really.

---

### Post by igknighted on 2008-12-15
QT's bindings are for C++, not C like GTK's.  The port would involve a complete rewrite of each program, not just the GUI.

FWIW, I think the object-oriented C++ would make it much more developer friendly.

---

### Post by Blutack on 2008-12-15
Buggy, broken and not backwards compatible...

---

### Post by LuisAugusto on 2008-12-15
Hmmm... probably the same, plus some advanced things that Gtk can't do.

---

### Post by Vadi on 2008-12-15
It would never be finished, because developers would tear their hair out and strangle themselves while attempting to work with the Qt Designer.

If they do manage to miraculiously finish it though, it would look completely out of place as Qt has no HIG on Linux to go by (they attempt to fit in Apple and Windows though), so their engineers just make up the default they *think* are good. Which are rather poor, so Qt on Linux looks crap.

---

### Post by bruce89 on 2008-12-15
> **LuisAugusto said:**
> Hmmm... probably the same, plus some advanced things that Gtk can't do.

I'm sure that GTK+ can do anything if developers wanted it to happen.

> **igknighted said:**
> FWIW, I think the object-oriented C++ would make it much more developer friendly.

GObject is a bit of a pain, but C++ is widely regarded as horribly complex. Also, GObject-introspection (automated binding generation) looks very interesting.

---

### Post by klange on 2008-12-15
It would all be written in C++ and suffer massive performance decreases.[/sarcasm]


Seriously, why does it matter what toolkit you use these days when we have emulation themes for every other toolkit. If you use QT, you have qgtkstyle (which is quite nice), and if you use GTK you have... um... whatever that one's called (I don't run KDE, and so I don't know...)

---

### Post by happysmileman on 2008-12-15
> **bruce89 said:**
> GObject is a bit of a pain, but C++ is widely regarded as horribly complex. Also, GObject-introspection (automated binding generation) looks very interesting.

C++ is basically a superset of C, C code will compile as C++ (well, almost all the time) and there's nothing forcing you to use all (OR ANY) of the features that people discredit C++ for.

---

### Post by phrostbyte on 2008-12-15
Total harmony? I don't think it is possible, Gnome would fork Qt to be GNU/Qt or GQt and change it enough to be completely incompatible with KDE version :lolflag:

---

### Post by klange on 2008-12-15
> **happysmileman said:**
> Can I see how this was shown? Seriously?
People say this but they all seem to go quiet when asked to prove it.
And for each link you can give claiming this I can give one claiming the opposite, claims on the internet are not proof.
You're clearly incapable of judging sarcasm on the Internet. You should see someone about that. I in no way believe using C++ would cause performance problems in GNOME.

---

### Post by bruce89 on 2008-12-15
> **phrostbyte said:**
> Total harmony? I don't think it is possible, Gnome would fork Qt to be GNU/Qt or GQt and change it enough to be completely incompatible with KDE version :lolflag:

Actually that reminds me. GTK+ is LGPL, but Qt is GPL. If GNOME used Qt (they never will), nothing commercial could be written for GNOME (barring licensing of Qt that is).

---

### Post by hanzomon4 on 2008-12-15
It would be like kde but with  G in front of everything.. so basically Gnome

---

### Post by happysmileman on 2008-12-15
> **WindowsSucks said:**
> You're clearly incapable of judging sarcasm on the Internet. You should see someone about that. I in know way believe using C++ would cause performance problems in GNOME.

Ah sorry, my web browser must be missing the ability to detect the tone of your e-voice.

---

### Post by hanzomon4 on 2008-12-15
> **happysmileman said:**
> Ah sorry, my web browser must be missing the ability to detect the tone of your e-voice.

It's all PulseAudio's fault!!!!

---

### Post by samjh on 2008-12-15
> **Blutack said:**
> Buggy, broken and not backwards compatible...

Like Gnome 1 -> Gnome 2.

:p

I've used KDE and Gnome since their baby-steps days, and they were both horribly bad compared to their modern evolutions.

> **master5o1 said:**
> Wild speculation thread :)

I wonder what Gnome would be if it were rewritten using QT but still in keeping with very Gnomish principles.

For users: No difference apart from the theme.

For programmers: API that actually make sense. ;)

---

### Post by Trail on 2008-12-16
> **happysmileman said:**
> C++ is basically a superset of C, C code will compile as C++ (well, almost all the time) and there's nothing forcing you to use all (OR ANY) of the features that people discredit C++ for.

Except when you *have* to use a particular library and said library requires the use of certain more advanced C++ features you are not familiar with. In this case, you are pretty much forced to study it.

First time I encountered templates was in such a library. And I was "zomg liek wtf? what are those bracket things?" Then I googled it. And I understood pretty much nothing :D And I hated my univ for staying about 256 years outdated on C++ (although our teacher was awesome, tbh).

After a LOT of time (6-12 months) I came to totally love templates, and I now use them comfortably and (I hope) proficiently. But the transition was anything but smooth.

C++ can be a total bitch, but once you learn it it's VERY powerful. Its beauty for me is in the libraries. It needs a lot of pain and skill to write a good library, but users of the library should be able to do miracles with just a few lines of code, easily and very maintainable.

And for those saying that C++'s performance is slower than C, well that is true. But marginally. However, it's not the C or C++ performance difference that you really see, but the developers algorithm's efficiency, unless said developer does something wrong (for example, making a lot of temporary objects, calls to constructors etc, instead of using references). I really admire several optimization techniques, anyway, especially in conjunction with debugging. I don't think that's any issue here. (And if nothing else, a bit slower machine execution is very much more preferable than a lot slower application development, isn't it?)

And personnaly, I admire both KDE's and QT's quality in terms of code. Now that the pain of writing the libraries is already invested, end-user code (front ends, configurations, plasmoids, stuff like that) is easy to write. You have already seen the huge growth of KDE4 in the last 6 months. I blame a large part of this on usage of C++.

tl;dr I support the usage of C++ over C.

---

### Post by ZuLuuuuuu on 2008-12-16
If Gnome would be rewritten with Qt there would be no serious place to use GTK and GTK would probably die or, at least, it would not be maintaned as fast as it is now. Then we would have no pretty GUI library to use with C language :( Also I would have no option but paying Trolltech to write closed source software or using ugly wxWidgets :(

---

### Post by Trail on 2008-12-17
> Also I would have no option but paying Trolltech to write closed source software

Trolltech^WQT Software uses a dual license. You don't need to pay anything if you are making open-source software. If you write a commercial program, there is licensing involved, but I'll go ahead and make the assumption that the company you work for will pay it :)

---

### Post by th-busch on 2008-12-17
You can write Gtk apps in (object-oriented) c++, just use the [gtkmm]("http://gtkmm.org/") wrapper (which is pretty good in my opinion), so you have a full-featured, object-oriented gui without the licensing restrictions QT has. That said, i don't like the idea of Gnome using QT.

---

### Post by ZuLuuuuuu on 2008-12-17
> **Trail said:**
> Trolltech^WQT Software uses a dual license. You don't need to pay anything if you are making open-source software. If you write a commercial program, there is licensing involved, but I'll go ahead and make the assumption that the company you work for will pay it :)

I know, that's why I wrote "closed source software" in the sentence.

---

### Post by Half-Left on 2008-12-17
Faster, By the way, it's Qt not QT.

---

### Post by Half-Left on 2008-12-17
> **th-busch said:**
> You can write Gtk apps in (object-oriented) c++, just use the [gtkmm]("http://gtkmm.org/") wrapper (which is pretty good in my opinion), so you have a full-featured, object-oriented gui without the licensing restrictions QT has. That said, i don't like the idea of Gnome using QT.

Qt is GPL, has been for a long time now.

---

### Post by Vadi on 2008-12-17
Only if you're an open-source project. Otherwise, there are hefty licensing fees.

---

### Post by Half-Left on 2008-12-17
> **Vadi said:**
> Only if you're an open-source project. Otherwise, there are hefty licensing fees.

Dont see a problem with that, you'd be surprised how many companies are willing to pay for it, Nokia for example.

---

### Post by mentallaxative on 2008-12-17
> **Half-Left said:**
> Faster, By the way, it's Qt not QT.

Proof? ;)

I think it would be almost the same, really.

---

### Post by loell on 2008-12-17
> **Half-Left said:**
> Dont see a problem with that, you'd be surprised how many companies are willing to pay for it, Nokia for example.

if you're a multi billion dollar company on a multi billion dollar industry, then hell yeah.. ;)

even [acquisition ]("http://www.techcrunch.com/2008/01/28/nokia-acquires-trolltech-for-153-million/") won't be a problem! :lolflag:

---

### Post by Half-Left on 2008-12-17
> **mentallaxative said:**
> Proof? ;)

I think it would be almost the same, really.

it's always been known that Qt is faster than GTK, much more responsive, cairo slowed down gtk rather badly, svg rendering is slow as hell.

---

### Post by Vadi on 2008-12-17
> **Half-Left said:**
> Dont see a problem with that, you'd be surprised how many companies are willing to pay for it, Nokia for example.

Nokia actually bought it. They can use it free all they want.

Yes, there are commercial companies that use Qt - it does a great job of poorly integrating with the majority of linux desktops (even with the qgtkstyle hacks and whatnot). That's about it!

---

### Post by Half-Left on 2008-12-17
> **loell said:**
> if you're a multi billion dollar company on a multi billion dollar industry, then hell yeah.. ;)

even [acquisition ]("http://www.techcrunch.com/2008/01/28/nokia-acquires-trolltech-for-153-million/") won't be a problem! :lolflag:

Sure but All opensource projects can use Qt free, which is what Ubuntu is about so it's a non issue.

---

### Post by Half-Left on 2008-12-17
> **Vadi said:**
> Nokia actually bought it. They can use it free all they want.

Yes, there are commercial companies that use Qt - it does a great job of poorly integrating with the majority of linux desktops (even with the qgtkstyle hacks and whatnot). That's about it!

What nonsense do you speak of?, KDE is one if not the most popular DE's out there, just because a few other desktop choose gtk dont mean anything.

---

### Post by loell on 2008-12-17
> **Half-Left said:**
> Sure but **All opensource projects can use Qt free**, 

nah.. not really, apache couldn't use it, and neither could the kernel. :biggrin:

but the fact there are twice as gtk apps for every qt apps, should say something about toolkit preferences alone.

---

### Post by Half-Left on 2008-12-17
> **loell said:**
> nah.. not really, apache couldn't use it, and neither could the kernel. :biggrin:

but the fact there are twice as gtk apps for every qt apps, should say something about toolkit preferences alone.

And do you know why that is?, for one start when Qt was not GPL many years ago and app devs already used gtk because of it so they got a head start.

More apps dont mean better, you should know that and there a many great Qt apps out there so your reason is worthless.

---

### Post by loell on 2008-12-17
> **Half-Left said:**
> And do you know why that is?, for one start when Qt was not GPL many years ago and app devs already used gtk because of it so they got a head start.

yes i know very well the reason, and it has nothing to do with QT's former license, that's because the kernel and apache are none UI **opensource applications**. :lolflag: 


> **Half-Left said:**
> 
More apps dont mean better, you should know that and there a many great Qt apps out there so your reason is worthless.

there you go, yes its true more apps doesn't mean "better" but it doesn't mean "worst" either.  "better" is subjective too. what i said was since there are more gtk applications, it should say something about UI toolkit preferences on Open source desktop applications. :)

---

### Post by mentallaxative on 2008-12-17
> **Half-Left said:**
> it's always been known that Qt is faster than GTK, much more responsive, cairo slowed down gtk rather badly, svg rendering is slow as hell.

Hmmm, ok. Thanks for the info. I'd like to see more lightweight Qt apps being developed if it is indeed faster than Gtk.

---

### Post by Half-Left on 2008-12-17
> **loell said:**
> yes i know very well the reason, and it has nothing to do with QT's former license, that's because the kernel and apache are none UI **opensource applications**. :lolflag: 




there you go, yes its true more apps doesn't mean "better" but it doesn't mean "worst" either.  "better" is subjective too. what i said was since there are more gtk applications, it should say something about UI toolkit preferences on Open source desktop applications. :)

It says nothing because of what I outlined previous, they picked GTK because Qt was not GPL at the time and they developed their apps from then, if Qt was always GPL from day one who knows what would have happened.

---

### Post by loell on 2008-12-17
> **Half-Left said:**
> It says nothing because of what I outlined previous. okay.. ;)

>  they picked GTK because Qt was not GPL at the time and they developed their apps from then

provide a proof that all gtk apps was created before the Dual licensing of Qt. can you? ;)


> if Qt was always GPL from day one who knows what would have happened.

let me add a couple, what if solaris and java was opensourced from day one?...

exactly! they would have become the choice of many many more!

---

### Post by Half-Left on 2008-12-17
> **loell said:**
> okay.. ;)



provide a proof that all gtk apps was created before the Dual licensing of Qt. can you? ;)




let me add a couple, what if solaris and java was opensourced from day one?...

exactly! they would have become the choice of many many more!

So you basing your entire point on the fact that there are more GTK apps than Qt ones?

Thats a very weak as I've outlined, more GTK apps dont mean the toolkit is better. Qt designer is extremely good and easy to use, VLC just ported to Qt4, opesuse's YaST going to Qt4 from Qt3. Also go look at qt-apps.org and kde-apps.org and tell otherwise.

---

### Post by Vadi on 2008-12-17
I've developed user interfaces with both gtk's glade designer and qt's qt designer.

Fact: You can't do everything in qt designer that you can do in qt, forcing you to add code to your interface. This completely breaks the idea of presentation and content (ala html/css).

Fact: qt partially follows mac guidelines on mac, windows guidelines on windows. on linux, it doesn't follow anybodys - their engineers make up their own. Which turn out to be rather poor, unthought out design decisions that make it hard to make a good user interface.

The thing about gtk is that it is *designed* to be hig-compliant, and makes it *easy* for developers to create good interfaces. It makes them to less work. For Qt, no. Designed for commercial usage, where "as long as the button works, we're good. Nobody gives a damn about usability or design" rules.

---

### Post by happysmileman on 2008-12-17
> **loell said:**
> provide a proof that all gtk apps was created before the Dual licensing of Qt. can you? ;)

Complete strawman, he never said or implied that all GTK apps were crated before then, but most of the largest ones (which have been dveeloped for a long time) such as GNOME were created before this, and then even after the dual-licensing since GNOME was written in GTK the trend kept up (since many programs are written with GNOME in mind)

> **Vadi said:**
> Yes, there are commercial companies that use Qt - it does a great job of poorly integrating with the majority of linux desktops (even with the qgtkstyle hacks and whatnot). That's about it!

Integrates perfectly with KDE, and at least Qt decided to make QGTKStyle to try and address this problem and integrate better, I've heard many people on these forums praising it, and from screenshots it looks decent (but not perfect), GTK made no such effort to integrate with KDE (Don't bother mentioning gtk-qt-engine, which AFAIK isn't developed by GTK)

---

### Post by Half-Left on 2008-12-17
In the end it's all if's and buts, just like Python is better than perl because it lets you do X better and Y.

---

### Post by loell on 2008-12-17
> **Half-Left said:**
> So you basing your entire point on the fact that there are more GTK apps than Qt ones?  obviously, yes. 

> **Half-Left said:**
> 
Thats a very weak as I've outlined

I don't see you're outline, sorry.

> **Half-Left said:**
> 
more GTK apps dont mean the toolkit is better. 

I think we've already established that. fewer qt apps doesn't mean better or worse either. more gtk  apps means, more developers prefer gtk.


>  VLC always ported to QT4.

i don't know what you really meant by that. but if you mean vlc is now Qt4, well? so? it didn't used gtk before. it was wxwidget. C++ UI mapping to another C++ UI toolkit is easier.

 > Also go look at qt-apps.org and kde-apps.org and tell otherwise.
actually, I went to [http://www.gtk-apps.org/]("http://www.gtk-apps.org/") and also did ```
apt-cache search gtk apps
``` ):P

ah well, as always these Qt vs Gtk argument is pointless, it makes other toolkits scream ( hey, what about us!!?)

---

### Post by Half-Left on 2008-12-17
> **happysmileman said:**
> Integrates perfectly with KDE, and at least Qt decided to make QGTKStyle to try and address this problem and integrate better, I've heard many people on these forums praising it, and from screenshots it looks decent (but not perfect), GTK made no such effort to integrate with KDE (Don't bother mentioning gtk-qt-engine, which AFAIK isn't developed by GTK)

Indeed, just look at Qt themes, Qt4 has cleanlooks which blend in well with Clearlooks, GTK has done nothing of the sort.

---

### Post by loell on 2008-12-17
> **happysmileman said:**
> Complete strawman,

correct :D , pick your own arguments with others will you? you're blowing my cover man. :lolflag:

---

### Post by Half-Left on 2008-12-17
> **loell said:**
> obviously, yes. 



I don't see you're outline, sorry.



I think we've already established that. fewer qt apps doesn't mean better or worse either. more gtk  apps means, more developers prefer gtk.




i don't know what you really meant by that. but if you mean vlc is now Qt4, well? so? it didn't used gtk before. it was wxwidget. C++ UI mapping to another C++ UI toolkit is easier.

 
actually, I went to [http://www.gtk-apps.org/]("http://www.gtk-apps.org/") and also did ```
apt-cache search gtk apps
``` ):P

ah well, as always these Qt vs Gtk argument is pointless, it makes other toolkits scream ( hey, what about us!!?)

ok, so 89% of computer users use Windows because it's a better OS do they?, nope, I dont think so.

I think you'll find that it's simply not true what your saying about more devs prefer gtk, if they changed the licence to some more restrictive then you'll find your point falls apart.

yes I know it was wxwidgets, but they didn't port it to this prefered GTK toolkit you talk of. BTW, Qt4 has phonon now so you can use it without having to bother about which of the 10's of backends to support for your player

---

### Post by happysmileman on 2008-12-17
> **Half-Left said:**
> ok, so 89% of computer users use Windows because it's a better OS do they?, nope, I dont think so.

I know I'm kinda on your side of the argument (to the extent that I'm on any side) but really, he didn't say that more apps using it made it better, in fact he specifically said that WASN'T the case.

---

### Post by Half-Left on 2008-12-17
Better/prefered is what I meant, depends on your interpretation.

---

### Post by loell on 2008-12-17
> **Half-Left said:**
> ok, so 89% of computer users use Windows because it's a better OS do they?, nope, I dont think so. 

i fail to see the relationship, you're still sticking with your "better". while i argued preference due to quantity of projects.


> **Half-Left said:**
> 
I think you'll find that it's simply not true what your saying about more devs prefer gtk, if they changed the licence to some more restrictive then you'll find your point falls apart.

i dunno, why you turned 90 degrees from you're original stance, wasn't your point, that the dual licensing was never an issue with both open source project and commercial applications that uses Qt? hence you mentioned Nokia?

that has been my point all along, that gtk app developers prefer gtk toolkit because its not dually licensed. Edit: that gtk toolkit can be used commercially without having to pay for commercial licensing.

---

### Post by Half-Left on 2008-12-17
> **loell said:**
> i fail to see the relationship, you're still sticking with your "better". while i argued preference due to quantity of projects.




i dunno, why you turned 90 degrees from you're original stance, wasn't your point, that the dual licensing was never an issue with both open source project and commercial applications that uses Qt? hence you mentioned Nokia?

that has been my point all along, that gtk app developers prefer gtk toolkit because its not dually licensed.

Nokia was a example, the fact they brought trolltech is not the point. In the end if any one dont want to pick a toolkit based of the fact it has a dual licence then thats there downfull(even though it doesn't effect them on their project), it's never harmed KDE.

---

### Post by Vadi on 2008-12-17
Half-Left, would be great if you didn't ignore my sticking points with Qt!

Also, have you ever read any HIGs or did interface design?

---

### Post by Half-Left on 2008-12-17
> **Vadi said:**
> Half-Left, would be great if you didn't ignore my sticking points with Qt!

Also, have you ever read any HIGs or did interface design?

It's not something I usually do, but I have used glade 3 in the past but didn't get into it enough but I did do a few UI designs.

As for HIG's well no but alot of GTK apps dont follow the GNOME HIG anyway.

---

### Post by LuisAugusto on 2008-12-17
My god, people is quite bad at making arguments:

[LIST]
[*]Quantity = Quality. So based on that Windows toolkit is a hell lot better, there are soooooooooooooooooooooooo much more application using it.

[*]Qt double license is bad?. Come on people, is one of the few examples of how to make a good open source business, if you're making OSS, be free, you can code whatever you want, if you're going to code closed source, pay us. It's perfect, it doesn't affect in any way the OSS and they earn money.
[/LIST]

---

### Post by Vadi on 2008-12-17
> **Half-Left said:**
> It's not something I usually do, but I have used glade 3 in the past but didn't get into it enough but I did do a few UI designs.

As for HIG's well no but alot of GTK apps dont follow the GNOME HIG anyway.

Well then, your word doesn't mean much, sorry. The Desktop Enviroment itself must be the epitome of the HIG it implements - 3rd party programs are a different thing. GTK, by nature, was designed to help you follow the HIG and a lot of times you don't need to do anything special, it "just works". Qt - hooh, good luck with that. It's as stripped down as it gets plus some (sorry) stupidity in the designer.

---

### Post by Half-Left on 2008-12-17
> **Vadi said:**
> Well then, your word doesn't mean much, sorry. The Desktop Enviroment itself must be the epitome of the HIG it implements - 3rd party programs are a different thing. GTK, by nature, was designed to help you follow the HIG and a lot of times you don't need to do anything special, it "just works". Qt - hooh, good luck with that. It's as stripped down as it gets plus some (sorry) stupidity in the designer.
 
Yes but they dont follow them regardless, lets not make out gnome enforce their HIG with monthly hangings like Apple do. :p

GNOME is has plently of ugly UI mess, their own dev pointed them out, didn't get fixed for years.

---

### Post by Vadi on 2008-12-17
> **Half-Left said:**
> Yes but they dont follow them regardless, lets not make out gnome enforce their HIG with monthly hangings like Apple do. :p

GNOME is has plently of ugly UI mess, their own dev pointed them out, didn't get fixed for years.

Please show the "plenty" of the mess and HIG clearly being broken - because I'm not entirely convinced...

---

### Post by Half-Left on 2008-12-17
> **Vadi said:**
> Please show the "plenty" of the mess and HIG clearly being broken - because I'm not entirely convinced...

Well they CAN break the HIG if need be, it's only a guide, GNOME are interface nazi's because they are, not because of some HIG that make it better.

---

### Post by loell on 2008-12-17
> **LuisAugusto said:**
> My god, people is quite bad at making arguments:

in your sig (** help me improve my English. Thanks in advance**) , hope you don't mind quoting your sig. because in your first point you need better reading comprehension.


> **LuisAugusto said:**
> 
[LIST]
**[*]Quantity = Quality**. So based on that Windows toolkit is a hell lot better, there are soooooooooooooooooooooooo much more application using it. 

who said that? 

> **LuisAugusto said:**
> 
[*]**Qt double license is bad?**. Come on people, is one of the few examples of how to make a good open source business, if you're making OSS, be free, you can code whatever you want, if you're going to code closed source, pay us. It's perfect, it doesn't affect in any way the OSS and they earn money.
[/LIST]

no, not a bad license per se, but if you're freelancing (small timer), you would very much prefer a toolkit that you don't have to pay ( or save the hassle from filing a "Qt i couldn't pay" form) in the event that you launch  you're desktop app commercially.

---

### Post by Half-Left on 2008-12-17
> **loell said:**
> 
no, not a bad license per se, but if you're freelancing (small timer), you would very much prefer a toolkit that you don't have to pay ( or save the hassle from filing a "Qt i couldn't pay" form) in the event that you launch  you're desktop app commercially.

So you are talking about commercial now?, What has that to do with what we are talking about?,

When you go commercial with your app, who is going to support your toolkit, fix bugs, I know one thing for sure, GTK dev's wont fix your bugs when you need it for your commercial app.

---

### Post by Vadi on 2008-12-17
At first you bash them with "GNOME is has plently of ugly UI mess, their own dev pointed them out, didn't get fixed for years.", then you excuse them with:
> **Half-Left said:**
> Well they CAN break the HIG if need be, it's only a guide, GNOME are interface nazi's because they are, not because of some HIG that make it better.

Sorry dude, but you aren't making a point here.

---

### Post by Half-Left on 2008-12-17
> **Vadi said:**
> At first you bash them with "GNOME is has plently of ugly UI mess, their own dev pointed them out, didn't get fixed for years.", then you excuse them with:


Sorry dude, but you aren't making a point here.

The point is it's down to the desktop itself to design it's own HIG and people my follow it as a guide, it doesn't make GTK app any better/prefered to develop for since you can break it anyway.

---

