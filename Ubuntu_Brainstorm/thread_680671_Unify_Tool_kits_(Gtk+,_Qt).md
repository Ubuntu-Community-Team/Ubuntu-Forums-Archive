---
title: "Unify Tool kits (Gtk+, Qt)"
date: 2008-01-28
forum: Ubuntu Brainstorm
---

### Post by mangar on 2008-01-28
Nokia just bought Trolltech (the makers of Qt).
It means that Qt may be released under BSD license. 

Since Gnome was started as a reaction to the (than) non free license of the Qt (which is now GPL), and now, as Qt may become BSD licensed, it will be possible to fork the toolkit to LGPL version, and merge it with Gtk+.

Why do so?
Qt is better documented, and got (IMHO) a better API and cross platform support than Gtk. 
On the other hand, Gtk+ got better memory management, and is somewhat (subjectively) faster.

Unification will simply the development stack, allow the application writers (whether they are FOSS or propriety) to concentrate on targeting a tool kit, rather than a desktop environment, and will (hopefully) reduce division of effort between two competing application / desktop stacks.

I do not imply unifing Gnome and Kde, from the same reasons that Xfce and Gnome are not unified, altough they use the same tool kit.

---

### Post by 23meg on 2008-01-28
This is going to be the biggest thread ever.

[QUOTE=mangar]It means that Qt may be released under BSD license.[/QUOTE]

Only if under Nokia's ownership Trolltech abandons Qt development, and that [looks unlikely]("http://trolltech.com/28012008/28012008-faq").

---

### Post by mangar on 2008-01-28
Nokia is a huge sponsor of Gtk related development.
[http://opensource.nokia.com/contributions.html](http://opensource.nokia.com/contributions.html)

Their business is communication devices; The tool kits, Os, and software stack is secondary to their main function, and it seems likely 
that Qt will now slowly rot, as their focus will now be mostly on the mobile aspect of the tool kit, rather than the general purpose one.

It's all assumptions, of course.

---

### Post by foerdi on 2008-01-28
Nokia would get absolute control about gtk+qt-whatever-it-will-be-named-united-future in this scenario.

Unlike Sun (OO.org) this finnish company is not (yet) known for Open-Source

I don't think that's a good idea, never trust capitalism. 

My opinion, in future qt will be specialized in mobile hardware... GTK for desktops

---

### Post by GeneralZod on 2008-01-28
Where's the "as difficult to do as 'merging' a cat with a toaster" option?

---

### Post by LaRoza on 2008-01-28
...or Democratic Party with the Republican Party (in USA)

---

### Post by smartboyathome on 2008-01-28
This would be a huge undertaking, as one toolkit would have to be totally rewritten as under a different language (doesn't GTK+ use C and Qt use C++?). In my opinion, this will never happen, nor should it since it DOES bring competition to the table within GNOME and KDE which otherwise wouldn't be there.

---

### Post by Auria on 2008-01-28
Original poster: if you are able to merge them, please go ahead and impress me :roll:

---

### Post by madmetal on 2008-01-29
> **LaRoza said:**
> ...or Democratic Party with the Republican Party (in USA)

i think they are pretty the same so lets try to do the same with Qt and Gtk+
:KS
also agree its to difficult and not business of the ubuntu community...

---

### Post by Zeroangel on 2008-01-29
Just out of curiosity, would an abstraction library slow down the process since your accessing the QT or GTK APIs through a proxy?

Would the efficiency of this pay off in difference to having two separate graphics toolkits loaded?

---

### Post by Shin_Gouki2501 on 2008-01-29
never ^^

---

### Post by maybeway36 on 2008-01-30
I thnk that GTK2and Qt should be able to use each other's styles. (There is gtk-qt-engine, so half of that is done.)

---

### Post by smartboyathome on 2008-01-30
The problem I see with GTK themes being applied to QT is that, while it is easier to apply QT widget images to the pixmap engine in order to use the theme with GTK, the opposite is harder because there exists gtk engines like clearlooks which doesn't make images, and each widget would have to be made into an image and applied as a QT theme. In my opinion, the gtk-to-qt part is harder to do than the qt-to-gtk part which was already done.

---

### Post by Shin_Gouki2501 on 2008-01-31
well i know u dudes dont like it but i would suggest to u using java ;)
with OSGI and RCP u can simply create amazing things!

---

### Post by Darkhack on 2008-01-31
> **GeneralZod said:**
> Where's the "as difficult to do as 'merging' a cat with a toaster" option?

That would be a catoastrophe!  :tongue:

Unifying GTK+ and Qt would essentially mean dropping one in favor of another since you really can't unify them to begin with.  Deciding which one to drop would most definitely bring about the largest internet flame war in history.

---

### Post by GeneralZod on 2008-02-01
> **Darkhack said:**
> That would be a catoastrophe!  :tongue:


:lolflag:

---

### Post by Shin_Gouki2501 on 2008-02-01
imo package depency hell could be quite good solved using osgi (especially for GUI apps!) but again thats just my opinion. People in Linux forums tend to love C/C++ ^_~

---

### Post by Steveway on 2008-02-01
> **Shin_Gouki2501 said:**
> imo package depency hell could be quite good solved using osgi (especially for GUI apps!) but again thats just my opinion. People in Linux forums tend to love C/C++ ^_~

Yes we like our apps speedy and light on ressources. No thanks to your Java-stuff.

---

### Post by Shin_Gouki2501 on 2008-02-01
speedy and light tried SWT? :D

but i dont want to start ethic wars about that, just my opinion :)

---

### Post by Steveway on 2008-02-01
> **Shin_Gouki2501 said:**
> speedy and light tried SWT? :D

but i dont want to start ethic wars about that, just my opinion :)

The problem is in Java, it is itself bloated and a ressource-hog.
On Linux C, C++ and recently Python are the main languages, for a reason.
Maybe you can advocate your Java-affinaty to the Solaris guy, I know they'll like it ;).
Also, dropping 2 very mature and excellent developed toolkits for a Java-based solution is very unlikely to happen.

---

### Post by Shin_Gouki2501 on 2008-02-02
well maybe its the kinda portability thought.. on gui apps..
sure QT is "known" in win32 but gtk+?!
with java u ain't got that probs also the standard libary is frickn amzing big....
if u dont like "java" u may use groovy or JRuby.
But "Bloated and ressource-hog" that sounds like some old prejudice did u code yourself ?
Can u compare considerable examples between Java and c/c++?!

Well i dont say Java is THE Cure. Games and some other apps still need c++ or even ASM optimizations but Desktop Applications. There u use frameworks complex components and such. U dont ( in general) invent _every_ time the wheel again. Llike i have the feeling all the time in all the "small" linux apps :/

Well its not replacing gtk+ and QT its more: if u write an GUI Aplication for linux u might start consider Java as well! => [http://en.wikipedia.org/wiki/IcedTea](http://en.wikipedia.org/wiki/IcedTea)
I don't know if u should be sad or confused because of ur solaris comment...
For me Java is just more then an ethic OS believe...
look what i read here:
[http://www.haiku-os.org/](http://www.haiku-os.org/)
If Java runs on there before QT and GTK+ libarys are ported. ;)
U got my idea?


In the end i want to speak pro java e.g. GUI application Desgin so that in future some people more consider Java for their Applications ( gui on Linux)  and start trying it before judging it ;)

---

### Post by mangar on 2008-02-02
Forget about Java.
It's not feasible for any multitasking environment - it eats about 10x memory than than any c/c++ toolkit, and although tests shows it's about on par with c/c++ in terms of speed, subjectively it feels sluggish as heck.

---

### Post by Steveway on 2008-02-02
And how do they invent the wheel again, like you said?
Cross-plattform-compatibility is not what we talk about here.
Java is and has always been a ressource-hog, look at Azureus then look at Deluge/Ktorrent for example. I would tell you more examples but there are so few Java-apps that I can't come up with a comparision at the top of my head.
So why should we write out applications in Java? Speed is a far more bigger concern than cross-plattform-compatibility, especially if we want to write something for Linux, why should we care?
EDIT: Yup like mangar said.

---

### Post by Shin_Gouki2501 on 2008-02-02
the "speed" issues comre from other aspects this subtlie "slow" feeling comes actually from  false programming appoaches!
But since u are all experienced C++ AND Java programmers ( so u could tell the diffrence) and have experienced the sucessfull implementation of many and big projects.
I can't tell u otherwise. Because its the way u think- If u try to do it on yourself u would see some interesting aspects.
As i stated before i dont want to turn this into an ethic discusion.

Ur comemnts just tell 1 thing: U don't have tried urself ( maybe 5 years ago?!)
But Java has changed a lot since then (see SWT) so i cut it here again this thread is a bout something else.

---

### Post by mangar on 2008-02-02
I've developed a little with Java 1.5 (for about a year, 10 people startup), and now I'm using c/c++/asm.
(professionally, I'm an embedded software developer). Java is a pig, and an unstable one at that. It simply sucks for anything not  server based, or in short, enterprise software. 
If you want to use a language that uses high abstraction, I recommend Python - it's much more fun and easy to use Python that any other language, ever. The cost is speed - Python is about 80 times slower than native (C/C++) code.

As to which toolkit to keep - I think that Qt better than Gtk+ for application development. Gtk+ strength  - are the HIG (actually, Gnome's), memory consumption, and license. In all other aspects, Qt is far better toolkit. 
(for honest disclosure - I use Gnome, and the only Qt application I've got is Skype).

---

### Post by Shin_Gouki2501 on 2008-02-02
i diasgree with :
"It simply sucks for anything not server based, or in short, enterprise software. "
I develop enterprise applications using SWT/Jface and recently RCP for me stable as it gets.
For embedded and automotive theres  lots who use C/C++ still java GUI APIs have come a long way and got better IMO..
I think to understand the "place" of a language is quite important. If u look at Google Android Platform its THE future:
[http://blogs.zdnet.com/Burnette/?p=515](http://blogs.zdnet.com/Burnette/?p=515)
gives qutie a nice overview check it out! ( its short) And there is  IMO a qutie good description were to use C/C++ and where Java on Mobile.
over and out from me :O

---

### Post by mangar on 2008-02-02
Interesting article.
They're using Java in a similar way Microsoft is using Visual Basic - for writing the UI, with everything else written in C/C++.
As far as I know, this is possible today with Gtk+ and Qt (using Java binding).
The missing point is that Qt and Gtk are more than widget tool-kits - they got a whole universe of supporting libraries..

---

### Post by Shin_Gouki2501 on 2008-02-02
well my point was in first place that u actually CAN ( and should for various reasons) use Java for GUI-Programming on linux ;)

The whole System design of android is highly efficient and consistent. May be some "desktop" Linux distros can and should learn from that. Besides the printing driver...
;)

---

### Post by SunnyRabbiera on 2008-02-02
I dont think a unification of the toolkits is a good idea as that will limit the options, but I would like to see some collaboration between qt developers and gtk developers though...
this way we have a good chance at a unified gui but have nothing being forced on anyone, both projects can go about as usual but have some level of cooperation

---

### Post by MaX on 2008-02-03
mangar sure likes these polls...

Why unify them, they are different and good at what they both set out to do.
It's not Qt's fault that KDE is a bloated piece of crap,
it's not Gtk+'s fault that GNOME doesn't have enough options...

It's just how things are.

---

### Post by rockin_goliath on 2008-02-04
I would just make them LOOK as similar as possible. It is confusing to the end-user to see two different styles of the interface.

---

### Post by smartboyathome on 2008-02-04
rockin_goliath: see post #13 to see why this would be difficult for GTK+, even though KDE has already done it.

---

### Post by hihihi on 2008-08-18
how about loosing both of them and go opengl?
a new machine we need,
gtk is very old
qt is old.

---

### Post by smartboyathome on 2008-08-18
> **hihihi said:**
> how about loosing both of them and go opengl?
a new machine we need,
gtk is very old
qt is old.

How about creating that new toolkit, and porting GNOME and KDE to it. :p

OpenGL is nice, but it isn't a graphical toolkit, its a 3D design toolkit (from what I understand). Even though GTK and Qt are old, they are still undergoing updates and GTK+ 3.0 may come out soon (Qt 4 being released along with KDE4).

---

### Post by bruce89 on 2008-08-18
> **smartboyathome said:**
> (Qt 4 being released along with KDE4).

Qt 4.x was around well before KDE 4.x was.

Technically, this would be impossible. For starters, Qt and GTK+ don't use the same language.

---

### Post by irrdev on 2008-08-19
First of all, I don't see Nokia releasing QT under the BSD license. Nokia has plans to tightly integrate QT into all of its mobile products, while fully maintaining the PC support. I expect that this will greatly increase QT's popularity in the long run by commercial companies, as it allows for multi-platform targeting using only one library and codebase.

Even if the license-change came about, your proposal is nigh-impossible. A better idea might be to write complete wrappers. A QT wrapper for GTK  would be the easiest, I imagine, while a GTK wrapper for QT would be correspondingly more difficult due to the lack of C++ class support. Either way, what's the point may I ask? Choice is good, and both libraries offer vast differences which better suit the needs of different developers.

---

### Post by smartboyathome on 2008-08-19
There are now engines which mask Qt programs as GTK, and vice versa. The only difference is that GTK masking engine works with pretty much all GTK+ programs, while the Qt masking program only works with Qt4. :(

---

### Post by bruce89 on 2008-08-19
> **smartboyathome said:**
> The only difference is that GTK masking engine works with pretty much all GTK+ programs, while the Qt masking program only works with Qt4. :(

Well, they only work with GTK+ 2.0 programs, which are pretty much all of them.

---

### Post by smith1234 on 2008-11-24
Hi pals,

Here is lakshmi and I wanted to take this opportunity to share with you some exciting news that Production Equipment Europe was established in 1983 to supply Tools, Equipment, Safety and Consumable products of the highest standard to the electronics and industrial, manufacturing and services sector. Since then we have gone from strength to strength in building a first class reputation for sales and service support throughout the industry. 

cheers

[URL=http://www.productionequipment.ie]Socket Set,Tool Chest,Tool Box,Tool Cases,Tool Wallet,Shipping Cases,PCB Carrying Cases
Tool Trolley,Snap On,Kennedy,Flambeau,Beach,Remline ,Bernstein[/URL]

---

