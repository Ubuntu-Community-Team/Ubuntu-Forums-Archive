---
title: "Font sizes after upgrading to 16.04"
date: 2016-03-25
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2016-03-25
I've just upgraded my main Ubuntu install from 15.10 to 16.04 using a method that I've never used before, that is upgrading using an ISO rather than via the update manager. 

Everything seems to have worked well and after adding the various PPAs that were deleted in the upgrade process I'm back to using Ubuntu but with one very significant difference. In some applications such as Google Chrome, gnome-terminal  and terminator the font sizes seem to be much smaller than what what I was seeing before the upgrade. In other applications I'm not seeing any change. :confused:

Is this a bug, just my imagination or have there been recent changes that I'm unaware of that would explain what I'm now seeing.?

---

### Post by QDR06VV9 on 2016-03-25
I have used that method myself PaulW2U and also thought the same as you(Font Size)
But after a couple of reboots they returned to normal..and this was coming from trusty to wily.
EDIT: I think I also increased the DPI to 99 and ticked slight for subpixel smoothing..
Hope this is helpful.

---

### Post by sudodus on 2016-03-25
I have seen similar issues in special cases (extremely small, almost unreadable fonts). I will keep an eye on this issue, and if it pops up again, when I don't want it. You can reproduce it this way:

Boot Lubuntu Xenial live

A.

1. Open a terminal window

2. Run the following command

```
xrandr -s 640x480
```

3. Start firefox

4. Watch the font sizes!

5. Run the following commands (to restore the default screen resolution)

```
xrandr -s $(xrandr | grep +$ | tr -s ' ' '\t' | cut -f2)
```

6. Watch the font sizes!

7. Close firefox

8. Open firefox and compare the font sizes!

9. Close firefox


B. If you don't notice the difference, try this one:

1. Run the following command (if 320x240 is listed by xrandr, otherwise run the lowest resolution)

```
xrandr -s [COLOR="#cc0000"]320x240[/COLOR]
```

2. Start firefox

3. Watch the font sizes!

4. Run the following command

```
xrandr -s $(xrandr | grep +$ | tr -s ' ' '\t' | cut -f2)
```

5. Watch the font sizes!

6. Close firefox

7. Open firefox and compare the font sizes!

-o-

This bug does not affect Xubuntu Xenial

---

### Post by PaulW2U on 2016-03-25
> **runrickus said:**
> I have used that method myself PaulW2U and also thought the same as you(Font Size)
> **sudodus said:**
> This bug does not affect Xubuntu Xenial
Thanks both. The fonts aren't too small but there's definitely a difference in some applications such as Chrome. I've not seen this in any of the upgrades that I've done before.

I've now converted that installation to Xubuntu just to prove that it can be done if you take enough care about what you remove. Most of Unity / Gnome has gone and has been replaced by Xfce alternatives but Xubuntu doesn't look and feel as good on this laptop as it does on the others.

No doubt a full installation of either Ubuntu or Xubuntu will be made sooner rather than later.

---

### Post by sudodus on 2016-03-26
Maybe the bug I call 'this bug' is not the same bug as the one that is affecting you, *PaulW2U*  :-P

---

### Post by PaulW2U on 2016-03-27
> **sudodus said:**
> Maybe the bug I call 'this bug' is not the same bug as the one that is affecting you, *PaulW2U*  :-P
Yes I realise that sudodus. The switch to Xubuntu was a direction in which I wanted to go but that flavour just doesn't look good on this laptop, a Dell N7110. It looks like I'll always be using more than one Ubuntu flavour due to the hardware that I have available.
 
Anyway, I'm now back posting with Ubuntu 16.04 and I am definitely seeing some changes using Chrome and Firefox. Program menu fonts are the same as in 15.10 but forum posts, here and elsewhere, seem to be using smaller fonts which don't always appear to be as "bold" as they were in Ubuntu 15.10. As someone who needs glasses/spectacles to see anything on a computer screen these days I'm finding it difficult to read some of what is posted here.

I'm also finding that terminal fonts are also a little smaller than on Ubuntu 15.10. That was the reason for starting this thread.

So, I might still need to completely reinstall Ubuntu without using existing settings in my /home directory. Or perhaps there have been changes relating to the default fonts used in the latest release that I am unaware of?

---

### Post by sudodus on 2016-03-27
Maybe if you install the Microsoft fonts (for example via the *ubuntu-restricted-extras metapackage) or some other package with fonts, you will get the look and feel of your previous version.

---

### Post by PaulW2U on 2016-03-30
> **sudodus said:**
> Maybe if you install the Microsoft fonts (for example via the *ubuntu-restricted-extras metapackage) or some other package with fonts, you will get the look and feel of your previous version.
Thanks sudodus. I finally got around to looking at this properly. I compared my Chrome/Chromium font settings between laptops and it seems that the Microsoft fonts were missing so smaller but similar fonts were used instead. I found that I had to reinstall ttf-mscorefonts-installer. As soon as the fonts were installed I saw that the settings changed to Chrome's defaults of Times New Roman, Arial and Monospace. Both Gnome terminal and LibreOffice also look better now.

May be I didn't check the box and accept the EULA agreement? Or may be I wasn't given a chance to do so by the upgrade process? I certainly don't remember doing so.

---

### Post by sudodus on 2016-03-30
I'm glad I could help you find a way to fix the fonts :-)

---

### Post by solak-v on 2017-02-07
Actually, I seem to recall installing the microsoft fonts around the time that Chrome started showing tiny text on the tab labels. Frobnicating the text settings of Chrome seems to affect all text *except* the tab labels and Chrome pop-ups.

[IMG]https://www.dropbox.com/s/df2pnx1r053kjyi/Screenshot%20from%202017-02-07%2002-00-35.png[/IMG] [https://www.dropbox.com/s/df2pnx1r053kjyi/Screenshot%20from%202017-02-07%2002-00-35.png?dl=0](https://www.dropbox.com/s/df2pnx1r053kjyi/Screenshot%20from%202017-02-07%2002-00-35.png?dl=0)

---

