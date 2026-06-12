---
title: "Panned desktop image in Compiz"
date: 2008-03-19
forum: Ubuntu Brainstorm
---

### Post by Triggerhapp on 2008-03-19
One idea I've been toying with is a setting in Compiz I would like to see, im not sure if here would be the best place to suggest it... XD
Here goes though, do tell me if i should look elsewhere.
An idea struck me a bit ago when I realised you could set seperate images on each face of your desktop cube, I edited one of my images, cutting it into 4 seperated images, and placed them in order on my cube.
I made a script which could do this automagically, which is enough for my own uses.
Would anyone else like to see said option, or am I just a wierdo ? :D

Regards, Trigg

---

### Post by Neon Lights on 2008-03-19
I would LOVE this. :D

---

### Post by Triggerhapp on 2008-03-20
Wow cool. So im not a rare breed then XD
I could pass you the script i hacked up, its as pretty as it'll get unless someone adds it as a plugin to compiz :)

---

### Post by Neon Lights on 2008-03-21
Hey, no guarantees, we might just be the only two in existence. ;P
and sure, please and thank you. =]

---

### Post by Triggerhapp on 2008-03-21
Its been a while since I ever lost a script...
I managed to lose it trying to tar it to upload XD Arg, when i get back from work this afternoon I'll have to remake it... fun stuff

I think i need to stop bieng so hit-and-run with Tar, I just filled my script with "^@" 's XD

---

### Post by Triggerhapp on 2008-03-21
Ok! this version isnt so clean, and for that reason may be a little dangerous.
The dangers are - Make sure you have compiz installed (duh?) make sure you;re not root (duh?) and have a home directory (duh?)

Alright, other than not bothering adding all the "if(-f " 's its all fine.
Its built on Perl, and requires the image::Magick package

```
sudo apt-get install perlmagick
``` should do enough to get what this script depends on.

Instructions are simple, untar it, run ```
./spanimage imagefile.ext faces
```
The script can also be used to change the number of faces on the "cube"

Enjoy

Edit: Oh yeah, added some images I found in a quick google search for "Panorama"

---

### Post by Triggerhapp on 2008-03-29
Hah I've gone a whole step futher, I've not made a Perl script to "skin" a cube/skydome by setting all the options up as the user wants and inserting/panning images...

Now im just lost as to Where to go with this, where to upload etc...

---

### Post by john91 on 2008-03-31
It's occurred to me that having a panned image would look even better using the desktop wall rather than the cube, since the wall pans rather than rotates to a new cube face.  will this script work with the wall as well, or just the cube? (I haven't taken a look at the script myself cause I'm not familiar with perl)

---

### Post by Triggerhapp on 2008-04-01
The skydome (wall, as you call it) already does that :) What this script does is set a panned image on the desktop, to compliment the skydome

---

### Post by john91 on 2008-04-01
the desktop wall is completely different from the skydome, considering the skydome is an extension of the cube plugin.  i don't use the cube plugin at all, but instead use the desktop wall plugin.  all i really wanted to know was if this script changes the values in compiz to set the desktop backgrounds in the cube plugin, or if it just divides the image.  if it changes the values itself, then the script can't be used for the desktop wall without change.

---

### Post by Triggerhapp on 2008-04-02
My mistake.
it divides the image and drops each into ~/.skydomeimg you can use these, I imagine, as your seperate desktops and never touch skydome :) Will look into that myself now

---

### Post by john91 on 2008-04-02
Alright, thanks.  I'd change the script myself, but like i said, I don't know perl.  

p.s.  Do different photo sizes, aspect ratios, or different screen resolutions affect this at all?

---

### Post by Triggerhapp on 2008-04-04
Images that are not originally panoramic will look stupid stretched across 4 displayes, Compiz automagically scales all images to fit the surface so Screen size, on a technicality, does not affect the image, change the number of displays if your image looks too horizontally stretched, if it looks compressed (everythings too small horizontally) then use more displays. 
:)

the aspect ratio, for best images, should be the same as that of your multiple desktops. so if you have a 1024x768 display, with 4 desktops...
4096x768 
5.33:1 aspect ratio.
Anyways, im blabbering :) Later

---

### Post by xelapond on 2008-04-10
This should also be implemented for desktop wall.  I would love to be able to set my 4x4 grid to one bug picture of the earth, and have each section have a small chunk of it.

I'm sure there is documentation for writing your own Compiz Plugins, in which case you should definitely do so.

---

### Post by xelapond on 2008-04-10
You could upload this to Gnome-Look, so other people could use, improve and give feedback to it.

---

### Post by Triggerhapp on 2008-04-10
Im too lazy to keep going after I get something working :P
This is why I'll never get hired for my programming abilities, I get inspiration, i make it work, then i drop it and try to think of something else...
Last night I wrote a script to parse Orage (calendar) files and give you todays (+ x days ahead) notification

It works and im not adding more features simply because ive lost the flame now XD

---

