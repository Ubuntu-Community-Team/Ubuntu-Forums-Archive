---
title: "call me stupid but I cant get IEs4Linux to work"
date: 2009-04-01
forum: Wine
---

### Post by fourtyseven on 2009-04-01
Normally I wouldn't really care but I need to use IE for a certain application at work. I am running Ubuntu 8.04 AMD64 and I've read countless forum threads concerning IEs4Linux and its associated problems. However I have not been able to find someone with the exact same problem as me.
I have downloaded and installed wine, cabextract and IEs4Linux but initially when I ran IEs4Linux I got the following common error:

> IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install everything at: /home/alan/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   98%  SCR56EN.CABAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/SCR56EN.CAB

My next step was to download SCR56EN.CAB manually and paste it in .ies4linux/downloads/IE6/EN-US. I also opened up the install.sh file in the IEs4Linux directory and commented out the part where its instructed to download SCR56EN.CAB. My reasoning was that I have all the necessary files and all I needed IEs4Linux to do was to install IE.
However, now I get the following output:

> IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install everything at: /home/alan/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB

  Downloading from macromedia.com:
   swflash.cab
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/alan/.ies4linux/downloads/ie6/EN-US/SCR56EN.CAB: WARNING; file possibly truncated by 7272 bytes.
/home/alan/.ies4linux/downloads/ie6/EN-US/SCR56EN.CAB: no valid cabinets found
An error occured when trying to cabextract some files.


I am now stuck and dont know how to proceed from here. Anyone know what Im doing wrong?

---

### Post by SeanHodges on 2009-04-01
> **fourtyseven said:**
> Normally I wouldn't really care but I need to use IE for a certain application at work. I am running Ubuntu 8.04 AMD64 and I've read countless forum threads concerning IEs4Linux and its associated problems. However I have not been able to find someone with the exact same problem as me.
I have downloaded and installed wine, cabextract and IEs4Linux but initially when I ran IEs4Linux I got the following common error:


My next step was to download SCR56EN.CAB manually and paste it in .ies4linux/downloads/IE6/EN-US. I also opened up the install.sh file in the IEs4Linux directory and commented out the part where its instructed to download SCR56EN.CAB. My reasoning was that I have all the necessary files and all I needed IEs4Linux to do was to install IE.
However, now I get the following output:



I am now stuck and dont know how to proceed from here. Anyone know what Im doing wrong?

I would delete the .ies4linux directory altogether (or rename it) and run the installer again. Copying arbitrary files from the Internet will probably just complicate things more as you'll need the exact version, and thats assuming it hasn't been modified for ies4linux.

---

### Post by fourtyseven on 2009-04-01
> **SeanHodges said:**
> I would delete the .ies4linux directory altogether (or rename it) and run the installer again.

Thanks for the reply. I have tried your suggestion countless times and I just end up with error number one; **98% SCR56EN.CABAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/SCR56EN.CAB**

---

### Post by SeanHodges on 2009-04-01
I expect you have already seen this thread: [http://ubuntuforums.org/showthread.php?p=6676592](http://ubuntuforums.org/showthread.php?p=6676592)

Sorry, I'm not sure what the problem might be. You might have some luck contacting the developer directly, as it looks like others have had similar difficulties: [http://www.tatanka.com.br/ies4linux/page/User:S%C3%A9rgio_Lopes#Contact](http://www.tatanka.com.br/ies4linux/page/User:S%C3%A9rgio_Lopes#Contact)

---

### Post by fourtyseven on 2009-04-01
I have read the particular ubuntu thread and tried all of the methods suggested; still no success. I have emailed the guy at ies4linux about two weeks ago but he has not replied. 
Is there anyone out there who can help with ies4linux or does anyone know of another method to get IE running in ubuntu?

---

### Post by fourtyseven on 2009-04-02
anyone?

---

### Post by fourtyseven on 2009-04-03
For anyone who may read this post, IEs4Linux does NOT work (for me anyway). I have tried for almost 3 weeks but have had no success. 
My solution was to install virtualbox, install xp into the virtualbox and use IE that way. Its slightly more effort but at least it works.

---

### Post by SeanHodges on 2009-04-03
> **fourtyseven said:**
> For anyone who may read this post, IEs4Linux does NOT work (for me anyway). I have tried for almost 3 weeks but have had no success. 
My solution was to install virtualbox, install xp into the virtualbox and use IE that way. Its slightly more effort but at least it works.

Sorry to hear you were had so much trouble fourtyseven, ies4linux always used to work for me (back when I needed it). Considering you have had no direct contact with the developer, it's possible that the project is dormant...

If I get chance, I'll take a look at it myself, in the meantime I guess Virtualbox will give you what you need.

---

### Post by alex.rayu on 2009-04-03
I suspect the IEs4Linux is falling into oblivion because IE6 can now be installed in WINE with winetricks. This is what I have been doing for a number of releases now. So, supposedly, the ies4linux developer does no longer see need to keep his project up.

---

### Post by Onesimus on 2009-04-03
I remember having this problem (though it was sometime ago).  I _think_ I solved it be just installing twice (i.e. directly over the first installation).  

You might want to re-start right from the beginning.  Just in case you have messed up the .ies4linux directory.  Then re-install twice.

Hope this helps

---

### Post by fourtyseven on 2009-04-03
> **alex.rayu said:**
> IE6 can now be installed in WINE with winetricks. 
I did not know this; I will give it a try.

---

### Post by Wim De Winter on 2009-04-06
Hi, I have comparable problems, but with the mfc42.cab file. Trying Virtualbox now.

---

### Post by enig_ on 2009-05-07
I had a similar problem when installing ies4linux, I would get this error: 
 DCOM98.EXE!! An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: DCOM98.EXE

I found how to fix this,  here: [http://tehpost.blogspot.com/](http://tehpost.blogspot.com/)
 
Just look under "ies4linux problem during installation" in case you can't find the post or if for some reason the post gets deleted, this is what you need to do:

When you run IE4Linux, click on the advance button, go to the Wget flags section and add this :
-t 10 -T 10

Everything should read like ths:
 -c -t 10 -T 10

Run ie4linux installation again .:P

---

