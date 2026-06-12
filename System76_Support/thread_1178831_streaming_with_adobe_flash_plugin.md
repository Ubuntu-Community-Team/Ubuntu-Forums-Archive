---
title: "streaming with adobe flash plugin"
date: 2009-06-04
forum: System76 Support
---

### Post by tessk on 2009-06-04
hey  there

first of all, would like to say i just got my darter today and am very pleased so far :)

however i'm having problems watching my favourite news cast

can you tell me how to stream the video from [http://www.cbc.ca/national/](http://www.cbc.ca/national/) please?

i tried downloading the latest version of the adobe flash plugin ".deb for Ubuntu 8.04+" but I get "Error: Wrong architecture 'i386'" when Package Installer runs.

i've tried a couple of the other linux versions of the plugin but i can't seem to work it out ... help please!!

thanks
tess

---

### Post by tessk on 2009-06-04
ps should've mentioned ... the first clip (very short advertisement) plays, but nothing beyond that

---

### Post by sccolbert on 2009-06-04
> **tessk said:**
> ps should've mentioned ... the first clip (very short advertisement) plays, but nothing beyond that

execute this in the terminal:

sudo apt-get install flashplugin-installer

---

### Post by sccolbert on 2009-06-04
first you should remove any other flash related plugins

---

### Post by tessk on 2009-06-05
I get:

Reading package lists... Done
Building dependency tree
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.

---

And sorry I don't know how to identify and remove other flash relate plugins so i didn't do that

---

### Post by majamba on 2009-06-05
or you could remove the flash player
aptitude purge flashplugin-installer 
and install gnash(alternative player for flash)
aptitude install gnash

---

### Post by tessk on 2009-06-05
hmmm thanks for the idea but now i don't even see the frame where the video is supposed to be (but the rest of the page is there)

---

### Post by MorphWVUtuba on 2009-06-05
> **tessk said:**
> I get:

Reading package lists... Done
Building dependency tree
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.

---

And sorry I don't know how to identify and remove other flash relate plugins so i didn't do that

Here's what I'd recommend.  

```
sudo apt-get dist-upgrade
```

That should fix the 41 not upgraded.  Then just try this:

```
sudo apt-get install ubuntu-restricted-extras
```

Let's see where that gets you.

---

### Post by tessk on 2009-06-05
hey thanks everyone for the replies but somehow i've got it working! i searched around a bit on these forums (which i probably should have done more of in the first place) ... not sure how this worked, but i executed the first step of this howto: [http://ubuntuforums.org/showthread.php?t=766683&highlight=cbc+the+national](http://ubuntuforums.org/showthread.php?t=766683&highlight=cbc+the+national) (the step in the 'preparation' section)

anyway seems to be working

MorphWVUtuba what's the restricted extras all about?

---

### Post by thomasaaron on 2009-06-05
Ubuntu Restricted Extras
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

Also, you probably should follow this tutorial...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)
...to get all of your multimedia stuff set up.

---

### Post by tessk on 2009-06-05
thanks thomas ... i'll check those out after work later today

---

### Post by Teasdale on 2009-06-06
> **MorphWVUtuba said:**
> Here's what I'd recommend.  

```
sudo apt-get dist-upgrade
```

That should fix the 41 not upgraded.  Then just try this:

```
sudo apt-get install ubuntu-restricted-extras
```

Let's see where that gets you.

Thanks - I had the same problem, and this seems to have worked.

I'll also read the posted tutorial.

---

