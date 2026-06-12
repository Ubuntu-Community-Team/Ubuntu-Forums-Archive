---
title: "HOWTO: Gtk1.2 not so ugly"
date: 2005-12-22
forum: Tutorials
---

### Post by shin on 2005-12-22
I haven't really found any good howto about gtk1.2 theme switching so here it is.

**0. What for?**

Gtk1.2 is still used by some old apps like xmms, gmplayer and stuff. Changing gtk2 (or qt) theme doesn't affect them. Plus there is no font antialias.

While font aliasing can't be turned on in these in any known for me way, you can still change gtk1.x theme and make them look not so ugly.

Still not convinced? Run gmplayer or xmms. And then compare its look with my attached screenshot.

**1. Let's do it - getting theme**

Firstly, find some nice gtk1 theme. In fact - that's the hard part.

Check:
[http://gnome-look.org/index.php?xsortmode=high&page=0](http://gnome-look.org/index.php?xsortmode=high&page=0)

I tested (and I recommend) either:
Plastig (from screenshot)
[http://gnome-look.org/content/show.php?content=9724](http://gnome-look.org/content/show.php?content=9724)

or Geramik
[http://gnome-look.org/content/show.php?content=3952](http://gnome-look.org/content/show.php?content=3952)

but feel free to use other theme.

Download it, unpack, move whole dir to /usr/share/themes/

E.g. for Plastig:
run terminal (konsole or anything..)
assuming you're in your home directory (prompt like user@server:~$)
```
wget http://gnome-look.org/content/download.php?content=9724&id=1
tar jxvf 9724-Plastig.tar.bz2
sudo mv Plastig /usr/share/themes/

```

for Geramik:
```
wget http://gnome-look.org/content/download.php?content=3952&id=1
tar zxvf 3952-Geramik-0.27.tar.gz
cd Geramik-0.27
./configure
make
```

if there was somekind of an error in using make:
```
apt-get install make
```

and finally

```
make install
```

Geramik is installed different way than Plastig but the results are the same - dir with theme is being created in /usr/share/themes/.

**2. Make it work**

So we got some themes. To enable them you need one more thing - libqtpixmap. To install it:

```
sudo apt-get install gtk-engines-qtpixmap

```

One can also find useful gtk-theme-switch:

```
sudo apt-get install gtk-theme-switch
```

It's a tool that was SUPPOSE to switch gtk1.x theme. And in fact it generates some good settings but in .gtkrc file, which is ignored by gtk1.x apps. Still you can use it to generate your own font settings or test new styles. 

In my opinion, it's not that useful.

Back to work.

```
echo "include \"$HOME/.gtkrc.mine\"" > ~/.gtkrc-1.2-gnome2
gedit .gtkrc.mine
```

and there paste something like:

```

include "/usr/share/themes/Plastig/gtk/gtkrc"
style "default-text" {
fontset = "-adobe-helvetica-medium-o-normal--10-100-75-75-p-57-iso10646-1,\
-*-r-*-iso10646-1,*"
}
class "GtkWidget" style "default-text"
```

first line is for our gtk theme, so for Geramik (or ThinGeramik) change:
include "/usr/share/themes/Plastig/gtk/gtkrc"
to
include "/usr/share/themes/Geramik/gtk/gtkrc"
or
include "/usr/share/themes/ThinGeramik/gtk/gtkrc"

I also used some font settings to make it a little nicer.

That's all.

**3. Oh boy it looks so pretty..**

No it doesn't. Don't be deceived. Gtk1 will never look as good as gtk2. Non-antialiased fonts still look ugly. If you're using mplayer - I recommend installing it from cvs (great howto - [http://ubuntuforums.org/showthread.php?t=85190](http://ubuntuforums.org/showthread.php?t=85190)) to get it work with gtk2.

**4. UPDATE - Anti aliasing fonts with GTK1.2**

Thanks for this one, emersonfxbx.

> **emersonfxbx said:**
> 
It's possible to get antialiased fonts with gtk-1.2

check this site: [http://gdkxft.sourceforge.net](http://gdkxft.sourceforge.net)

Screenshot of nerolinux running with anti-aliased fonts (theme WindowMaker):

[http://br.geocities.com/emerson_freitas/nerolinux.png](http://br.geocities.com/emerson_freitas/nerolinux.png)


Havent tried that yet, but for those who doesnt like compiling anything found some deb packages:

[http://mirror.anl.gov/debian/pool/main/g/gdkxft/](http://mirror.anl.gov/debian/pool/main/g/gdkxft/)
[http://debian.mirror.frontiernet.net/debian/pool/main/g/gdkxft/](http://debian.mirror.frontiernet.net/debian/pool/main/g/gdkxft/)
[http://altruistic.lbl.gov/mirrors/debian/pool/main/g/gdkxft/](http://altruistic.lbl.gov/mirrors/debian/pool/main/g/gdkxft/)

there are all the same mirrors.
To be honest - havent tried that yet, but to use it on i386 architecture all you need to do is download for example:

[http://debian.mirror.frontiernet.net/debian/pool/main/g/gdkxft/libgdkxft0_1.5-4_i386.deb](http://debian.mirror.frontiernet.net/debian/pool/main/g/gdkxft/libgdkxft0_1.5-4_i386.deb)

install it by

```

sudo dpkg -i libgdkxft0_1.5-4_i386.deb
```

and that should do it.
Oh, these .debs are specifically for Debian, but stay calm, you can use it in Ubuntu, they will work.

If you're using GNOME, you may also want to download capplet gdkxft-capplet_1.5-4_i386.deb

This capplet allows you to edit gdkxft configuration file from within GNOME control-center.

Handy, isnt it?

If anything wont work, you may try emersonfxbx instructions for using it.
> **emersonfxbx said:**
> 
After install, you must edit the file /etc/gdkxft.conf and remove the comment on the first line.

To run a GTK 1.2 application with anti-aliased fonts you could use:

sh -c "LD_PRELOAD=/usr/lib/libgdkxft.so LANG=C application"


**5. Credits**

[LIST][*]salvadhor from forum.ubuntu.pl (for the main idea but his howto was far from complete)
[*]guys from this topic [http://ubuntuforums.org/showthread.php?t=26354](http://ubuntuforums.org/showthread.php?t=26354)
[*]especially felix.rommel whose font settings I used here
[*]emersonfxbx for info about gdkxft
[/LIST]

---

### Post by mtron on 2006-01-09
Very nice, thanks! 

Man, with warty it took me ages to figure out a way for doing this. A very nice guide.

---

### Post by limit223 on 2006-01-09
I followed exactly your guide and nothing change in my xmms look.
I'm looking for long time to change this big ugly fonts in xmms preference, so far I couldn't do anything. This is a shot with both xmms and gmplayer


PS And another thing: in  ~/.gtkrc.mine if you insert that line as: /usr/share/themes/Plastig/gtk/gtkrc and open up the file gtkrc from that path you'll find out that first line is:
pixmap_path "~/.themes/Plastig/gtk"

but following your guide  in ~/.themes/Plastig/gtk we don't have any file of this theme...
Probably would be more indicated to install the theme in home directory than in /usr/share/theme path or copy the theme in home directory or just modify that path...anyway...none of the solutions work for my xmms look.

---

### Post by _jB on 2006-03-18
thanks alot.. Not perfect but WAY better than before :D

---

### Post by Levez on 2006-03-20
Thanks so much **shin** - that looks so much better.  I don't use many gtk1.2 apps anymore, but it's really annoying when you come across one looking so hideous as they do by default.

**limit223** - I might have a solution.  Using the (very nice) Plastig theme, I edited /usr/share/themes/Plastig/gtk/gtkrc, changing the top line to point instead of ~/.themes/ to /usr/share/themes/Plastic/gtk/grkrc - in full.  That got it working for me.  If you still aren't getting the font look you want, try editing ~/.gtkrc.mine

Here is mine, edited to use the Bitstream Vera Sans font.

```
include "/usr/share/themes/Plastig/gtk/gtkrc"
style "default-text" {
       fontset = "-bitstream-bitstream vera sans-medium-r-*-*-12-*-*-*-*-*-iso8859-*,\
                  -bitstream-bitstream vera sans-medium-r-*-*-12-*-*-*-*-*-iso8859-*,\
                  -bitstream-bitstream vera sans-medium-r-*-*-12-*-*-*-*-*-iso8859-*,\
                  -bitstream-bitstream vera sans-medium-r-*-*-12-*-*-*-*-*-iso8859-*"
}
class "GtkWidget" style "default-text"

```

If you want to use another font, use the **xfontsel** program to generate your own font strings (as suggested by **Juippisi** on [this thread]("http://ubuntuforums.org/showthread.php?t=88508&highlight=gtk1.2+font").

Note: When I did so, it wouldn't let me change the font size in xfontsel.  Just alter it yourself manally after you paste it into your .gtkrc.mine -- in my case, I used 12.

---

### Post by Tamale on 2006-04-01
awesome.. thanks!

---

### Post by Whoopie on 2006-05-11
Hi,

first, thanks for your howto!!!

I have one question:
How can I change the color for the mouse-over button effect? It's nearly black here.

Thanks for helping.
Best regards,
Whoopie

---

### Post by Omnios on 2006-05-11
Amazing little how to it solved a magor peave with gtk that I had now it looks pretty.

> Back to work.
```
echo "include \"$HOME/.gtkrc.mine\"" > ~/.gtkrc-1.2-gnome2 gedit .gtkrc.mine
```

 Note: I had some problems with this because my terminal was in the directory that I untared the themes. A simple cd so the home directory " cd " solves this.

 Now to move on to another peave which is synaptic, it looks real ugy Im not shure if it is using gtk 1 or 2 but if it is using 1 how do I apply this how to to root. 
Edit: just did a sudo natilus and its ugy to so I think its a root thing. 

 Anyways thanks for the great how to.

---

### Post by shin on 2006-05-11
[QUOTE=Omnios]
 Now to move on to another peave which is synaptic, it looks real ugy Im not shure if it is using gtk 1 or 2 but if it is using 1 how do I apply this how to to root. 
Edit: just did a sudo natilus and its ugy to so I think its a root thing. [/QUOTE]

Synaptic is using gtk 2 and yeah it's root problem. Probably you downloaded some additional themes for gtk by means of gnome art downloader or you just put themes in your home directory. In that case if you run app with sudo or just root access it will use default theme. To change it - move everything that is in directory ~/.themes (as far as I remember) to /usr/share/themes (not sure about that too but if it exists, assume I remember correctly ;)).

To do that:

```
mv ~/.themes/* /usr/share/themes -rf
```

I hope that helps.

---

### Post by shin on 2006-05-11
[QUOTE=Whoopie]
How can I change the color for the mouse-over button effect? It's nearly black here.[/QUOTE]

This is probably some theme specific issue. Try using another theme for gtk.

---

### Post by Freddd on 2006-05-16
Does anyone know if this will work for rapidsvn?

---

### Post by prismatic7 on 2006-05-17
um...

what about

```
#sudo apt-get install gtk-engines-geramik
```

?

There's lots to choose from (in universe):

```


gtk-engines-begtk - BeOS-like theme for GTK+
gtk-engines-eazel - The Eazel GTK+ theme engine, including the Crux theme
gtk-engines-geramik - Geramik GTK1.x Theme
gtk-engines-geramik-data - Geramik GTK Theme bitmaps
gtk-engines-icegradient - Ice-Gradient theme for GTK+
gtk-engines-industrial - Flat-looking GTK+ 1.x engine from Ximian
gtk-engines-lighthouseblue - LighthouseBlue theme for GTK+ 1.2
gtk-engines-metal - Metallic theme for GTK+ 1.2
gtk-engines-mist - A flat theme for GTK+ 1.2
gtk-engines-mono - Mono theme for GTK+ 1.2
gtk-engines-notif - Motif-like theme for GTK+ 1.2
gtk-engines-pixmap - Pixmap-based theme for GTK+ 1.2
gtk-engines-qtpixmap - QtPixmap GTK1.x theming engine
gtk-engines-raleigh - GTK+ 2.0-like theme for GTK+ 1.2
gtk-engines-redmond95 - Windows-like theme for GTK+ 1.2
gtk-engines-thingeramik - ThinGeramik GTK1.x Theme
gtk-engines-thingeramik-data - ThinGeramik GTK Theme bitmaps
gtk-engines-thinice - ThinIce theme for GTK+ 1.2
gtk-engines-xenophilia - Customisable GTK+ engine with a plain look
gtk-smooth-themes - A set of themes for the Smooth GTK+ Engine
gtk-theme-switch - GTK+ theme switching utility

```

and you can uninstall them easily, unlike the compiled versions...

---

### Post by FISHERMAN on 2006-08-27
Is it possible to make this work on Xubuntu?

---

### Post by detyabozhye on 2006-08-27
Yes, it's a gtk setting, not a gnome setting.

---

### Post by maxter on 2006-10-18
it is possible a further configuration...
the qtpixmap engine obtain the widget colours from ~/.qt/qtrc

so using qtconfig (apt-get install qt3-qtconfig) it is possible to modify the color schemes of gtk aplications.

it a little bit strange thinking that to configure a gtk application, gtk must emulate qt that emulate gtk (2.0 of course) :-)

by the way.... this work!

---

### Post by Turin Turambar on 2006-11-16
Hey, thanks!!! This finally worked!!!!

---

### Post by emersonfxbx on 2006-11-25
It's possible to get antialiased fonts with gtk-1.2

check this site: [http://gdkxft.sourceforge.net](http://gdkxft.sourceforge.net)

To compile it on Ubuntu (I use the 6.10 version), you must have installed
xorg-dev and libgtk1.2-dev.

Once uncompressed the tarball, the following commands (must be run as root)  will build the library:

CPPFLAGS="-I/usr/include/freetype2" --configure --prefix=/usr --sysconfdir=/etc

make && make install

gtkxft_sysinstall -t

After install, you must edit the file /etc/gdkxft.conf and remove the comment on the first line.

To run a GTK 1.2 application with anti-aliased fonts you could use:

sh -c "LD_PRELOAD=/usr/lib/libgdkxft.so LANG=C application"

Screenshot of nerolinux running with anti-aliased fonts (theme WindowMaker):

[http://br.geocities.com/emerson_freitas/nerolinux.png](http://br.geocities.com/emerson_freitas/nerolinux.png)


PS.: sorry the errors, but english is not my native language...

---

### Post by shin on 2006-11-26
Thanks a lot emersonfxbx. Will try that. HOWTO already updated thanks to your info.

---

### Post by ironphil on 2007-01-04
Thanks emersonfxbx, that did it almost perfectly. Just a few things. On my system, the line:
```
CPPFLAGS="-I/usr/include/freetype2" --configure --prefix=/usr --sysconfdir=/etc
```
Should be:
```
env CPPFLAGS="-I/usr/include/freetype2" ./configure --prefix=/usr --sysconfdir=/etc
```
And the line
```
gtkxft_sysinstall -t
```
Should be:
```
gdkxft_sysinstall -t
```

After that, it seems to work if I launch an application the way you described:
```
sh -c "LD_PRELOAD=/usr/lib/libgdkxft.so LANG=C application"
```

Now, how can I change the font that is used be gdkxft? My applications do not look like your Nero screenshot and I cannot find where I can change the fonts used by gtk 1.2 apps. Thanks again.

---

### Post by emersonfxbx on 2007-01-17
> **ironphil said:**
> Thanks emersonfxbx, that did it almost perfectly. Just a few things. On my system, the line:
```
CPPFLAGS="-I/usr/include/freetype2" --configure --prefix=/usr --sysconfdir=/etc
```
Should be:
```
env CPPFLAGS="-I/usr/include/freetype2" ./configure --prefix=/usr --sysconfdir=/etc
```
And the line
```
gtkxft_sysinstall -t
```
Should be:
```
gdkxft_sysinstall -t
```

After that, it seems to work if I launch an application the way you described:
```
sh -c "LD_PRELOAD=/usr/lib/libgdkxft.so LANG=C application"
```

Now, how can I change the font that is used be gdkxft? My applications do not look like your Nero screenshot and I cannot find where I can change the fonts used by gtk 1.2 apps. Thanks again.

Hi,

In the beginning of the thread, "shin" instructs how to change the font of GTK1.2 apps. Just edit the file ~/.gtkrc. I did that way.
And don't forget to uncomment out the first line of the file /etc/gdkxft.conf (remove the exclamation mark "!").

PS.:
Sorry again. I promise I will take an  english course on the next vacations :biggrin:

---

### Post by NTolerance on 2007-05-07
Unfortunately changing the GTK1 theme causes apps not to render when Desktop Effects are enabled.

---

### Post by alexgieg on 2007-12-23
I'd love to know whether doing the reverse procedure, i.e., making a GTK1.2 app (such as Synaptic) adopt a GTK2.0 look and feel, is possible. That's because I've installed the LiNsta theme and everything looks perfect, except for older GTK1.2 apps, who now show the standard GTK1.2 theme.

---

### Post by K.Mandla on 2008-01-01
I don't know for sure, but I have a feeling that changing an application from GTK1.2 to GTK2 would require recompiling at the least, and possibly recoding it. 

There might be a revision of a GTK1.2 application that does that -- for example, there's [sylpheed-gtk1]("http://packages.ubuntu.com/gutsy/mail/sylpheed-gtk1") and [sylpheed]("http://packages.ubuntu.com/gutsy/mail/sylpheed"), or [emelfm]("http://packages.ubuntu.com/gutsy/utils/emelfm") and [emelfm2]("http://packages.ubuntu.com/hardy/x11/emelfm2"). Both are vast improvements, visually.

---

### Post by ~LoKe on 2008-01-02
Heh, I never really knew why gmplayer didn't follow the gtk2 themes.  Now I know.

So...is there a way to recompile gmplayer to support gtk2 themes or would it require a complete re-write?

---

### Post by AnoPoli on 2009-08-22
While the problem still exists in 2009 and ubuntu 9.04 lets solve it!!
I have to say that none of the utilities solved the problem with GTK in
that recent version of ubuntu, at least for me. So we will solve it the
Linux way :) --> Does the word "manually" means anything to you? :)
No big deal at all. Just a few easy steps.
1) Download the GTK-1 theme "Industrial" from gnome-look.org
2) Untargunzipit to your /usr/share/themes folder, so at the end you have an
"Industrial" folder with 2 sub folders "GTK" and "GTK-2.0
3) sudo gedit /etc/gtk/gtkrc.utf-8
4) make it look like this:
include "/usr/share/themes/Industrial/gtk/gtkrc"
style "default-text" {
       fontset = "-*-verdana-medium-r-normal--*-80-*-*-*-*-utf-8,\
       		  -*-helvetica-medium-r-normal--*-80-*-*-*-*-*-*"
}

class "GtkWidget" style "default-text"
5) Done! Run your GTK-1 app and feel free to cry out if you like :-P
-----------
NOTE
-----------
I am using Hellenic Localization, and i'm always changing all the fonts
from the GTK-2.0 default ubuntu theme to verdana and size 8. This gives me a very pleasant experience. Try it out and you 'll see. That's why
i'm replacing the "fontset=" above with verdana. This way i have a complete ubuntufied theme, also for GTK-1 apps (like ePSXe).
You can change the font to anything you 're using with your theme.
If you don't have Verdana:
"sudo apt-get install msttcorefonts"
or you can have it from your other WindowsXP partition (if you have one).
P.S.
I REALLY like the default ubuntu theme and especially the colors of it.
Good luck!!!

---

### Post by Drainouri on 2012-06-11
lo que yo queria, gracias

---

