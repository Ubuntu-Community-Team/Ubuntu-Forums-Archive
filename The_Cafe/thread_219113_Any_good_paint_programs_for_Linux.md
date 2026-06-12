---
title: "Any good paint programs for Linux?"
date: 2006-07-19
forum: The Cafe
---

### Post by BuffaloX on 2006-07-19
I tried Gimp, but I don't like it so much.
Tried cinepaint, it crashed in 5 mins. (my first crash in Ubuntu)
I tried to compile MTpaint, but can't make it work.

Are there any good programs like painter for windows.
Note I'm NOT looking for a replacement of Photoshop, I don't like that so much either.

Thanx for your interest. :p

---

### Post by Gadren on 2006-07-19
The best Paint-like program I've found is KolourPaint.  It's KDE, but if you like Gnome, it's still worth it to use it.

---

### Post by aysiu on 2006-07-19
I'll vouch for Kolourpaint, too.

---

### Post by Engnome on 2006-07-19
Tried Gnu paint? A paint look alike, doesn't fit me but maybe you'll like it?

---

### Post by ComplexNumber on 2006-07-19
try [mypaint]("http://gnomefiles.org/app.php?soft_id=1189"). click.

---

### Post by BuffaloX on 2006-07-19
THANX guys. :D 

**Mypaint looks extremely interesting.**
Kolourpaint is very basic, but could come in handy for very small tasks.
GNU paint is much too basic not for me. (Kolourpaint is better)

Unfortunately I couldn't find mypaint in repository,
and it won't compile on my system...
Have to look into that, I definetely need to give it a try. :p 

Further suggestions are of course very welcome.=P~

---

### Post by mips on 2006-07-19
Krita ?

---

### Post by BuffaloX on 2006-07-19
Krita is also nice.
But I had a couple of problems.
When I made a floodfill and wanted to undu I couldn't.
I couldn't imediately make the airbrush work. :confused:
It seems to have a couple of nice features though, so it may still come in handy. :p

---

### Post by hizaguchi on 2006-07-19
Inkscape is good for certain things too.  KolourPaint is the best I know of if you're looking for something like MS Paint though.

---

### Post by BuffaloX on 2006-07-19
Inkscape is Vector based, and yes I agree it's very nice, and meets my needs for vector graphics.
I'm looking for a nice Pixel app.
Thanx anyway. :p

---

### Post by darkmaster on 2008-02-16
In understand your problem. I have the very same issue. No real painting program for Linux... it seems like people thinks Gimp is a painting program :(

It is absolutely not. Corel Painter is a painting program, Artrage is a painting program... Gimp is an image manipulation program.
Here's something I wrote some time ago to get people in the idea of what the problems is all about for me and a lot of other people looking for a painting program in Linux:

[http://thedarkmaster.wordpress.com/2007/08/12/painting-programs-for-linux/](http://thedarkmaster.wordpress.com/2007/08/12/painting-programs-for-linux/)

i this article you'll also find some suggestions on how to install nice software like Artrage or DeepPaint in Linux using Wine.... unfortunately, these are not opensource apps, but at least they are freeware. A pro version of Artrage is available too and it costs only $20, but it is more than worth the expense. Well, now in Linux something is moving anyway... Krita is becoming much more functional with the net release, looks like it will support some painting simulation tool...
Plus there are a pair of opensource apps, still primitive apps, but getting better with time and looking really promising. I'm talking about Gogh and MyPaint. The patter is already pretty nice but still lacking an incredible number of important tools... it is impossible to use an erasing tool for example.. you should use a painting tool with the white color instead.... and it does not support any transparency, paper type.... well, rpetty anything :(
But at least, hey, this is a try on the right direction! Nothing else is available in Linux today for Painting, so, better than nothing...

P.S.: I really find it fun and sad when people mention a vector based tool such as Inkscape (an incredibly good verctor based tool) when talking about painting programs :(
If only someone out there is capable of understanding what the problem is and what we're talking about, then there are really few chances that OpenSource software can get better in these direction...

---

### Post by sloggerkhan on 2008-02-16
> **darkmaster said:**
> I
If only someone out there is capable of understanding what the problem is and what we're talking about, then there are really few chances that OpenSource software can get better in these direction...

The reason people do this is because of mspaint:
To most people the words computer and paint now mean that you are going to airbrush a pixely image using a dumbed down version of kid pix. And of course the first thing that come to mind is that using an easy to use vector graphics program makes better images than trying to paint using bad raster tools and mouse.

---

### Post by ssam on 2008-02-16
tuxpaint :-)

maybe [Gogh]("http://www.gnomefiles.org/app.php/Gogh")

---

### Post by darkmaster on 2008-02-16
> **sloggerkhan said:**
> The reason people do this is because of mspaint:
To most people the words computer and paint now mean that you are going to airbrush a pixely image using a dumbed down version of kid pix. And of course the first thing that come to mind is that using an easy to use vector graphics program makes better images than trying to paint using bad raster tools and mouse.

Thank you, honestly this explains a lot to me. I'm Italian and in Italy we say "dipingere" for paint. So MS paint is a program everyone knows about but it is so insignificant that no one cares. When saying painting programs I never thought of something like "programs similar to MS Paint" because in Italy we always say "programmi per dipingere" and I didn't think of the possible misunderstanding deriving from the "MS paint" name..

---

### Post by Omnios on 2008-02-16
Same here looking for a paintshop clone lol. 

 Really like making skins and avatars with it a very long time ago.

---

### Post by %hMa@?b&lt;C on 2008-02-16
tuxpaint :P

I have had good luck with Krita. I really like krita.  You can always try Pixel (it costs money though) Gimp-Shop is another that you can try.

---

### Post by LaRoza on 2008-02-16
[http://www.linfo.org/software_artists.html](http://www.linfo.org/software_artists.html)

Might be something good there.

---

### Post by Martje_001 on 2008-02-16
> **BuffaloX said:**
> Unfortunately I couldn't find mypaint in repository,
and it won't compile on my system...
Have to look into that, I definetely need to give it a try. :p 
You have to install some things:
```
sudo apt-get install build-essential pkg-config libglib2.0-dev libgtk2.0-dev python2.5-dev python-gtk2-dev
```

---

### Post by darkmaster on 2008-02-16
As I said, the only primitive, veru primitive, alternative to Corel Painter I can see around is MyPaint or Gogh. Bot are just sketches of real programs and are able of doing pretty nothing in the actual stage if compared to Painter or Artrage... but they are the only tools on the right root. Tuxpaint, gimpshop / gimp, pixel, these are not painting programs. These are just image manipulation programs. It is very different: you cannot simulate real painting with any of those softwares, sorry.

If you wish to give MyPaint a shot, from the main site there is the link to a precompiled deb, created bu those of getdeb, so no need to compile anything, really.

---

