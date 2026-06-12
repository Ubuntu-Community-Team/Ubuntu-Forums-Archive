---
title: "XFCE 4.10 PPA gone live!"
date: 2012-05-03
forum: The Cafe
---

### Post by mips on 2012-05-03
[https://launchpad.net/~mrpouit/+archive/ppa](https://launchpad.net/~mrpouit/+archive/ppa)

Will later be moved to [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)


[SIZE="3"]**[COLOR="Red"]Please note:[/COLOR] XFCE 4.10 is not officially supported in Ubuntu 12.04 and earlier, so if you have any issues then you are on your own.**[/SIZE]
XFCE 4.10 will make it's official debut in Xubuntu 12.10





.

---

### Post by tewth on 2012-05-03
Ah, thank god. Just spent the last 4 hours doing it manually only to get it installed broken.
Used this and it was done in five minutes

EDIT: Whats not ready about it? The only thing that came up weird for me was that the separator on the top bar between the windows and notification area wasn't set to expand... Looks like I'm in for some suprises

---

### Post by mips on 2012-05-03
> **tewth said:**
> 
EDIT: Whats not ready about it? The only thing that came up weird for me was that the separator on the top bar between the windows and notification area wasn't set to expand... Looks like I'm in for some suprises

All the packages have not finished building yet, it's still in progress. See [https://launchpad.net/~mrpouit/+archive/ppa/+builds?build_state=pending](https://launchpad.net/~mrpouit/+archive/ppa/+builds?build_state=pending)

DO NOT INSTALL YET, wait until the build process is completed.

---

### Post by neu5eeCh on 2012-05-03
> **mips said:**
> **EDIT: [COLOR=Red]Ignore this, it's not ready yet.[/COLOR]**

A little jumpy, are we? ;)

---

### Post by mips on 2012-05-03
> **VTPoet said:**
> A little jumpy, are we? ;)

Me? Never :biggrin:

Guess I'll have to wait in check back in the morning when I wake up, 00:30 here so time for a bit of reading and bed. G'night.

---

### Post by tedbell on 2012-05-03
Anyone else having this work? They wouldn't release it if it weren't ready would they? Just when I've found an easy way to install I can't use it. :(

---

### Post by mips on 2012-05-04
> **tedbell said:**
> Anyone else having this work? They wouldn't release it if it weren't ready would they? Just when I've found an easy way to install I can't use it. :(

See post #3.

---

### Post by CharlesA on 2012-05-06
Moved back to the Cafe.

---

### Post by mips on 2012-05-06
> **CharlesA said:**
> Moved back to the Cafe.

Thank you!


I have installed the amd64 bit version on a base install of Xubuntu 12.04 and so far so good.

---

### Post by neu5eeCh on 2012-05-06
The 4.10 PPA is being discussed [here]("http://ubuntuforums.org/showthread.php?t=1935375"), along with solutions to a few problems that have come up. I installed it on my experimental partition (Xubuntu Desktop in Ubuntu then the PPA) and it's working beautifully.

---

### Post by mips on 2012-05-06
> **VTPoet said:**
> I installed it on my experimental partition (Xubuntu Desktop in Ubuntu then the PPA) and it's working beautifully.

How's your fonts? :tongue::biggrin:

I installed 4.10 on a Xubuntu base install I did from the alternate image. I have no 4.8 components at all. My fonts are tack sharp, Droid Sans 11, Enabled anti-aliasing, Hinting Full, Sub-pixel order RGB, Custom DPI disabled.

---

### Post by neu5eeCh on 2012-05-06
> **mips said:**
> How's your fonts? :tongue::biggrin:

I installed 4.10 on a Xubuntu base install I did from the alternate image. I have no 4.8 components at all. My fonts are tack sharp, Droid Sans 11, Enabled anti-aliasing, Hinting Full, Sub-pixel order RGB, Custom DPI disabled.

:rolleyes: After an epic round of trial and error, I finally got my font rendering up to Ubuntu's standards which, to me, are as good as this laptop is going to get.

Ubuntu 10
Anti-Aliasing: Checked
Hinting : Slight
DPI: I alternate between disabled and 112. 112 makes for a very clean menu, but a little large.

But _the key to the whole thing_, the _**crucial option**_, was LCD Hinting:

xfconf-query -c xsettings -p /Xft/Lcdfilter -n -t string -s lcddefault

Unfortunately, there's no way to know about this unless you pester an XFCE dev (which is what I did) or google just the right search term -- which I never managed.

(Had been "lcdnone". And that was a disaster. Other options: lcdnone, lcdlight, lcdlegacy)

---

### Post by mips on 2012-05-06
> **VTPoet said:**
> 
But _the key to the whole thing_, the _**crucial option**_, was LCD Hinting:

xfconf-query -c xsettings -p /Xft/Lcdfilter -n -t string -s lcddefault

Unfortunately, there's no way to know about this unless you pester an XFCE dev (which is what I did) or google just the right search term -- which I never managed.


I would never in my life have discovered that. I just checked and I don't even have a /Xft/Lcdfilter option specified!

---

### Post by neu5eeCh on 2012-05-06
> **mips said:**
> I would never in my life have discovered that. I just checked and I don't even have a /Xft/Lcdfilter option specified!

The way to check is at terminal:  xrdb -query

**Edit:** If you change the LCD Hinting, you have to log out/in before it takes effect. Look [here]("http://docs.xfce.org/xfce/xfce4-settings/appearance") for more information.

---

### Post by mips on 2012-05-06
> **VTPoet said:**
> The way to check is at terminal:  xrdb -query

**Edit:** If you change the LCD Hinting, you have to log out/in before it takes effect.

Ok I changed mine to lcddefault and the Ubuntu font look really good but I think it makes the default xubuntu droid sans font look worse. But it still seems like a bit of a hit & miss affair as you make a font one size bigger then it looks weird again.

Anyway, I've decided for now to settle on Ubuntu 11, anti-aliased, medium hinting, rgb sub-pixel order and custom dpi disabled.

Thanks for sharing that lcd setting stuff!

---

### Post by ammofreak on 2012-05-06
):P Righto....

---

### Post by Toz on 2012-05-06
> **VTPoet said:**
> The way to check is at terminal:  xrdb -query

**Edit:** If you change the LCD Hinting, you have to log out/in before it takes effect. Look [here]("http://docs.xfce.org/xfce/xfce4-settings/appearance") for more information.

Following up from the other thread about the fonts, what do you have in your ~/.Xdefaults file? I have (Xft-related):
> ! Xft settings ---------------------------------------------------------------

Xft.dpi:        96
Xft.antialias:  true
Xft.rgba:       rgb
Xft.hinting:    true
Xft.hintstyle:  hintslight
Xft.lcdfilter:  lcddefault


...and apparently this file comes from xubuntu-default-settings. Since you've installed Unity/Ubuntu first, I wonder whether you have this code there.

I've installed Xubuntu only and don't have the font issue you have and am wondering where this inconsistency is coming from.

---

### Post by neu5eeCh on 2012-05-06
> **Toz said:**
> I've installed Xubuntu only and don't have the font issue you have and am wondering where this inconsistency is coming from.

I installed the xubuntu-desktop in 12.04 Ubuntu and all the settings were blank - I know that because first, I was having the same poor font rendering and, second, because I checked. One of the biggest complaints about LMDE, which uses XFCE, is the poor font quality and it probably all stems from users installing the DE on laptops or monitors with the wrong LCD settings - the settings being blank. I noticed the same problem with #! XFCE. All this time I thought it was endemic to XFCE. It *is*, but it's fixable.

---

### Post by Toz on 2012-05-06
I don't have access to an ubuntu install right not check, but I have a theory. I'm wondering whether when you install ubuntu, it doesn't create (or doesn't need to create, or creates a parital) .Xdefaults file that includes the necessary xfce Xft settings. When you add xubuntu-desktop, it will create the /etc/skel/.Xdefaults file, but won't propagate it to the home directory of existing users. I'll try to test this when I get access to an ubuntu install.

---

### Post by mips on 2012-05-07
> **Toz said:**
> Following up from the other thread about the fonts, what do you have in your ~/.Xdefaults file? I have (Xft-related):


...and apparently this file comes from xubuntu-default-settings. Since you've installed Unity/Ubuntu first, I wonder whether you have this code there.

I've installed Xubuntu only and don't have the font issue you have and am wondering where this inconsistency is coming from.

I don't even have that file at all. So it does not come installed with a xubuntu base install and the xfce 4.10 install does not create one either. maybe it's part of xubuntu-default-settings or one of those packages.

I see FF does not follow my systems default font theme.

At some point I will do a vm install of xubuntu 12.04, I alreay have a vm image for ubuntu 11.10 and then compare the various font settings between them. Will install VB-4.1 today.

---

### Post by Toz on 2012-05-07
> **mips said:**
> I don't even have that file at all. So it does not come installed with a xubuntu base install and the xfce 4.10 install does not create one either. maybe it's part of xubuntu-default-settings or one of those packages.

Yes, its part of xubuntu-default-settings. Its installed to /etc/skel. It only gets copied to a user account when a new account is created _and_ it (.Xdefaults) exists in /etc/skel.

---

### Post by mips on 2012-05-07
> **Toz said:**
> Yes, its part of xubuntu-default-settings. Its installed to /etc/skel. It only gets copied to a user account when a new account is created _and_ it (.Xdefaults) exists in /etc/skel.

I can't install that package as it wants to remove some of my 4.10 components. I'll just copy the file over from normal install in a vm.

---

### Post by neu5eeCh on 2012-05-07
> **mips said:**
> I can't install that package as it wants to remove some of my 4.10 components. I'll just copy the file over from normal install in a vm.

4.10 doesn't use *xfce4-settings-helper*. It uses *xfsettinfsd*. I'm barely figuring this out as I go along, so don't ask me anything more than that. ;)

---

### Post by mips on 2012-05-07
> **VTPoet said:**
> 4.10 doesn't use but *xfce4-settings-helper*. It uses *xfsettinfsd*. I'm barely figuring this out as I go along, so don't ask me anything more than that. ;)

Yes, aware that some packages have changed ;)

The one thing I would like to change though is the desktop menu, I only wanna see what's in the panel menu and not the other additional stuff.

[IMG]http://ompldr.org/vZG5scg/menu.png[/IMG]

Or somehow move that into the root and remove some of the main options. Kinda like it looked in 4.6 I think.

---

