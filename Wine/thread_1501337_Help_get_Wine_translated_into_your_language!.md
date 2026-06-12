---
title: "Help get Wine translated into your language!"
date: 2010-06-04
forum: Wine
---

### Post by YokoZar on 2010-06-04
To check Wine's translation status, visit [this page](http://source.winehq.org/transl/index.php) - as of this writing, only 4 languages (Dutch, French, German, and Lithuanian) are fully translated.

Wine is different from most programs in Ubuntu - it doesn't use the standard Rosetta translation infrastructure.  The reason is that Wine, internally, must use the same translation mechanisms as Windows.  That means resource files, which in the Windows world require some manual adjustments other than simply changing strings.

**However**, if you don't like messing around with resource files, fear not!  Several Wine developers have volunteered to do all the dirty work for you (even sending patches); all you need to do is translate the actual words.  They send you a glorified text file (.po), and you send it back with your translations included.

It's very easy to get involved, just visit this page: [http://wiki.winehq.org/Wine1.2Translations](http://wiki.winehq.org/Wine1.2Translations)  -- pick one of the developers listed there, shoot them an email, and tell them the language you'd like to translate for.

---

### Post by max127 on 2010-11-14
Wine's translation is the global village for four language of the world...
It is a really amazing.

---

### Post by Kate the Enthusiast on 2011-04-20
> **max127 said:**
> Wine's translation is the global village for four language of the world...
It is a really amazing.

Statistics now: 100% of translation: 

English (United States),
Lithuanian,	
Polish,
Russian,
Swedish,
Swedish (Finland)

---

### Post by dayrehabs on 2011-09-29
Wine binary files can contain the same resource in several languages. 
Wine will choose which language to display based on user settings. For example, the command "LANG=ru_RU wine winecfg" will launch winecfg in Russian (this requires that you have Russian locale information installed in Linux/your other native system). 
The  resources are stored in Windows standard .rc files, which can be  compiled with wrc (the Wine resource compiler). There are also gettext  .po translations in the [po/]("http://source.winehq.org/git/wine.git/?a=tree;f=po;hb=HEAD") directory.
----------------------------------------------------------------------
[COLOR=#1f497d][FONT=Arial]****[/FONT][/COLOR][COLOR=#000000][FONT=Arial]****[/FONT][/COLOR][[COLOR=#000000][FONT=Arial]holistic drug rehabs[/FONT][/COLOR][COLOR=#000000][FONT=Arial]****[/FONT][/COLOR]]("http://www.biophysical-drugrehabs.org/blog/")
[COLOR=#1f497d][FONT=Arial]****[/FONT][/COLOR][COLOR=#000000][FONT=Arial]****[/FONT][/COLOR][[COLOR=#000000][FONT=Arial]holistic rehabs[/FONT][/COLOR][COLOR=#000000][FONT=Arial]****[/FONT][/COLOR]]("http://www.biophysical-drugrehabs.org/blog/")

---

### Post by KenSharp on 2011-10-14
The English locales all default to another English locale (British if I recall correctly).  There is so little difference between them that it's not worth the extra code to duplicate translations.  Therefore I would be very surprised if all English locales were not 100%.

Believe me, I've done a fair bit of work on the translations throughout Ubuntu (including parts of Wine).

---

### Post by shiw on 2011-11-26
> **dayrehabs said:**
> Wine binary files can contain the same resource in several languages. 
Wine will choose which language to display based on user settings. For example, the command "LANG=ru_RU wine winecfg" will launch winecfg in Russian (this requires that you have Russian locale information installed in Linux/your other native system). 
The  resources are stored in Windows standard .rc files, which can be  compiled with wrc (the Wine resource compiler). There are also gettext  .po translations in the [po/]("http://source.winehq.org/git/wine.git/?a=tree;f=po;hb=HEAD") directory.
----------------------------------------------------------------------
[[COLOR=#000000][FONT=Arial]holistic drug rehabs[/FONT][/COLOR]]("http://www.biophysical-drugrehabs.org/blog/")
[[COLOR=#000000][FONT=Arial]holistic rehabs[/FONT][/COLOR]]("http://www.biophysical-drugrehabs.org/blog/")


Hello friends.. wine can be translated through google translate.. you people dont need to complicate things..
Wine is i guess french word but i m not sure.
Have fun

[klarinet]("http://soundshop.si/pihala/klarinet")

---

### Post by Ravi5kumar on 2012-08-15
> **shiw said:**
> Hello friends.. wine can be translated through google translate.. you people dont need to complicate things..
Wine is i guess french word but i m not sure.
Have fun

[klarinet]("http://soundshop.si/pihala/klarinet")

What?! Google translate is sometimes do correct translation but most of the time its not. Do not rely on it!

---

### Post by KenSharp on 2012-08-16
> **shiw said:**
> Hello friends.. wine can be translated through google translate.. you people dont need to complicate things..
Wine is i guess french word but i m not sure.
Have fun

[klarinet]("http://soundshop.si/pihala/klarinet")

Take no notice of this.

---

### Post by smartboyhw on 2012-08-16
OK, I'll help in Chinese (Traditional)

---

### Post by lazarojhr16 on 2012-10-15
thanks for this, now I'm going to help translate into Spanish

---

### Post by U202E on 2013-02-13
would be fun to see wine in 1337 5P34K F0&#1071; TH4 H4X0&#1071;5.
I could translate it to dutch :-)

A lot of people don't mind that wine is not available in their language, because you just (double) click an .exe file and it starts right up.
and most online tutorials are made for the english' wine.

---

### Post by YokoZar on 2013-02-25
This thread is now obsolete -- Wine is translated through standard .po files now (albeit not using Rosetta).  See [http://wiki.winehq.org/Translating](http://wiki.winehq.org/Translating)  for more info if you'd like to help.

---

