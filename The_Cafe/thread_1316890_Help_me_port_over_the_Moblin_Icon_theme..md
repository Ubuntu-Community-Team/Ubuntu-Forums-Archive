---
title: "Help me port over the Moblin Icon theme."
date: 2009-11-06
forum: The Cafe
---

### Post by Islington on 2009-11-06
I think the elegance and simplicity of the moblin icon theme, needs to find a wider audience. Would anybody here be willing to help me port over, and in many cases complete the icon theme? 

Here is what I think we need:
[list]
[*]A few artists, that are good with inkscape, willing to take and give helpful critique.
[*]A coder, that can help us get a team together on launchpad.
[*]A coder to help package the theme, both for testing and final, possibly maintain a ppa.
[*]A coder to help maintain the code branch. (I know we can do this the old fashioned way with manual versioning, but I think we should go about this correctly.)
[*]A coder to set up and maintain a wiki page. 
[*]Eventually we will need lots of testers as well.
[/list]
So I think we need all sorts of people with all sorts of skills. A goal is for the icon theme to be included in Lucid Lynx, if not officially then in the community packages. 

Would you be interested?

---

### Post by Islington on 2009-11-06
[reserved in case]

I have already started the work. See attached tar file, for file organization, one canvas workflow, and the clipping script, & two ported over Icons.

The moblin Icon theme can be found in the git here: [http://git.moblin.org/cgit.cgi/moblin-icon-theme/](http://git.moblin.org/cgit.cgi/moblin-icon-theme/)

---

### Post by Islington on 2009-11-06
[final reserved just in case]

---

### Post by xuCGC002 on 2009-11-06
Wait, so all you want to do is copy the icons from Moblin to Ubuntu? And then you want them to get into official releases?

Why not just put the icons on GNOME-look? People can use them if they want to, and it's way less complicated than getting a PPA and packages together for just a simple icon theme.

---

### Post by Islington on 2009-11-06
> **xuCGC002 said:**
> Wait, so all you want to do is copy the icons from Moblin to Ubuntu? And then you want them to get into official releases?

Why not just put the icons on GNOME-look? People can use them if they want to, and it's way less complicated than getting a PPA and packages together for just a simple icon theme.

I dont think you understand, that the moblin theme is very incomplete. I want to port over the official icons, and complete the theme. And the launchpad will help with version control, which can be notoriously difficult on sites like *-look.

---

### Post by hugmenot on 2009-11-06
You might not be aware that Jakub Steiner (jimmac) has already completed a fairly comprehensive set of moblin icons, ready to be used in Gnome:

[http://jimmac.musichall.cz/i.php?i=moblin](http://jimmac.musichall.cz/i.php?i=moblin)
[http://www.flickr.com/photos/jakubsteiner/tags/moblin/](http://www.flickr.com/photos/jakubsteiner/tags/moblin/)
[http://repo.or.cz/w/moblin-icon-theme.git](http://repo.or.cz/w/moblin-icon-theme.git)

It has a build system that will generate an index.theme, ready to use in the theme chooser.

---

### Post by Islington on 2009-11-06
> **hugmenot said:**
> You might not be aware that Jakub Steiner (jimmac) has already completed a fairly comprehensive set of moblin icons, ready to be used in Gnome:

[http://jimmac.musichall.cz/i.php?i=moblin](http://jimmac.musichall.cz/i.php?i=moblin)
[http://www.flickr.com/photos/jakubsteiner/tags/moblin/](http://www.flickr.com/photos/jakubsteiner/tags/moblin/)
[http://repo.or.cz/w/moblin-icon-theme.git](http://repo.or.cz/w/moblin-icon-theme.git)

It has a build system that will generate an index.theme, ready to use in the theme chooser.

oh excellent! I did not know about this, thanks!

---

