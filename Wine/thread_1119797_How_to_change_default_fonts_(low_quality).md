---
title: "How to change default fonts (low quality)"
date: 2009-04-08
forum: Wine
---

### Post by UranUtan on 2009-04-08
Using Wine 1.1.18 on Ubuntu 8.10 x64.

The look of Gnome desktop is OK. However, when I use Wine, the fonts are rendered with pretty low quaility. From the Wine configuration screen to the applications running from within Wine (mp3Tag and WinRar). This issue exist on 3 different machines (physical, not VM) with totally different hardware.

The fonts look small, pixelated and thin. In the application, sometimes, the icons in the toolbar becomes all black. If I minimize & maximize the application window then the icon re-appear with colors.

The applications works OK which is the main goal. However, it would be nice if the fonts are displayed with the same quality than Gnome or Windows.

Hope there is an easy fix. Thanks in advance for any help.

---

### Post by UranUtan on 2009-04-08
Found a quite acceptable way to fix:

1. Copy ONE Windows font in /home/ (username) /.wine/drive_c/windows/Fonts

2. Then open wine Config screen, the font in Step #1 will be picked up by wine as default font. ead that somewhere from Google search results, forgot to keep the URL.

3. Copy the remaining Windows fonts, that you think you will use, in the same target folder than Step #1

4. Activate anti-aliasing by using the method described in "Easy way to enable font smoothing in Wine "
[http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)

5. Wine config, select Graphics tab. Set screen resolution, change value to 125 dpi. This will scale the font to be bigger.

Now the fonts look OK, but still too thin. I use Trebuchet MS font and within Wine it looks different than normally (thinner and smaller). Hope someone can figure out how to fix this for good.

---

