---
title: "Gimp 2.2.14 for Feisty?"
date: 2007-05-12
forum: Repositories &amp; Backports
---

### Post by Lucifiel on 2007-05-12
Well, I tried to install Gimp 2.2.14 .deb (for debian) only to find out that .deb packages for Debian aren't always meant for Feisty. :p 

Then, I've attempted to build Gimp 2.2.14 myself but that too failed. That is: I booted using the livecd, downloaded checkinstall and ran several commands but meh, Gimp couldn't build.

I don't think this falls under a backport, though... ^^;; 

So, any brave soul willing to build this package? :p I'm tight on time and though I'd love to keep trying to build the package myself, I'm committed to other projects and tasks. :) However, Gimp keeps crashing everytime I try to save a .psd file which is required for my tasks since I'm working with someone who uses Photoshop on Windows. 


Thank you!
Lucifiel

---

### Post by hikaricore on 2007-05-12
Anything wrong with 2.3.13?

[http://ubuntuforums.org/showthread.php?t=311020&highlight=gimp](http://ubuntuforums.org/showthread.php?t=311020&highlight=gimp)

Works fine for me on edgy and feisty.

---

### Post by Lucifiel on 2007-05-13
Hmm...2.3.13 is really beta, isn't it? 

Oh, I held off on trying it but I'll give it a shot now. :) 

Hmmm... just installed it and it seems rather sluggish. It takes about 3 to 4 seconds for certain options to respond, for certain windows to appear. Yeah... that wouldn't be an issue if I wasn't rushing for time and have thousands of images to compile and work with.

Edit: Hmmm... encountered some issues after installing Gimp 2.3.13 . The tools within Gimp 2.2.13 no longer worked nor did the tools within Gimp 2.3.13. As a result, I was forced to purge all the .gimp2.3 and .gimp2.2 folders and remove Gimp 2.3.13 and reinstall Gimp 2.2.13. That fixed everything.

---

### Post by Lucifiel on 2007-05-14
Okay, managed to get Gimp 2.3.13 another shot today.

Looks good but I think they changed the way the "Brightness and Contrast" tool works, so now I can't use it anymore. What I'm doing is comparing images on a "by-pixel" level. 

That is: You place two similar(but not exactly similar) images on top of another, as 2 separate layers. 

Then, Set Layer effects = "Difference" and Merge the layers.

Then, by using Brightness and Contrast, you'll be able to expose all pixels with differing values.

That said, this does not look good for me as Gimp has been crashing non-stop as of late. =/

---

### Post by G.W. on 2007-05-14
Maybe you would be interested in [this]("http://www.imagemagick.org/script/compare.php").

---

### Post by Lucifiel on 2007-05-24
> **G.W. said:**
> Maybe you would be interested in [this]("http://www.imagemagick.org/script/compare.php").

Thank you for the link. Although, running a script for hundreds to thousands of non-sequential named and numbered images one by one is not feasible at all. I guess that could be an option if I only had a few images to compare, though. :)

Looks like my only option is to try and compile this myself. Failing which, I'll just use Windows XP for now since I rely a lot on Gimp after all.

---

### Post by Lucifiel on 2007-05-24
Okay, man, I downloaded a ton of libraries and such, so that I could do ./configure, make and sudo make install to get a package for 2.2.14. That didn't work. 

*shrugs*

---

### Post by zgornel on 2007-05-25
> **Lucifiel said:**
> Okay, man, I downloaded a ton of libraries and such, so that I could do ./configure, make and sudo make install to get a package for 2.2.14. That didn't work. 

*shrugs*

Get the latest gimp 2.3 (2.3.16) : [http://ubuntuforums.org/showthread.php?t=428330](http://ubuntuforums.org/showthread.php?t=428330) . It is stable enough...

---

