---
title: "Thousands of built-in low quality fonts makes typography very hard to manage"
date: 2015-04-01
forum: Ubuntu, Linux and OS Chat
---

### Post by halfbeing on 2015-04-01
Isn't it time for Ubuntu to rethink the fonts that come with it? I have just done a clean install and I have over 1900 fonts (including the few installed with Wine). Most of these fonts are low quality novelty fonts. It is impossible to sift through all this dross to find the fonts I need. Even within the main families of fonts, i.e. serif, sans etc, the quality is very variable and it is very hard to choose the one that will actually work or will have all the characters I might need (for instance the default font in my browser turned out yesterday to render an o-ogonek very badly). How can we know which are the genuinely high quality multi-lingual fonts? I think this mess really needs to be sorted out. Better to have a handful of good fonts than hundreds of half-baked attempts at proper typefaces and a legion of useless gimmicks.

---

### Post by Ko_Char on 2015-04-01
1. Does the font look ugly in other applications other than browser? (what does it look like in Libreoffice?)

Default font in browser might not be the font you think. Websites overwrite which fonts to be displayed. Unless you manually forced your browser to display a particular font for a particular language, websites displays what they think is best for most of their visitors.

When websites choose to display Microsoft fonts, there is a problem. OS uses different technologies to display fonts. The fonts that work perfectly in Microsoft might look very ugly in Linux or may be even wrong for complex script. If the browser displays that kind of Microsoft font, you get ugly font in your browser. 

Ubuntu has its own set of fonts that work in Ubuntu. To avoid that, please don't mix fonts. Some fonts that are for Microsoft or that comes with Wine are really really bad in browsers. 

2. You can use font manager to manage fonts or find characters that you want. (Fontmatrix is an example)

3. There is project from Google called Google Noto Fonts. They support multi-languages. If you still think the current fonts are unusable, you may consider using that. 

[https://www.google.com/get/noto/#/](https://www.google.com/get/noto/#/)

---

### Post by craig10x on 2015-04-01
Did you install the microsoft fonts when you installed ubuntu restricted extras?  I always do, and fonts look fine to me when i browse.  Unfortunately, the license agreement windows (where you have to say yes to get them) doesn't always pop up when installing the restricted extras from the software center, so i'd suggest you install synaptic package manager (if you don't already have it) and look for: ttf-mscorefonts-installer
then have it re-install them and check yes when the agreement window pops up (always works in package manager)...It may show them as installed but they aren't until the agreement window is checked yes...
Worth a try, anyway... ;)

---

### Post by ian-weisser on 2015-04-02
> **halfbeing said:**
> I have just done a clean install and I have over 1900 fonts (including the few installed with Wine). Most of these fonts are low quality novelty fonts. It is impossible to sift through all this dross to find the fonts I need.

We welcome recommendations to remove specific packages that include low-quality fonts.
Use 'dpkg -S /path/to/font' to discover which package provides a font.

Typographers are also welcome to contribute improvements to upstream open fonts, or to fork and publish an improved version.

Those packages may be dependencies of other applications, making them harder to remove. Do feel free to file upstream bugs, either to remove the dependency, to improve the font, to remove the font from the package, to use a substitute open font, etc.

Sifting through the fonts and packages and coming up with specific recommendations is a task for community members, not paid engineers. So feel free to pitch in anywhere you like.

After there are specific package recommendations to discuss, the ubuntu-desktop mailing list seems the appropriate place for the discussion.

---

### Post by grahammechanical on 2015-04-02
Ubuntu along with other Linux distibutions use Unicode fonts. These Unicode fonts have a character set large enough to hold thousands of characters unlike the old Microsoft Truetype fonts which held a very limited number of characters. Thus requiring the development of many fonts to get the character coverage and variety that people needed.

When I was using Windows 98 and wanted to include Greek characters in my documents I had to install a Greek Truetype font. I do not have to do that now that I am using Unicode fonts. I simply change the keyboard layout.

Take for example FreeSerif. That font has 7,203 characters. It includes character sets for several languages as well as some sets of what you call novelty fonts but which others find useful. If I had the skill, I could write in many different languages just using the one font.

Then there is the Ubuntu font family. It contains character sets for between 200 and 250 languages in five different language scripts but in reality it is only five fonts: Ubuntu; Ubuntu Monospace; Ubuntu Light; Ubuntu Medium and Ubuntu condensed.

Libreoffice brought in the Liberation Serif set. But I do not have trouble finding the fonts I prefer because Libreoffice remembers which fonts I was using with the document and they are presented at the top of the font selection menu.

It is my opinion that what you are counting as fonts are actually groups of characters inside a few Unicode fonts.

---

