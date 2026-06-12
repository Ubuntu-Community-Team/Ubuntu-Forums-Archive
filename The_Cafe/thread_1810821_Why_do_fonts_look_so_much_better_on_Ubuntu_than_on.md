---
title: "Why do fonts look so much better on Ubuntu than on other distros?"
date: 2011-07-23
forum: The Cafe
---

### Post by ninjaaron on 2011-07-23
Ok, I don't know if fonts actually look bad on all other distros.  I'm trying out another very popular one right now, which will remain nameless, and the fonts on my LCD screen were HORRIBLE out of box.  I tried about a million fixes and they are no longer offensive to the eyes, but they don't look as good as on Ubuntu.

What is Ubuntu doing right that this "other distro" doesn't know about?  After I "fixed" the problem, the fonts look about as good as they did when I started using Ubuntu in 2008. These days, the font rendering is on par with OSX, and it comes with that wonderful "Ubuntu" font as the system default, which is the best system font on any platform, in my opinion.

---

### Post by Thewhistlingwind on 2011-07-23
I'll go ahead and say that some of the fonts on fedora 15 make my eyes burn.

I'm not sure, but the Ubuntu font is my favourite too.

---

### Post by Legendary_Bibo on 2011-07-23
Using proprietary font rendering technologies.

---

### Post by ninjaaron on 2011-07-23
I installed proprietary font rendering engines (or I think they were) on the other distro, and it's still not as good.

---

### Post by el_koraco on 2011-07-23
You have to patch some libraries. It would help if you named the distro, so someone can help you with specifics.

---

### Post by 3Miro on 2011-07-23
You can install Ubuntu fonts under any distro. I am using Gentoo and they are available in the repos.

Ubuntu fonts are completely FOSS.

---

### Post by Legendary_Bibo on 2011-07-23
> **3Miro said:**
> You can install Ubuntu fonts under any distro. I am using Gentoo and they are available in the repos.

Ubuntu fonts are completely FOSS.

He's not asking for open source fonts, he's just trying to get font rendering to work correctly.

---

### Post by ninjaaron on 2011-07-23
> **el_koraco said:**
> You have to patch some libraries. It would help if you named the distro, so someone can help you with specifics.

I've done several patches already.  The Fonts are ok now, just not as good as Ubuntu.

And it's F15.

And I also installed the Ubuntu fonts, but they weren't in the repos.  I had to run around the dang internet and track down the ttf files.

---

### Post by el_koraco on 2011-07-23
Did you apply the infinality patches? I see no difference once they're applied. maybe it's due to my screen.

---

### Post by 3Miro on 2011-07-23
> **ninjaaron said:**
> I've done several patches already.  The Fonts are ok now, just not as good as Ubuntu.

And it's F15.

And I also installed the Ubuntu fonts, but they weren't in the repos.  I had to run around the dang internet and track down the ttf files.

You said that everything works fine on Ubuntu. Check the default settings and then use the same settings with F15 using Ubuntu fonts. I get no difference in Ubuntu vs Gentoo font rendering.

---

### Post by Bachstelze on 2011-07-23
> **Legendary_Bibo said:**
> Using proprietary font rendering technologies.

Proprietary no more since May 2010.

[http://en.wikipedia.org/wiki/Freetype#Font_Hinting_patent_conflict](http://en.wikipedia.org/wiki/Freetype#Font_Hinting_patent_conflict)

---

### Post by ScionicSpectre on 2011-07-23
The fonts seem to be just as well for me under Arch, and I don't remember installing anything specific to make them this way. I'm a designer with experience in typography, so I think I'd notice if it were very different in rendering (I don't suppose Arch is the very first distribution Ubuntu users look to as an alternative, either).

I will agree that the default fonts in Ubuntu itself are quite nice, of course. I tend to use Cantarell and Ubuntu as my fonts even in environments like KDE due to their sound design for use screens.

---

### Post by ninjaaron on 2011-07-23
> **el_koraco said:**
> Did you apply the infinality patches? I see no difference once they're applied. maybe it's due to my screen.

Did it.  I think the difference might be something to do with the way it handles kerning... something seems funny about the spacing. The fonts also look slightly more thin and stretched in smaller sizes, and sometimes they seem to be a little bit fuzzier.

@ScionicSpectre:  It may be that there is some kind of proprietary voodoo going on both in Ubuntu and Arch.  They both have a more lenient policy when it comes to proprietary technologies than Fedora.

---

### Post by el_koraco on 2011-07-23
> **ninjaaron said:**
> Did it.  I think the difference might be something to do with the way it handles kerning... something seems funny about the spacing. The fonts also look slightly more thin and stretched in smaller sizes, and sometimes they seem to be a little bit fuzzier.


Did you set hinting to slight and rendering to RGB? In Gnome Tweak Tool?

---

### Post by ninjaaron on 2011-07-23
> **el_koraco said:**
> Did you set hinting to slight and rendering to RGB? In Gnome Tweak Tool?

rendering is rgba (not sure what the "a" can mean if we're talking abou pixels, but whatever), There was no option labelled simply "RGB".  I think I set the hinting to "full." Is that bad?

edit: ok, I set the hinting to slight.  That doesn't seem to have made a huge difference.  The main thing is that they seem more stretched or something than in Ubuntu, but I can also tell that the antialiasing isn't quite as good as in Ubuntu.  It's definitely much, much better than it was when I installed, but it still isn't perfect.

---

### Post by hhh on 2011-07-23
@ninjaaron, pics or it didn't happen. I've never noticed any font problems on any of the Linux distros I've tried after setting up a basic ~/.fonts.conf file...```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="antialias" mode="assign"><bool>true</bool></edit>
    <edit name="hinting" mode="assign"><bool>true</bool></edit>
    <edit name="hintstyle" mode="assign"><const>hintslight</const></edit>
    <edit name="rgba" mode="assign"><const>rgb</const></edit>
  </match>
</fontconfig>
```
Can anyone post a comparison pic of what he/she's talking about?

---

### Post by ninjaaron on 2011-07-23
> **hhh said:**
> @ninjaaron, pics or it didn't happen.

It happened.  Two pictures of the same firefox tab in the same size.  I realize that the font in fedora appears slightly smaller, but the settings are the same:

---

### Post by Legendary_Bibo on 2011-07-23
> **ninjaaron said:**
> rendering is rgba (not sure what the "a" can mean if we're talking abou pixels, but whatever), There was no option labelled simply "RGB".  I think I set the hinting to "full." Is that bad?

edit: ok, I set the hinting to slight.  That doesn't seem to have made a huge difference.  The main thing is that they seem more stretched or something than in Ubuntu, but I can also tell that the antialiasing isn't quite as good as in Ubuntu.  It's definitely much, much better than it was when I installed, but it still isn't perfect.

a = alpha channel which controls transparency.

---

### Post by ninjaaron on 2011-07-23
> **Legendary_Bibo said:**
> a = alpha channel which controls transparency.

I know.  I thought this had to do with subpixel smoothing.  There's no alpha channel on an LCD pixel.

---

### Post by hhh on 2011-07-23
> **ninjaaron said:**
> It happened.
Lol! Thanks for posting that... wow. I take it that text colors and tab colors are different due to different themes, but even so, the difference in the rendering of the letter "o", for example is noticeable different. And you have a .fonts.conf file in Fedora? Wow.

---

### Post by Legendary_Bibo on 2011-07-23
> **ninjaaron said:**
> I know.  I thought this had to do with subpixel smoothing.  There's no alpha channel on an LCD pixel.

pixels as your computer sees them do have an alpha channel. If an LCD screen could physically display the alpha channel then you would be able to see through the screen and look at all the components in the monitor.

---

### Post by ninjaaron on 2011-07-23
> **hhh said:**
> And you have a .fonts.conf file in Fedora?

You bet you're booty.  It was much worse before I had the all the tweaks though. Unusable, I'd say. The fonts are pretty good now, I just get hung up on details.  The font rendering (of all things) was actually the thing that bothered me the most when I first switched to Ubuntu from OSX.  Everything else could be tweaked to get it the way I liked, but the rendering just wasn't the same.  Then a little while later I noticed that Ubuntu's rendering improved and was nearly on the same level as OSX (I think it was in 9.10 or 10.04).  I also get freaked out because Abiword and OpenOffice/LibreOffice don't handle typography the same way (Abiword has better support for OpenType features).  I've even designed a couple of novelty fonts, just for kicks, for Greek and Hebrew, based on ancient inscriptions and manuscripts.

tl;dr version: I'm pedantic about shapes and lines.

---

### Post by 3Miro on 2011-07-23
Fedora uses the Liberation fonts and those are different from Ubuntu. Using the Ubuntu settings would work only with Ubuntu fonts, I don't know how to handle Liberation.

I had to also set "Custom DPI Settings" and set that to 96.

---

### Post by Legendary_Bibo on 2011-07-23
> **ninjaaron said:**
> You bet you're booty.  It was much worse before I had the all the tweaks though. Unusable, I'd say. The fonts are pretty good now, I just get hung up on details.  The font rendering (of all things) was actually the thing that bothered me the most when I first switched to Ubuntu from OSX.  Everything else could be tweaked to get it the way I liked, but the rendering just wasn't the same.  Then a little while later I noticed that Ubuntu's rendering improved and was nearly on the same level as OSX (I think it was in 9.10 or 10.04).  I also get freaked out because Abiword and OpenOffice/LibreOffice don't handle typography the same way (Abiword has better support for OpenType features).  I've even designed a couple of novelty fonts, just for kicks, for Greek and Hebrew, based on ancient inscriptions and manuscripts.

tl;dr version: I'm pedantic about shapes and lines.

You could use the Fusion repos and there might be something in there to help. I recommend Fuduntu, it's based on Fedora, but it has the Fusion repos installed and a bunch of other great software, it's Fedora, but with proprietary software installed.

---

### Post by kaldor on 2011-07-24
> **ninjaaron said:**
> Ok, I don't know if fonts actually look bad on all other distros.  I'm trying out another very popular one right now, which will remain nameless, and the fonts on my LCD screen were HORRIBLE out of box.  I tried about a million fixes and they are no longer offensive to the eyes, but they don't look as good as on Ubuntu.

What is Ubuntu doing right that this "other distro" doesn't know about?  After I "fixed" the problem, the fonts look about as good as they did when I started using Ubuntu in 2008. These days, the font rendering is on par with OSX, and it comes with that wonderful "Ubuntu" font as the system default, which is the best system font on any platform, in my opinion.

Fedora 15 has horrible font rendering. I put it on my laptop and my eyes got strained really badly after the first 20 minutes. I installed gnome-tweak-tool and turned on hinting and changed the font from the (really bad) default GNOME 3 font.

---

### Post by Dustin2128 on 2011-07-24
> **kaldor said:**
> Fedora 15 has horrible font rendering. I put it on my laptop and my eyes got strained really badly after the first 20 minutes. I installed gnome-tweak-tool and turned on hinting and changed the font from the (really bad) default GNOME 3 font.
I don't think it's the default Gnome 3 font- it looks great on arch.

---

### Post by Spice Weasel on 2011-07-24
> **3Miro said:**
> Fedora uses the Liberation fonts and those are different from Ubuntu. Using the Ubuntu settings would work only with Ubuntu fonts, I don't know how to handle Liberation.
[IMG]http://omgcheesecake.net/public/style_emoticons/default/facepalm.gif[/IMG]

---

### Post by mips on 2011-07-24
> **ScionicSpectre said:**
> The fonts seem to be just as well for me under Arch...

There are patched packages available in Arch for Ubuntu and Infanality, [https://wiki.archlinux.org/index.php/Font_Configuration#Patched_packages](https://wiki.archlinux.org/index.php/Font_Configuration#Patched_packages)

My fonts in Arch look the same as in Ubuntu.

---

### Post by handy on 2011-07-24
My fonts in Arch look noticeably better than they do in OSX!

---

### Post by mips on 2011-07-24
> **handy said:**
> My fonts in Arch look noticeably better than they do in OSX!

I think the fonts on most things look better than on OSX :p

---

