---
title: "GNOME icons open source?"
date: 2010-08-13
forum: The Cafe
---

### Post by ltwinner on 2010-08-13
I was looking for some icons for my website and I came across the gnome desktop icons which can be downloaded off [http://ftp.gnome.org/pub/gnome/sources/gnome-desktop/](http://ftp.gnome.org/pub/gnome/sources/gnome-desktop/)

I'm wondering what is the deal with using these icons on my website? Could I get it trouble for copyright or are they open source?

---

### Post by Bachstelze on 2010-08-13
> **ltwinner said:**
> 
I'm wondering what is the deal with using these icons on my website? Could I get it trouble for copyright or are they open source?

They are open source, so you can use them as long as you comply with the terms of the license.

---

### Post by ltwinner on 2010-08-13
From what I can make out it looks like im free to use them. I'd appreciate any other opinions though

---

### Post by ve4cib on 2010-08-13
As long as you're not redistributing them compiled into a closed-source binary you should be fine.  Using them on your website is fine.  (If you want to you can put a link back to Gnome on your about/credits page as a thank-you to Gnome, or make a donation to them, but that's not required.)

---

### Post by Bachstelze on 2010-08-13
> **ve4cib said:**
> As long as you're not redistributing them compiled into a closed-source binary you should be fine.  Using them on your website is fine.  (If you want to you can put a link back to Gnome on your about/credits page as a thank-you to Gnome, or make a donation to them, but that's not required.)

Actually, attribution (i.e. saying where the icons come from) *is* required. Also required is redistributing the "source" (whatever that is, I don't know what Gnome uses to make their icons), especially if you modify the icons.

---

### Post by ve4cib on 2010-08-13
> **Bachstelze said:**
> Actually, attribution (i.e. saying where the icons come from) *is* required. Also required is redistributing the "source" (whatever that is, I don't know what Gnome uses to make their icons), especially if you modify the icons.

Really?  I didn't know attribution was required under the GPL.  (I'm assuming the Gnome icons are GPL -- I haven't actually looked.)  I knew it was required for most CC licenses, but not for GPL.  Hmm.  You learn something new every day.

As for the source, in terms of images the source is the image itself.  The GPL doesn't apply terribly elegantly to things like books, images, etc... but the image and the source are the same entity.  You don't need to go and get the GIMP .xcf files or whatever the Gnome devs use to make the images and distribute those as the source.  The png/svg files are sufficient.

---

### Post by Bachstelze on 2010-08-13
> **ve4cib said:**
> 
As for the source, in terms of images the source is the image itself.  The GPL doesn't apply terribly elegantly to things like books, images, etc... but the image and the source are the same entity.  You don't need to go and get the GIMP .xcf files or whatever the Gnome devs use to make the images and distribute those as the source.  The png/svg files are sufficient.

You are wrong. The GPL (v2, v3 is similar, I don't know which version the GNOME icons are distributed under) says:

> The source code for a work means the preferred form of the work for making modifications to it.

That is very clear. Take, for example, this image (from phpBB):

[img]http://itsuki.fkraiem.org/stuff/button_topic_new.gif[/img]

and try to modify it, for example to translate the text in another language. Very hard  if you don't have the .psd/.xcf/whatever file, trivial if you do. Pretty obvious what "the preferred form of the work for making modifications to it" is.

---

### Post by Bachstelze on 2010-08-13
> **ve4cib said:**
> Really?  I didn't know attribution was required under the GPL.  (I'm assuming the Gnome icons are GPL -- I haven't actually looked.)  I knew it was required for most CC licenses, but not for GPL.  Hmm.  You learn something new every day.

Of course it is. By putting an image on your website, you are in effect redistributing it (anyone can download it from your website). Redistributing a work without proper copyright notice of the author is a violation, not only of a license, but also of copyright law.

EDIT: meant to edit my other post, oh well...

---

### Post by bunburya on 2010-08-13
Presumably they are free to use, but the extent of attribution and stuff depends on the terms of the particular licence. Given that GNOME icons are more like artwork than computer programs I would have thought they'd have used something other than the GPL, like CC, but I'm probably wrong...

Surely the licence info can be found on the website.

---

### Post by ve4cib on 2010-08-13
Clearly I need to re-read the newer versions of the GPL.  I've only ever read through the LGPL and the GPL v1 (and that was a long time ago), so my memory for these things is clearly not as good as I thought it was.  Sorry for accidentally spreading misinformation on the subject.


> **Bachstelze said:**
> Of course it is. By putting an image on your website, you are in effect redistributing it (anyone can download it from your website). Redistributing a work without proper copyright notice of the author is a violation, not only of a license, but also of copyright law.

Including the copyright information and citing the original source are not necessarily the same thing, are they?  I mean, as long as the license itself is present do you actually need to specify that the icons came from Gnome.org?  Or just state that the icons fall under the auspices of the GPL and leave the original source unmentioned?


> The source code for a work means the preferred form of the work for making modifications to it.
So does this mean that every single icon set and background on [Gnome-Look](http://gnome-look.org) that's licensed under the GPL must include the XCF/PSD/whatever files in the download or be themselves in violation of the GPL?  90% of the icon sets I've downloaded from there that were licensed under the GPL did not include anything other than PNGs.  I've even put a few backgrounds on Gnome-Look licensed as GPL, but only added PNGs; I never saved the XCF files, so I cannot distribute the file in "its preferred format for making changes" -- no such file exists.  Am I unknowingly violating the GPL for not saving the files in a more easy-to-edit format before distributing them?

---

