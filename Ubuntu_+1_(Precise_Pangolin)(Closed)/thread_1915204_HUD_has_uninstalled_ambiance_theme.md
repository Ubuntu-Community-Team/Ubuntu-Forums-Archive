---
title: "HUD has uninstalled ambiance theme"
date: 2012-01-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by the_blue_box on 2012-01-25
Hi,
I wanted to try out the new HUD menu :D so I installed the PPA etc.

But when I logged back in, the HUD was there and working, but I no ambiance :(
According to the User Interface theme settings I now only have: Adwaita, High Contrast and High Contrast inverse.

I have no idea what has happened.
I hope there is a simple way to get ambiance back ie reinstalling it, but I have Googled around and can't seem to find how to do it :(

Any help would be great :)

Thanks in advance

---

### Post by go7Ul1ai on 2012-01-25
Sounds like you did a partial upgrade without looking at what packages would be removed

---

### Post by the_blue_box on 2012-01-25
Well that would make sense apart from the fact that it didn't say it was going to remove anything.

Anyway I just want ambiance back :(

---

### Post by mc4man on 2012-01-25
> **the_blue_box said:**
> Well that would make sense apart from the fact that it didn't say it was going to remove anything.

Anyway I just want ambiance back :(

Well ambiance is in the light-themes package, check if it's installed

---

### Post by kansasnoob on 2012-01-25
Is ambiance truly no longer installed?

I'm trying HUD just to have a look and I didn't encounter that, but about a week ago I found some themes just no longer working:

[http://ubuntuforums.org/showpost.php?p=11620274&postcount=353](http://ubuntuforums.org/showpost.php?p=11620274&postcount=353)

I suspect there's some gtk borkage going on since this old installer bug resurfaced:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/830923](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/830923)

But I'm truly clueless.

---

### Post by MacUntu on 2012-01-25
Probably did a partial upgrade, did you?

Yes, you did! I know, because I just did the same (sh*t happens :D):

That's what got removed here. Try to reinstall 'ubuntu-desktop' at a later time.

```
  gtk2-engines-murrine ia32-libs ia32-libs-multiarch:i386
  libasound2-plugins:i386 libpulse-mainloop-glib0:i386 libpulse0:i386
  libpulsedsp:i386 libsdl-image1.2:i386 libsdl-mixer1.2:i386
  libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 light-themes
  skype ubuntu-artwork ubuntu-desktop wine wine1.3
```

---

### Post by the_blue_box on 2012-01-25
> **mc4man said:**
> Well ambiance is in the light-themes package, check if it's installed
Agggg! no it's not installed and when I try to install it (though Synaptic) I get...

```
Depends: gtk2-engines-murrine but it is not going to be installed
```

So I'm guessing that "gtk2-engines-murrine" must have upgraded when I installed HUD.
Any clue as to how I fix this?

---

### Post by MacUntu on 2012-01-25
Run ```
sudo apt-get install ubuntu-desktop
``` &#8594; that worked fine for the themes here (couldn't reinstall the ia32-libs, though).

---

### Post by the_blue_box on 2012-01-25
Ah :) Thanks MacUntu :) I only just saw your first post.

```
sudo apt-get install ubuntu-desktop
```
Did the trick 
Thanks again :)

---

### Post by frankzen on 2012-01-28
So, did you keep HUD when you re-installed ubuntu-desktop ?

---

### Post by the_blue_box on 2012-01-30
Yes I did and everything is working without a problem so far.

---

