---
title: "Styles Introducing QGtkStyle,  Qt with Gtk looks."
date: 2008-05-14
forum: The Cafe
---

### Post by loell on 2008-05-14
from [http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/]("http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/")

code available at: **svn://labs.trolltech.com/svn/styles/gtkstyle **

[SIZE="5"]One less reason to have Gtk vs Qt wars!!![/SIZE] :KS



[IMG]http://chaos.troll.no/~jbache/textedit.png[/IMG]

[IMG]http://chaos.troll.no/~jbache/spreadsheet.png[/IMG]


[IMG]http://chaos.troll.no/~jbache/browser.png[/IMG]

[IMG]http://chaos.troll.no/~jbache/human.png[/IMG]

---

### Post by bufsabre666 on 2008-05-14
personally id prefer gtk with qt looks, gtk is more stable for me, but qt looks nicer

---

### Post by klange on 2008-05-14
> **bufsabre666 said:**
> personally id prefer gtk with qt looks, gtk is more stable for me, but qt looks nicer

That's already out there...

Wonderful! Finally, I can start using my various qt-based apps effectively...

---

### Post by Xanatos Craven on 2008-05-14
> **bufsabre666 said:**
> personally id prefer gtk with qt looks, gtk is more stable for me, but qt looks nicer
When you say "more stable" and "Qt", have you noticed this with KDE apps (and what version of KDE, if so?), or pure Qt apps? And is this on Kubuntu? It's been a while since I used Kubuntu, but I've heard more than once that KDE stuff is buggier than on other distros.

And I like this news. It's about time... maybe someday I won't need QtCurve to make Amarok and VirtualBox not look completely out of place. Who knows.

---

### Post by bufsabre666 on 2008-05-14
> **Xanatos Craven said:**
> When you say "more stable" and "Qt", have you noticed this with KDE apps (and what version of KDE, if so?), or pure Qt apps? And is this on Kubuntu? It's been a while since I used Kubuntu, but I've heard more than once that KDE stuff is buggier than on other distros.

And I like this news. It's about time... maybe someday I won't need QtCurve to make Amarok and VirtualBox not look completely out of place. Who knows.

kde 3.5.7 in openSuSE, i cant stand kubuntu out of all the kde distros ive used it it by far the buggiest, but im talking if i have alot of native Qt apps running kde will randomly crash, i mean it reloads right away and works fine but its just an irritating thing, ive never had that problem with gtk apps

---

### Post by iMerlin on 2008-05-15
Very nice indeed. I'm too lazy to compile this myself though, waiting for the dpkg :)

This means I can stop avoiding the Kapps on my box.

---

### Post by p_quarles on 2008-05-15
This is really cool news. I'm off to roll me a copy. :)

---

### Post by FuturePilot on 2008-05-15
This is really cool. I might have to try this. VirtualBox and HPLIP Toolbox stick out like a sore thumb.

Edit: where's the code?

---

### Post by maniacmusician on 2008-05-15
Wonderful news. I really love the folks over at Trolltech. They seem to be truly and absolutely dedicated to open source development, interoperability, and just making their users happier. I see plenty of Gnome and KDE people breaking out in arguments and constantly insulting each other in their blogs, and it disgusts me. 

It's totally understandable that competition between the two DEs will make each better, but it doesn't have to be hostile competition like some people believe. Interoperability, sharing of code, and friendly communication between the two will increase efficiency, cut down on application clones, and just generally make life better for the users.

---

### Post by loell on 2008-05-15
> **FuturePilot said:**
> 
Edit: where's the code?

its at there subversion yet.

**svn://labs.trolltech.com/svn/styles/gtkstyle **

---

### Post by maniacmusician on 2008-05-15
> **loell said:**
> its at there subversion yet.

**svn://labs.trolltech.com/svn/styles/gtkstyle **
Yes, and I believe it's only usable with Qt4.4, which isn't available on Hardy. So, according to my understanding, it would only work with Qt applications using Qt4.4 or higher, and you would have to have Qt4.4 installed.

Correct me if I'm wrong.

It's good that this was provided as a plugin to Qt4.4, which means that it should work with all KDE4 apps. It will probably only be released as part of Qt when they release 4.5.

---

### Post by loell on 2008-05-15
yes, this can only be compiled by users using

kubuntu 8.04 KDE 4 remix

---

### Post by jensbw on 2008-05-15
As the author of QGtkStyle I'll be more than happy to correct you on that. Qt 4.4 is binary compatible with all previous Qt 4 versions so can use it with all the existing Qt 4 applications. Here is a screenshot showing the current last.fm client and skype running on ubuntu Hardy:

[IMG]http://chaos.troll.no/~jbache/qt4.png[/IMG]

---

### Post by maniacmusician on 2008-05-15
> **jensbw said:**
> As the author of QGtkStyle I'll be more than happy to correct you on that. Qt 4.4 is binary compatible with all previous Qt 4 versions so can use it with all the existing Qt 4 applications. Here is a screenshot showing the current last.fm client and skype running on ubuntu Hardy:

{image was here}

awesome! that's really good news. Thanks for taking the time to correct me on that. I've always wondered, how do you developers happen to find threads about your work in forums like this? I've seen many people just drop out of nowhere and post in a thread relevant to their work. Notified by a colleague or a friend? obsessive searches? how do you do it? ;)

On a separate note, thanks for putting forward your best effort in terms of interoperability. Even as a mainly KDE user and sometimes Gnome user, I really appreciate it, and I hope more people follow suit (even if interoperability is only sought with self-interest in mind, it still ends up benefiting everyone).

---

### Post by loell on 2008-05-15
great to have the developer participating with the discussion :)

---

### Post by klange on 2008-05-15
Probably missing something here, but...

```
qgtkstyle.o: In function `prepare_window_widget()':
qgtkstyle.cpp:(.text+0x4102): undefined reference to `XSetErrorHandler'
qgtkstyle.cpp:(.text+0x4121): undefined reference to `XSetErrorHandler'
collect2: ld returned 1 exit status
make: *** [libgtkstyle.so] Error 1

```

I'd love to get it compiled so I can better make use of the various Qt apps I have.

---

### Post by cb951303 on 2008-05-15
Finally! Thanks for this little but very useful piece of code...

---

### Post by Sanjay on 2008-05-15
Anybody care to explain how i can compile/use this? There's no makefile/config script, and i've tried throwing g++ at the source all to no avail?

Cheers, Sanjay

---

### Post by geoken on 2008-05-15
Same question as Sanjay. I've managed to find a repo, and instal QT 4.4 but I'm way too noobish to figure out how to compile.

I can't wait to get a working version of this on my box. I'll surely switch to digikam, amarok and kmail. I may even try swapping nautilus/thunar with Dolphin.

---

### Post by GeneralZod on 2008-05-15
> **Sanjay said:**
> Anybody care to explain how i can compile/use this? There's no makefile/config script, and i've tried throwing g++ at the source all to no avail?

Cheers, Sanjay

You'll need libqt4-dev and (I presume) gtk dev headers, too. 

Simply run

```

qmake qgtkstyle.pro

```

(ensuring that qmake is the *qt4* version of qmake) and then make and make install, as usual.

I'm hoping to get KDE4Daily 4.1 up and running this weekend - I'll ask Jens if he wants this included for testing or not.

---

### Post by ice60 on 2008-05-15
is there a spot the difference screenshot with a load of gtk apps and one qt? probably not lol

i'm sure i could tell the difference, i hope i'm wrong though :) either way, it's still pretty cool, i've always not liked the way qt looks and it's put me off ever using kde.

---

### Post by SunnyRabbiera on 2008-05-15
looks neat, once a eebian installer is avilible I will probably put it on my system and hold off for KDE4.1 with anticipation :D

---

### Post by jensbw on 2008-05-15
> **maniacmusician said:**
> awesome! that's really good news. how do you developers happen to find threads about your work in forums like this? I've seen many people just drop out of nowhere and post in a thread relevant to their work. Notified by a colleague or a friend? obsessive searches? how do you do it? ;)


Obsessive perhaps? I was simply looking for some initial reactions and this thread was on the first page I got up on google.

---

### Post by jensbw on 2008-05-15
> I'm hoping to get KDE4Daily 4.1 up and running this weekend - I'll ask Jens if he wants this included for testing or not.

I personally think it is a little bit too early for any large-scale testing or deployment. There are also some KDE-specific issues with clipped icons and palettes making things look a little strange at the moment.

---

### Post by GeneralZod on 2008-05-15
> **jensbw said:**
> I personally think it is a little bit too early for any large-scale testing or deployment. There are also some KDE-specific issues with clipped icons and palettes making things look a little strange at the moment.

Ok, no problem - it can always be rolled in an update if you change your mind :)

Anyway, I forgot to say "thanks" for this great piece of work :)

---

### Post by maniacmusician on 2008-05-15
> **ice60 said:**
> is there a spot the difference screenshot with a load of gtk apps and one qt? probably not lol

i'm sure i could tell the difference, i hope i'm wrong though :) either way, it's still pretty cool, i've always not liked the way qt looks and it's put me off ever using kde.
I'm not sure what you expect; it was literally released 2 days ago. I think it's excellent even now, but it's sure to improve.

---

### Post by wedderburn on 2008-05-15
just compiled this and...
colour me impressed, cleanlooks was always half assed but his is damn nice, infact i've gone through and installed some of the kde4 apps just to for kicks.

slightly off topic, alot of the icons in apps like dolphin seem to be hard coded things like navigations buttons and such.

---

### Post by maniacmusician on 2008-05-16
> **wedderburn said:**
> just compiled this and...
colour me impressed, cleanlooks was always half assed but his is damn nice, infact i've gone through and installed some of the kde4 apps just to for kicks.

slightly off topic, alot of the icons in apps like dolphin seem to be hard coded things like navigations buttons and such.
I doubt that's really the case. Depending on where you're installing them from, you're probably getting very early versions that don't reflect the current svn of those apps. The navigation buttons are almost certainly part of the icon theme.

Using the most recent openSUSE based KDE Four Live CD (which was a 4.1 alpha snapshot of the subversion), when I change the icon theme, the navigation buttons in Dolphin do change.

edit: duh, you probably mean with QGtkStyle. Sorry.

---

### Post by c.ovidiu on 2008-05-16
If anyone managed to install this on Ubuntu Hardy, please write a little how-to. Is QT4.4 required or not? Mine seems to be 4.3 (the libqt4-core version is 4.3.4-0ubuntu3).

This is what I did:

1. Got the code via svn
2. Installed build-essential
3. Installed libgtk2.0-dev and libqt4-dev
4. Ran qmake. No complaints there.
5. Ran make. Got compiling errors:

qgtkstyle.cpp: In member function ‘virtual void QGtkStyle::drawPrimitive(QStyle::PrimitiveElement, const QStyleOption*, QPainter*, const QWidget*) const’:
qgtkstyle.cpp:1105: error: ‘PE_PanelItemViewItem’ was not declared in this scope
qgtkstyle.cpp:1106: error: expected primary-expression before ‘const’
qgtkstyle.cpp:1106: error: expected `)' before ‘const’
qgtkstyle.cpp:1107: error: ‘vopt’ was not declared in this scope
make: *** [qgtkstyle.o] Error 1

Am I doing it wrong?

---

### Post by maniacmusician on 2008-05-16
Make sure you're running the Qt4 version of qmake. You can check with 

qmake -v

---

### Post by DeadSuperHero on 2008-05-16
Does this theme actually emulate whatever your real GTK theme, or is this just a clearlooks clone?

And, if it DOES emulate, what happens when you make the GTK theme emulate whatever your Qt theme is, and your Qt theme emulates your GTK theme?

---

### Post by GeneralZod on 2008-05-16
> **Mr. Psychopath said:**
> Does this theme actually emulate whatever your real GTK theme, or is this just a clearlooks clone?

And, if it DOES emulate, what happens when you make the GTK theme emulate whatever your Qt theme is, and your Qt theme emulates your GTK theme?

To the best of my (very limited) knowledge:

It actually uses GTK itself to render the widgets (hence the need for libgtk-dev).  If you look in prepare_window_widget(), there is a check for whether or not you are using the GTK_Qt engine, avoiding the circularity you describe.

---

### Post by jensbw on 2008-05-16
I made it compile on 4.3 with slightly reduced functionality, which basically means it should work on Hardy right out of the box now.

Note that people might have to add a fonts.conf file to their home directory to get the correct sub-pixel font settings.

I thought people might be interested in seeing how it looks with some KDE 4 applications:

[IMG]http://chaos.troll.no/~jbache/gtk-kde.png[/IMG]

---

### Post by Xanatos Craven on 2008-05-16
That is beyond awesome. If the KDE/Qt icons and file dialogs can be replaced with Gtk ones, this will be almost perfect.

Is it technically possible for Qt3 to have a GTK plugin, or is there something that makes this possible only in Qt4? I'm not volunteering myself or anything, just curious...

---

### Post by smartboyathome on 2008-05-16
It mostly works! :D Only one little bug, see the screenshot attached.

---

### Post by jensbw on 2008-05-17
> **smartboyathome said:**
> It mostly works! :D Only one little bug, see the screenshot attached.

Please file your bugreports here:
[http://code.google.com/p/qgtkstyle/issues/list](http://code.google.com/p/qgtkstyle/issues/list)

---

### Post by boomtisk on 2008-05-17
Does this also work for Kopete? I used to have Kopete installed in Gutsy before I moved to Hardy (haven't felt the need to reinstall it yet) and I installed some kind of QT configuration program and Kopete flat out refused to use the settings I'd applied while the official Last FM thingy did. I thought every KDE program used QT?

---

### Post by dixon on 2008-05-17
Ok, so I've compiled and installed the qgtkstyle, but I can't see any difference. Do I have to enable it somehow?
THX

---

### Post by Colonel Kilkenny on 2008-05-17
> **dixon said:**
> Ok, so I've compiled and installed the qgtkstyle, but I can't see any difference. Do I have to enable it somehow?
THX

Use qt4-qtconfig and choose theme GTK.

---

### Post by ice60 on 2008-05-19
> **maniacmusician said:**
> I'm not sure what you expect; it was literally released 2 days ago. I think it's excellent even now, but it's sure to improve.
i'm not putting it down at all, it was more thinking out aloud. it's one of the best projects i can think of because i really don't like the look of qt, but i really want to try kde and use qt apps on my gtk desktops more. i've never used kde apart from livecds and i'd love it try it.

i hope in the end it's not possible to tell qt apps from native gtk :)

---

### Post by doorknob60 on 2008-05-19
Hmm, if I still used Gnome I'd be downloading it right now, as I can't live wihout Amarok and a few other KDE apps. And I agree Kubuntu is buggier than other KDE distros, but it's still really stable.

---

### Post by Doctor Nick on 2008-05-20
This is a custom fonts configuration that should make KDE apps play nice with your font settings. This is the default for most systems, so it shouldn't mess up your gtk apps. 

Save this in your home directory as ".fonts.conf"
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<match target="font">
		<edit name="rgba" mode="assign">
			<const>rgb</const>
		</edit>
		<edit name="hinting" mode="assign">
			<boolean>true</boolean>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>hintmedium</const> <!--or what ever you prefer-->
		</edit>
		  
	</match> 
</fontconfig>


```

---

### Post by Kingsley on 2008-05-20
Now I need some lightweight KDE apps to test this on. :D

---

### Post by paulms on 2008-05-20
I could compile it too! looks great but I have to install some qt 4 applications to test it more.

How I install (if it helps someone)
in Ubuntu Hardy
1. Install  libqt4-dev
2. Install libgtk2.0-dev
3. Install svn
4. svn co svn://labs.trolltech.com/svn/styles/gtkstyle
5. sudo qmake && make

then select gtk theme in qt4-qtconfig (you must install it too)

---

### Post by OZFive on 2008-05-21
I am not really getting what I need to do to install this at all.  I cannot find a package called QT 4.4 nor gtk2-x11-dev

---

### Post by jensbw on 2008-05-22
> **OZFive said:**
> I am not really getting what I need to do to install this at all.  I cannot find a package called QT 4.4 nor gtk2-x11-dev

The packages you are looking for are libqt4-dev, libgtk2.0-dev. Qt 4.4 is not yet available for ubuntu, but It should work with 4.3 as well.

---

### Post by samwyse on 2008-05-22
Hardy backports has QT 4.4.

---

### Post by geoken on 2008-05-22
There's also a QT4.4 hardy repo somewhere. When I get home I'll check my sources and post the apt link to the repo if no one else does before then.

---

### Post by geoken on 2008-05-22
btw, Ars just did a post on this;

[http://arstechnica.com/journals/linux.ars/2008/05/22/qgtkstyle-makes-kde-apps-fit-in-with-gnome]("http://arstechnica.com/journals/linux.ars/2008/05/22/qgtkstyle-makes-kde-apps-fit-in-with-gnome")

---

### Post by tgelter on 2008-05-22
users of hardy:
In addition to installing the packages listed previously on this thread, I had to install qt4-dev-tools. Hopefully this helps someone.

---

### Post by geoken on 2008-05-22
Is there somewhere in specific that the files need to be put? I succesfully compiled everything but the theme doesn't show up in qt4-qtconfig

---

### Post by Xanatos Craven on 2008-05-22
The last step is "sudo make install", in the same directory you compiled in.

---

### Post by geoken on 2008-05-22
Thanks Xanatos.

---

### Post by dixon on 2008-05-23
> **Xanatos Craven said:**
> The last step is "sudo make install", in the same directory you compiled in.
I'd rather use sudo checkinstall as it creates the deb packages and it's much easier to uninstall/install again....

---

### Post by paranoid_humanoid on 2008-05-23
this is awesome, but it doesn't work with qt3 apps, right?
last.fm and musicbrainz picard changed while amarok is still the same..

---

### Post by mrgnash on 2008-05-23
Wow! That actually makes KDE apps look decent!

---

### Post by OZFive on 2008-05-23
OKAY.... I think I have it done, but now how do I apply the changes to make them show?

---

### Post by geoken on 2008-05-23
To get the changes to show up in many KDE 4 apps, you'll need to install systemsettings-kde4 (it's in synaptic). Once installed it won't show up in any menu's (unless I glossed over too quickly and simply missed it). There is however a .desktop entry in usr/share/apps/kde4 that you can use to launch it. From there you can change the default theme from Oxygen to GTK (you can also do other things like make the scroll wheel match gnome's and switch the single click double click settings).

---

### Post by OZFive on 2008-05-23
I did what you said and went to the folder you described and I do not see a folder KDE4...

---

### Post by geoken on 2008-05-23
> **OZFive said:**
> I did what you said and went to the folder you described and I do not see a folder KDE4...

Yeah, sorry about that. 

It's actually usr/share/applications you'll see a folder called KDE4 in there.

(gratuitous shot of gtk styled Dolphin)

---

### Post by geoken on 2008-05-23
I'm I the only one getting a wierd issue where this is causing GTK apps to be launched with a weird color scheme?

For example, if I use dolphin and attempt to open a jpeg it will launch F-Spot but the color will be off. If I shut down F-spot and re-launch it the color will look normal again. Also, If I launch F-spot, then use Dolphin to launch a second instance of it (by opening a jpeg) the color is fine. (note: I'm only using F-spot as an example, this happens with all gtk apps)

---

### Post by Mateo on 2008-05-24
For those who have done it.  How about some screenshots of *common* KDE apps, meaning not generic text editors and file browsers ;).  Give me Konqueror or Amarok or something notable.

---

### Post by Mateo on 2008-05-24
Doesn't seem to work in Kdevelop...

---

### Post by Falcorian on 2008-05-30
> **Mateo said:**
> For those who have done it.  How about some screenshots of *common* KDE apps, meaning not generic text editors and file browsers ;).  Give me Konqueror or Amarok or something notable.
I just ran into the ars article, and I too would like to see some apps that I'd actually use, like Amarok. ;) 

Regardless, I'm going to compile and give it a shot when I get home! (And if I succeed I'll throw up Amarok shots at least.)

---

### Post by geoken on 2008-05-30
> **Falcorian said:**
> I just ran into the ars article, and I too would like to see some apps that I'd actually use, like Amarok. ;) 

Regardless, I'm going to compile and give it a shot when I get home! (And if I succeed I'll throw up Amarok shots at least.)


Amarok nightly didn't work for me when I tried it earlier, it's just looked like default KDE 4. I think amarok may be using a lot of custom widgets, or widgets that are directly drawn by the app as SVG's.

I noticed the KDE4 version of contact is up and running. If I get my hands on that I'll install and post a screenshot.

After using this for a while I have to say I'm pretty happy. I'm almost at the point where I'm using Dolphin as my default file manager. The only thing I wish I could change is the focus box that gets drawn around selected items.

---

### Post by geoken on 2008-05-30
Here is a pic of KWord and Krita (nautlius is in the bottom corner to show how these apps compare to my GTK theme)

---

### Post by Devport on 2008-05-30
Does anyone have an idea why the qt4 game PokerTH does still use Plastik instead of qgtkstyle and how it may be forced to use it instead ?

Works wonderful with other apps, e.g dragonplayer or marble.

---

### Post by geoken on 2008-05-30
Did you install KDE 4 system settings and QT4 Settings?

---

### Post by Devport on 2008-05-31
> **geoken said:**
> Did you install KDE 4 system settings and QT4 Settings?
Its a qt4 app - theres only qt4 installed and PokerTH - no kde packages at all. The configuration shouldnt have anything to do with KDE. But PokerTH does not use the configured style qgtkstyle but instead uses the qt4 default one.

---

### Post by frenchn00b on 2008-05-31
> **Xanatos Craven said:**
> but I've heard more than once that KDE stuff is buggier than on other distros. It is the Distro itself ;) It is based on Debian testing and unstable.

---

### Post by flitzjoy on 2008-05-31
I've installed all dependencies, copy the svn revision 632 but got no sucess to compile it.

No errors at qmake but when I run make...

```
qgtkstyle.cpp:3002: erro: \u2018SE_TabBarTabLeftButton\u2019 was not declared in this scope
qgtkstyle.cpp:3003: erro: \u2018SE_TabBarTabRightButton\u2019 was not declared in this scope
qgtkstyle.cpp:3004: erro: \u2018SE_TabBarTabText\u2019 was not declared in this scope
make: ** [qgtkstyle.o] Erro 1
```

Maybe I'm trying with a buggy revision I don't know.

Someone could host a PPA in launchpad.net with a QGtkStyle package. Would be a nice for everyone.

I would love to finally run Opera in nice GTK+.

---

### Post by jensbw on 2008-06-02
> **flitzjoy said:**
> I've installed all dependencies, copy the svn revision 632 but got no sucess to compile it.

No errors at qmake but when I run make...

Maybe I'm trying with a buggy revision I don't know.

Someone could host a PPA in launchpad.net with a QGtkStyle package. Would be a nice for everyone.


It was a plain regression this weekend. A Qt 4.5 dependency entered the repository but it should be working fine now. This is of course why the should still be considered unstable. If someone wants to package and maintain a semi-official (and somewhat tested) Ubuntu package for it I would not mind any more. There are already packages for Arch and Fedora.

> **flitzjoy said:**
> 
I would love to finally run Opera in nice GTK+.


Might still take some time since Opera uses static builds for Qt4. It should be resolved once QGtkStyle makes it way back into Qt though.

---

### Post by jensbw on 2008-06-02
> **Devport said:**
> Does anyone have an idea why the qt4 game PokerTH does still use Plastik instead of qgtkstyle and how it may be forced to use it instead ?

Works wonderful with other apps, e.g dragonplayer or marble.

This is most likely because pokerth sets the style manually on the application as any application is free to do. They use some heavy customizations for the green tabs for instance so they probably did want to support all the custom styles with it. You can file it as a suggestion for them to support QGtkStyle though but it is certainly not related to QGtkStyle iteself.

---

### Post by Devport on 2008-06-02
> **jensbw said:**
> This is most likely because pokerth sets the style manually on the application as any application is free to do. They use some heavy customizations for the green tabs for instance so they probably did want to support all the custom styles with it. You can file it as a suggestion for them to support QGtkStyle though but it is certainly not related to QGtkStyle iteself.

Thanks for all your answers !

---

### Post by klerfayt on 2008-06-07
also getting error, installed every package mentioned (can't find ***gtk2-x11-dev*** though) in previous posts to no avail:
```
~/gtkstyle$ qmake && make
g++ -c -pipe -fpermissive -g -fvisibility=hidden -fvisibility-inlines-hidden -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DQT_PLUGIN -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o qgtkstyle.o qgtkstyle.cpp
qgtkstyle.cpp: In member function ‘virtual QPixmap QGtkStyle::standardPixmap(QStyle::StandardPixmap, const QStyleOption*, const QWidget*) const’:
qgtkstyle.cpp:3060: error: ‘SP_BrowserReload’ was not declared in this scope
qgtkstyle.cpp:3063: error: ‘SP_BrowserStop’ was not declared in this scope
make: *** [qgtkstyle.o] Error 1

```

---

### Post by dyerseve5867 on 2008-06-07
I'm having the exact same problem as klerfayt:

```

~/Desktop/qgtkstyle/gtkstyle$ qmake qgtkstyle.pro

~/Desktop/qgtkstyle/gtkstyle$ make
g++ -c -pipe -fpermissive -g -fvisibility=hidden -fvisibility-inlines-hidden -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DQT_PLUGIN -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o qgtkstyle.o qgtkstyle.cpp
qgtkstyle.cpp: In member function ‘virtual QPixmap QGtkStyle::standardPixmap(QStyle::StandardPixmap, const QStyleOption*, const QWidget*) const’:
qgtkstyle.cpp:3060: error: ‘SP_BrowserReload’ was not declared in this scope
qgtkstyle.cpp:3063: error: ‘SP_BrowserStop’ was not declared in this scope
make: *** [qgtkstyle.o] Error 1

~/Desktop/qgtkstyle/gtkstyle$ qmake -v
QMake version 2.01a
Using Qt version 4.3.4 in /usr/lib

```

---

### Post by jensbw on 2008-06-09
> **dyerseve5867 said:**
> I'm having the exact same problem as klerfayt:

```

~/Desktop/qgtkstyle/gtkstyle$ qmake qgtkstyle.pro

~/Desktop/qgtkstyle/gtkstyle$ make
g++ -c -pipe -fpermissive -g -fvisibility=hidden -fvisibility-inlines-hidden -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DQT_PLUGIN -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o qgtkstyle.o qgtkstyle.cpp
qgtkstyle.cpp: In member function ‘virtual QPixmap QGtkStyle::standardPixmap(QStyle::StandardPixmap, const QStyleOption*, const QWidget*) const’:
qgtkstyle.cpp:3060: error: ‘SP_BrowserReload’ was not declared in this scope
qgtkstyle.cpp:3063: error: ‘SP_BrowserStop’ was not declared in this scope
make: *** [qgtkstyle.o] Error 1

~/Desktop/qgtkstyle/gtkstyle$ qmake -v
QMake version 2.01a
Using Qt version 4.3.4 in /usr/lib

```

It is basically a build breakage due to a 4.4 dependency. Do expect these from time to time as  I rarely test using Qt 4.3. It should be working again within the hour though.

---

### Post by klerfayt on 2008-06-09
it compiled now I did sudo make install and I'm able to select "GTK" in Qt 4 settings, but I don't see the applied style neither in kde3 nor in kde4 applications

---

### Post by geoken on 2008-06-09
> **klerfayt said:**
> it compiled now I did sudo make install and I'm able to select "GTK" in Qt 4 settings, but I don't see the applied style neither in kde3 nor in kde4 applications

QT settings is only for QT apps. You need to also install the KDE settings manager (KDE 4 version) and chnage the theme settings from inside their.

I'm pretty KDE 3 apps wont work.

---

### Post by klerfayt on 2008-06-09
> **geoken said:**
> ... You need to also install the KDE settings manager (KDE 4 version) and chnage the theme settings from inside their ... I'm pretty KDE 3 apps wont work.I reread this topic from page one. Indeed - the only way I could get kde4 applications to use GTK style was to run "/usr/lib/kde4/bin/systemsettings" and select it there. However this doesn't explain several recommendations to install qt4-qtconfig and select GTK from there:confused: Too bad it won't apply to kde3 apps:cry:

---

### Post by MonkeeSage on 2008-06-22
@jensbw:

Nicely done. :)

---

### Post by mexlinux on 2008-07-01
Last.fm is using new gtk theme.
But skype is not, why not?
how to make it work?
(its the medibuntu version, is NOT the static version)

---

### Post by bruce89 on 2008-07-01
> **mexlinux said:**
> Last.fm is using new gtk theme.
But skype is not, why not?
how to make it work?
(its the medibuntu version, is NOT the static version)

I expect Skype is using Qt 3, not 4.

---

### Post by mexlinux on 2008-07-02
> 
I expect Skype is using Qt 3, not 4.

Nope, Qt4 is in the pacage dependencies, and is also in the skype minimum requierments

---

### Post by FuturePilot on 2008-07-02
Skype is using QT4 and I noticed the same behavior. For some odd reason it starts with Cleanlooks. However if you open QT4config and reselect GTK from the list and do File&#8594;Save while Skype is running, it will switch. But then you have to do that every time you start Skype. :|

---

### Post by mexlinux on 2008-07-02
I confir this wired behavior in skype

---

### Post by jensbw on 2008-07-05
> **mexlinux said:**
> I confir this wired behavior in skype

There is actually a simple solution for it. Just start with the argument "--disable-cleanlooks" and it will then use your preferred Qt platform theme such as QGtkStyle.

---

### Post by mexlinux on 2008-07-05
> **jensbw said:**
> There is actually a simple solution for it. Just start with the argument "--disable-cleanlooks" and it will then use your preferred Qt platform theme such as QGtkStyle.

It works, thanks!

---

### Post by Vadi on 2008-07-09
Apps can choose their own theme style too. That's what skype was doing.

---

### Post by yorik on 2008-07-11
Awesome program!!! Thanks a lot, jensbw

---

### Post by klange on 2008-07-11
People still use Skype after that whole debacle? ;)

Wish I had more QT4 apps to work with, but as I lean towards GTK in the first place I don't. Is there a version/update/whatever for QCad that uses GTK? That would interest me.

---

### Post by c0rrupt on 2008-07-12
> And, if it DOES emulate, what happens when you make the GTK theme emulate whatever your Qt theme is, and your Qt theme emulates your GTK theme?

I assume it would be like dividing by zero.

[[IMG]http://img501.imageshack.us/img501/5686/dividebyzerolo7.th.gif[/IMG]](http://img501.imageshack.us/my.php?image=dividebyzerolo7.gif)

---

### Post by loell on 2008-07-12
heheh..

---

### Post by Canis familiaris on 2008-07-12
Does Sun VIrtualBox use Qt4? 
I have set Qt4 settings to use GTK theme but Virtualbox still has the Qt look and feel.

---

### Post by pt123 on 2008-07-12
Anyone know if this will be available in Ibex?

---

### Post by Vadi on 2008-07-12
Virtualbox is QT3 and doesn't apply to the theme.

---

### Post by BuilderQ on 2008-07-15
Is it just my GTK settings or does using QGtkStyle disable the display of the colors in the palette section of Kolourpaint's Color Box?

---

### Post by jensbw on 2008-07-18
> **BuilderQ said:**
> Is it just my GTK settings or does using QGtkStyle disable the display of the colors in the palette section of Kolourpaint's Color Box?

Looks like issue 42:
[http://code.google.com/p/qgtkstyle/issues/detail?id=42](http://code.google.com/p/qgtkstyle/issues/detail?id=42)

A fix should be on the svn within the hour.

---

### Post by kef_kf on 2008-07-30
Some screenshots of akregator kde4 on ubuntu 8.04.
first 3 are shots of default install with gorgeous oxygen goodness, the latter 3 are with QGtkStyle with my ubuntu theme.

[[IMG]http://img148.imageshack.us/img148/5530/screenshotjv2.th.png[/IMG]](http://img148.imageshack.us/my.php?image=screenshotjv2.png)[[IMG]http://img67.imageshack.us/img67/200/screenshot1ih9.th.png[/IMG]](http://img67.imageshack.us/my.php?image=screenshot1ih9.png)[[IMG]http://img67.imageshack.us/img67/4132/screenshot2ah0.th.png[/IMG]](http://img67.imageshack.us/my.php?image=screenshot2ah0.png)[[IMG]http://img522.imageshack.us/img522/3228/screenshot3bq5.th.png[/IMG]](http://img522.imageshack.us/my.php?image=screenshot3bq5.png)[[IMG]http://img67.imageshack.us/img67/4464/screenshot4xv8.th.png[/IMG]](http://img67.imageshack.us/my.php?image=screenshot4xv8.png)[[IMG]http://img522.imageshack.us/img522/7136/screenshot5yi6.th.png[/IMG]](http://img522.imageshack.us/my.php?image=screenshot5yi6.png)

---

### Post by mexlinux on 2008-08-01
If some one cares, attached is a deb package I made with checkinstall..

---

### Post by Vadi on 2008-08-01
Checkinstall most likely won't work on another person's computer too well... and that's a 32bit one only anyway. [This link]("http://ubuntuforums.org/showthread.php?p=5222533") has both 32bit and 64bit packages.

---

### Post by pt123 on 2008-08-01
Thanls for the link.

I installed it an ran the config utility set the option to GTK, saved it. 

Opened KTorrent, K3B and QSopcast and they still look the same. i.e. the ugly plastiq look.

---

### Post by geoken on 2008-08-01
> **pt123 said:**
> Thanls for the link.

I installed it an ran the config utility set the option to GTK, saved it. 

Opened KTorrent, K3B and QSopcast and they still look the same. i.e. the ugly plastiq look.

If you're seeing plastik and not oxygen then it's pretty safe to assume the apps in question are Qt3 apps. This only works for Qt4 apps. For the most part you'll need to get the Kubuntu KDE 4 PPA repo to install unfinished KDE 4 ports (if they even exist).

---

### Post by pt123 on 2008-08-01
^ Thanks for the info.

---

### Post by Foster Grant on 2008-08-01
Sorry, but ... no. I won't be Qt-dependent under any circumstances.

Nokia owns Trolltech, which owns Qt. Given [[color=#FF0000]the disingenuous and deceitful FUD campaign Nokia mounted against Ogg Theora[/color]](http://www.boingboing.net/2007/12/09/nokia-to-w3c-ogg-is.html) (because [Ogg Theora](http://en.wikipedia.org/wiki/Theora) is incompatible with DRM schemes), at this point Qt is not something I want on my computer.

In fact, here's a better idea: KDE can switch to GTK+ 3. Solves my problem, anyway. :)

---

### Post by Vadi on 2008-08-02
No offtopic, please.

---

### Post by dancavs on 2008-08-21
this is awesome; ive just started first steps in qt4 coding, i was put off when my windows werent "embracing" gnome desktop look/feel. 

cheers jensbw :)

---

### Post by flocki on 2008-12-03
I have just found this, and it is great!

For those of you who have been irritated by skype not using the GTK style (as opposed to the screenshot posted by jensbw), skype enforces the cleanlooks style. To disable this behaviour, start skye with:

```
skype --disable-cleanlooks
```

[http://forum.skype.com/index.php?showtopic=108936](http://forum.skype.com/index.php?showtopic=108936)

---

### Post by jjpcexpert on 2009-02-28
I have an issue doing this in Kde

---

