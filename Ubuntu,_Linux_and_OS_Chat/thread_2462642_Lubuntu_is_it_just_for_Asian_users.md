---
title: "Lubuntu: is it just for Asian users?"
date: 2021-05-24
forum: Ubuntu, Linux and OS Chat
---

### Post by GhX6GZMB on 2021-05-24
Just did a Lubuntu 20.04.2 fresh install on an empty machine.
Language: German
Keyboard: German
Locale: Europe, Berlin
BIOS set to German

This is the list of installed fonts:

```
ab_admin@6910p:/usr/share/fonts/truetype$ ls -la
insgesamt 204
drwxr-xr-x 50 root root 4096 Feb  4 03:34 .
drwxr-xr-x  8 root root 4096 Feb  4 03:34 ..
drwxr-xr-x  2 root root 4096 Feb  4 03:34 abyssinica
drwxr-xr-x  2 root root 4096 Feb  4 03:34 ancient-scripts
drwxr-xr-x  2 root root 4096 Feb  4 03:33 dejavu
drwxr-xr-x  2 root root 4096 Feb  4 03:33 droid
drwxr-xr-x  2 root root 4096 Feb  4 03:34 fonts-beng-extra
drwxr-xr-x  2 root root 4096 Feb  4 03:33 fonts-deva-extra
drwxr-xr-x  2 root root 4096 Feb  4 03:34 fonts-gujr-extra
drwxr-xr-x  2 root root 4096 Feb  4 03:34 fonts-guru-extra
drwxr-xr-x  2 root root 4096 Feb  4 03:33 fonts-kalapi
drwxr-xr-x  2 root root 4096 Feb  4 03:34 fonts-orya-extra
drwxr-xr-x  2 root root 4096 Feb  4 03:34 fonts-telu-extra
drwxr-xr-x  2 root root 4096 Feb  4 03:34 fonts-yrsa-rasa
drwxr-xr-x  2 root root 4096 Feb  4 03:34 freefont
drwxr-xr-x  2 root root 4096 Feb  4 03:34 Gargi
drwxr-xr-x  2 root root 4096 Feb  4 03:34 Gubbi
drwxr-xr-x  2 root root 4096 Feb  4 03:34 hack
drwxr-xr-x  2 root root 4096 Feb  4 03:33 kacst
drwxr-xr-x  2 root root 4096 Feb  4 03:33 kacst-one                                                                          
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lao                                                                                
drwxr-xr-x  2 root root 4096 Feb  4 03:33 liberation                                                                         
drwxr-xr-x  2 root root 4096 Feb  4 03:34 liberation2                                                                        
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-assamese                                                                     
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-bengali                                                                      
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-devanagari                                                                   
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-gujarati
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-kannada
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-malayalam
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-oriya
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-punjabi
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-tamil
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-tamil-classical
drwxr-xr-x  2 root root 4096 Feb  4 03:34 lohit-telugu
drwxr-xr-x  2 root root 4096 Feb  4 03:33 malayalam
drwxr-xr-x  2 root root 4096 Feb  4 03:34 Nakula
drwxr-xr-x  2 root root 4096 Feb  4 03:34 Navilu
drwxr-xr-x  2 root root 4096 Feb  4 03:34 noto
drwxr-xr-x  2 root root 4096 Feb  4 03:34 openoffice
drwxr-xr-x  2 root root 4096 Feb  4 03:34 padauk
drwxr-xr-x  2 root root 4096 Feb  4 03:34 pagul
drwxr-xr-x  2 root root 4096 Feb  4 03:34 Sahadeva
drwxr-xr-x  2 root root 4096 Feb  4 03:34 samyak
drwxr-xr-x  2 root root 4096 Feb  4 03:34 samyak-fonts
drwxr-xr-x  2 root root 4096 Feb  4 03:34 Sarai
drwxr-xr-x  2 root root 4096 Feb  4 03:34 sinhala
drwxr-xr-x  2 root root 4096 Feb  4 03:34 tibetan-machine
drwxr-xr-x  2 root root 4096 Feb  4 03:34 tlwg
drwxr-xr-x  2 root root 4096 Feb  4 03:34 ttf-khmeros-core
drwxr-xr-x  2 root root 4096 Feb  4 03:34 ubuntu
```

Huh?

Comments from the Lubuntu Team (if they even read this) are also welcome.

Thanks.

---

### Post by guiverc on 2021-05-24
We occasionally hear this comment, but as close to Asia as any team member, being an aussie (*thus Australasian*) who only speaks English (badly).

I picked one font (`fonts-kalapi` a font I've never used) from your listing; I did an `apt-cache rdepends` and see that it's a requirement of LibreOffice.   

Are you asking us not to include LibreOffice? because it pulls in fonts you don't like as dependencies?

You can look at [https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop) and search for *fonts* and see what we list as dependencies (3 font packages only are required)
  

[LIST]
[*][fonts-dejavu-core]("https://packages.ubuntu.com/focal/fonts-dejavu-core")      Vera font family derivate with additional characters 
[*][fonts-freefont-ttf]("https://packages.ubuntu.com/focal/fonts-freefont-ttf")        Freefont Serif, Sans and Mono Truetype fonts 
[*][xfonts-efont-unicode]("https://packages.ubuntu.com/focal/xfonts-efont-unicode")   /efont/ Unicode fonts for X which cover various scripts 
[/LIST]

---

### Post by CatKiller on 2021-05-24
> **guiverc said:**
> We occasionally hear this comment, 

... and it's always from this guy.

---

### Post by CharlesA on 2021-05-24
What's wrong with the list of fonts provided?

---

### Post by QIII on 2021-05-24
It would seem that the Lubuntu developers are in cahoots with the Kubuntu developers.  The default fonts listed are exactly the same.

I'd spin up a vanilla Ubuntu VM, but I'm pretty sure what I'd find.

The answer to the pointedly Eurocentric question in your title is "No".  Ubuntu is for everyone, not just speakers of English and German.

---

### Post by guiverc on 2021-05-25
Kubuntu & Lubuntu are Qt based; maybe the Libreoffice requirements are pulled in because of our common Qt libs with LibreOffice...  in my prior comment I stopped my examination of how `fonts-kalapi` go into my Lubuntu system when I got to

`libreoffice-l10n-gu`

 & just wrote LibreOffice in my post (LibreOffice pulls in a lot of language files).

Apologies to whomever reported my last thread. I used some language that I wondered about before I pressed "POST"; and should have acted first. Sorry

Maybe helpful : [https://askubuntu.com/questions/1140030/how-to-disable-unused-asiatic-fonts](https://askubuntu.com/questions/1140030/how-to-disable-unused-asiatic-fonts)

---

### Post by mastablasta on 2021-05-25
> [COLOR=#000000][FONT=&quot]ab_admin@6910p:/usr/share/fonts/truetype$ ls -la
[/FONT][/COLOR][COLOR=#ff0000]**[FONT=&quot]insgesamt 204[/FONT]**[/COLOR]

these are not all 204 fonts. you have posted only 50 in your code tags. they provide you with various other characters to write. i bet German fonts are also installed. as are other CE fonts, so you can read and write &#269;,&#353;,&#263;,&#382;,&#273; for example or &#321;, so you can write and read the name of author Stanis&#322;aw Lem for exmaple.

i mean i usually have no need for ö, ü, ß and simillar nonsense in my day to day communication, but i have them installed on linux, windows, android... because there is an occasion when i want to read or write something in German.

and who knows maybe i want to read & write in Chinese or Japanese as well on occasion (i would have to learn them first though). still their letters (fonts) display properly on my PC because they are installed.

---

### Post by The Cog on 2021-05-25
No. It's for all users. I think you will find that all those fonts you list are also capable of rendering non-asian characters.
Which characters are you having difficulty rendering?

---

### Post by coffeecat on 2021-05-25
Previous threads about the same subject:

[https://ubuntuforums.org/showthread.php?t=2435727](https://ubuntuforums.org/showthread.php?t=2435727)
[https://ubuntuforums.org/showthread.php?t=2442361](https://ubuntuforums.org/showthread.php?t=2442361)

@ml9104, posting about Asian fonts in any Ubuntu flavour again will not be well received.

Thread closed.

---

