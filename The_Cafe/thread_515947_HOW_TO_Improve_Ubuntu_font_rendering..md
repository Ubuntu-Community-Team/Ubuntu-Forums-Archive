---
title: "HOW TO: Improve Ubuntu font rendering."
date: 2007-08-02
forum: The Cafe
---

### Post by phrostbyte on 2007-08-02
[http://tux.fau.edu/index.php/topic,93.0.html]("http://tux.fau.edu/index.php/topic,93.0.html")

"This patch (shell script) will improve Ubuntu 7.04 font rendering. It works pretty well in my opinion. I always thought Ubuntu font's look great but this adds to the beauty (imo). It enchants the current fonts with subpixel rendering and vertical anti-aliasing. It also adds Red Hat's "Liberation" font set, a very nice Microsoft-compatible font set that I am sure you will enjoy."

---

### Post by phrostbyte on 2007-08-02
Screenshot below

---

### Post by yabbadabbadont on 2007-08-02
In order to prevent people from having to change forums to get the patch, here it is for your perusal.
```
#! /bin/bash
## Ubuntu Font Improver Patch
## by emet of FAU LUG (http://tux.fau.edu)

## Add special repository to apt sources list
echo "################################" >> /etc/apt/sources.list
echo "# Ubuntu Font Improvement Patch" >> /etc/apt/sources.list
echo "deb http://www.telemail.fi/mlind/ubuntu feisty fonts" >> /etc/apt/sources.list
echo "deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts" >> /etc/apt/sources.list
echo "################################" >> /etc/apt/sources.list

## Get the GPG key for the repository
wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | sudo apt-key add -

## Update the APT database
apt-get update

## Install the needed packages
apt-get -y install libfreetype6 libcairo2 libxft2

## Now add Red Hat Liberation Fonts

## Download the fonts from Red Hat
wget https://www.redhat.com/f/fonts/liberation-fonts-ttf-3.tar.gz

## Extract the package
tar -xvf liberation-fonts-ttf-3.tar.gz

## Copy the fonts to the proper directory
cp -r liberation-fonts-0.2 /usr/share/fonts/truetype/

## Delete temporary files
rm -r liberation-fonts-0.2/ liberation-fonts-ttf-3.tar.gz

## Rebuilt the font cache
fc-cache

## Display confirmation
clear
echo "Ubuntu font improvement successfully installed!"
echo "Font rendering improved with subpixel and vertical anti-aliasing."
echo "Also installed new Red Hat \"Liberation\" font set. Very sexy fonts!"
echo "You must either restart your computer or restart the X Display to see the changes."
echo "Visit http://tux.fau.edu/ for more tips and cool stuff."

```
Please note that this **adds an extra third party repository** to your /etc/apt/sources.lst.  You should only do that if you trust the creator of the repository...

---

### Post by vambo on 2007-08-02
Thanks for that. Very nice  :)

---

### Post by phrostbyte on 2007-08-02
Thanks. They may look a little weird when you first load but after an hour or so you'll wonder how you used Ubuntu without this. :guitar:

---

### Post by aks44 on 2007-08-02
I was about to create a thread about this, but I may as well ask in this one...

What's all that fuss about Ubuntu's (supposedly) defficient font rendering?

Personnaly I find it way superior to MSFT's "ClearType" (which should be more adequately dubbed "BlurType" IMO).

There are only two things I can think of that would explain that my point of view is different from most other Ubuntu users:

- I'm one of the few using KDE... maybe the font rendering engine is better that GNOME's?
- (most plausible solution) I'm one of the few still using a CRT monitor.


Would anyone care to enligthen me on this one please? (I really wonder...)

---

### Post by miggols99 on 2007-08-02
I've found that KDE renders fonts much better than Gnome. I have a computer running Gnome, and found that the font rendering isn't that good. But that's a CRT. I have another running Xfce, which didn't look too good, until I used a nice patch out of the AUR for better font rendering (I'm running Arch :))

---

### Post by mrazster on 2007-08-02
I already had the "subpixel font rendering" patched....however the ***Liberation font*** was really nice. Very clean, simpel and clear..really liked it.....thnx a bunch

---

### Post by dizee on 2007-08-02
This patch is excellent, thanks. KDE does have far superior font rendering to Gnome in my experience but this pretty much levels it out.

---

### Post by Depressed Man on 2007-08-02
Could anyone post a before and after picture? Because I'm looking at the screenshot and comparing it to my desktop and I really can't tell a difference.. (all I did was install the MS fonts)

---

### Post by mrazster on 2007-08-02
> **Depressed Man said:**
> Could anyone post a before and after picture? Because I'm looking at the screenshot and comparing it to my desktop and I really can't tell a difference.. (all I did was install the MS fonts)

Well...sorry I can't give any before/after screens....but I can tell you this...run that script and then use the Liberation font....then you will see the difference.

---

### Post by phrostbyte on 2007-08-02
You can definitely tell if you look at the attached PNG image I think. It's not immediately noticeable but the patched libfreetype gives the fonts a nice blended look. It's hard to explain. It's much more noticeable when the fonts are on a different background then white.

---

### Post by ssergeje on 2007-08-27
Great work =D> Better put it in the Wiki and push it in the mainstream.
It seems kinda blurry for the first time, but not that much as MS ClearType. I'll attach the images. The first is before, second after. You can see how fonts went juicy :D

---

### Post by nb123 on 2007-09-15
I recently applied this patch, but I'd like to remove it, could someone please explain to me how to do this? Because I find the vertical anti-aliasing hard to read... Please help, thanks

---

### Post by avik on 2007-09-15
Looking at the screenshots, I don't really like this type of font rendering.  I can see the different colors around the edges of the font due to the subpixel rendering.  It's the same reason I don't use subpixel and instead I use a grayscale antialiasing.

Maybe I can just see the colors a little better than others?  Whatever the case, it bothers me.  But other than that, it looks pretty good!

---

### Post by forrestcupp on 2007-09-15
> **yabbadabbadont said:**
> In order to prevent people from having to change forums to get the patch, here it is for your perusal.
```
#! /bin/bash
## Ubuntu Font Improver Patch
## by emet of FAU LUG (http://tux.fau.edu)

## Add special repository to apt sources list
echo "################################" >> /etc/apt/sources.list
echo "# Ubuntu Font Improvement Patch" >> /etc/apt/sources.list
echo "deb http://www.telemail.fi/mlind/ubuntu feisty fonts" >> /etc/apt/sources.list
echo "deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts" >> /etc/apt/sources.list
echo "################################" >> /etc/apt/sources.list

## Get the GPG key for the repository
wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | sudo apt-key add -

## Update the APT database
apt-get update

## Install the needed packages
apt-get -y install libfreetype6 libcairo2 libxft2

## Now add Red Hat Liberation Fonts

## Download the fonts from Red Hat
wget https://www.redhat.com/f/fonts/liberation-fonts-ttf-3.tar.gz

## Extract the package
tar -xvf liberation-fonts-ttf-3.tar.gz

## Copy the fonts to the proper directory
cp -r liberation-fonts-0.2 /usr/share/fonts/truetype/

## Delete temporary files
rm -r liberation-fonts-0.2/ liberation-fonts-ttf-3.tar.gz

## Rebuilt the font cache
fc-cache

## Display confirmation
clear
echo "Ubuntu font improvement successfully installed!"
echo "Font rendering improved with subpixel and vertical anti-aliasing."
echo "Also installed new Red Hat \"Liberation\" font set. Very sexy fonts!"
echo "You must either restart your computer or restart the X Display to see the changes."
echo "Visit http://tux.fau.edu/ for more tips and cool stuff."

```
Please note that this **adds an extra third party repository** to your /etc/apt/sources.lst.  You should only do that if you trust the creator of the repository...
Which line is it that enables the subpixel rendering and vertical antialiasing?

> **ssergeje said:**
> Great work =D> Better put it in the Wiki and push it in the mainstream.
It seems kinda blurry for the first time, but not that much as MS ClearType. I'll attach the images. The first is before, second after. You can see how fonts went juicy :D I like the before pics better.

---

### Post by salsafyren on 2007-09-15
this is for people who like ClearType.

I would like to get Mac-like font rendering.

I am already using Mac fonts because they look much better but Ubuntu still is lacking in graphical quality compared to the Mac.

---

### Post by nb123 on 2007-09-15
I definitely prefer truetype,  I installed the patch by using the instructions from the link, downloading the font_patch.sh..... it seemed to do a lot of things... and I'm kinda new to ubuntu so I don't even know where to start to undo it!

---

### Post by nb123 on 2007-09-16
Anyone? Please?

---

### Post by tageiru on 2007-09-16
> **dizee said:**
> This patch is excellent, thanks. KDE does have far superior font rendering to Gnome in my experience but this pretty much levels it out.
That would be strange as the font rendering system of GNOME and KDE is exactly the same, freetype. I know GNOME and KDE have different dpi settings which affects the font rendering, but that can easily be changed.

---

### Post by daverich on 2007-09-16
hey that's much better.

Thanks -

I vote for this to be in gutsy ;)

Kind regards

Dave Rich

---

### Post by zekica on 2007-09-16
> **tageiru said:**
> That would be strange as the font rendering system of GNOME and KDE is exactly the same, freetype.

Using the same settings (DPI, font hinting, etc.) rendered fonts look exactly the same.

In following screenshot, Firefox rendering is left, Konqueror rendering is right.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43616&stc=1&d=1189951860[/IMG]

---

### Post by vexorian on 2007-09-16
It is odd, the fonts in the screenshots look harder to read than the default rendering I got right now, I guess that having used it so long got me used to it.

---

### Post by zekica on 2007-09-16
Just to clarify: my screenshot is without that patch applied. I simply use Full Hinting with subpixel hinting. It works very well with my TFT display, and I find it very easy to read (more readable than ClearType). I just wanted to show what **tageiru** wrote.

---

### Post by taisao on 2007-09-16
> **forrestcupp said:**
> Which line is it that enables the subpixel rendering and vertical antialiasing?

 I like the before pics better.

Uninstall libfreetype6, libcairo2 and libxft2 should revert it back to normal. I think.

---

### Post by nb123 on 2007-09-16
Thanks for replying, when I go to synaptic to uninstall the three packages, when I try to mark them for removal or complete removal, It notifies me that I must uninstall a lot of other packages such as my beryl-manager, open office, xorg files and like 50 others.... How do I get around this!

---

### Post by taisao on 2007-09-16
so you choose for removal of complete removal?
I would say to choose for the normal removal (first choice).

---

### Post by dizee on 2007-09-16
> **zekica said:**
> Using the same settings (DPI, font hinting, etc.) rendered fonts look exactly the same.

In following screenshot, Firefox rendering is left, Konqueror rendering is right.
[IMG]http://ubuntuforums.org/attachment.php?[/IMG]

There's probably some configuration that is different between my Gnome set-up and my KDE one alright. Just the KDE set-up was perfect without needing to be tweaked right after I installed it unlike the gnome one. Either way my fonts look nice in both DEs now.

---

### Post by nb123 on 2007-09-16
No I didn't choose anything yet, I was waiting to ask you, but even if I choose removal, it still says to remove many packages like beryl, xserver-xorg files... etc... I can't remove these right... so what do I do?

---

### Post by jrusso2 on 2007-09-16
> **daverich said:**
> hey that's much better.

Thanks -

I vote for this to be in gutsy ;)

Kind regards

Dave Rich

I think the subpixel font rendering is a Microsoft  technology thats why its off by default.

---

### Post by yabbadabbadont on 2007-09-16
> **nb123 said:**
> No I didn't choose anything yet, I was waiting to ask you, but even if I choose removal, it still says to remove many packages like beryl, xserver-xorg files... etc... I can't remove these right... so what do I do?

In synaptic, select one of the custom packages that you wish to remove.  Then, on the Package menu, select Force Version.  You should then be able to choose to install the standard version from the repositories.  You'll need to do this for each of the custom packages that you installed.

---

### Post by jrusso2 on 2007-09-16
> **daverich said:**
> hey that's much better.

Thanks -

I vote for this to be in gutsy ;)

Kind regards

Dave Rich

I think the subpixel font rendering is a Microsoft  technology thats why its off by default.

---

### Post by nb123 on 2007-09-16
thanks for the help yabbadab, I did as you said, and downgraded all 3 packages libfreetype6, libcairo2 and libxft2 and restarted my computer, but unfortunately either the vertical antialiasing is still there or I'm imagining it.... here's a screenshot, any idea what else it might be? If you take a look at the screenshot, especially the bold text in the tab title and document.... the vertical antialiasing is still there isnt' it??

---

### Post by yabbadabbadont on 2007-09-16
> **nb123 said:**
> thanks for the help yabbadab, I did as you said, and downgraded all 3 packages libfreetype6, libcairo2 and libxft2 and restarted my computer, but unfortunately either the vertical antialiasing is still there or I'm imagining it.... here's a screenshot, any idea what else it might be? If you take a look at the screenshot, especially the bold text in the tab title and document.... the vertical antialiasing is still there isnt' it??

Since I don't trust binaries produced by non-official sources, I've never followed this guide.  Although the shell script only lists those three packages on the "apt-get" line, perhaps other packages were automatically updated as required version dependencies?  You might see if you can contact the author of the script and find out.  Also, you might try reconfiguring fontconfig.  ```
sudo dpkg-reconfigure fontconfig-config
```

---

### Post by forrestcupp on 2007-09-16
> **daverich said:**
> 
I vote for this to be in gutsy ;)


Actually, a lot of people that are testing Gutsy think that default font rendering in Gutsy is way better than it is in Feisty.  I can testify to this.  Fonts in Feisty was one of the things my wife hated about my using Linux.  When I installed the Gutsy alpha, my wife noticed a big improvement.  Others have pointed that out on the Gutsy section of the forums.

---

### Post by nb123 on 2007-09-16
I tried reconfiguring fontconfig-config, didn't help, sigh, I'm getting a headache just looking at it... :-(.... I guess I'll have to write to the guy at florida atlantic university....

---

### Post by nb123 on 2007-09-16
forrestcup, I look forward to using gutsy... I'm very new to linux, just started using it like 1 or 2 weeks ago.... but I love ubuntu, except for the font rendering.... personally I find Microsoft's normal sub-pixel rendering without anti-aliasing to be best for my eyes, would you say that I should definitely be looking to gutsy then?

---

### Post by taisao on 2007-09-16
> **nb123 said:**
> I tried reconfiguring fontconfig-config, didn't help, sigh, I'm getting a headache just looking at it... :-(.... I guess I'll have to write to the guy at florida atlantic university....

have you have set the font setting right? try running gnome-font-properties

---

### Post by forrestcupp on 2007-09-16
> **nb123 said:**
> forrestcup, I look forward to using gutsy... I'm very new to linux, just started using it like 1 or 2 weeks ago.... but I love ubuntu, except for the font rendering.... personally I find Microsoft's normal sub-pixel rendering without anti-aliasing to be best for my eyes, would you say that I should definitely be looking to gutsy then?

Look to Gutsy, but if you're new, wait for the release.  It's not that far off.

---

### Post by nb123 on 2007-09-16
taisao, I'll try that first thing tomorrow or late tonight, hopefully it'll fix it...

---

### Post by otterstrom on 2007-09-17
I installed this patch and am a little confused still, do I need to go to "font preferences" and set each option to the liberation font and then select "Subpixel (LCD)" ?

---

### Post by taisao on 2007-09-17
yes, just try it out :KS

---

### Post by nb123 on 2007-09-17
oh, gnome-font-properties is the general font settings under system --> preferences ---> font , I already tried that, I currently am using sub-pixel rendering with slight hinting cos it looks best.... I've tried full hinting and none, doesn't solve the vertical anti-aliasing problem... 

When I upgrade to gutsy gibbon in october, it will undo any changes I've made to the font settings right? Or do I have to do a full reinstallation by liveCD to revert to my original font settings?

---

### Post by Stone123 on 2007-09-17
[[IMG]http://img33.picoodle.com/img/img33/9/9/17/t_Screenshot1m_f9cb377.png[/IMG]](http://www.picoodle.com/view.php?img=/9/9/17/f_Screenshot1m_f9cb377.png&srv=img33)

I am using Lucida MAC fonts and this patch, it works. Thanks.

---

### Post by frychiko on 2007-09-18
I must be missing something here...

I find Feisty and Gutsy's default fonts with default settings to be much better than Windows fonts with or without cleartype turned on.

I don't see any improvement in the above screenshot, in fact it looks alot worse (If you're talking about the titlebar/menu text..

---

### Post by skiffler on 2007-11-03
> **yabbadabbadont said:**
> In order to prevent people from having to change forums to get the patch, here it is for your perusal.
```
#! /bin/bash
## Ubuntu Font Improver Patch
## by emet of FAU LUG (http://tux.fau.edu)

## Add special repository to apt sources list
echo "################################" >> /etc/apt/sources.list
echo "# Ubuntu Font Improvement Patch" >> /etc/apt/sources.list
echo "deb http://www.telemail.fi/mlind/ubuntu feisty fonts" >> /etc/apt/sources.list
echo "deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts" >> /etc/apt/sources.list
echo "################################" >> /etc/apt/sources.list

## Get the GPG key for the repository
wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | sudo apt-key add -

## Update the APT database
apt-get update

## Install the needed packages
apt-get -y install libfreetype6 libcairo2 libxft2

## Now add Red Hat Liberation Fonts

## Download the fonts from Red Hat
wget https://www.redhat.com/f/fonts/liberation-fonts-ttf-3.tar.gz

## Extract the package
tar -xvf liberation-fonts-ttf-3.tar.gz

## Copy the fonts to the proper directory
cp -r liberation-fonts-0.2 /usr/share/fonts/truetype/

## Delete temporary files
rm -r liberation-fonts-0.2/ liberation-fonts-ttf-3.tar.gz

## Rebuilt the font cache
fc-cache

## Display confirmation
clear
echo "Ubuntu font improvement successfully installed!"
echo "Font rendering improved with subpixel and vertical anti-aliasing."
echo "Also installed new Red Hat \"Liberation\" font set. Very sexy fonts!"
echo "You must either restart your computer or restart the X Display to see the changes."
echo "Visit http://tux.fau.edu/ for more tips and cool stuff."

```
Please note that this **adds an extra third party repository** to your /etc/apt/sources.lst.  You should only do that if you trust the creator of the repository...

This looks as if it's exactly what I'm looking for. However being a Linux newbie, I have a question: where does this code go? Does it have to be compiled? I don't understand what to do with it, and I'm feeling rather stupid...

---

### Post by taisao on 2007-11-03
[http://ubuntuforums.org/attachment.php?attachmentid=39659&d=1186088862](http://ubuntuforums.org/attachment.php?attachmentid=39659&d=1186088862)

It's a shell script, which doesn't need to be compiled, everything in the script can be typed right onto the terminal. But a faster way is to put them in a file and then run that file. To do that:

- Copy and paste to a file, like font_path.sh
the others steps are in **bold** in the screenshot above.

---

### Post by skiffler on 2007-11-04
OK, I've done all that and after a bit of fiddling around have installed the new fonts and changed them in Appearance, restarted the X thingie, and indeed the fonts have changed. Yes, they do look nice, but the problem that I'm trying to overcome (which I didn't mention in the OP) is that the text shown on a Firefox page is rather weedy and nowhere near as well rendered as the Ubuntu ones used elsewhere in the UI: this also applies to OpenOffice. Working on the assumption that the vast majority of web pages define MS fonts in their CSS, I downloaded the MS fonts, but this has made no difference to the fonts shown in Firefox, or those shown in a Word generated document opened in OO. It is this more than anything that has me confused. Why, in particular, are non-MS fonts shown in FF even though they are installed.)

---

