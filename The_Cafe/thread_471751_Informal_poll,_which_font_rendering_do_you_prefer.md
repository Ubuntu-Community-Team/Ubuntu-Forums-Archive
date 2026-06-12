---
title: "Informal poll, which font rendering do you prefer?"
date: 2007-06-12
forum: The Cafe
---

### Post by daveisadork on 2007-06-12
[img]http://img.davehayes.org/compare-standard.png[/img]

[img]http://img.davehayes.org/compare.png[/img]

The top one is standard sized and the bottom is blown up a bit to expose some of the more subtle differences. So, just as the title states, which of the above font renderings do you prefer? Which one is your least favorite? What do you like and dislike about each of them? After a little bit of discussion I'll reveal where each of the 3 came from. If you're wondering, the text is from [http://www.apple.com/mac](http://www.apple.com/mac) and the font is Lucida Grande.

:popcorn:

---

### Post by karellen on 2007-06-12
the one in the middle (and as technology, I prefer cleartype for smoothing and anti-aliasing)

---

### Post by Footissimo on 2007-06-12
Yeah, I prefer the middle one too - would go for 'smooth' rather than 'sharp'

---

### Post by Tom Mann on 2007-06-12
I like the left one, the middle one looks too dark and the right one looks too light, almost malformed. (look at the m)

---

### Post by jgrabham on 2007-06-12
The two at the sides look like mistakes, the middle one!

---

### Post by init1 on 2007-06-12
The middle. It's the darkest one.

---

### Post by Spr0k3t on 2007-06-12
I like the thin and clean look.  I'd go with the one on the right.

---

### Post by use a name on 2007-06-12
No 2. :)

---

### Post by Al Fairclough on 2007-06-12
Left.

---

### Post by gabng on 2007-06-12
> **Al Fairclough said:**
> Left. x2

---

### Post by daveisadork on 2007-06-12
Well this is kind of interesting. I hadn't expected so many people to prefer the left rendering, which is Epiphany on Ubuntu Feisty. The middle on is Safari 3 on OS X 10.4 and the right one is IE7 on Windows XP with ClearType.

---

### Post by juxtaposed on 2007-06-12
MIddle, probably.

---

### Post by v8YKxgHe on 2007-06-12
I'd say the left one - the middle IMO is to bold.

---

### Post by bobbocanfly on 2007-06-12
The middle one followed closely by the Left had one.

The right hand side one is just too light and frail

---

### Post by starcraft.man on 2007-06-12
Just subtle differences, all are readable IMO and I take what I can get. That said, I really don't like the one on the right (I turn off clear type wherever I go) and if I had to pick only one its the left one I think I'd pick. Honestly though, long as I can read it its fine I think.

---

### Post by reclusivemonkey on 2007-06-12
Out of the three options on show, definitely the left. However I think my rendering is better than all three ;-)

---

### Post by reacocard on 2007-06-12
Left is best of the shown, but I like mine better. (see attachment) It's firefox in Ubuntu 7.04, with libfreetype upgraded with the subpixel rendering patches.

---

### Post by starcraft.man on 2007-06-12
> **reacocard said:**
> Left is best of the shown, but I like mine better. (see attachment) It's firefox in Ubuntu 7.04, with libfreetype upgraded with the subpixel rendering patches.

Your text does look better... maybe I should give that a try. You did [this fix]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty") right?

---

### Post by daveisadork on 2007-06-12
> **reacocard said:**
> Left is best of the shown, but I like mine better. (see attachment) It's firefox in Ubuntu 7.04, with libfreetype upgraded with the subpixel rendering patches.

I would be interested to see how yours does when using the correct font. Would you mind installing Lucida Grande and making a new screenshot?

---

### Post by reacocard on 2007-06-12
> **starcraft.man said:**
> Your text does look better... maybe I should give that a try. You did [this fix]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty") right?

Not quite. I used those freetype packages, but not the cairo or xft packages from the repo (they make it worse). 

After installing them, do a 
```
sudo dpkg-reconfigure fontconfig-config
```
selecting 'Autohinter',  'Automatic', and 'No' in that oder. Then do 
```
sudo dpkg-reconfigure-fontconfig
```
for the above to take effect. Then open System -> Preferences -> Font and choose 'Subpixel smoothing'. FInally, place the following in /home/<username>/.fonts.conf
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/local.conf file for local customizations -->
<fontconfig>
<!-- If the font is bold, turn off autohinting -->
<match target="font">
 <test name="weight" compare="more"><const>medium</const></test>
 <edit mode="assign" name="autohint"><bool>false</bool></edit>
</match>
</fontconfig>
```
Log out and back in, and the fonts should be like mine. The repo packages appear to have changed since I installed mine, so idk if it'll be exactly the same, but they should be similar.

---

### Post by starcraft.man on 2007-06-12
Ok, thanks for that... I took SS from two different sites (Forum this thread first and then Ubuntu guide). I didn't change any fonts or any settings other than what was in the two guides (ubuntuguide's and reacocard's). I'll put them all here and you can judge.

**Forums (Old/Guide/Reacocard)**
[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumOLD.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumNEW.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumSECOND.png[/IMG]

**UbuntuGuide (Old/Guide/Reacocard)**
[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideOLD.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideNEW.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideSECOND.png[/IMG]

I'm not sure which I like best just yet, I'll stare at them for a while... I just put it up for people to see... >.>

---

### Post by starcraft.man on 2007-06-12
> **starcraft.man said:**
> Ok, thanks for that... I took SS from two different sites (Forum this thread first and then Ubuntu guide). I didn't change any fonts or any settings other than what was in the two guides (ubuntuguide's and reacocard's). I'll put them all here and you can judge.

**Forums (Old/Guide/Reacocard)**
[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumOLD.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumNEW.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumSECOND.png[/IMG]

**UbuntuGuide (Old/Guide/Reacocard)**
[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideOLD.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideNEW.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideSECOND.png[/IMG]

I'm not sure which I like best just yet, I'll stare at them for a while... I just put it up for people to see... >.>

Oh and its not the same font as you were using Dave, its the same one consistently through... maybe I should get this Lucida font you like and try that...

---

### Post by reacocard on 2007-06-12
> **starcraft.man said:**
> Ok, thanks for that... I took SS from two different sites (Forum this thread first and then Ubuntu guide). I didn't change any fonts or any settings other than what was in the two guides (ubuntuguide's and reacocard's). I'll put them all here and you can judge.

**Forums (Old/Guide/Reacocard)**
[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumOLD.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumNEW.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/ForumSECOND.png[/IMG]

**UbuntuGuide (Old/Guide/Reacocard)**
[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideOLD.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideNEW.png[/IMG]

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GuideSECOND.png[/IMG]

I'm not sure which I like best just yet, I'll stare at them for a while... I just put it up for people to see... >.>

Glad it worked. The reason I like mine over the guide default is mine are less blurry. Some people may prefer the soft edges, but I like my fonts crisp.

---

### Post by christhemonkey on 2007-06-12
I preferred the left one if the informal poll is still open!

---

### Post by mech7 on 2007-06-12
middle

---

