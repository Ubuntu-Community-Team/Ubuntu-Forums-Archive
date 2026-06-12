---
title: "Bible languages"
date: 2006-09-26
forum: Ubuntu Christian Edition
---

### Post by rogier.de.groot on 2006-09-26
Alright, dumb question mode on:

are there bible translations other then the English one hiding in the repositories somewhere? There seems to be a Spanish one,
but I can't seem to find one in my native Dutch. For the sword thing I mean, if that wasn't obvious... Or is there some other program with a Dutch bible translation?

*note for people who know me*
It's for my girlfriend - I'm perfectly capable of reading the English version myself

---

### Post by Raphink on 2006-09-26
Hi,

There are a few sword modules in the repositories. The Ichthux team [cares to add more of them]("https://features.launchpad.net/products/ichthux/+spec/more-sword-modules"), so please let us know which ones you would like to see, among the GPL-compliant ones on [the Sword modules page]("http://crosswire.org/sword/modules/index.jsp").

In Edgy, we currently have the following modules packaged:
sword-comm-mhcc - Matthew Henry Concise Commentary for SWORD
sword-comm-pers - Personal Commentary for SWORD
sword-comm-scofield - Scofield Reference Notes, 1917 edition for SWORD
sword-comm-tdavid - C. H. Spurgeon's Treasury of David for SWORD
sword-dict-naves - Naves Topical Bible for SWORD
sword-dict-strongs-greek - Strong's Greek Bible Dictionary for SWORD
sword-dict-strongs-hebrew - Strong's Hebrew Bible Dictionary for SWORD
sword-text-arasvd - SWORD module of the Smith & Van Dyke 1865 Arabic Bible
sword-text-frelsg - French Louis Segond Version with Strongs Numbers for SWORD
sword-text-gerlut1545 - SWORD module of Martin Luther's 1545 German Bible
sword-text-itadio - SWORD module of the 1649 Italian Giovanni Diodati Bibbia Bible
sword-text-kjv - King James Version with Strongs Numbers for SWORD
sword-text-rst - 1876 Russian Synodal Translation SWORD module
sword-text-sparv - Spanish Reina-Valera Bible (1909) for SWORD
sword-text-tr - Textus Receptus (1550/1894) Greek New Testament SWORD module
sword-text-web - World English Bible (WEB) for SWORD
sword-text-wlc - Westminster Leningrad Codex Version with Strong Numbers for SWORD


We also provide language packs in Ubuntu to make it easier to install the [Sword modules by languages]("https://features.launchpad.net/products/ichthux/+spec/locale-bibles"): 
sword-language-pack-ar - Sword modules for the Arabic language
sword-language-pack-de - Sword modules for the German language
sword-language-pack-el - Sword modules for the Greek language
sword-language-pack-en - Sword modules for the English language
sword-language-pack-es - Sword modules for the Spanish language
sword-language-pack-fr - Sword modules for the French language
sword-language-pack-he - Sword modules for the Hebrew language
sword-language-pack-it - Sword modules for the Italian language
sword-language-pack-ru - Sword modules for the Russian language


God bless


Raphaël

---

### Post by montgoej on 2006-09-26
Try [Crosswire]("http://crosswire.org/sword/modules/ModDisp.jsp?modType=Bibles") for Bibles.  The link has a Bible in Dutch(language code NL I believe) and many others.  It is a raw zip file, so you'll have to install it yourself, but it shouldn't be too hard.  If you have any trouble pm me and I may be able to help.
~Jordan Montgomery

---

### Post by mhancoc7 on 2006-09-26
You can use the "Module Manager" in GnomeSword. You can access it with  Edit > Module Manager. You can change the settings from CDROM to Remote. After you refresh you can install the modules directly.

I hope that helps, Jereme

---

### Post by rogier.de.groot on 2006-09-27
I'm actually using Kubuntu, so no joy on the gnomesword idea, but I will try installing those modules. Thanks to all

---

### Post by Raphink on 2006-09-27
Ichthux is based on Kubuntu and will provide what you need, together with BibleTime and Kio-Sword as Biblestudy programs :)

God bless


Raphaël

---

### Post by jimw on 2006-10-05
I just tried to apt-get some of these.  All I get is an error message, for example:
 
 Couldn't find package sword-language-pack-en

I'm using the Dapper release, with gnomesword.

I've had spotty success downloading and installing from the raw-text offerings.  The Chamorro and Kekchi, for istance, give nothing but verse-numbers, no text.

I have been able to get the WEB in, which I greatly appreciate.

Though I installed them all by the same method, taking the .conf files from the mods.d files of the particular language pack and putting them in the /usr/share/sword/mods.d directory, then taking the cointents of the ztext files of the packs and putting them into the /usr/share/sword/modules/texts/ztext directory, three work fine, two don't.  

Can anyone give me some pointers?

Thanks,

JimW

---

### Post by Raphink on 2006-10-05
Hi Jim,

The sword-language-packs packages have been added to Edgy, not to Dapper. If you want to benefit from the language packs, you have two options: either upgrade to Edgy (or wait for it to be released as stable, in 20 days), or add the following line to your sources.list:

deb [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main

and then update.

This will allow you to install the following packages:

[LIST]
[*] sword-language-pack-ar: Sword modules for the Arabic language
[*]   sword-language-pack-de: Sword modules for the German language
[*]   sword-language-pack-el: Sword modules for the Greek language
[*]   sword-language-pack-en: Sword modules for the English language
[*]   sword-language-pack-es: Sword modules for the Spanish language
[*]   sword-language-pack-fr: Sword modules for the French language
[*]   sword-language-pack-he: Sword modules for the Hebrew language
[*]   sword-language-pack-it: Sword modules for the Italian language
[*]   sword-language-pack-ko: Sword modules for the Korean language
[*]   sword-language-pack-ru: Sword modules for the Russian language
[*]   sword-text-arasvd: SWOD module of the Smith & Van Dyke 1865 Arabic Bible
[*]   sword-text-frelsg: French Louis Segond Version with Strongs Numbers for SWORD
[*]   sword-text-gerlut1545: SWORD module of Martin Luther's 1545 German Bible
[*]   sword-text-itadio: SWORD module of the 1649 Italian Giovanni Diodati Bibbia Bible
[*]   sword-text-korean: Korean Bible SWORD module
[*]   sword-text-rst: 1876 Russian Synodal Translation SWORD module
[*]   sword-text-tr: Textus Receptus (1550/1894) Greek New Testament SWORD module
[*]   sword-text-wlc:  Westminster Leningrad Codex Version with Strong Numbers for SWORD
[/LIST]

... and others, that are listed on [http://archive.ichthux.com/](http://archive.ichthux.com/) . This archive should only be used with Ubuntu Dapper though, and should not used with Ubuntu Edgy anymore.

These modules are also in Ubuntu Edgy, apart from the Korean one which currently misses some licensing informations, so they will be maintained in the future when you upgrade your system.

God bless


Raphaël

---

### Post by jimw on 2006-10-05
[QUOTE=Raphink;1582645]Hi Jim,

The sword-language-packs packages have been added to Edgy, not to Dapper. If you want to benefit from the language packs, you have two options: either upgrade to Edgy (or wait for it to be released as stable, in 20 days), or add the following line to your sources.list:

deb [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main

and then update.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Thanks.  If it's only 20 days, I think I'll wait for Edgy.

No notion of what might have gone wrong with the other ones, e.g. the Kekchi and Chamorro?

Jimw

---

### Post by thathatman on 2006-10-16
Regarding the WLC (Hebrew text) and WHNU (Greek Text) modules, I am not seeing any vowel markings or accents. Are there fonts that I need to install in order to see those correctly? The WLC info does indeed say that it has vowel markings and other pointings. I could probably handle an unaccented greek text, but without vowels in Hebrew I'm absolutely lost.

Thanks in advance.

---

