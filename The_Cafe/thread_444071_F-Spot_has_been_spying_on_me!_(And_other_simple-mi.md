---
title: "F-Spot has been spying on me! (And other simple-minded image management stuff)"
date: 2007-05-15
forum: The Cafe
---

### Post by Mr. Picklesworth on 2007-05-15
I recently won a rather nice, simple entry-level digital camera. (Darn good for entry level, however. Only problem is it uses Memory Stick, but that and my exciting MicroSD -> Memory Stick Pro Duo adaptor is another story).
I was previously using specifically film for everything, so this is quite a treat :)
It doesn't use any weird oddball drivers, either!

This has finally allowed me to try something that I have always been curious about: Photo management in Ubuntu. I have two programs installed, both of which seem to conflict with one another; they both organize their stuff differently, and both claim to be photo managers. Those programs are gThumb and F-Spot.
For *image management* (comic books, pictures collected from the web, computer artwork), I tried gThumb since its interface is less specific to photographs, then I realized that just plain Nautilus worked just as well so that was the end of that...

Anyway, to decide which one to use, I decided on a simple, somewhat classic sort of test: I popped in the camera, and the first program to greet me with "You have inserted a camera! Would you like to import these photos into your collection?" would win and gain the pleasure of watching its competitor be deleted.
The winner there was gThumb. (A *very* nice feature, by the way). However, I soon found gThumb a bit lacking; it is a bit *too* close to the file manager (normally not a bad thing! I like that most of the time), such that my imported files were dumped straight to a directory with the date as its name. Opening specific folders then seemed the only obvious way to browse images by date.

...So, since the winner was imperfect, I decided to give F-Spot a chance anyway. I hadn't opened this program in ages - probably not since I started running the Feisty dev version, so at least 6 months.
I was *shocked* to find that my collection of images in there had increased in size by 1034! *Every single* image that I can remember ever looking at - and some that I don't - seems to have been imported to F-Spot. That's everything from a render of an armchair that I had on a flash drive (which never touched my hard drive), to a sprite used in a game engine example, all the way to both of the little Greasemonkey icons (grey and not grey) used by Firefox (which I never use).

What is the meaning of this?!
Did F-Spot really just index every single image in the universe, or is it grabbing these from Beagle, or what? It's cool and all, and I can see a million uses here, but this just baffles me...

A few more things: What do you use? gThumb or F-Spot, or both? Why? (And for what?)
For regular image management vs. photo management, what do you recommend? Is there maybe a program that's sort of a cross between gThumb and F-Spot, allowing stellar and attractive resources for photo management along with sensible ways to organize plain old images? (Or should I just stop looking for unifying programs and go with both / use Nautilus?)
Can I get F-Spot giving me a helpful "Import photos" thing the moment I plug in my camera like gThumb does? I think I prefer F-Spot now for camera stuff (definitely more photograph oriented!), but gThumb keeps bothering me with its attractive dialogue.


Edit:
Okay, it isn't as crazy as I had first thought. These images seem to all be from removable storage devices, which have carried most of the images I can remember. It's actually weirder, come to think of it, that there aren't thousands from my hard drive as well (since the removable storage is hardly in there for long!) but ah well...

---

### Post by pmj on 2007-05-15
So far I sort by directories and text files that I can find with tracker, since I refuse to be locked into using a certain application. I've been avoiding f-spot as well since supposedly it enforces its own directory structure which is something I don't like. It's my data and no program should touch it in any way whatsoever.

Oh, and for comics, try comix. Keep them in the zip/rar format they came in or zip/rar them up and then rename to cbz/cbr and they'll be thumbnailed too.

---

### Post by ssam on 2007-05-15
some cameras don't look any different to a computer than a usb memory stick. if you insert a usb stick with photos on it ubuntu will guess that its a camera and offer to import them.

another possibility is that it is importing images from you ~/.thumbnails folder (show hidden files in your home folder to see it)

@pmj
there is an option to tell f-spot not to copy you photos into its directory structure.

---

### Post by Dragonbite on 2007-05-15
What about digiKam (yes, I know it's a KDE-based app) or Picasa from Google?

---

### Post by engla on 2007-05-19
Your competition there was unfair :) -- Ubuntu is preconfigured to let gthumb import it for you. If you go to System > Settings > Removable units you can change from gthumb-import-something to f-spot-import and have F-spot do the importing..

---

### Post by Mr. Picklesworth on 2007-05-19
Yes, I discovered that just now. Quite cool :)

I was worried that I wouldn't get the cool "do you want to import" dialogue along with it, but I do, so it's excellent.

---

### Post by Obor on 2007-05-19
> **Dragonbite said:**
> What about digiKam (yes, I know it's a KDE-based app) 

+1
I've tried every photo management program that I could find and digiKam does exactly what I need. Yeah its KDE but I think its way better than any gnome based photo manager and way faster then Picasa. Worth a try (unless you have something against mixing gnome and KDE :)

Just my 2p.

---

### Post by macogw on 2007-05-19
I just use Nautilus.  I tried gThumb, but I can't figure out where the heck the files GO or how to tell it which ones to save and whatever.  It shows what's on the card, sure, but how do I tell it which ones to keep, and once I get that figured out, where are they on my hard drive?

---

### Post by mrgnash on 2007-05-19
I can't get F-Spot to do anything but crash, and Digikam wants to pull in too much KDE stuff, so I use a combination of Gthumb and Picasa.

---

### Post by russell.h on 2007-05-20
I quite like F-spot's interface, but its slow as all hell, and not terribly stable. I blame Mono.

Is there a non-mono f-spot alternative around?

---

### Post by mrgnash on 2007-05-20
> **russell.h said:**
> I quite like F-spot's interface, but its slow as all hell, and not terribly stable. I blame Mono.

Is there a non-mono f-spot alternative around?

See above.

---

