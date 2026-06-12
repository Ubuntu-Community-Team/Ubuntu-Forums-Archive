---
title: "Apache2 and foreign characters"
date: 2005-05-03
forum: Server Platforms
---

### Post by blueplazma on 2005-05-03
I use apache2 with libapache2-mod-php4 and php4-mysql to run phpBB. I have some users that have French characters in their posts, such as accented characters, etc. They do not show up. I know it is not client related, because they appear correctly on other web pages. How do I tell Apache to print these characters properly? As it is now, I get things like this when there should be an accented "e" there. 
> * Les arm&#65533;es, les drapeaux*

---

### Post by Gandalf on 2005-05-25
[QUOTE=blueplazma]I use apache2 with libapache2-mod-php4 and php4-mysql to run phpBB. I have some users that have French characters in their posts, such as accented characters, etc. They do not show up. I know it is not client related, because they appear correctly on other web pages. How do I tell Apache to print these characters properly? As it is now, I get things like this when there should be an accented "e" there. 
[/i][/QUOTE]
 i have the exact same problem :(

---

### Post by LordHunter317 on 2005-05-25
You both quite likely have a database locale issue, and possible a system locale issue for Apache as well.

What locale is the MySQL database set to?

---

### Post by Gandalf on 2005-05-25
[QUOTE=LordHunter317]You both quite likely have a database locale issue, and possible a system locale issue for Apache as well.

What locale is the MySQL database set to?[/QUOTE]
 how to know it? i don't have this problem when someone post, mysql is correct, but when i upload via FTP i have this problem, i added all possible fr and en locale to /etc/locale.gen and i ran sudo locale-gen

---

### Post by LordHunter317 on 2005-05-25
[QUOTE=Gandalf]how to know it? i don't have this problem when someone post, mysql is correct, but when i upload via FTP i have this problem, i added all possible fr and en locale to /etc/locale.gen and i ran sudo locale-gen[/QUOTE]
 Well, if your transmitting the file in text mode, stop.  THat'll surely eat it alive over FTP.  Send it as binary.

Make sure you perform the import with the correct locale setting.  Verify by typing 'locale' on the command line.

Make sure the file is in that encoding first. You may want to use iconv to convert it to the proper locale before placing it in MySQL.  

You may also have to tell mysqldump the correct character set.

Without some actual commands, providing real help is difficult.

---

### Post by Gandalf on 2005-05-25
[QUOTE=LordHunter317]Well, if your transmitting the file in text mode, stop.  THat'll surely eat it alive over FTP.  Send it as binary.

Make sure you perform the import with the correct locale setting.  Verify by typing 'locale' on the command line.

Make sure the file is in that encoding first. You may want to use iconv to convert it to the proper locale before placing it in MySQL.  

You may also have to tell mysqldump the correct character set.

Without some actual commands, providing real help is difficult.[/QUOTE]
 i've sent the file via FTP as tar.gz, i decompressed it there and the problem persist ( [http://www.nasreddine.com](http://www.nasreddine.com) is a test site see the characters)

locale output:
```

LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

/etc/locale.gen
```

en_US.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_HK.UTF-8 UTF-8
en_IE.UTF-8 UTF-8
en_IN UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_ZA.UTF-8 UTF-8
en_ZW.UTF-8 UTF-8
en_AU ISO-8859-1
en_BW ISO-8859-1
en_CA ISO-8859-1
en_DK ISO-8859-1
en_GB ISO-8859-1
en_GB.ISO-8859-15 ISO-8859-15
en_HK ISO-8859-1
en_IE ISO-8859-1
en_IE.UTF-8@euro UTF-8
en_IE@euro ISO-8859-15
en_NZ ISO-8859-1
en_PH ISO-8859-1
en_SG ISO-8859-1
en_US ISO-8859-1
en_US.ISO-8859-15 ISO-8859-15
en_ZA ISO-8859-1
en_ZW ISO-8859-1

ar_AE.UTF-8 UTF-8
ar_BH.UTF-8 UTF-8
ar_DZ.UTF-8 UTF-8
ar_EG.UTF-8 UTF-8
ar_IN UTF-8
ar_IQ.UTF-8 UTF-8
ar_JO.UTF-8 UTF-8
ar_KW.UTF-8 UTF-8
ar_LB.UTF-8 UTF-8
ar_LY.UTF-8 UTF-8
ar_MA.UTF-8 UTF-8
ar_OM.UTF-8 UTF-8
ar_QA.UTF-8 UTF-8
ar_SA.UTF-8 UTF-8
ar_SD.UTF-8 UTF-8
ar_SY.UTF-8 UTF-8
ar_TN.UTF-8 UTF-8
ar_YE.UTF-8 UTF-8
ar_AE ISO-8859-6
ar_BH ISO-8859-6
ar_DZ ISO-8859-6
ar_EG ISO-8859-6
ar_IQ ISO-8859-6
ar_JO ISO-8859-6

ar_LB ISO-8859-6
ar_LY ISO-8859-6
ar_MA ISO-8859-6
ar_OM ISO-8859-6
ar_QA ISO-8859-6
ar_SA ISO-8859-6
ar_SD ISO-8859-6
ar_SY ISO-8859-6
ar_TN ISO-8859-6
ar_YE ISO-8859-6

fr_BE.UTF-8 UTF-8
fr_CA.UTF-8 UTF-8
fr_CH.UTF-8 UTF-8
fr_FR.UTF-8 UTF-8
fr_LU.UTF-8 UTF-8
fr_CA ISO-8859-1
fr_CH ISO-8859-1
fr_FR ISO-8859-1
fr_LU ISO-8859-1
fr_LU.UTF-8@euro UTF-8
fr_LU@euro ISO-8859-15

```

---

### Post by LordHunter317 on 2005-05-25
And how did you load it?  What locale were the files in before you loaded them?  If they came from a computer using ISO 8559-1 for example and you loaded them as UTF-8, that would cause the issues you're seeing.

---

### Post by Gandalf on 2005-05-25
[QUOTE=LordHunter317]And how did you load it?  What locale were the files in before you loaded them?  If they came from a computer using ISO 8559-1 for example and you loaded them as UTF-8, that would cause the issues you're seeing.[/QUOTE]
 hmmmm... i download it this time directly with wget still having the issue :o
which locale-gin file you advise? i like to have french-arabic in addition of english characters

---

### Post by LordHunter317 on 2005-05-26
Look, generating locales isn't going to fix crap, so put down the locale-gen and listen.

What locale were the files in on the machine you're generating this tarball and FTP'ing to your current box from?

You need, nay must, answer this question first before you're going to be able to fix this.  This ought to be as easy as logging into that box and running 'locale'.  

Then, on the other box, run iconv to convert the files from that locale to UTF-8.  It'll make your life much eaiser.

---

### Post by Blinklys on 2005-05-26
Have you checked the AddDefaultCharset setting in your httpd.conf? It might be set to On (which implies ISO-8859-1) or a specific charset like UTF-8. This setting can lead to problems.

For example if your editor saves files with ANSI-encoding and Apache's AddDefaultCharset is set to UTF-8. I once had this problem with a Fedora-machine where AddDefaultCharset is set to UTF-8 by default. I don't know what Ubuntu's default setting is, because i haven't tried Apache on Ubuntu yet.

IMHO its best to set AddDefaultCharset to Off, and tell the browser which encoding your using by putting something like in this your HTML:

[HTML]<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">[/HTML]
Of course if your using something like phpBB you probably don't want go in and add all this to yourself ;-) so your best option is probably setting AddDefaultCharset to the same encoding as the files.

---

### Post by Gandalf on 2005-05-26
[QUOTE=LordHunter317]Look, generating locales isn't going to fix crap, so put down the locale-gen and listen.

What locale were the files in on the machine you're generating this tarball and FTP'ing to your current box from?

You need, nay must, answer this question first before you're going to be able to fix this.  This ought to be as easy as logging into that box and running 'locale'.  

Then, on the other box, run iconv to convert the files from that locale to UTF-8.  It'll make your life much eaiser.[/QUOTE]
 the problem is hat i don't know what encoding was the machibe with, i tod you itried rar archive donwload via wget and i unrar it directly

---

### Post by LordHunter317 on 2005-05-26
Then you're going to have to guess.  ISO8859-1 is a good start.  I'm almost 99% certain your issue is your loading the data as UTF-8 when it's really in an another encoding.  Until you figure out what encoding it is and either load it as that, or convert it to UTF-8 (I recommend the latter) you're going to have trouble.

Making a backup and using iconv to convert from likely locales to UTF-8 and view the output would be a good way to go about this.

---

### Post by Gandalf on 2005-05-26
[QUOTE=LordHunter317]Then you're going to have to guess.  ISO8859-1 is a good start.  I'm almost 99% certain your issue is your loading the data as UTF-8 when it's really in an another encoding.  Until you figure out what encoding it is and either load it as that, or convert it to UTF-8 (I recommend the latter) you're going to have trouble.

Making a backup and using iconv to convert from likely locales to UTF-8 and view the output would be a good way to go about this.[/QUOTE]
 is there a way to make ubuntu use ISO8859-1 by default?
what is the encoding of debian sarge?

---

### Post by LordHunter317 on 2005-05-26
[QUOTE=Gandalf]is there a way to make ubuntu use ISO8859-1 by default?
what is the encoding of debian sarge?[/QUOTE]
 Debian sarge is likely using the traditional C/POSIX ASCII locale by default.  Maybe ISO-8859-1.

You could change the default locale, but I don't really recommend it.  UTF-8 is the future, and it's eaiser to convert things now to be the right way then fall back to the old way.

---

### Post by Avatar on 2005-10-13
I have the same problem..

Trying to find what's wrong I've noticed this:
the same page, on the Web is shown correctly but loaded from my Apache isn't

Could it be a problem with my Apache2 charset encoding? something not reletad to Linux fonts, but to the way the web server try to encode them?

---

### Post by dudus on 2006-04-12
[QUOTE=Avatar]I have the same problem..

Trying to find what's wrong I've noticed this:
the same page, on the Web is shown correctly but loaded from my Apache isn't

Could it be a problem with my Apache2 charset encoding? something not reletad to Linux fonts, but to the way the web server try to encode them?[/QUOTE]
try this:
```
sudo vim /etc/apache2/conf.d/charset
```
and change the file to:
```
AddDefaultCharset ISO-8859-1
```

Then restart apache:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by HuitZiloP on 2006-07-30
Thank you very much dudus,that did the trick! :D

---

