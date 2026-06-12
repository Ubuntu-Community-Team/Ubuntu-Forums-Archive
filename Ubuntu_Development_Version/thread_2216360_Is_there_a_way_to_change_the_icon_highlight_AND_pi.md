---
title: "Is there a way to change the icon highlight AND pip size on the Unity bar in 14.04?"
date: 2014-04-11
forum: Ubuntu Development Version
---

### Post by Roasted on 2014-04-11
Hello friends. While I am really enjoying 14.04, I am finding a few UI changes to the Unity bar to be a bit of a drawback, namely the size of the pips (white dots/triangle by the application icons in the Unity bar) as well as the way the icons are highlighted when they need attention that are located in the Unity bar.

For example, here are a few screenshots. First up, the highlight differences of applications that need attention. Here I am comparing 13.10 versus 14.04 using the same application (Quassel) as an example.

[https://www.dropbox.com/s/097fmys59nk61dm/pips1.png](https://www.dropbox.com/s/097fmys59nk61dm/pips1.png)
All four sides are highlighted. Very easy to see. 

[https://www.dropbox.com/s/k80loqpzgj45xt2/pips2.png](https://www.dropbox.com/s/k80loqpzgj45xt2/pips2.png)
Only two sides are highlighted. Meh.

Any way to change this? My settings in Unity Tweak Tool on BOTH installations are identical under the "Launcher" tab.



Second up we have the size of the pips. As mentioned, the pips are the small white items next to the application icon within the Unity bar. These signify whether an application is currently running or not as well as the number of windows that application has open. In these examples, again comparing 13.10 and 14.04, show the size difference of the pips. While the size difference isn't monumental, actual real world usage of 13.10 and 14.04 definitely suggests 13.10 is far easier to see what is running quickly despite my rather decent vision.

[https://www.dropbox.com/sh/mc4k4yyjm5nbbzk/4t6SgqVN8H#lh:null-13.10-unity-32px.png](https://www.dropbox.com/sh/mc4k4yyjm5nbbzk/4t6SgqVN8H#lh:null-13.10-unity-32px.png)
13.10 @ 32 px Unity bar

[https://www.dropbox.com/sh/mc4k4yyjm5nbbzk/4t6SgqVN8H#lh:null-14.04-unity-32px.png](https://www.dropbox.com/sh/mc4k4yyjm5nbbzk/4t6SgqVN8H#lh:null-14.04-unity-32px.png)
14.04 @ 32 px Unity bar

I hate to say it, but if I could have the 13.10 pips + 13.10 highlighting, but in 14.04, I'd be incredibly happy. As it stands I'm not sure how else I can change the above items. I did file a bug regarding the pips if anybody is interested in reading up on the report, or even +1'ing it if you find you share a similar opinion as I do.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1304073](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1304073)

Thank you for your time.

---

### Post by Mateusz Stachowski on 2014-04-11
The pips and launcher in 14.04 are now in SVG to make them scale on HiDPI screens.

[https://plus.google.com/108101042776723451522/posts/5cNhiek1C6h](https://plus.google.com/108101042776723451522/posts/5cNhiek1C6h)

You would think that they should look better now be more clear but I agree they are to small. I checked your bug report as affecting me, lets hope it gets resolved.

I don't use the Edge Illumination Toggles highlithning that you use but when I checked it on my system it also doesn't highlight four sides. This is a regression compared to 13.10 and I think you should open bug or check if it wasn't already reported.

---

### Post by Roasted on 2014-04-11
Thanks for that insight, as well as the +1. Despite the fact I'm a bit late to that G+ party, I posted a comment there highlighting my concerns as well as a link to the bug report. I'm all for improving support for different things, such as HiDPI, but not at the expense of detracting usability from already tried and proven implementations.

EDIT - Also, question for you. What type of highlighting do you use? I switched it back to default but I still cannot figure out what need attention and what doesn't. As far as I can see, the tiny little pip turns blue, but the shade of blue is not all that wildly different for its given size to white. So, roughly translated, this is a seemingly useless way to decipher if something needs attention. Add in the fact that things like Quassel and Skype have no (or broken) implementations to work with Message Tray and you can see why something like this is wildly important, but so far, missing in 14.04.

---

### Post by Mateusz Stachowski on 2014-04-11
Well for things that need attention there is animation setting with two choices. 

For highlighting I use the setting that is called in Unity Tweak Tool "Open applications only" but highlighting doesn't change apart from blue pip when app needs attention.

---

### Post by Roasted on 2014-04-11
> **Mateusz Stachowski said:**
> Well for things that need attention there is animation setting with two choices. 

For highlighting I use the setting that is called in Unity Tweak Tool "Open applications only" but highlighting doesn't change apart from blue pip when app needs attention.

So the only way to tell is by the color of the pip... but the pip is too small... hmm... I'll be 'that guy' for a moment and fire out my blunt translation.

So... that basically means the highlighting feature in Ubuntu 14.04 is broken and useless. 

:(

---

### Post by Roasted on 2014-04-14
Does anybody have anything to add? Any way to increase the pip sizes or perhaps get the highlights to look more obvious and easier to the user to tell of an application needs attention?

I made some gif's to further show what my point is. Both gif's were done on the same computer using the 42px size of the Unity bar, which is far larger than I personally prefer, but it makes the visibility of this a bit easier to see.

In both cases I was testing Skype. One slide shows Skype without needing attention, the next shows Skype with an unread message. It continually flips back and forth so you can see how poor the highlighting is in between the two instances.

One done with colored edges and the other done with the stock "backgrounds only on open icons."

[http://oi62.tinypic.com/nxjgh3.jpg](http://oi62.tinypic.com/nxjgh3.jpg)
[http://oi59.tinypic.com/21mi1w0.jpg](http://oi59.tinypic.com/21mi1w0.jpg)

---

### Post by Mateusz Stachowski on 2014-04-15
You could check if there are other bug reports regarding this problem. I found this one reported in June 2012:

[Is not clear enough when an application has information or not Bug #1012204]("https://bugs.launchpad.net/unity/+bug/1012204")

---

### Post by Roasted on 2014-04-15
Thanks - I sent a comment to that report as well. I hate to sound like a whiny Ubuntu user who feels as though his opinion should matter, but I find something like this to be quite an issue in terms of usability. I'm just surprised I'm not seeing more frustrated users out of this.

---

### Post by toby-whaymand02 on 2014-04-15
it ask to type in the command line to check and the output was:

0:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8210] [1002:9834] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

It keeps repeating itself

---

### Post by toby-whaymand02 on 2014-04-15
It's an AMD Graphic card.  Got this from Amazon:

---

### Post by toby-whaymand02 on 2014-04-15
[http://www.amazon.co.uk/Acer-Aspire-V5-123-Notebook-Silver/dp/B00FLPFZSG#productDetails](http://www.amazon.co.uk/Acer-Aspire-V5-123-Notebook-Silver/dp/B00FLPFZSG#productDetails)

All the specs are on there. :)

---

### Post by Roasted on 2014-04-15
> **toby-whaymand02 said:**
> [http://www.amazon.co.uk/Acer-Aspire-V5-123-Notebook-Silver/dp/B00FLPFZSG#productDetails](http://www.amazon.co.uk/Acer-Aspire-V5-123-Notebook-Silver/dp/B00FLPFZSG#productDetails)

All the specs are on there. :)

Hey there, Toby. You might be best off starting your own thread with that particular issue. This thread has been centralized around a specific change to Unity in 14.04. :)

---

