---
title: "Xubuntu 18.04: system load monitor question"
date: 2018-02-27
forum: Ubuntu Development Version
---

### Post by vasa1 on 2018-02-27
What does increasing or decreasing "Power-saving interval" do in the System Load Monitor?

---

### Post by kerry_s on 2018-02-27
it's an on/off thing, like the sleep command.

---

### Post by kerry_s on 2018-02-27
so i how does it feel to you?

i tried xubuntu 18 a few nights ago, felt a bit slower than previous versions. probably just me. ;)

---

### Post by vasa1 on 2018-02-27
> **kerry_s said:**
> it's an on/off thing, like the sleep command.
In that case, there would only be an on/off option. By pressing "+/-", I can increase'decrease the interval.
> **kerry_s said:**
> so i how does it feel to you?

i tried xubuntu 18 a few nights ago, felt a bit slower than previous versions. probably just me. ;)
I last used it during 12.10. At that time, a lot more applications were gtk2. I guess moving over to gtk3 may have some overhead.

---

### Post by kerry_s on 2018-02-27
yeah, it feels like xfce is just stuck. it's exactly like it was back then. i'm sure there's work going on but not really anything you can see.

---

### Post by flocculant on 2018-02-27
> **kerry_s said:**
> yeah, it feels like xfce is just stuck. it's exactly like it was back then. i'm sure there's work going on but not really anything you can see.

More has been done in Xfce than we're seeing in Xubuntu, not wanting to bring in newer gtk3 versions right at the start of the next LTS basically.

[https://wiki.xfce.org/releng/4.14/roadmap](https://wiki.xfce.org/releng/4.14/roadmap)

If you're interested in what I see in Xubuntu -

[https://launchpad.net/~shimmerproject/+archive/ubuntu/daily?field.series_filter=bionic](https://launchpad.net/~shimmerproject/+archive/ubuntu/daily?field.series_filter=bionic)
[https://launchpad.net/~xubuntu-dev/+archive/ubuntu/experimental?field.series_filter=bionic](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/experimental?field.series_filter=bionic)
[https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa?field.series_filter=bionic](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa?field.series_filter=bionic)

---

### Post by wildmanne39 on 2018-02-27
Thanks flocculant, I will check out the new themes now that I have xubuntu 18.04 installed.

---

### Post by vasa1 on 2018-02-27
> **flocculant said:**
> ...
[https://launchpad.net/~shimmerproject/+archive/ubuntu/daily?field.series_filter=bionic](https://launchpad.net/~shimmerproject/+archive/ubuntu/daily?field.series_filter=bionic)
...
So they've brought back Blackbird? IIRC, there was a time they dropped it.

---

### Post by slickymaster on 2018-02-28
Backbird has been some what neglected but it's a fabulous theme. One of my favorites.

---

### Post by flocculant on 2018-02-28
> **wildmanne39 said:**
> Thanks flocculant, I will check out the new themes now that I have xubuntu 18.04 installed. No problem :)

> **vasa1 said:**
> So they've brought back Blackbird? IIRC, there was a time they dropped it. It's not actually in the default Xubuntu install afaik

> **slickymaster said:**
> Backbird has been some what neglected but it's a fabulous theme. One of my favorites.You'd think as someone in Xubuntu Team - you'd at least get the name right, just wait till I catch you in #x-dev ;)

---

### Post by slickymaster on 2018-03-01
> **flocculant said:**
> .....

You'd think as someone in Xubuntu Team - you'd at least get the name right, just wait till I catch you in #x-dev ;)

:lolflag:

No fast typing will go unpunished :p

---

### Post by vasa1 on 2018-03-01
> **flocculant said:**
> ...

 It's not actually in the default Xubuntu install afaik
...
Thanks! I got something using *sudo apt-get install blackbird-gtk-theme*. And its gtk3 theme is still the old-fashioned one without the compiled stuff. I don't know if it's by the Xubuntu team.

```
/usr/share/themes/Blackbird/gtk-3.0$ ls
apps  assets  gtk.css  gtk-widgets-assets.css  gtk-widgets-backdrop.css  gtk-widgets.css  settings.ini
/usr/share/themes/Blackbird/gtk-3.0$ 
```
Whereas Greybird has```
/usr/share/themes/Greybird/gtk-3.0$ ls
apps                 _common.scss      gtk-contained.css        gtk.css            _lightdm-gtk-greeter.scss  settings.ini
assets               _drawing.scss     gtk-contained-dark.css   gtk-dark.css       _others.scss               _unity.scss
_colors-public.scss  Gemfile           gtk-contained-dark.scss  gtk.gresource      parse-sass.sh              _xfce.scss
_colors.scss         _gnome-apps.scss  gtk-contained.scss       gtk.gresource.xml  README
/usr/share/themes/Greybird/gtk-3.0$ 
```

---

### Post by slickymaster on 2018-03-01
> **vasa1 said:**
> Thanks! I got something using *sudo apt-get install blackbird-gtk-theme*. And its gtk3 theme is still the old-fashioned one without the compiled stuff. I don't know if it's by the Xubuntu team.

```
/usr/share/themes/Blackbird/gtk-3.0$ ls
apps  assets  gtk.css  gtk-widgets-assets.css  gtk-widgets-backdrop.css  gtk-widgets.css  settings.ini
/usr/share/themes/Blackbird/gtk-3.0$ 
```
Whereas Greybird has```
/usr/share/themes/Greybird/gtk-3.0$ ls
apps                 _common.scss      gtk-contained.css        gtk.css            _lightdm-gtk-greeter.scss  settings.ini
assets               _drawing.scss     gtk-contained-dark.css   gtk-dark.css       _others.scss               _unity.scss
_colors-public.scss  Gemfile           gtk-contained-dark.scss  gtk.gresource      parse-sass.sh              _xfce.scss
_colors.scss         _gnome-apps.scss  gtk-contained.scss       gtk.gresource.xml  README
/usr/share/themes/Greybird/gtk-3.0$ 
```

Even though they are members of both teams, Blackbird is maintained by the Shimmer Project team.

---

### Post by vasa1 on 2018-03-02
Regarding the original point, I could find this:>  Added a power-saving interval option using upower (if present at build time)from [http://goodies.xfce.org/projects/panel-plugins/xfce4-systemload-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-systemload-plugin). So it's been there since 2012.

---

