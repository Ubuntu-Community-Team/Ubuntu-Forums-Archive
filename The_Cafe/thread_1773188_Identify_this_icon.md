---
title: "Identify this icon"
date: 2011-06-01
forum: The Cafe
---

### Post by hhh on 2011-06-01
[[img]http://s4.postimage.org/25ir6ltno/Screenshot_05312011_09_02_33_PM.png[/img]](http://www.postimage.org/)

I use xfce4-notifyd for notifications and this icon appears when the "Downloads complete" popup appears. It clashes horribly with my [carefully customized]("http://s4.postimage.org/5ctz2bdkt/Screenshot_05312011_09_02_33_PM.png") desktops. It looks very similar to the Gnome icon-set download icon, but that's not it. It's not part of Tango either, as far as I can see, nor hicolor. I can't find it in /usr/share/app-install/icons or /usr/share/pixmaps. The only other icon themes I have are Clarity and Any Color You Like, and it surely isn't part of those sets.

Does anyone recognize this fiendishly-difficult-for-me-to-locate icon?

---

### Post by Macskeeball on 2011-06-01
0 results on TinEye.

---

### Post by Larkspur on 2011-06-01
I'm pretty sure it's the Firefox download icon.  It looks the same as the one in the "Customize" dialogue, anyway.

---

### Post by hhh on 2011-06-01
I was thinking that too, though that seems very strange. That icon would be packaged in a .jar file, wouldn't it? I do use Iceweasel 4.0.1 from mozilla.debian.net, but I haven't found the icon anywhere yet. I guess I can temporarily purge Iceweasel and see if the icon still appears. Thanks for the guess.

Yeah, I checked TinEye first thing.

---

### Post by Aquix on 2011-06-01
It's the Firefox downloads icon. I use it right now since my internet speed is reduced and unstable, and I need to continue downloads. I usually use the 'download statusbar' extension. You can set it to disappear when downloads are complete.

I'm not sure if its firefox native. I also have the toolbar buttons extension.

---

### Post by Legendary_Bibo on 2011-06-01
Hey at least you're not in the situation I am and can't seem to find your entire Faenza icon directory. I installed the Cupertino one as well because I wanted blue folders. I've looked in every possible directory the icons would be in, and no luck.

---

### Post by jerrrys on 2011-06-01
if it turns out not being firefox; what theme are you running?

---

### Post by hhh on 2011-06-01
@Bibo, icons can only be in /usr/share/icons or ~/.icons. If they're not there then you moved them to another folder by mistake. You can use Catfish for a search front end.

@jerry, I use Clarity icons, they use a template.svg file that you can add your own color values to and then run an included "change_theme" script.

OK, marking this solved... it is the Firefox download icon. I just downloaded a Knoppix iso via Transmission and the Transmission icon from /usr/share/pixmaps showed up. I guess I can't customize the Firefox icon without opening up browser.jar or some such file. I'll experiment a bit but it's no big deal. Thanks for the help, all.

---

### Post by Legendary_Bibo on 2011-06-01
> **hhh said:**
> @Bibo, icons can only be in /usr/share/icons or ~/.icons. If they're not there then you moved them to another folder by mistake. You can use Catfish for a search front end.

@jerry, I use Clarity icons, they use a template.svg file that you can add your own color values to and then run an included "change_theme" script.

OK, marking this solved... it is the Firefox download icon. I just downloaded a Knoppix iso via Transmission and the Transmission icon from /usr/share/pixmaps showed up. I guess I can't customize the Firefox icon without opening up browser.jar or some such file. I'll experiment a bit but it's no big deal. Thanks for the help, all.

OMG! They were in ~/.icons thank you!

I had no idea that folder existed.

---

### Post by Tibuda on 2011-06-01
> **Legendary_Bibo said:**
> OMG! They were in ~/.icons thank you!

I had no idea that folder existed.

it is a hidden for a reason :lolflag:

---

### Post by hhh on 2011-06-02
VICTORY IS MINE!!!

[[img]http://s3.postimage.org/5i991txg/Screenshot_06022011_04_29_25_PM.jpg[/img]](http://postimage.org/image/5i991txg/)

That was. Freaking. Hard! Doubt I'll be doing that everytime I create a new theme, but it was fun solving the problem.

Thanks again for the help and your welcome, Bibo.

---

### Post by koleoptero on 2011-06-02
Persistence wins :D

---

### Post by forrestcupp on 2011-06-02
> **hhh said:**
> It clashes horribly with my [carefully customized]("http://s4.postimage.org/5ctz2bdkt/Screenshot_05312011_09_02_33_PM.png") desktops.

The Last Samurai is awesome.

---

