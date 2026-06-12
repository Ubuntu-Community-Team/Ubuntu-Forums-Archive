---
title: "Fonts looking bad in ubuntu?"
date: 2007-02-22
forum: The Cafe
---

### Post by timpino on 2007-02-22
I've been trying different OS's and always thought that Ubuntu (among others) have really ugly fonts, they simply do not look crisp and nice. However PCLinuxOS does seem to have really nice fonts. Why is that? do they use some proprietary fonts or are they just better at rendering fonts?

---

### Post by shining on 2007-02-22
After looking at several font related thread, it turns out that fonts looking "bad", or "not crisp and nice" doesn't mean anything at all. A bit like colors, it's just a matter of taste.
Maybe your preference goes to microsoft fonts, and pclinux os is using these, with antialiasing disabled.
It's hard to tell without having access to a pclinuxos system. Just a screenshot would already help. Then, what is in the kde fonts configuration panel. And to have all the details, directly at the config files : system-wide in /etc/fonts/ and user wide, the ~/.fonts* files.

---

### Post by anaconda on 2007-02-22
automatix can install windows fonts for you if you prefer them..

---

### Post by timpino on 2007-02-22
here is a screenshot with the fonts config open, seems to be the sans serif font at 96 dpi and anti aliasing turned on, though other fonts look awesome aswell, might they have better antialiasing (to my liking that is)

Off topic:

What is beans? everybody's got like 7000 and i've got 0 :(

---

### Post by ~LoKe on 2007-02-22
Fonts are fine once you adjust to 'em.

---

### Post by Erunno on 2007-02-22
Nevertheless, this is a major problem as most people will expect "good looking" fonts out of the box. Since Ubuntu is targeted at a rather non-technical audience forcing the user to hunt down information on the internet in order to have fonts that look at least as good as on Windows out of the box is a big no-no.

On a sidenote: The situation on Kubuntu is even more dire, the default fonts look terrible, especially the rendering of small fonts and no amount of tinkering has made them similar in quality to Mircosoft's fonts on my computer yet.

---

### Post by Brunellus on 2007-02-22
> **Erunno said:**
> Nevertheless, this is a major problem as most people will expect "good looking" fonts out of the box. Since Ubuntu is targeted at a rather non-technical audience forcing the user to hunt down information on the internet in order to have fonts that look at least as good as on Windows out of the box is a big no-no.

On a sidenote: The situation on Kubuntu is even more dire, the default fonts look terrible, especially the rendering of small fonts and no amount of tinkering has made them similar in quality to Mircosoft's fonts on my computer yet.
This is a question of taste and conditioning.  I find Ubuntu's fonts nonobjectionable.

Oddly, I find that I like Ubuntu's anti-aliased fonts *much more* than I like Microsofts anti-aliased fonts on XP.  On the other hand, without anti-aliasing, Microsoft's fonts look better .  If your idea of "major problem" with the OS is typography. . . well, you haven't seen "major" yet.

Hauling it back on default fonts:  I wish ubuntu would ship with a nicer default console font, though.  I've taken to changing mine from fixedsys to terminus, and find that I *love* terminus.  I suppose it's not something any of the devs think about, since so few people in Ubuntu ever leave X, judging from the panic that X breakage seems to spark.

---

### Post by Erunno on 2007-02-22
I never had personally any problems with the default fonts and the rendering on Ubuntu but I remember a case when someone looked over my shoulder while I was runnung Ubuntu/GNOME and asked me why the fonts looked so blurred. Granted, this is anectodal evidence and it's difficult to judge whether this perception is representative for the majority of the user base but from the internets I got the impression that font rendering seems suboptimal to many users on Linux. And about the conditioning: Almost everybody who's coming to Linux is a former windows user so that's the standard they'll compare fonts on linux to.

---

### Post by karellen on 2007-02-22
fonts are not a big problem. they can be adjusted to look the way you want. using linux I found out I really like fonts like nimbus sans or dejavu sans :)

---

### Post by Brunellus on 2007-02-22
> **Erunno said:**
> I never had personally any problems with the default fonts and the rendering on Ubuntu but I remember a case when someone looked over my shoulder while I was runnung Ubuntu/GNOME and asked me why the fonts looked so blurred. Granted, this is anectodal evidence and it's difficult to judge whether this perception is representative for the majority of the user base but from the internets I got the impression that font rendering seems suboptimal to many users on Linux. And about the conditioning: Almost everybody who's coming to Linux is a former windows user so that's the standard they'll compare fonts on linux to.
and while we're at it, we can implement a registry, full binary windows compatibility, and BonziBuddy.  And we can give every new user a pony to go with their shipit cds.

I think a lot of it is that Windows users don't use anti-aliased fonts, by and large.  I remember when my office rolled out WinXp, and I turned on anti-aliasing.  I *hated* it, and turned it right off *immediatly*.  

Funnily enough, I  went right home and sat in front of my anti-aliased GNOME desktop and loved it.  

Weird.

---

### Post by steve101101 on 2007-02-22
I agree with the Kubuntu fonts. I am running Kubuntu on my ps3 and can barely read them. I am going to swith to Ubuntu because im more used to it and the fonts always were easier to read.

---

### Post by Anthem on 2007-02-22
> **timpino said:**
> What is beans? everybody's got like 7000 and i've got 0 :(
"beans" is your post count.

Posts in the Cafe don't count... only posts in technical forums.

---

### Post by timpino on 2007-02-22
> **Anthem said:**
> "beans" is your post count.

Posts in the Cafe don't count... only posts in technical forums.

Ah, I see, so I'm being punished for liking the flimsyness of the Café :)

On Fonts: It seems this is more or less a question of taste. I seem to enjoy the more heavily anti-aliased fonts since i'm running a 15'' monitor at 1600x1200 and need the fonts to be a bit bolder, but not bold :)

---

### Post by ice60 on 2007-02-22
i always put a .fonts.conf file in my home directory to make my fonts look better. this is what i have in mine right now -

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```

try saving that as .fonts.conf and see if it helps :confused:

edit. log out and back in again for it to work i think.

---

