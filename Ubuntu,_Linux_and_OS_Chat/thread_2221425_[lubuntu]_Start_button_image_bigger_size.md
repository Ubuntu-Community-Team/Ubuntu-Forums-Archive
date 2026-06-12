---
title: "[lubuntu] Start button image bigger size"
date: 2014-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by abbat.81 on 2014-05-02
Hi, in lubuntu 14.04 distro start button image is limited to 56x24 px.

[ATTACH=CONFIG]252742[/ATTACH]

But I use panel size  bigger height, so that image interpolates, like this:

[ATTACH=CONFIG]252743[/ATTACH]

Where can I get that logo image with better size?
Thanks.

---

### Post by vasa1 on 2014-05-02
People may not want to visit **.ru** sites. Why don't you upload the images from your PC via the attachment feature of the forum?

---

### Post by abbat.81 on 2014-05-02
> **vasa1 said:**
> People may not want to visit **.ru** sites. Why don't you upload the images from your PC via the attachment feature of the forum?
I've just fixed it.
Thanks)))

---

### Post by vasa1 on 2014-05-02
Right-click on the Menu icon
Choose "Menu" settings
Then browse to a suitable icon path.

---

### Post by bapoumba on 2014-05-02
> **abbat.81 said:**
> I've just fixed it.
Thanks)))

Sorry, may be it is just me, but I do do see the screenshots or pics.
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

---

### Post by abbat.81 on 2014-05-02
> **vasa1 said:**
> Right-click on the Menu icon
Choose "Menu" settings
Then browse to a suitable icon path.

I did it, but my panel height is 35 px and icon height is 24.
So I get very bad interpolated icon.

Were else I could ask about those icon?

---

### Post by bapoumba on 2014-05-02
> **abbat.81 said:**
> I did it, but my panel height is 35 px and icon height is 24.
So I get very bad interpolated icon.

Were else I could ask about those icon?

I tried (normal size is 24 here).
Right click on Panel > Panel Settings > Geometry, see screenshot attached.

---

### Post by abbat.81 on 2014-05-02
> **bapoumba said:**
> I tried (normal size is 24 here).
Right click on Panel > Panel Settings > Geometry, see screenshot attached.

:(
I can wish to set Panel Height 135 px, so  my Start button would like this

[ATTACH=CONFIG]252738[/ATTACH]
do you like this image?
That's what I mean.

---

### Post by vasa1 on 2014-05-02
One possibility is to use an svg image and then scale it to your need. Look at */usr/share/icons/lubuntu/symbolic/start-here.svg* for example. 
You can use an svg editor to make images of a suitable size.
If you don't want to install Inkscape, then there's an online resource here: [http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html](http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html)

---

### Post by abbat.81 on 2014-05-02
> **vasa1 said:**
> One possibility is to use an svg image and then scale it to your need. Look at */usr/share/icons/lubuntu/symbolic/start-here.svg* for example. 
You can use an svg editor to make images of a suitable size.
If you don't want to install Inkscape, then there's an online resource here: [http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html](http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html)

I like Inkscape and I have it.
I have not distro Lubuntu 14.04 now, so I want to ask you to attach those _***/usr/share/icons/lubuntu/symbolic/start-here.svg ***_to message here.
Thank you in advance :)

---

### Post by abbat.81 on 2014-05-02
> **vasa1 said:**
> One possibility is to use an svg image and then scale it to your need. Look at */usr/share/icons/lubuntu/symbolic/start-here.svg* for example. 
You can use an svg editor to make images of a suitable size.
If you don't want to install Inkscape, then there's an online resource here: [http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html](http://svg-edit.googlecode.com/svn/trunk/editor/svg-editor.html)
Unfortunelly,  */usr/share/icons/lubuntu/symbolic/start-here.svg - *is not the image I asked for :(

I need this image with better resolutions

[ATTACH=CONFIG]252745[/ATTACH]

---

### Post by bapoumba on 2014-05-02
[http://lubuntublog.blogspot.fr/p/artwork.html](http://lubuntublog.blogspot.fr/p/artwork.html)

You can download all the icons. TBH, I had a quick look and did not find the exact same one.. There are a couple you could use though.

---

### Post by vasa1 on 2014-05-02
Why don't you make your own image for the menu button? That's what I did:
```
<svg width="48" height="64" xmlns="http://www.w3.org/2000/svg" xmlns:svg="http://www.w3.org/2000/svg">
   <rect fill="#333" x="3" y="10.25" width="43" height="9"/>
   <rect fill="#333" x="3" y="28.25" width="43" height="9"/>
   <rect fill="#333" x="3" y="46.25" width="43" height="9"/>
</svg>
```

---

### Post by abbat.81 on 2014-05-02
> **vasa1 said:**
> Why don't you make your own image for the menu button? That's what I did:
```
<svg width="48" height="64" xmlns="http://www.w3.org/2000/svg" xmlns:svg="http://www.w3.org/2000/svg">
   <rect fill="#333" x="3" y="10.25" width="43" height="9"/>
   <rect fill="#333" x="3" y="28.25" width="43" height="9"/>
   <rect fill="#333" x="3" y="46.25" width="43" height="9"/>
</svg>
```

How can I use you code?
I tried to use it in terminal :)

please, help me! :)

---

### Post by vasa1 on 2014-05-02
That is just the contents of an svg image file. I saved it as ~/Pictures/menu1.svg. Then, after right-clicking on the existing Menu icon and choosing "Menu settings", I pointed to that file.

Obviously, that doesn't look like what you want but it is scalable whereas .png files need to be modified on a pixel-by-pixel basis (IIRC) if you don't have one of the size you want.

I'm not sure if an older Lubuntu (13.10 or 13.04 or older)had the image you want as .svg. I think it did. But I don't have an older Lubuntu to look at :(

---

### Post by bapoumba on 2014-05-03
From here, I found it in Quantal theme, but it is a .png.
[http://lubuntublog.blogspot.com.es/p/artwork.html](http://lubuntublog.blogspot.com.es/p/artwork.html)

---

