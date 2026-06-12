---
title: "Why aren't Ubuntu's font-rendering patches standard upstream?"
date: 2011-09-28
forum: The Cafe
---

### Post by ninjaaron on 2011-09-28
They provide much better rendering than any other non-ubuntu-based distro.  In every other distro, I have "do something about the fonts" before it's really usable, and that "something" is usually applying the Ubuntu patches.  Infinaltiy is also alright, but it's buggy, and it's not like any distro comes with it built in.

I can't really see how anyone could prefer the standard freetype2, libxft, and libcairo packages over those in Ubuntu.  Some people do hate anti-aliasing, but it can be turned off either way, and if your going to have it, it might as well be smooth, like in Ubuntu.

So, why aren't the Ubuntu patches standard?


*Note:  These observations are based on Arch, Debain, and Fedora, three of the most popular distros that aren't based on Ubuntu.  I haven't tried OpenSUSE, so maybe it's better.  Font's also look good in Chrome OS, but I believe there is some Ubuntu backending invloved in that, as well as a special version of cleartype.*

---

### Post by kaldor on 2011-09-28
I agree. Ubuntu has the best out of the box readability of any distro I've ever used. Fedora 15 is pure ugly by default without messing around.

I also think the Ubuntu font family should be standardized for GNOME. It's much more readable than Cantarell.

---

### Post by el_koraco on 2011-09-28
> **ninjaaron said:**
> 
So, why aren't the Ubuntu patches standard?


i think it's blowing their own horn. Nowadays, Debian doesn't have the patch because the upstream devs don't want it. Fedora is served by infinality, so I guess they're ok with it. I mean, did you see the discussions in the Debian forums regarding the issue? You get guys pretty much likening patched versions of libcairo to the devil. And the guides with the excuse "some people find it hard to get used to the sharp fonts". 

lolol

Dejavu Sans with the patches for Firefox, bitmap for everything else and you're good.

---

### Post by XubuRoxMySox on 2011-09-28
[satire]
They reject Ubuntu's contributions so they can continue to whine about Ubuntu "not contributing to Linux."
[/satire]

---

### Post by ninjaaron on 2011-09-28
> **el_koraco said:**
> i think it's blowing their own horn. Nowadays, Debian doesn't have the patch because the upstream devs don't want it. Fedora is served by infinality, so I guess they're ok with it. I mean, did you see the discussions in the Debian forums regarding the issue? You get guys pretty much likening patched versions of libcairo to the devil. And the guides with the excuse "some people find it hard to get used to the sharp fonts". 

lolol

Dejavu Sans with the patches for Firefox, bitmap for everything else and you're good.

Infinality is certainly a vast improvement on standard Linux font rendering, but it still doesn't come standard in Fedora or any other distro, as far as I'm aware.  In Arch, the "Beginners Guide" has something near the end about "a lot of people will want to modify the default font rendering at this point," with a direct link about getting the Ubuntu and Infinality patches via PKGBUILD scripts.  This is alright, since it's Arch, and that's how everything is, and it takes five minutes to make and install the packages  (well, the build for libcairo actually takes a little longer, but it takes care of itself while you watch youtube or whatever).

I spent a few hours today trying to build patched debs for Debain with out-of-date instructions, didn't succeed, tried changing some stuff, didn't succeed, tried dowloading the Ubuntu debs directly and installing those, didn't succeed (cause the versions on Sid are already newer than Ubuntu's.  I could probably force it with some flag for dpkg, but I haven't bothered to look yet.  gdebi said 'no').

I'll probably try to find newer instructions about applying the patches tomorrow and try that route again, since figuring out package buiding is the whole reason I installed Debain in the first place.  I somehow suspect that this might be easier had I not switched to the unstable repos, but I guess we'll have to see about that.

It is kind of funny that Debian people are freaking out that much about it, for a distro that claims to be "agnostic" about interface choices.  Course, it's foolish to actually expect Debain to be agnostic about anything, given their stance on... well, just about everything.

But what I really don't get is why the patches aren't adopted by the people who develope libcairo (in particular, since that provides the most dramatic improvement)

---

### Post by 3Miro on 2011-09-28
Ubuntu-font-family is in the Gentoo official repos. Those are the fonts that I am using and it looks just like Ubuntu's great fonts.

I don't think that they need special font patches, just the fonts themselves, which anyone can download and install (or package).

---

### Post by ninjaaron on 2011-09-28
> **3Miro said:**
> Ubuntu-font-family is in the Gentoo official repos. Those are the fonts that I am using and it looks just like Ubuntu's great fonts.

I don't think that they need special font patches, just the fonts themselves, which anyone can download and install (or package).

I'm not talking about the fonts.  While the Ubuntu font is excellent, Ubuntu also has a heavily patched rendering library that makes a huge difference (as well as extensive font-specific instructions in fontconfig).  Perhaps Gentoo has adopted the same patches.  Also, some people don't notice or care about the difference.  Nightwishfan (of blessed memory) and I have had a couple of arguments cause I've picked on Debian's rendering and he thinks it's totally fine (and is hot and bothered for Debian).  For him, as for many others, it's a non-issue.  Personally, it drives me crazy, and I know I'm not the only one.

---

### Post by benerivo on 2011-09-28
I don't know why they aren't upstream. Even fedora don't use infinality by default -- which i think it was originally made for. Maybe distros believe what they have is good enough.

---

### Post by 3Miro on 2011-09-28
> **ninjaaron said:**
> I'm not talking about the fonts.  While the Ubuntu font is excellent, Ubuntu also has a heavily patched rendering library that makes a huge difference (as well as extensive font-specific instructions in fontconfig).  Perhaps Gentoo has adopted the same patches.  Also, some people don't notice or care about the difference.  Nightwishfan (of blessed memory) and I have had a couple of arguments cause I've picked on Debian's rendering and he thinks it's totally fine (and is hot and bothered for Debian).  For him, as for many others, it's a non-issue.  Personally, it drives me crazy, and I know I'm not the only one.

When I first installed the Ubuntu fonts under Gentoo, I just downloaded them from the Canonical site. They were added to the Gentoo repos later. I was able to get perfect rendering under xfce from the start.

Have you tried to just download the fonts under say Debian, then put them in /usr/share/fonts/truetype and then select them from the Appearance settings and play with the settings (i.e. get an Ubuntu machine and see what they have selected, like slight hinting and so on).

---

### Post by mips on 2011-09-28
I actually prefer the standard fonts in Debian/Arch without patches. Find them much sharper & crisper.

---

### Post by realzippy on 2011-09-28
This question is discussed/answered by the debian folks:
[http://forums.debian.net/viewtopic.php?f=6&t=50742&start=0](http://forums.debian.net/viewtopic.php?f=6&t=50742&start=0)

---

### Post by benerivo on 2011-09-28
> **3Miro said:**
> ...Have you tried to just download the fonts under say Debian, then put them in /usr/share/fonts/truetype and then select them from the Appearance settings and play with the settings (i.e. get an Ubuntu machine and see what they have selected, like slight hinting and so on). I've tried that and it is definitely different. Personally, i prefer the look with the Ubuntu fontconfig, freetype2, libxft, and libcairo packages. If those Ubuntu packages weren't considered as an improvement, why do they exist?

---

### Post by ninjaaron on 2011-09-28
> **3Miro said:**
> Have you tried to just download the fonts under say Debian, then put them in /usr/share/fonts/truetype and then select them from the Appearance settings and play with the settings (i.e. get an Ubuntu machine and see what they have selected, like slight hinting and so on).Yes.  I download Ubuntu fonts on everything.  I even downloaded them on Windows when I had it.

But it's not about the font.  libcairo is patched.  The patch changes the way fonts are rendered.  This is a fact regardless of whether some people notice it or not.  Some people certainly do notice it, and the code is there in black and white for all to see.

> **mips said:**
> I actually prefer the standard fonts in Debian/Arch without patches. Find them much sharper & crisper.

With "Native" or "Full" hinting selected, some font families (such as Droid and Dejavu) do look a bit sharper, but the shapes are not as full or rounded (in my experience).  If you run dpkg-reconfigure fontconfig-configure in Debian and select "autohinting," you get the opposite.  The shapes are a bit better, but the antialiasing is a mess.  Furthermore, if you use any kinds of fonts besides TrueType hinted, Debian will almost always be fuzzier, as the stock cairo filters only work with such fonts.

It would be possible to do the same with the hinting settings in Ubuntu, though it would be a bit of work (well, you would have open up fontconfig and modify it).  If you did, I suspect it would be sharper in Ubuntu than in Debian, assuming you are using an LCD screen, as the patched libcairo has much augmented sub-pixel filtering.

---

### Post by FuturePilot on 2011-09-28
I've been wondering this for years.

I remember hearing it had to do with a certain patent but I also remember that patent expired a while ago.

---

### Post by Famicube64 on 2011-09-28
> **ninjaaron said:**
> ...and it's not like any distro comes with it built in.

lrn2fuduntu

---

### Post by el_koraco on 2011-09-28
> **ninjaaron said:**
> 
I'll probably try to find newer instructions about applying the patches tomorrow and try that route again, since figuring out package buiding is the whole reason I installed Debain in the first place. 

If you wanna learn to package, then cool. An easier way is to add the crunchbang repo to your sources list, force libcairo from there with Synaptic and then apt-pin it in /etc/apt/preferences. 

```
Package: libcairo2 (I think that's the name)
Pin: release n=statler
Pin-Priority: 1001
```The 1001 value will ensure it doesn't get overwritten by anything. But check with an apt-get dist-upgrade -s, I'm not the ultimate authority on apt-pinning, so apt might try to downgrade GDM, Grub and stuff if I'm wrong about the config. My fonts.conf to achieve Ubuntu-like rendering in GTK apps: 

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font">
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
   <edit mode="assign" name="lcdfilter">
   <const>lcddefault</const>
   </edit>
 </match>
</fontconfig>

```

As a side-note, i think LMDE also has the patched package, so you might go with that too.

---

### Post by ninjaaron on 2011-09-28
> **Famicube64 said:**
> lrn2fuduntu
I was just about to ask you a question about funtoo, and then I realized that you were talking about something else entirely.


> **el_koraco said:**
> If you wanna learn to package, then cool. An easier way is to add the crunchbang repo to your sources list, force libcairo from there with Synaptic and then apt-pin it in /etc/apt/preferences.

Thanks.  I may try that if I can't get the packages to work.

It's not such a huge deal, as it's just a partition for effing around.  There is something rather appealing about Debian in terms of stability and overall "vanilla-ness," not to mention hardcorecrazy fossiness (which, I'll admit, turns me on a little bit).  However, I don't think Arch is going anywhere soon as my main working distro at the moment.  It beats them all in terms of "vanilla," except possibly Gentoo, and because of this, it tends to get updates even sooner than Sid, and they still don't break stuff (unless you force it when it warns you).  I'd probably end up erasing debian and fedora eventually and dual boot Ubuntu and Arch.  Arch for all the real work (I seriously can't figure out how I ever got anything done without tiling), Ubuntu to keep my data partion in sync with the cloud and for when I want to get some specific task done quickily that I haven't "figured out on Arch" without hunting around the wiki for an hour or two.

Maybe one day I'll give Debain a serious run, once they get their fonts sorted.

---

