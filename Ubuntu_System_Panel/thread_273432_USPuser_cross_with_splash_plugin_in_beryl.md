---
title: "USPuser cross with splash plugin in beryl"
date: 2006-10-08
forum: Ubuntu System Panel
---

### Post by delfick on 2006-10-08
would it be possible to make the logo part of the USPuser plugin act like the splash caused from the splash plugin in beryl?

so that my logo thingo would look like this when i open up the usp [http://delfick755.googlepages.com/that_is_cool.mpeg](http://delfick755.googlepages.com/that_is_cool.mpeg)

also can it be made as an option for the USPuser plugin to only display the logo, and not the text that goes with it?

that would be awsome!

thnx

---

### Post by Malac on 2006-10-09
> **delfick said:**
> would it be possible to make the logo part of the USPuser plugin act like the splash caused from the splash plugin in beryl?

so that my logo thingo would look like this when i open up the usp [http://delfick755.googlepages.com/that_is_cool.mpeg](http://delfick755.googlepages.com/that_is_cool.mpeg)

also can it be made as an option for the USPuser plugin to only display the logo, and not the text that goes with it?

that would be awsome!

thnx
Hi delfick,
I could add the option for hiding the user name as well as the logged on info.
I'll put it on my (ever increasing) list. :)

I don't have beryl on my system yet and the mpeg wouldn't play on my system for some reason so I'm not sure what you want as far as the logo goes.

---

### Post by delfick on 2006-10-09
> **Malac said:**
> Hi delfick,
I could add the option for hiding the user name as well as the logged on info.
I'll put it on my (ever increasing) list. :)

cool, thnx :D

> I don't have beryl on my system yet and the mpeg wouldn't play on my system for some reason so I'm not sure what you want as far as the logo goes.

try this one [http://delfick755.googlepages.com/logo.mpeg](http://delfick755.googlepages.com/logo.mpeg)
it doesn't look as good as the other one but you get the idea from it.....
(note that when i try to view them it takes a few minutes and during that firefox becomes unresponsive, so maybe ur not waiting long enough ?

---

### Post by Malac on 2006-10-09
> **delfick said:**
> 
also can it be made as an option for the USPuser plugin to only display the logo, and not the text that goes with it?

Done, that was the easy one.
See plugins thread here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

I'll have to look at the other later.

---

### Post by delfick on 2006-10-09
> **Malac said:**
> Done, that was the easy one.
See plugins thread here: [http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

I'll have to look at the other later.

cool, thnx :D

also so that clicking the logo opens the home folder?

thnx :D

---

### Post by Malac on 2006-10-09
> **delfick said:**
> cool, thnx :D

also so that clicking the logo opens the home folder?

thnx :D
Don't think this is a good idea for the majority of users but if you want to do it yourself open USPuser.py and find the lines :
```
    def FaceChooser(self, widget):
            os.system('gdmphotosetup &')
```
and change it to read :
```
    def FaceChooser(self, widget):
           os.system('nautilus &')
```
which should do what you want.

Hope this helps.

---

### Post by delfick on 2006-10-09
> **Malac said:**
> Don't think this is a good idea for the majority of users but if you want to do it yourself open USPuser.py and find the lines :
```
    def FaceChooser(self, widget):
            os.system('gdmphotosetup &')
```
and change it to read :
```
    def FaceChooser(self, widget):
           os.system('nautilus &')
```
which should do what you want.

Hope this helps.

awsome ! :D

thnx....

only problem is that the menu doesn't close after clicking it.....

also, would it be possible to put the logo in the top right corner of the menu, like in my attached mockup?

that would be very cool :D

---

### Post by chanders on 2006-10-09
Hey Delfick, due to the limitations of GTK, positioning of the avatar in that position is not possible (along with true transparency which I know you are anxiously waiting on). I myself am anxiously awaiting composite aware GTK for python.

I havent seen animated images in GTK apps before either. I think it wont be impossible but it would require a bit of coding to simulate an animated image.

---

### Post by delfick on 2006-10-09
> **chanders said:**
> Hey Delfick, due to the limitations of GTK, positioning of the avatar in that position is not possible (along with true transparency which I know you are anxiously waiting on). I myself am anxiously awaiting composite aware GTK for python.

I havent seen animated images in GTK apps before either. I think it wont be impossible but it would require a bit of coding to simulate an animated image.

damn :( 

o well, i'll just have to dream for a few decades that it is possible, untill it is :D

though, if copacity is made for beryl, there could be a possbility of something like true transparency....

and what if the usp could have a continues splash image at that position when it is open, and then if the splash plugin is made to do that effect to all splashes (which i'm gonna ask for anyway) then it could work :D

---

