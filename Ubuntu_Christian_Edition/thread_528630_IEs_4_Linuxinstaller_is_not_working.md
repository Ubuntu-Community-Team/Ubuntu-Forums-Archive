---
title: "IEs 4 Linuxinstaller is not working"
date: 2007-08-18
forum: Ubuntu Christian Edition
---

### Post by redlabour on 2007-08-18
I get this Message everytime i try to install IEs 4 Linux under Ubuntu CE (Feisty)

> There seems to have been an error. You will need to run the IEs 4 Linux Installer again. This is not uncommon and is usually due to a problem with some of the downloaded files.

But in the Console it tells me everything was ok. :(

---

### Post by mhancoc7 on 2007-08-18
> **redlabour said:**
> I get this Message everytime i try to install IEs 4 Linux under Ubuntu CE (Feisty)



But in the Console it tells me everything was ok. :(

That error message usually means that some of the files needed were not successfully downloaded. This is very common with the core IEs4Linux script. Usually if you keeping trying it eventually the needed files will get downloaded.

Jereme

---

### Post by redlabour on 2007-08-19
Try it now for 2 weeks .... :(

---

### Post by mhancoc7 on 2007-08-19
> **redlabour said:**
> Try it now for 2 weeks .... :(

Sorry for your trouble. What connection speed do you have?

Jereme

---

### Post by redlabour on 2007-08-19
Adsl 20.000

---

### Post by mhancoc7 on 2007-08-20
> **redlabour said:**
> Adsl 20.000

Well, I was honestly hoping you would say dial up. ;) That would have made for an easy answer. I will try to test it out to be sure that I am able to download the needed files.

Thanks, Jereme

---

### Post by redlabour on 2007-08-20
Well, the Download of all Files are working and there are no Errormessages. Only at the End after installing all Packages there is this Error.

---

### Post by mhancoc7 on 2007-08-20
> **redlabour said:**
> Well, the Download of all Files are working and there are no Errormessages. Only at the End after installing all Packages there is this Error.

There are lots of files that get fetched and then the script cabextracts them to get the needed files. The error that you are seeing means that some of the files that are used from the cabextracted ones are not there.

Jereme

---

### Post by redlabour on 2007-08-20
Maybe a incompatibility if some of the Packages are allready installed after e-sword Installation or something else?

---

### Post by mhancoc7 on 2007-08-20
> **redlabour said:**
> Maybe a incompatibility if some of the Packages are allready installed after e-sword Installation or something else?

It should not have anything to do with that because each script creates separate installation directories  to avoid conflicts.

Jereme

---

### Post by redlabour on 2007-08-21
OK - did not use the Ubuntu CE IEs4Linux Installer any longer.

With the official Installer from [http://www.tatanka.com.br/ies4linux/page/De/Hauptseite](http://www.tatanka.com.br/ies4linux/page/De/Hauptseite) it works ! :guitar:

---

### Post by mhancoc7 on 2007-08-21
> **redlabour said:**
> OK - did not use the Ubuntu CE IEs4Linux Installer any longer.

With the official Installer from [http://www.tatanka.com.br/ies4linux/page/De/Hauptseite](http://www.tatanka.com.br/ies4linux/page/De/Hauptseite) it works ! :guitar:

Glad that you got it working. That is quite strange though since the Ubuntu CE installer downloads that one and then runs it. :confused:

Oh well, I am just glad you got it working. :)

Jereme

---

### Post by tak1150 on 2007-09-04
I have the same problem and the original package from tatanka.com did not work for me either.

The download seemed to have gone ok, but the actual cabextracting seems to cause the problems. Here is the error mssg:

```
Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/tak/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IE_EXTRA.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: no valid cabinets found
/home/tak/.ies4linux/downloads/ie6/EN-US//VGX.CAB: no valid cabinets found
An error occured when trying to cabextract some files.

```

---

### Post by tak1150 on 2007-09-05
oops. I had the "cab" files blocked in Dansguardian and I forgot (excuse: dansguardian is not on my computer, but on the proxy server). After I allowed "cab" files. installation worked fine.

But when I run ie6, the address bar just says "h" and it cannot connect to most sites (I can connect to microsoft and tatanka.com) :confused:

---

### Post by mhancoc7 on 2007-09-05
> **tak1150 said:**
> oops. I had the "cab" files blocked in Dansguardian and I forgot (excuse: dansguardian is not on my computer, but on the proxy server). After I allowed "cab" files. installation worked fine.

But when I run ie6, the address bar just says "h" and it cannot connect to most sites (I can connect to microsoft and tatanka.com) :confused:

Yes, you must Disable filtering in Ubuntu CE before running the script. There is a warning in the installer.

I had the problem with IE6 having the "h" the url field. This seems to be fixed in the latest release of Wine.

Jereme

---

### Post by rykel on 2007-12-04
> **tak1150 said:**
> 
```
Installing IE 6
snip
An error occured when trying to cabextract some files.

```

Hi,

I am using Ubuntu Gutsy worldly edition, and having the same problem... any idea what I should do?

---

### Post by jgt157 on 2008-01-21
I'm having the same problem.  None of the files are downloading with ies4linux-2.99.0.  Anybody know what's going on?  I checked the ies4linux support forum and everything is locked.  Has Microsoft put the brakes on this maybe?

JimT

---

