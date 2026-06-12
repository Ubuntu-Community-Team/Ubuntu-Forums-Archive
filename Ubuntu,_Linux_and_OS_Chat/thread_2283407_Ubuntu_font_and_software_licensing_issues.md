---
title: "Ubuntu font and software licensing issues?"
date: 2015-06-21
forum: Ubuntu, Linux and OS Chat
---

### Post by notjustanotherone on 2015-06-21
Hi, I don't even know which subforum to ask these questions under, so I will try here because it seems to deal with the Ubuntu operating system itself.

1. First, were the default fonts in LibreOffice writer installed by LibreOffice or by Ubuntu?

2. Second, where are the licenses for the fonts that came preinstalled with the Ubuntu operating system (assuming there were in fact such fonts)? I'm currently using 14.04 LTS.

Let me give some background to these questions. Whenever I download a new font, I make sure to check the font's license file to make sure I have permission to use the font for my purposes. Some fonts from sites like Google Fonts are freely usable by everyone. Other fonts require users to pay a license fee before they are allowed to use the font.

Suppose I'm planning to write a book or some other commercial publication. Would it be safe to use the fonts available by default in LibreOffice? I can think of at least 2 possible reasons why they might not be safe. For one, I don't know what license these fonts were available under, so I don't know whether it's safe to use these fonts for commercial purposes.

But there's an even bigger problem. If these fonts were made available under the GNU GPL, any publication I write may be considered a derivative work of the font, which means I would be forced to make the publication available under the GNU GPL also. Doesn't this mean I basically gave up the copyright to the book if I spent all that time and had to make it freely available?

There's yet another problem. Ubuntu and LibreOffice are both open source software. If I write anything in it, wouldn't my work be considered a derivative work of open source work?

Given these problems, can any person who writes for commercial purposes safely use open source programs or any fonts that came with Ubuntu to do their work?

---

### Post by grahammechanical on 2015-06-21
To start with, there is this

[http://font.ubuntu.com/licence/](http://font.ubuntu.com/licence/)

As for the rest of the fonts such as those that come with LibreOffice, open the Font View uitilty, select an font and click Info.  That will give you details about the copyright holder of that particular font. Use the internet to track down the licensing conditions.

As for the rest of the stuff that you go on about, I am afraid that none of us here have the legal qualifications to give answers. That is what you want is it not? Professional advice and not simple opinions of users? 

[https://www.microsoft.com/typography/fontpack/eula.htm](https://www.microsoft.com/typography/fontpack/eula.htm)

[http://www.gnu.org/licenses/gpl-3.0.en.html](http://www.gnu.org/licenses/gpl-3.0.en.html)

[https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

[http://www.gnu.org/licenses/license-list.html#SoftwareLicenses](http://www.gnu.org/licenses/license-list.html#SoftwareLicenses)

I think that you will find that Open Source licenses apply to software source code and not to documents or even files produced by programs licensed for use under an Open source licence.

You are missing the point about Free and Open Source Software (FOSS) licensing.

[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

[http://www.gnu.org/philosophy/pragmatic.html](http://www.gnu.org/philosophy/pragmatic.html)

These other fonts that you have used in the past? Did the copyright holders claim ownership of work that you created using their fonts? No? So, why do you think that the copyright holders of fonts that are installed by an open source application would be any different?

[https://creativecommons.org/licenses/](https://creativecommons.org/licenses/)

Regards.

---

### Post by Bucky Ball on 2015-06-21
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by notjustanotherone on 2015-06-21
[QUOTE=grahammechanical]

As for the rest of the fonts such as those that come with LibreOffice, open the Font View uitilty, select an font and click Info.  That will give you details about the copyright holder of that particular font. Use the internet to track down the licensing conditions.

[/QUOTE]

Let's start with this. Where is this "Font View" utility?

---

### Post by CantankRus on 2015-06-22
Let's start with this. [**_[COLOR="#B22222"]How to Find applications using the dash[/COLOR]_**]("https://help.ubuntu.com/stable/ubuntu-help/unity-dash-intro.html")

---

### Post by Geoffrey_Arndt on 2015-06-22
You can also find font info for many fonts on wikipedia (including the Liberation font family, bitstream and others).   Your publisher has experts and resources that can advise of any potential issues, but as long as your using open source fonts, you're fine (you copyright the content, not the tools, materials, etc.)

---

### Post by notjustanotherone on 2015-06-25
Thanks for all the helpful posts. I've done some serious reading, and if I'm not mistaken, the GPL does not require the output of programs such as LibreOffice to also be licensed under the GPL.

Fonts are really the only difficulty left. I know the license of every font I download and install, but there are some that came with the system or might have been installed through packages. Wine's ttf-mscorefonts-installer package is one example. Font Viewer is a good start because it gives the copyright holder's name for every font. The only real difficulty left is to track down the licenses for each of those fonts. So far I've resorted to Googling every one, but surely there's a better way. Does anyone know if license files for the fonts that came installed with the system were installed along with the fonts?

---

### Post by coldraven on 2015-06-26
> Wine's ttf-mscorefonts-installer package is one example.
When installing that package you have to agree to it's terms and conditions. Most people don't read them but in your case I suppose that you would.
You can find the terms in READ_ME! here: /usr/share/doc/msttcorefonts , it's inside the compressed file READ_ME!.gz just double click to extract or read it.

---

### Post by notjustanotherone on 2015-06-29
I did find the package ttf-mscorefonts-installer installed on my computer, but /usr/share/doc/msttcorefonts does not exist. Are you sure that's the right directory?

---

### Post by CantankRus on 2015-06-29
/usr/share/doc/ttf-mscorefonts-installer

---

### Post by notjustanotherone on 2015-06-30
Well, that license agreement contains a restrictive provision. This line might mean I can't use the fonts in ttf-mscorefonts-installer:

"Copies of the SOFTWARE PRODUCT may not be distributed for profit either on a standalone basis or included as part of your own product."

If I distribute a document with the font files embedded, those font files are software, so a lawyer might argue that I can't distribute the document because of the agreement. So I should be able to distribute a copy of the document without the fonts right? Then I saw this line:

"You may not rename, edit or create any derivative works from the SOFTWARE PRODUCT, other than subsetting when embedding them in documents."

Even if I had permission to use the fonts, it sounds like that permission assumes my document is a derivative work of the software product. How can I not own the copyright to something I wrote? Unless someone with legal training comes up with a better interpretation, I'd say the fonts in ttf-mscorefonts-installer are out.

Thanks for the help on finding the license agreement for this package. I'm still looking for the licenses for all the other fonts that were preinstalled. I don't know if those other fonts were installed by Ubuntu, LibreOffice, or some other package, so any help would be appreciated. There must be a better way than Googling every font in Font Viewer.

---

