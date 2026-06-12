---
title: "Do You Like Cairo Dock?"
date: 2010-03-26
forum: The Cafe
---

### Post by Frogs Hair on 2010-03-26
Hi,
 
Last night I installed Cairo Dock and played with it until midnight. I haven't decided weahter it's an eye candy toy or tool.
 
Using Cairo for a few hours it became clear that there are many possibilities. I have open GL but like the on GL menu better.
 
One thing I like about Ubuntu is the drop down menus. It  was nice removing the empty toolbar from the lower screen, as it makes the screen look bigger.
 
If, you like Cairo tell me why ? If you have links to help me use it to its fullest that would be great.

---

### Post by Vunutus on 2010-03-26
Personally I've never been able to get to a point where using any sort of dock feels natural to me. I've tried several times to use both cairo dock and AWN, but uninstalled after several days.

---

### Post by koleoptero on 2010-03-26
Cairo must be the only dock I haven't tried. :/

---

### Post by PuddingKnife on 2010-03-26
No. Its always been hit and miss re: installing and running. 

AWN is far more stable and is not biting Ma'c style too hard.

---

### Post by Paqman on 2010-03-26
It's ok, but AWN is still the best dock for Linux IMO.

---

### Post by Roasted on 2010-03-26
I've used Cairo, AWN, and Docky2.

Cairo, in my opinion, is not that great. It's buggy, cumbersome, and quite frankly - ugly.

AWN and Docky2 are both more elegant docks to use and feel much smoother. I've personally grown partial to Docky2. I use Docky so much on my Ubuntu systems that yesterday I worked on a standard Ubuntu install and was so taken back by how blah the bottom bar was in the Gnome interface. 

I definitely prefer using a dock, but if you're going to use a dock, use a good one. Try AWN or Docky2 out.

---

### Post by NightwishFan on 2010-03-26
I like many programs that use Cairo and cairo dock is flexible. I wish they would give it better defaults though. It always seems to have incorrect icons and button names I have to manually fix. Awn is to my tastes but is much heavier and requires compositing.

---

### Post by gnomeuser on 2010-03-26
Cairo dock always seemed a bit more like the cairo test case it was born as. Personally I have been using Docky for a while and I really enjoy it's integration of Zeitgeist and the Win7 like application actions.

---

### Post by Frogs Hair on 2010-03-26
Thanks for the input,

It seems I will have to check into AWN .

---

### Post by rahilm on 2010-03-26
I use cairo-dock. I find it manageable. i replaced AWN with cairo-dock much time ago and i don't regret it. Also DockbarX is great too.

---

### Post by Lightstar on 2010-03-26
Cairo is good, I used it for awhile, though the reason I used it was because I had AWN issues :P

I like AWN better, especially now that I can put it on the side of the screen.

---

### Post by cgroza on 2010-03-26
Cairo-dock forever... just installed and configured today.

---

### Post by Frogs Hair on 2010-03-26
> **rahilm said:**
> I use cairo-dock. I find it manageable. i replaced AWN with cairo-dock much time ago and i don't regret it. Also DockbarX is great too.

I found some reviews, and one said Cairo is a much lighter program. I could not see much difference from 
the screen shots I found , they both have their share of , just flat out ugly icons .

---

### Post by Ichido on 2010-03-29
> **Paqman said:**
> It's ok, but AWN is still the best dock for Linux IMO.

I'm using Cairo-dock, but I'm looking for a "Better" Dock, so..
Do I install "awn-manager" or "Avant-Window-Manager" or Both?
Thanks

---

### Post by AlanR8 on 2010-03-29
Have been using Cairo for about 9 months now and like an earlier poster, I find a standard installation awkward to use these days! I don't use OpenGL, I prefer the non version.

I find the icons match the theme, I use Mac4Lin so that may have something to do with icon styles. I also find it works smoothly and is not a resource hog.

That said, I've been thinking of playing with Docky and Gnome Shell but that's what's good about Linux. Freedom of choice to experiment!

---

### Post by Cam42 on 2010-03-29
AWN and Docky are the best docks around, IMO.
Cairo is just buggy on my system.

---

### Post by Psumi on 2010-03-29
I like docky the most, but... it needs a menu implementation, or a gnome menu implementation.

---

### Post by AlanR8 on 2010-03-29
> I like docky the most, but... it needs a menu implementation, or a gnome menu implementation.

I also use the Global Menu addition in my top task bar so have access to all menu functions at all times. See attached screen shot from my new Compaq Mini

---

### Post by Psumi on 2010-03-29
> **AlanR8 said:**
> I also use the Global Menu addition in my top task bar so have access to all menu functions at all times. See attached screen shot from my new Compaq Mini

gnome menu/menu are not application menus.

They're menus that LIST the currently installed applications.

apt-cache show gnome-menus
```
Package: gnome-menus
Priority: optional
Section: gnome
Installed-Size: 1868
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: i386
Version: 2.28.0.1-4
Replaces: kdelibs-data (<< 4:3.3.2-1ubuntu1)
Depends: python (>= 2.3), python-gmenu (= 2.28.0.1-4)
Filename: pool/main/g/gnome-menus/gnome-menus_2.28.0.1-4_i386.deb
Size: 213030
MD5sum: 29f002f8d9df51913b3efdb7f6de5763
SHA1: 4468ba0a1a204e3db4abbb81f5485bb0a909a437
SHA256: c21af1770f230ebfc2940eac4ccbf6852bb4a487a3edb816fef26b12481591e7
Description: an implementation of the freedesktop menu specification for GNOME
 The package contains an implementation of the draft
 "Desktop Menu Specification" from freedesktop.org:
 .
 http://www.freedesktop.org/Standards/menu-spec
 .
 Also contained here are the GNOME menu layout configuration files, .directory
 files and assorted menu related utility programs.
Tag: admin::configuring, interface::x11, role::program, scope::utility, suite::gnome, uitoolkit::gtk, x11::application, x11::library
```

apt-cache show menu
```
Package: menu
Priority: optional
Section: admin
Installed-Size: 2004
Maintainer: Bill Allombert <ballombe@debian.org>
Architecture: i386
Version: 2.1.43
Depends: libc6 (>= 2.2), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.4.0), dpkg (>= 1.15.4) | install-info
Suggests: gksu | kdebase-bin | kdebase-runtime | ktsuss | sux
Filename: pool/main/m/menu/menu_2.1.43_i386.deb
Size: 452718
MD5sum: 71a556beaef4207145a0801680fc4b0c
SHA1: 1f8ce60c029604026793191d48aa93addddb8303
SHA256: c566e292f559fdff07832cd63ad026ba7e7dac2e2692efea88b59357b53887a9
Description: generates programs menu for all menu-aware applications
 Debian menu keeps transparently the menus in the different
 window-managers in sync with the list of installed programs.
 .
 Debian menu relies on a list of menu entries provided by programs
 and a list of menu-methods provided by window-managers and other
 menu-aware applications.
 .
 Menu provides system-level and user-level configuration and overrides
 for both menu entries and menu-methods.
Tag: admin::configuring, role::program, scope::utility, suite::debian
Task: desktop
```

---

### Post by ctrlmd on 2010-03-29
Cairo dock
yeah its the best dock i have ever used on linux, windows 
unlike other dock it doesn't use your cpu resources like others plus it features and eye candy in another word i love it :)

---

### Post by Psumi on 2010-03-29
> **ctrlmd said:**
> Cairo dock
yeah its the best dock i have ever used on linux, windows 
unlike other dock it doesn't use your cpu resources like others plus it features and eye candy in another word i love it :)

Who needs a dock/panel with openbox? :|

I love openbox now. :)

---

### Post by Frogs Hair on 2010-03-29
Hi again,

I haven't  removed Cairo Dock yet , it's working very well. I found some ways around the icon issue , so it looks better to me anyway. I have to say the Docky screen shots that I have seen  look nice.

---

### Post by Frogs Hair on 2010-03-29
My latest look.

---

### Post by Ichido on 2010-03-31
It was Way Too Buggy, so I trashed it.

---

### Post by robertneville777 on 2010-03-31
Yeah, same here. Last time I used it, it was just way too buggy. That was back a few versions ago, around ubuntu 8.10 I believe, so maybe it's a lot more stable now.

The only reason I used cairo dock for a little bit was because I was retarded back then and tried to get my desktop to look like OS X Leopard. I needed the real zoom effect on the dock bar, so I had to go with cairo. I think cairo is still the only dock bar that has that type of zoom effect.

Anyway, I would seriously check out AWN (avant window navigator). Really stable and has cool applets to boot :guitar:

---

