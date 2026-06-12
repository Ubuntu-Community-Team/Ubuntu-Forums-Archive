---
title: "Unity Panel Bar Won't Show Transparent"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by leo4kusuma on 2013-04-22
I've tried some methodes to convert unity panel bar become transparent. It's worked on Quantal Quetzal, but it won't be on my Raring Ringtail. As you see these, using Unity Tools and Compiz.
[http://img692.imageshack.us/img692/1666/forumunitypanel2.jpg](http://img692.imageshack.us/img692/1666/forumunitypanel2.jpg)
[http://img14.imageshack.us/img14/384/forumunitypanel1.jpg](http://img14.imageshack.us/img14/384/forumunitypanel1.jpg)

---

### Post by Frogs Hair on 2013-04-22
I know Myunity and Unsettings had the ability to change the panel color opacity to zero , but the Unity Tweak tool doesn't have that feature. I'm not sure if Unsettings is still active and I lost track of Myunity after it was removed from the 12.10 repository.

---

### Post by tdockery97 on 2013-04-22
Might it be hardware related?  Using unity-tweak-tool works for me in setting whatever level of transparency is desired.

---

### Post by leo4kusuma on 2013-04-22
both myunity & unsetting won't be installed on raring ringtail. i did it last 2 days ago.

---

### Post by leo4kusuma on 2013-04-22
> **tdockery97 said:**
> Might it be hardware related?  Using unity-tweak-tool works for me in setting whatever level of transparency is desired.

it works on my Quantal Quetzal. transparent effect can add on window panel bar, but why it won't be used on unity panel?

---

### Post by mc4man on 2013-04-22
It's possible to get a transparent panel but there are some limitations

For quite some time going back to 12.10 the level of trans has been borked, it wasn't & still isn't linear anymore. 
Now, quite unfortunately,  in 13.04  the panel *can be* affected by the opacity setting in Background Color which previously only affected the opacity of the Dash.

So for a completely trans panel you need to set the panel opacity to 0.000 **&** turn Background Color opacity on, ie., any setting over 0. So as in screen the panel is transparent but here then I'm prevented from raising high to get a dark Dash. Other not desired results may be that by using the custom 'Background' color one would get a crappy launcher color 
(not an issue here because I want #000000 as the color of the launcher anyway

So now I may set opacity in Background to 100 or so & get a slightly darkened Dash & slightly trans panel
(if it wasn't for this current turn of events I would use no blur, Background color opacity of around 200 & panel opacity of about 3 to match..

(feels like a bug as the Background color opacity shouldn't affect panel opacity

---

### Post by leo4kusuma on 2013-05-05
FINALLY: It's so simple why unity panel bar won't show transparent. Using Unity Tweak Tools, go to Unity, then go to [Search Tab]. in General option, turn off [Background blur]. Now, go to [Panel Tab], turn on [Transparency], then try to slide [Transparency level].

---

### Post by leo4kusuma on 2013-05-05
hei... where the prefix then i'll give [SOLVED]....???

---

