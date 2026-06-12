---
title: "LXDE-QT, will Lubuntu go to this?"
date: 2013-07-06
forum: Ubuntu, Linux and OS Chat
---

### Post by tnmarktx on 2013-07-06
I've been reading about the qt version of lxde.  Will lubuntu consider going to this version?

---

### Post by Elfy on 2013-07-06
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by mips on 2013-07-06
Dunno, I just think QT is more progressive than GTK.

---

### Post by Copper Bezel on 2013-07-06
I've had that impression, at least that that's the perception, but I don't know why, so I'm curious. I get that LXDE needs to move from GTK2 to *something*, and GTK2 -> GTK3 isn't an easy port, so they're equally free to transition either to Qt or to GTK3. But more generally, what's the difference between the toolkits? I know that Qt seems to be more broadly used than GTK3 and in a more cross-platform manner, while GTK3 seems to be Gnome's wholly owned project and subject to their whims in changes from iteration to iteration. Are there differences in the capabilities of the toolkits themselves? I know that GTK3 was a huge step from GTK2, with features like being able to be rendered through a web browser and so on, but I don't know what those features really mean in practice or how they match up to Qt.

Also, is my impression correct that GTK3 defines more of how the application looks and behaves in a pre-packaged way, while Qt is thinner and more flexible? I also got the sense that Qt intends to separate the interface from the functional code of the application, where GTK seems rather the opposite. Are any of those impressions accurate?

---

### Post by vasa1 on 2013-07-06
> **Copper Bezel said:**
> .... Are any of those impressions accurate?
Some more impressions here: [http://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/](http://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/)

---

### Post by Copper Bezel on 2013-07-07
Yeah, I've actually read that before, and it's a very insightful little gem - the snippet about the ultimatum handed down to the Transmission devs is fairly damning. That's the sort of thing that led to my impression that GTK3 was Gnome's pet project (along with seeing theme breakage with every upgrade myself.)

I found [this from WikiVS]("http://www.wikivs.com/wiki/GTK_vs_Qt") useful as well, in a more general sense - it answered some of my questions and corrected some of my misconceptions. Apparently, Qt does actually have more application functionality baked in, as well, and the project has a lot more full-time devs. It also comes with [resolution-independent scaling]("http://askubuntu.com/questions/281092/why-is-canonical-choosing-qt-over-gtk-for-unitys-next-generation") in a way that GTK doesn't and doesn't require X, which is why it works on mobile. Given that Gnome seems to want to own GTK3 in a way it didn't own GTK2, while its own dev base is not comparable to Qt's, I can see why Qt is the more popular choice at the moment. (It also starts to make sense why Ubuntu writes Unity exclusively in Qt while shipping it on top of a Gnome environment; at some point, Unity really *is *going to become a Qt-based DE of its own, isn't it?) 

None of that has to do with the decision LXDE is making at this point. [The plan]("http://blog.lxde.org/?p=1013") is apparently to develop Qt versions of core apps starting on a Qt 5.1 base that was released all of four days ago, and preview apps were just recently released. Qt and GTK2 environments [will both be maintained]("http://en.wikipedia.org/wiki/LXDE#Qt_port"), and the fact that Qt takes slightly more memory to run than GTK2 is not considered a great weakness. However, PCMan, the lead developer and original creator of LXDE, notes in the same post:
[QUOTE=PCMan][FONT=tahoma]Since gtk+ 2 is no longer supported by its developer and is now being deprecated, porting to Qt is not a bad idea at the moment.[/FONT][/QUOTE]
That dual support, then, can only apply for as long as GTK2 is a thing that people still use, and at some point the option vanishes into the ether. I also ran into an [older reference]("http://comments.gmane.org/gmane.comp.desktop.lxde.pcmanfm/239") that I think is enlightening. PCMan in 2011 explained a list of compatibilities with GTK3 that would need to be addressed for LXDE to transition, including rebuilding the file manager and storing separate settings and so on (as was ultimately done for Qt) and notes:
[QUOTE=PCMan][FONT=palatino]Having a desktop environment composed by mixed gtk2/3 programs is a very bad idea since the resource usage is doubled for no additional benefit. This is not acceptable for LXDE. As most non-Gnome GTK+ based applications are not yet ported to gtk3, unless we're going to depend on gnome components, migration to gtk3 now brings harms only.[/FONT][FONT=palatino]
To sum up, we're not going to do gtk3 migration in LXDE now. The reasonable timing for the migration is when XFCE and other non-Gnome programs, especially Chromium, which has many users, start the migration.[/FONT][/QUOTE]
So, separate GTK2 and Qt environments can, according to PCMan, happily coexist under the LXDE brand, and [LXDE-Qt is a mixed entity now]("http://blog.lxde.org/?p=1026"). Yet, supporting separate GTK2 and GTK3 libs in a mixed desktop experience was an expense not worth spending in 2011, and building two separate environments for GTK2 and GTK3 wasn't even under consideration. Objectively, a GTK3 environment or a Qt environment has to load exactly the same redundant GTK2 libs to run Chromium; there's exactly the same redundancy (GTK2 + something) in LXDE Qt now as there is in Gnome.

So there's a mixed version introducing Qt now, apparently because the toolkit now does what PCMan wants it to do and because GTK2 is going away. There's also the existing GTK2 version that may or may not, some day, start transition to GTK3, as soon as Chromium does. 

I wouldn't hold my breath. = ) 

I did find [one reference]("http://wiki.lxde.org/en/LXDE:Questions#Plans_to_migrate_to_GTK3.2B.3F") to Lubuntu wanting to take the GTK3 path instead, but I can't find anything else on it. [This]("https://launchpad.net/~lubuntu-dev/+archive/gtk3") looks not to be promising in that regard (check out the last build.) The Lubuntu project by itself frankly doesn't have the resources to tackle something like that; it needs upstream support. So ultimately, yeah, Lubuntu is going to end up with a Qt desktop. But that could be years away.

---

### Post by vasa1 on 2013-07-07
> **Copper Bezel said:**
> .... There's also the existing GTK2 version that may or may not, some day, start transition to GTK3, as soon as Chromium does. 
....

Nice post!

Why did you mention Chromium? Did you come across anything about Chromium and gtk3? I haven't looked but didn't come across any plans in my casual browsing.

Lubuntu 13.10 will ship with Firefox as the default browser and, if I understand correctly, Chromium will not be part of the iso (which will be kept at standard CD size for the near future).

Along with Chromium, Firefox is also largely gtk2, as is LibreOffice. So I'm not sure about gtk2 going away soon.

---

### Post by Copper Bezel on 2013-07-07
Thanks. And yeah, I'd tend to agree with that on GTK2; given their development strategy combined with their monopoly on the Linux office suite, LibreOffice alone may hold the line for GTK2 for the next decade or so. = ) (But the new mono icons are awesome!) Hell, in a few years, Gnome will be deprecating GTK3 in favor of GTK4 while still shipping with GTK2 support. Outside of projects like elementary, it's getting hard to see a distinction between "GTK2 apps" and "apps made by shops other than Gnome."

I just used Chromium as the example because PCMan did in the second quote. Why he didn't use Firefox instead is anyone's guess. *My* guess is that it's because Firefox is its own weird toolkit that uses some GTK2, like LibreOffice, and neither is going to be arsed any time soon to switch what GTK libs it *does* use to GTK3 for compliance reasons that it already doesn't care about, while Chromium is a pure GTK2 app that might conceivably become a pure GTK3 app at some point in the future.

---

### Post by vasa1 on 2013-07-07
> **Copper Bezel said:**
> ..., while Chromium is a pure GTK2 app that might conceivably become a pure GTK3 app at some point in the future.
Well, I had asked [Satya]("http://funsurf-blog.blogspot.com/"), a guy who's made a lot of themes and is "at home" with gtk,  about Chrome/Chromium. He didn't feel that Chrome/Chromium is pure anything.

And Google keeps (more than) one eye on market share and I'm not sure they'll bother with keeping up with the various gtk3 avatars. Plus, the GNOME guys are pushing their own "integrated" browser, Web (formerly Epiphany) so co-operation may not be a priority for either party.

---

### Post by Copper Bezel on 2013-07-07
Right on. I made a bad assumption, then, given that Chrom[e/ium] simply had better desktop integration than the others (excepting its weird little HTML-rendered scrollbar and skinned toolbar and ability to draw its own title bar and basically draw around the window manager and its need for special consideration under any theme that makes it look native and ... yeah, so it's not very GTK2 to begin with.) What I'm saying is that PCMan singled out Chromium and I don't know crap about toolkits, but I thank you for the insight. = )

Web-neé-Epiphany amuses me, and I always have to keep it installed and never run it. I mean, it is a very different, unique, innovative clone of the iOS browser UI, and I wish it all the best. I like that Firefox and Chrome are each, in their own ways, "integrated" browsers under Unity, each capable of creating web applications that Unity treats as native (Firefox under Canonical's initiative and Chrom[e/ium] under its own,) while Gnome chooses to develop their own browser to support their own standard instead. But that's another topic, I suppose. '~'

---

### Post by vasa1 on 2013-07-07
> **Copper Bezel said:**
> ... its weird little HTML-rendered scrollbar ...
It that the scrollbar we see on many Google pages? GMail, Google News, GDrive? I haven't understood why it's there :( but as you say it's better off in another thread :D

---

### Post by TenPlus1 on 2013-07-07
I personally would love for Lubuntu to switch to LXDE-qt since the core apps all have their respective qt native versions or substitutes available which work perfectly during testing...

---

### Post by vasa1 on 2013-07-07
On-topic link: [No, LXDE-Qt is not bloated]("http://blog.lxde.org/?p=1026")

---

### Post by smellyman on 2013-07-07
razor-qt is already there and mature now.

more qt is great though.

---

### Post by BreezyBrooke on 2013-07-07
From what I infered from the Razor-QT and LXDE talks is that they might merge into a new desktop. Essentially two communities working together on one product, each bringing their own features to the table.

---

### Post by smellyman on 2013-07-07
> **BreezyBrooke said:**
> From what I infered from the Razor-QT and LXDE talks is that they might merge into a new desktop. Essentially two communities working together on one product, each bringing their own features to the table.

Well that would be cool.  two communities merging rather than forking.......nice change

---

