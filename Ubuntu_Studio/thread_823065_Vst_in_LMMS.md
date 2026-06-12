---
title: "Vst in LMMS"
date: 2008-06-08
forum: Ubuntu Studio
---

### Post by ethanklein on 2008-06-08
Does anyone know a decent tutorial as to getting VSTs/VSTis working in LMMS.
LMMS= Linux Multimedia Studio.

---

### Post by pgiblox on 2008-06-10
No decent tutorial.  It is passed down generation to generation.  Basically, goto your Settings Dialog and look at where the VST Directory is.  Then, copy your VST DLL's into that folder.  You will need WINE support to use VSTi in LMMS.

There is a Vestige article in our Wiki. But it is currently empty.  Maybe someone wouldn't mind updating it?  Otherwise, I'll make sure this is documented before we release LMMS-0.4.0 later this month.  [http://lmms.sourceforge.net/wiki/index.php?title=Plugins]("http://lmms.sourceforge.net/wiki/index.php?title=Plugins")

---

### Post by d3k4y on 2009-04-18
I took the time to write a thorough tutorial for you guys on how to load a VST-plugin in LMMS.  Check it out, and let me know what you think.

[http://hacktivision.com/index.php/2009/04/18/how-to-load-vsts-in-lmms-using-vestige?blog=2]("http://hacktivision.com/index.php/2009/04/18/how-to-load-vsts-in-lmms-using-vestige?blog=2")

It's a beautiful day in Chicago today, and I sat here writing this, so check out the rest of my blog and/or give me some feedback if you have time.  Thanks!

---

### Post by neu2buntu on 2009-04-18
good tutorial.... im not seeing the images (using firefox) ...... and another thing to add that some vst need the extra files alongside the .dll  eg on synth1 v107 the .sy1 files are the soundbank settings... i usually just extract all the files in the .zip to my vst folder and use the "recreate folders " option in file-roller and this seems to work for most vst...

---

### Post by simtaalo on 2009-04-18
the key thing to remember is just make sure the .dll file for vst effects HAS to be in the vst folder directly , but with vsti you can have that within another subdirectory in order to keep things tidy.

nice tutorial, although it only explains vsti. think i might have to do a segment on this for the open source musician podcast.

---

### Post by elliotn on 2009-04-19
Fl studio vst?

---

### Post by simtaalo on 2009-04-20
> **elliotn said:**
> Fl studio vst?

???

---

### Post by d3k4y on 2009-04-20
The images are hosted on flickr.  I guess I'm a cheapo when it comes to bandwidth.  Anyways, if you can't see them, perhaps you are at work and flickr is blocked?  See the post just before the tutorial to fix that problem.

---

### Post by K.Stoyanov on 2009-05-14
Ok, but this is for VSTi (instruments), I want to add VST effect - how?

---

### Post by tobydox on 2009-05-15
Put the according DLL files into ~/lmms/vst/ (or whatever your VST directory is (which you can specify in the settings dialog)) and then all those DLLs in there should be listed as effects in the effect-select-dialog.

---

### Post by neu2buntu on 2009-05-15
> **tobydox said:**
> Put the according DLL files into ~/lmms/vst/ (or whatever your VST directory is (which you can specify in the settings dialog)) and then all those DLLs in there should be listed as effects in the effect-select-dialog.
hi tobydox,how are you? are you 1 of the developers of lmms as in your "ppa"

it is a brilliant software, vst(i) support is really good through vestige...if you need any testing done i can oblige !!

---

### Post by tubunu on 2009-12-23
> **d3k4y said:**
> I took the time to write a thorough tutorial for you guys on how to load a VST-plugin in LMMS.  Check it out, and let me know what you think.

[http://hacktivision.com/index.php/2009/04/18/how-to-load-vsts-in-lmms-using-vestige?blog=2]("http://hacktivision.com/index.php/2009/04/18/how-to-load-vsts-in-lmms-using-vestige?blog=2")

Could someone update this information? The link is broken. Thanks.

---

### Post by logistical on 2010-04-27
does anyone know if its possble to automate knobs in plugins? i went to FL just for that, but FL gives me nothing but problems.

---

### Post by logistical on 2010-04-28
bump

---

### Post by Mr_Squiggles on 2010-05-25
Very good tutorial, images work fine in chrome

---

### Post by mmetelko on 2012-03-17
> **ethanklein said:**
> Does anyone know a decent tutorial as to getting VSTs/VSTis working in LMMS.
LMMS= Linux Multimedia Studio.
Try this:
[tutorial]("http://hacktivision.com/index.php/2009/04/18/how-to-load-vsts-in-lmms-using-vestige?blog=2")
good luck!
:guitar:

---

### Post by adam933 on 2012-06-11
I'm using LMMS 4.13 and Vestige.
The VST GUI pops up (MDA_piano.dll) after a few seconds, but Vestige never completes the load, and LMMS is frozen.  I have to click on the "x" (close window) to finally get a pop-up to close LMMS.  I've tried several VSTi that supposedly work in LMMS.

Any ideas for me to try?
Thanks

---

### Post by sgx on 2012-06-12
Reaper in a pre-1.4 wine, with wineasio, is by far, the best
vst combination for linux. Get an nVidia graphics card
that is a year or two older than the newest, and an
maudio pci soundcard. Problems will vanish,
like hippies who turned down the soap aisle at the grocery.

Cheers

---

### Post by Sylos on 2012-06-12
> **sgx said:**
> Problems will vanish,
like hippies who turned down the soap aisle at the grocery.


Quality!!!:lolflag:

I never managed to get Reaper to work. Might just be me and my set up (I've had mucho problemo with other stuff) I moved onto festige which at least seems to load some of my VSTs but I havent had time to test the functionality yet. As a back up you could try running festige and jacking in and out of the VST.

Cheers

---

### Post by sgx on 2012-06-16
[http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound](http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound)

wine 1.4 now requires a quick registry edit to enable alsa in wine, which may be needed for reaper to work. Wineasio needs to be installed,
and run command

regsvr32 wineasio.dll

then choose asio and wineasio in the reaper Device prefs,
and enable your midi keyboard in the reaper Midi prefs.

Cheers

what would happen to the hippies if the  Coca Cola and Twinkies
were stocked in the middle of the soap aisle?

---

