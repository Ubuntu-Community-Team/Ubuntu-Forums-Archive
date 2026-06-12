---
title: "gtk2 themes in gtk3 apps aka menu's not working in calculator app."
date: 2015-12-22
forum: Ubuntu Development Version
---

### Post by matt_symes on 2015-12-22
Is anybody else unable to change the calculator app's mode ? 

Every time i try to change it from basic to advanced (or any of the other modes), nothing happens. Same with the top left hand menu.

I'm using xub with all the dev ppa. Is anybody else having the same problem in xub, ub, lub or any other flavour ?

---

### Post by sammiev on 2015-12-22
16o4 is working as should with lubuntu.

---

### Post by sammiev on 2015-12-22
Tried it on Ubuntu-gnome and no issues.

---

### Post by matt_symes on 2015-12-22
Thanks sammiev. That's two down.

BTW. This xub install was from a daily iso, dev ppas added and then updated every day since.

It's been pretty stable apart from wifi that drops the connection perhaps once a day or so.

---

### Post by sammiev on 2015-12-22
Well it seems Unity doesn&#8217;t work. There isn't even a menu to select from basic to advanced.

Actually, no menu what so ever.  :(

---

### Post by matt_symes on 2015-12-22
> **sammiev said:**
> Well it seems Unity doesn&#8217;t work. There isn't even a menu to select from basic to advanced.

Actually, no menu what so ever.  :(

Interesting. Thanks sammiev.

This is what i'm seeing but it's not working.

Kind regards

---

### Post by sammiev on 2015-12-22
I see that same menu with Ubuntu-gnome but it works.

I should of added : I have no other 16o4 flavors installed but the above. :(

---

### Post by matt_symes on 2015-12-22
> **sammiev said:**
> I see that same menu with Ubuntu-gnome but it works.

I'll install the daily xub iso and see if i get the same issue.

Thanks for looking at this sammiev.

---

### Post by sammiev on 2015-12-22
I will download it as well, might as well add one more for testing.

---

### Post by MikeMecanic on 2015-12-22
Works fine on xubuntu Dec.21st build.

---

### Post by matt_symes on 2015-12-22
> **MikeMecanic said:**
> Works fine on xubuntu Dec.21st build.

Thanks. It may just be my install.

I'm currently installing the last xub daily. I'll test it there then add the dev ppas and test again.

---

### Post by matt_symes on 2015-12-22
I think this may be a problem with themes.

install the daily iso, (i then installed the dev ppas but this may not matter) change the theme to numix and the calc menu's are not working. infact calc is almost invisible :)

---

### Post by matt_symes on 2015-12-22
seems you do need to install the devs ppas.

install daily iso -> update/upgrade -> add the 3 dev ppas -> update/upgrade -> (reboot maybe) -> start calc app from menu -> switch to numix theme from settings -> appearance.

Anybody else in a position to test that ?

I'll try to narrow down which ppa tomorrow.

I use calc :)

---

### Post by sammiev on 2015-12-22
> **matt_symes said:**
> Thanks. It may just be my install.

I'm currently installing the last xub daily. I'll test it there then add the dev ppas and test again.

Seems to be working fine as posted above with the fresh install of Xubuntu.

It maybe one of the dev ppas.

---

### Post by matt_symes on 2015-12-22
> **sammiev said:**
> Seems to be working fine as posted above with the fresh install of Xubuntu.

It maybe one of the dev ppas.

Any chance you could add these ppas

```
ppa:xubuntu-dev/ppa
ppa:xubuntu-dev/xubuntu-staging
ppa:shimmerproject/daily
```

update and upgrade and start calc and try the numix theme ?

You may need to reboot (try it without rebooting first). I think it may be the last ppa on that list.

---

### Post by sammiev on 2015-12-23
Will look at it in the am, it 00:45 here. Need a few zzzzz's :)

---

### Post by flocculant on 2015-12-23
yup - borked in numix with the up to date ppa 

you'll see the same in catfish - and I guess any gtk3 app

edit - and  for the up to date news, if it doesn't work and there are no patches, it's probably not going to make release

---

### Post by matt_symes on 2015-12-23
> **flocculant said:**
> yup - borked in numix with the up to date ppa 

you'll see the same in catfish - and I guess any gtk3 app

edit - and  for the up to date news, if it doesn't work and there are no patches, it's probably not going to make release

Thanks flocculant.

I originally noticed it in the theme i am using, which is a great theme from the xfce-look website.

So it's a gtk2->3 transitional effect.

---

### Post by MikeMecanic on 2015-12-23
> **MikeMecanic said:**
> Works fine on xubuntu Dec.21st build.

I must say that to achieve stability, I made a second fresh install immediately after the first one.  
When I have 2-3 bugs on post-installation in the first 20-25 minutes, I always do a second installation.  I learned that from experience.
Knowing that the xub December 19th build was a buggy one, that's what I did Monday: 2 installations back to back (LVM default configuration) in less then 30 minutes.
I'm now running a stable installation on Kernel 4.4 rc6, XFCE default.


P.S.:  Bugs or problems are always related to desktop environment instability on post-installation.


Regards,

---

### Post by zika on 2015-12-23
> **MikeMecanic said:**
> I must say that to achieve stability, I made a second fresh install immediately after the first one.  
When I have 2-3 bugs on post-installation in the first 20-25 minutes, I always do a second installation.  I learned that from experience.
Knowing that the xub December 19th build was a buggy one, that's what I did Monday: 2 installations back to back (LVM default configuration) in less then 30 minutes.
I'm now running a stable installation on Kernel 4.4 rc6, XFCE default.


P.S.:  Bugs or problems are always related to desktop environment instability on post-installation.


Regards,Full installations or just update/upgrade cycle? If it's first how do You support/explain that habbit of Yours? Any SW/HW (except some faults in net/hdd...) facts to support/explain that? ;)

---

### Post by flocculant on 2015-12-23
maybe a theme issue/gtk3/graphic driver combo going on

anyway - the long and short is that if we don't see patches from the one working with numix, then we will drop it from 16.04

---

### Post by flocculant on 2015-12-23
> **matt_symes said:**
> Thanks flocculant.

I originally noticed it in the theme i am using, which is a great theme from the xfce-look website.

So it's a gtk2->3 transitional effect.

yep - seems so

thanks for bringing it up - it reminded me :)

---

### Post by sammiev on 2015-12-23
I never tried it after reading flocculant post this morning and have been using my computer to burn DVD's all day.

Its that time of the year. :)

---

### Post by Image on 2015-12-23
> **sammiev said:**
> Well it seems Unity doesn’t work. There isn't even a menu to select from basic to advanced.

Actually, no menu what so ever.  :(

Same result here. No menu what so ever. Not even a maximize button.

---

### Post by P-I H on 2015-12-23
Strange,
gnome-calculator works fine on my system with Unity.

However I'm using padoka PPA and this kernel [http://phoronix.net/downloads/linux-image-4.4.0-rc3-4.5-next-phx-xmas_4.4.0-rc3-4.5-next-phx-xmas-1_amd64.deb](http://phoronix.net/downloads/linux-image-4.4.0-rc3-4.5-next-phx-xmas_4.4.0-rc3-4.5-next-phx-xmas-1_amd64.deb)

---

### Post by flocculant on 2015-12-23
might want to get a mod involved in the thread to make the title more specific :)

---

### Post by matt_symes on 2015-12-23
> **flocculant said:**
> might want to get a mod involved in the thread to make the title more specific :)

:lolflag:

> menu's not working for calculator app (maybe others). gtk2->gkt3 theme / app issue 

Better ?

Trying to work out how to change the post titles after post #1.

---

### Post by flocculant on 2015-12-23
Personally - I would 'gtk2 themes in gtk3 apps' or something - what do I know :)

pm sent

---

### Post by MikeMecanic on 2015-12-23
> **zika said:**
> Full installations or just update/upgrade cycle? If it's first how do You support/explain that habbit of Yours? Any SW/HW (except some faults in net/hdd...) facts to support/explain that? ;)

  [FONT=&amp]First, it takes 5-7 minutes to complete a fresh install but trying debugging a faulty one can take hours. [/FONT]
 

  [FONT=&amp]For me, the main goal of a fresh install is to achieve stability with the latest ISO image.  Sometimes it works, sometimes it doesn’t.  [/FONT]

  
  [FONT=&amp]Errors generated by Apport and bugs are usually indicators that the hard disk might be unhealthy. [/FONT]
  [FONT=&amp]My habit of doing a second fresh install comes from the fact that I have a strong feeling that the installer didn't do his work properly.  [/FONT]
  
  [FONT=&amp]On my second installation, bugs or errors that I’ve encountered previously are gone once and for all. If I don’t do that it becomes time consuming and takes a lot of energy.  [/FONT]
  
  
  [FONT=&amp]Take care,[/FONT]

---

### Post by matt_symes on 2015-12-23
> **flocculant said:**
> Personally - I would 'gtk2 themes in gtk3 apps' or something - what do I know :)

pm sent

done.

pm sent back :)

---

### Post by Smask on 2015-12-25
So maybe that's why I got Indicator-panel-complete spamming my syslog with:

```
org.gnome.panel.applet.IndicatorAppletCompleteFactory[1299]: (indicator-applet-complete:1708): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
org.gnome.panel.applet.IndicatorAppletCompleteFactory[1299]: (indicator-applet-complete:1708): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
```

---

