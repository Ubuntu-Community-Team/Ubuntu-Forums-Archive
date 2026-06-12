---
title: "HOWTO: Make WINE non-ugly."
date: 2009-07-05
forum: Wine
---

### Post by X-BANE on 2009-07-05
[IMG]http://i803.photobucket.com/albums/yy313/ACRO_ASARVA/LOL.png[/IMG]

Looks better than the ugly 'Windows Classic' theme doesn't it?

So, if you want to get rid of the ugliness, here's a guide...

******
Step 1:
******

Download this file;

[http://rapidshare.com/files/252454969/Resources.tar.gz.html](http://rapidshare.com/files/252454969/Resources.tar.gz.html)

And extract it too your desktop. Next copy the extracted Resources folder too; 

**Applications>Wine>Browse C:\ Drive > windows.** 

******
Step 2:
******

 Goto;

**Applications>Wine>Configure Wine**

Click the **"Desktop Intergration" tab**, and click the dropdown "Theme" menu (it says 'No Theme'), and select "Windows XP style", then in the dropdown "Color" menu under the dropdown "Theme" menu select your color scheme (Default (blue), Silver or Olive Green) and click apply. Now close Wine Configuration, and re-open it (Applications>Wine>Configure Wine), you now have a nice new Windows XP style Color scheme!

Next onto Wine font smoothing...

******
Step 3:
******

Copy & paste this into terminal (Applications>Accessories>Terminal);

**wget [http://files.polosatus.ru/winefontssmoothing_en.sh]("http://files.polosatus.ru/winefontssmoothing_en.sh%28press")**

(now press enter)

And then copy & paste this too;

**bash winefontssmoothing_en.sh**

(now press enter)

This will bring up a little menu inside the Terminal which looks like this;

[IMG]http://i803.photobucket.com/albums/yy313/ACRO_ASARVA/Menu.png[/IMG]
                                                                  

Select number 3 "Subpixel smoothing (ClearType) RGB" (press down twice and hit enter) and your done!

Now Wine has full font smoothing!

Enjoy!

**EDIT: This is a W.I.P so please be patient. Also apparently some people may experience slowdown due to the use of theming. I have never experienced this, and I have run a large amount of software under Wine. But due to the slight possibility this may affect you, please be aware :)**

---

### Post by cogadh on 2009-07-05
I know this is still a work in progress, but you might want to let people know about the significant performance hit they may take by using a Windows theme with Wine.

---

### Post by X-BANE on 2009-07-05
> **cogadh said:**
> I know this is still a work in progress, but you might want to let people know about the significant performance hit they may take by using a Windows theme with Wine.

There is no performance hit, what are you talking about?

---

### Post by cogadh on 2009-07-05
Wine's support for theming is limited at best and using anything other than the "classic" Windows theme can slow Wine down to unusable levels. Fixing this is one part of Wine's contribution to the [Google Summer of Code]("http://wiki.winehq.org/SummerOfCode") and has been the subject of some of Wine and Ubuntu's outstanding bugs:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/111061](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/111061) (note the comments)
[http://bugs.winehq.org/show_bug.cgi?id=18546](http://bugs.winehq.org/show_bug.cgi?id=18546)

---

### Post by X-BANE on 2009-07-05
I have done this since Wine 1.0, and I've never experienced any slowdown. Does it only affect certain hardware setups?

---

### Post by cogadh on 2009-07-05
Not that I am aware of, though what apps you are running with Wine may affect it.

---

### Post by X-BANE on 2009-07-05
> **cogadh said:**
> Not that I am aware of, though what apps you are running with Wine may affect it.

I've run everything from MS Office to Oblivion, and the only problems I've hit are the inherent limitations of Wine itself. Never has changing the theme affected anything!

---

### Post by SunnyRabbiera on 2009-07-06
Yeh I installed the royale theme with no issue.

---

