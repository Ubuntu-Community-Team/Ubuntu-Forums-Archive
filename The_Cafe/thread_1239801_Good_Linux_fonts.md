---
title: "Good Linux fonts?"
date: 2009-08-13
forum: The Cafe
---

### Post by Ranax on 2009-08-13
I am yet to find a single good Linux font. They are usually too big or have *some other issue*. So can people please post any decent, attractive fonts that they know of!

Thanks in advance! :)

---

### Post by Bölvaður on 2009-08-13
You might like these, but possibly only because you are used to them, personally I find them horrid.

[click to install]("apt:ttf-mscorefonts-installer")

---

### Post by Firestem4 on 2009-08-13
I personally love Deja Vu sans. Best looking font *ive* ever seen for daily use.

---

### Post by steveneddy on 2009-08-13
I use some MS fonts.

Otherwise just search for free fonts or just fonts in Google.


or

```
sudo apt-get install ttf-liberation
```

[http://packages.ubuntu.com/search?searchon=names&keywords=ttf-liberation](http://packages.ubuntu.com/search?searchon=names&keywords=ttf-liberation)

[https://fedorahosted.org/liberation-fonts/](https://fedorahosted.org/liberation-fonts/)

---

### Post by mrgnash on 2009-08-13
I like the Droid series, and use them pretty much exclusively, apart from outputted LaTeX documents, where I generally use Adobe Utopia.

---

### Post by TheAL76 on 2009-08-14
I like unDotum, and unDotum bold. Looks great on an LCD monitor.

---

### Post by hobo14 on 2009-08-14
I installed Lucida Grande

---

### Post by Ozor Mox on 2009-08-14
I'm using [Zekton](http://gnome-look.org/content/show.php/Zekton?content=50553) at the moment. It isn't designed for readability, but I think it looks cool :)

---

### Post by Barrucadu on 2009-08-14
The DejaVu family, Liberation family, Nimbus family&#8230; There are lots of good fonts if you search around.

---

### Post by Tibuda on 2009-08-14
I like Bitstream Vera Mono and Liberations Sans.

---

### Post by Bachstelze on 2009-08-14
There is no such thing as "Linux fonts". Linux mostly uses the TrueType font format, which is not specific to it, so you can basically install any font you like.

---

### Post by 3rdalbum on 2009-08-14
There's no such thing as a "Linux font", just as there's no such thing as a "Linux jpeg". Linux uses Truetype fonts, which are (in reality) platform-neutral.

EDIT: Great minds think alike, but genius minds think exactly the same thing with similar wording :-)

---

### Post by sertse on 2009-08-14
If the screenshot thread is anything to go by...

GE Inspira :P

---

### Post by imlinux on 2009-08-14
> **Ranax said:**
> I am yet to find a single good Linux font. They are usually too big or have *some other issue*. So can people please post any decent, attractive fonts that they know of!

Thanks in advance! :)
 you can make any fonts to look better,fonts in ubuntu doesn't look good by default.just make a file " .fonts.conf in your home directory  " and paste this log out and log in fonts will look better than before.
 
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintnone</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
``` 
IMO fonts are matter of personal choices.

---

### Post by pjalegria on 2009-08-14
Can someone tell me what is the diference between Sans and DejaVu Sans, because they look the same...:lolflag:

Thanks

---

### Post by Bachstelze on 2009-08-14
> **pjalegria said:**
> Can someone tell me what is the diference between Sans and DejaVu Sans, because they look the same...:lolflag:

Thanks

They does not *exactly* look the same. ;) The difference between fonts can sometimes be very subtle.

---

### Post by andrek on 2009-08-14
Aller Sans, Myriad Pro

---

### Post by pjalegria on 2009-08-14
> They does not exactly look the same.  The difference between fonts can sometimes be very subtle.

exactly what...

---

### Post by blithen on 2009-08-14
**Terminus** **Terminus** **Terminus** **Terminus** **Terminus** Im telling you it's the best EVER. Im on windows at the moment so I can't get a screen shot. I believe the package is called xfonts-terminus, its amazing...

---

### Post by Ranax on 2009-08-14
Thank you for all the suggestions so far! I will try them out later :)

---

### Post by #11u-max on 2009-08-14
ubuntu title font ;)

---

### Post by Barrucadu on 2009-08-14
> **pjalegria said:**
> Can someone tell me what is the diference between Sans and DejaVu Sans, because they look the same...:lolflag:

Thanks

Well&#8230; they look different. I'm not sure how to explain it better than that. I think Sans is a horrible font, and I think DejaVu Sans is wonderful.

---

### Post by itreius on 2009-08-14
I'm using Liberation Sans 10 together with the following ~/.fonts.conf, and I find it to be easy on the eyes.
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<!--  Use the Antialiasing -->
<match target="font">
    <edit name="antialias" mode="assign">
        <bool>true</bool>
    </edit>
</match>
<!--  Use the Autohinter -->
<match target="font">
    <edit name="autohint" mode="assign">
        <bool>true</bool>
    </edit>
</match>
<!--  Use Slight Hinting -->
<match target="font">
    <edit name="hintstyle" mode="assign">
        <const>hintslight</const>
    </edit>
</match>
<!--  Enable sub-pixel rendering -->
<match target="font">
    <edit name="rgba" mode="assign">
        <const>rgb</const>
    </edit>
</match>
</fontconfig>
```

---

### Post by decoherence on 2009-08-14
Helvetica and Times are the ONLY fonts!!! :biggrin:

---

### Post by cookieofdoom on 2009-08-14
Droid and Liberation are great open source fonts. I always use Droid Sans for all my fonts in Linux (except console fonts, I use Droid Mono there).

Otherwise just about any fonts should work with Linux....

---

### Post by phrostbyte on 2009-08-14
I love the Liberation font set. It looks great in print and on monitors.

the package name is ttf-liberation, and the fonts are prefixed with the word "Liberation", eg "Liberation Sans"

---

### Post by mystmaiden on 2009-08-14
I use a true type font, Harrington, for everything on my desktop. Too girly for most, but then that's why I like it!
:)

mystmaiden

imlinux wrote > you can make any fonts to look better,fonts in ubuntu doesn't look good by default.just make a file " .fonts.conf in your home directory " and paste this log out and log in fonts will look better than before.
 

copy and paste that in the terminal? I noticed that in my fonts config file there are 5 other .cache-2's , do I leave them there?

---

### Post by running_rabbit07 on 2009-08-14
> **steveneddy said:**
> I use some MS fonts.

Otherwise just search for free fonts or just fonts in Google.


or

```
sudo apt-get install ttf-liberation
```[http://packages.ubuntu.com/search?searchon=names&keywords=ttf-liberation](http://packages.ubuntu.com/search?searchon=names&keywords=ttf-liberation)

[https://fedorahosted.org/liberation-fonts/](https://fedorahosted.org/liberation-fonts/)

Thanks for that. I was happy to see it listed for Karmic.

---

### Post by treesurf on 2009-08-15
> **andrek said:**
> Aller Sans, Myriad Pro

Aller Sans is my current favorite.  Very nice font.

[IMG]http://media2.smashingmagazine.com/images/15-beautiful-free-fonts/allersans.gif[/IMG]

---

### Post by Anzan on 2009-08-15
sudo apt-get install ttf-droid

I use it system wide, including in Firefox (Shiretoko).

For ODFs and publications I use DejaVu Sans and Serif.

---

### Post by szymon_g on 2009-08-15
i like terminus and proggy fonts [http://www.proggyfonts.com/index.php?menu=download](http://www.proggyfonts.com/index.php?menu=download)

---

### Post by RATM_Owns on 2009-08-15
Terminus. :D

---

### Post by Irihapeti on 2009-08-15
Linux libertine

---

### Post by Gen2ly on 2009-08-15
Liberation Sans and use font config to replace ms fonts.

---

