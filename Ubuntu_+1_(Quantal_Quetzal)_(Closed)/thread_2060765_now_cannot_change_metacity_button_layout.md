---
title: "now cannot change metacity button layout"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by funicorn on 2012-09-20
Due to latest unity upgrade to version 6.6.0, metacity button layout setting in gconf-editor is neglected. All window button are shifted to top left again. 
In unity changelog it says,
> * debian/unity-common.install, debian/control:
    - don't ship gconf schemas as not built anymore (the gsettings schema ones are already shipped)

not sure it's related. 

So how could I move metacity window buttons from top left to top right without implement of gconf ? And how to personalize the buttons, like only keep 'close' button?

---

### Post by funicorn on 2012-09-21
OK I think I found the solution: 
```
gsettings set  org.gnome.desktop.wm.preferences button-layout :close
```
this will make window button right-sided and only 'close' button is left

---

### Post by Alan F on 2012-09-21
I fear that the mess is worse than suggested.

When windows are maximised the buttons are at the top left.

When they are not maximised they are at the top right.

The dconf setting should have them in the top left position.

I await patiently for this to be sorted.

---

### Post by funicorn on 2012-09-21
Why is that ? Top-right window buttons are introduced for a reason and should be kept for the same reason.  A man with left hand cut shouldn't cut his right one just for stupid 'coherence'. Not to mention it's wrong to put buttons to the top left of unity panel in the first place.

---

### Post by Warprunner on 2012-09-21
> **funicorn said:**
> OK I think I found the solution: 
```
gsettings set  org.gnome.desktop.wm.preferences button-layout :close
```
this will make window button right-sided and only 'close' button is left

Thank you Funicorn... after an update today they changed back to the left. Editing in GConf-Editor didn't do anything. 
Well appreciated.  :KS :KS  :KS
Warp

---

### Post by jbicha on 2012-09-21
Alan, I thought Unity always had the buttons in the same order in the top left corner for maximized windows no matter what you set. Anyway, you're welcome to file a bug requesting that Unity respect that setting. Try searching to see if it's already been reported first.

---

### Post by Warprunner on 2012-09-21
Just to let everyone know, mine stuck after the fix above. However I had to add two back. So I ran:
gsettings set  org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close

---

### Post by funicorn on 2012-09-21
Basically we are talking about different stuff. Buttons of maximized window are managed through unity panel, whereas buttons of unmaximized are done by the genuine window decorator, in my case it's metacity. It's always not good to place window buttons on the left side far away from mouse using by the right-sided. Just as I have said, a man with left hand cut should not cut hist right hand just because he wants to make his body look coherent. That's ridiculous.

> **jbicha said:**
> Alan, I thought Unity always had the buttons in the same order in the top left corner for maximized windows no matter what you set. Anyway, you're welcome to file a bug requesting that Unity respect that setting. Try searching to see if it's already been reported first.

---

### Post by jbicha on 2012-09-21
> **funicorn said:**
> Basically we are talking about different stuff. Buttons of maximized window are managed through unity panel, whereas buttons of unmaximized are done by the genuine window decorator, in my case it's metacity. It's always not good to place window buttons on the left side far away from mouse using by the right-sided. Just as I have said, a man with left hand cut should not cut hist right hand just because he wants to make his body look coherent. That's ridiculous.

Are you trying to say that right-handed people find it more difficult to use the right side of the screen? That's ridiculous.

For the record, my preferred desktop is GNOME Shell with close: (in other words the Activities overview is in the top left and so is the close window button), and I'm right-handed. I use Unity quite a bit too and it's convenient to not have the window management buttons switch from the left side to the right side just because I'm using a different session.

The Unity panel has never allowed customizing the window button order or placement; I believe it's hard-coded to only work one way.

---

### Post by funicorn on 2012-09-22
I think you misread a little. I'm saying a window button on the top left of screen is far away from mouse used by right-handed people in most occasions  hence is NOT good.
Even though one cannot change the fact that buttons of a maximized window appear on the top left of unity panel, he should at least keep the buttons of unmaximized ones 
on the top right. One should care more about convenience than coherence. It's like a man with left hand cut would not have the right one cut off just for not being incoherent.

> **jbicha said:**
> Are you trying to say that right-handed people find it more difficult to use the right side of the screen? That's ridiculous.

For the record, my preferred desktop is GNOME Shell with close: (in other words the Activities overview is in the top left and so is the close window button), and I'm right-handed. I use Unity quite a bit too and it's convenient to not have the window management buttons switch from the left side to the right side just because I'm using a different session.

The Unity panel has never allowed customizing the window button order or placement; I believe it's hard-coded to only work one way.

---

### Post by cariboo on 2012-09-22
Actually, with most operating systems most action is on the left of the desktop, I have yet to see a desktop where the majority of the functions are on the right.

---

