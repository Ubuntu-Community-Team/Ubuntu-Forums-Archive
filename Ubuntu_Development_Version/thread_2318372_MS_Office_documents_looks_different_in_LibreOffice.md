---
title: "MS Office documents looks different in LibreOffice."
date: 2016-03-25
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-03-25
[COLOR=#111111][FONT=Ubuntu]System / Software (s)
Ubuntu 16.04
Windows 10
MS Office version 2016
LibreOffice Vers. 5.1.1.3
Font: Calibri[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
It seems fonts are bigger in LibreOffice than windows MS office:[/FONT][/COLOR][HTML]
Something that would fit in one line in windows.

Something that would fit in one line in
windows

[/HTML][COLOR=#111111][FONT=Ubuntu]Top MS Office
Bottom LibreOffice


Pictures:

[/FONT][/COLOR][https://dl.dropboxusercontent.com/u/443930/Libreoffice/LibreOffice.png ]("https://dl.dropboxusercontent.com/u/443930/Libreoffice/LibreOffice.png")
[https://dl.dropboxusercontent.com/u/443930/Libreoffice/windows.png](https://dl.dropboxusercontent.com/u/443930/Libreoffice/windows.png)[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The company logo placed in the Top Text Right side also appears on the top left further down than it should.
Installed the restricted fonts, no difference. ([FONT=Consolas]ttf-mscorefonts-installer)
[/FONT]
This is not a major issue but it would be nice to move as much work as possible over til Ubuntu so I dont have to fire up the VM every time i need to edit or send something. I need to be able to trust that it will look the same in all platforms. [/FONT][/COLOR]

---

### Post by italo.vignoli on 2016-03-25
First of all, according to the license you are allowed to use Calibri only when running Microsoft Office. Second, Calibri has been designed to preserve the metrics information only whit Microsoft Office, so the result that you get is intentional. Third, LibreOffice installs the free font Carlito which is metrically compatible with Calibri but does not have the same legal limitations, and you should configure LibreOffice to replace Calibri with Carlito (and Cambria with Caladea) to preserve the visual aspect of the document. Calibri is not part of MS Core Fonts, and is not available for Linux in any legal way. MS C-Fonts, or ClearType fonts, should be avoided as much as possible, even by MS Office users. Please have a look at the patents that cover ClearType fonts, and you will understand why.

---

### Post by izznogooood on 2016-03-25
This is a good answer, but please tell me how to do this?....

---

### Post by QDR06VV9 on 2016-03-25
You can download the fonts from [www.openfontlibrary.org]("http://www.openfontlibrary.org")

In LibreOffice, you exchange Calibri and Cambria with Carlito and Caladea this way:

    Open LibreOffice
    Select Tools
    Choose "Fonts"
    Define a substitution for each of the two fonts (Calibri -> Carlito, Cambria -> Caladea).
    Remember to check "Always" in the substitution lines.
**EDIT: You may have to rebuilt your font cache after installing..**
```
sudo fc-cache -f -v
```

---

### Post by vasa1 on 2016-03-25
It's very nice to see someone from tdf answering questions here. Welcome, Sir!

> **runrickus said:**
> You can download the fonts from [www.openfontlibrary.org]("http://www.openfontlibrary.org")

In LibreOffice, you exchange Calibri and Cambria with Carlito and Caladea this way:

    Open the "**Extras**" menu.
...
Couple of clarifications please ...
Do you not have *Carlito* installed by default? I seem to have it by default on my LibreOffice (downloaded direct from [https://www.libreoffice.org/](https://www.libreoffice.org/)).

Don't you mean "Tools" menu?

> **a.m.andersen said:**
> ... I need to be able to trust that it will look the same in all platforms. ...
If an application is available natively across platforms, that *should* be possible. If "looking the same in all platforms" is paramount, you'll need to find such an application. I think it is unlikely that a creator of one application will be able to decode another application's closed source to accommodate such a need. Also, AFAICT, LibreOffice is compliant with international specifications. 

Why don't you just stay with MS Windows? I'm suggesting this because you'll be bound to come across more such instances and there's no point in sacrificing your productivity.

I, fortunately, don't have such a requirement. On the once-a-year occasion that I need proprietary software for filing and uploading my tax returns, my CA does the job (and gouges me).

---

### Post by izznogooood on 2016-03-26
Thank you very much.

---

### Post by QDR06VV9 on 2016-03-26
> **vasa1 said:**
> 
Couple of clarifications please ...
Do you not have *Carlito* installed by default? I seem to have it by default on my LibreOffice (downloaded direct from [https://www.libreoffice.org/](https://www.libreoffice.org/)).

Don't you mean "Tools" menu?

Thanks vasa1 I was very much in a hurray to post but did a very poor job...to the OP that probably sounded like i had a new language  going on.
Just open LibreOffice  And as vasa1 kindly pointed out go to tools>down to Options click that and off to left you will see fonts check that then on the right side you will see below the main greyed out window an option with a checkbox that will read **"Apply replacement table**" Tick that.
Now you can change the font you want(Carltio) from the automatic or default drop-downs.
To make permanent Check the box that reads **"Always" **then hit[B] OK.
[/B]I have included a screenshot to help make sense of the steps.
Well I hope this is a little more understandable.

---

### Post by vasa1 on 2016-03-26
@runrickus, could you clarify whether you had to download the Carlito font from [www.openfontlibrary.org](www.openfontlibrary.org) or did it come with your LibreOffice install?

---

### Post by QDR06VV9 on 2016-03-26
> **vasa1 said:**
> @runrickus, could you clarify whether you had to download the Carlito font from [www.openfontlibrary.org]("http://www.openfontlibrary.org") or did it come with your LibreOffice install?

Yes had to download from the link provided.
Just checked also in Xenial and no Carlito to be found.

---

### Post by izznogooood on 2016-03-26
I still have the problem where the logo switch sides. (which is minor)

Other than that i also had to download and unzip the fonts to /usr/share/fonts. chmod 755 (I forgot and had an epiphany in the shower) and this works great!

---

### Post by vasa1 on 2016-03-26
> **runrickus said:**
> Yes had to download from the link provided.
Just checked also in Xenial and no Carlito to be found.
Hi, can you mention the version of LibO on your Xenial. I install LibO direct from [http://www.libreoffice.org/download/libreoffice-fresh/](http://www.libreoffice.org/download/libreoffice-fresh/) and not from the standard repos or ppas. My LibO is version 5.1.0.3. And it has Carlito by default which is why I'm asking. Going back a bit, it seems these fonts should be available even on LibO installed from standard repos or ppas:  [[MIR] Caladea and Carlito fonts, essential fallback fonts]("https://bugs.launchpad.net/ubuntu/+source/fonts-crosextra-caladea/+bug/1276252"), [https://ask.libreoffice.org/en/question/15041/calibri-and-cambria-fonts-in-libreoffice/](https://ask.libreoffice.org/en/question/15041/calibri-and-cambria-fonts-in-libreoffice/)

More: [https://wiki.debian.org/SubstitutingCalibriAndCambriaFonts](https://wiki.debian.org/SubstitutingCalibriAndCambriaFonts). Sickening or pragmatic / putting bread on the table.

---

### Post by QDR06VV9 on 2016-03-27
> **vasa1 said:**
> Hi, can you mention the version of LibO on your Xenial. I install LibO direct from [http://www.libreoffice.org/download/libreoffice-fresh/](http://www.libreoffice.org/download/libreoffice-fresh/) and not from the standard repos or ppas. My LibO is version 5.1.0.3. And it has Carlito by default which is why I'm asking. Going back a bit, it seems these fonts should be available even on LibO installed from standard repos or ppas:  [[MIR] Caladea and Carlito fonts, essential fallback fonts]("https://bugs.launchpad.net/ubuntu/+source/fonts-crosextra-caladea/+bug/1276252"), [https://ask.libreoffice.org/en/question/15041/calibri-and-cambria-fonts-in-libreoffice/](https://ask.libreoffice.org/en/question/15041/calibri-and-cambria-fonts-in-libreoffice/)

More: [https://wiki.debian.org/SubstitutingCalibriAndCambriaFonts](https://wiki.debian.org/SubstitutingCalibriAndCambriaFonts). Sickening or pragmatic / putting bread on the table.


As mentioned already by me and the OP the fonts were not there..had to be downloaded.
This is with stock(standard repos) and no addtional PPA's.
This install of xenial is a few months old also.
```
Version: 5.1.1.3
Build ID: 1:5.1.1-0ubuntu1
CPU Threads: 2; OS Version: Linux 4.5; UI Render: default; 
Locale: en-US (en_US.UTF-8)
```
Kind Regards

---

### Post by vasa1 on 2016-03-27
So this seems to be a policy decision by Canonical *not* to include certain fonts that the original version supplies. I wonder what the thinking behind that is.

---

