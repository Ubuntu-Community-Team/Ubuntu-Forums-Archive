---
title: "lmms error"
date: 2011-10-09
forum: Ubuntu Studio
---

### Post by marcia on 2011-10-09
Dear All,

I am able to play my little inexpensive old radio shack midi keyboard through lmms version 0.4.12 64 bit using my x-midi usb e-mu connector. It makes this humble keyboard sound great except I keep getting an error pop up every few moments: Counld not write file /recover.mmp. You probaably are not permitted to write to this file. Please make sure you have write-access to the file and try again. 

I did make sure permissions were allowing write access however I still get this error. I researched it and it seems there was very little about this error, so I am asking here. I have kubuntu lucid 10.04 with kxstudio repos enabled. Any suggestions for correcting this will be greatly appreciated.

Thank you.

Marcia

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-10
Try going here [http://lmms.sourceforge.net/ ]("http://lmms.sourceforge.net/")
to use the IRC channel to get support.
I used my sister-in-law's casio keyboard and it worked well in Lmms, but I have 0.4.10 running on Ubuntu 11.04 (I think I also tried it on Lubuntu 11.04)....  you might try installing the 32bit.  I know 32 bit stuff works on the 64 bit machines, and usually tends to be less buggy.  Or check out Launchpad, they usually respond pretty quick if you need help.

---

### Post by marcia on 2011-10-10
Thank you for your suggestions. I will check this out and report back. I appreciate your help.

Thanks.

Marcia

---

### Post by sgx on 2011-10-10
Hi, you can use your keyboard without lmms, follow this guide
with screenshots to use a world-class synthesizer, zynaddsubfx:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

lmms adds a lot of possibilities, and therefore complexities, that many people don't need, and bugs that people don't want. Mastering qjackctl will let you use many instruments.

Cheers

---

### Post by marcia on 2011-10-12
Thank you for the great link. I will study that. 

Yes, I have and do use zynaddsubfx and I like it very much. There are just a few sounds I still need that zyn does not have that I get from using soundfonts such as the sitar sound. Maybe I can incorporate that with zyn using jack and qsynth.Actually I think zynaddsubfx always sounds great with my radio shack midi keyboard. 

I like to try many audio apps and love variety I suppose.I have used and liked amsynth, ams, horgand, aeolus, lmms. zynaddsubfx, ladspa effects, ardour, audacity, hydrogen,etc., and want to try even more. 

Thanks for the great suggestions.

Marcia

---

### Post by sgx on 2011-10-13
Hi, here are more excellent  soundbanks for zynaddsubfx users,
from Folderol, Cormi, Laba170 and Adriano Petrosillo,
and the Author himself, in case you, or anyone have missed them. They work in Yoshimi also.

[www.kvraudio.com/banks.php?s=dl&id=1365](www.kvraudio.com/banks.php?s=dl&id=1365)
[www.kvraudio.com/banks.php?s=dl&id=1455](www.kvraudio.com/banks.php?s=dl&id=1455)
[www.kvraudio.com/banks.php?s=dl&id=1285](www.kvraudio.com/banks.php?s=dl&id=1285)

For this next one below, right-click on the link, and choose
save-as with your browser:

[http://www.gospel.bo.it/albums/userpics/10222/Adriano_Petrosillo_Banks_-_06-Nov-09_tar.gz](http://www.gospel.bo.it/albums/userpics/10222/Adriano_Petrosillo_Banks_-_06-Nov-09_tar.gz)

Paul Nasca, zynaddsubfx author has provided 180 sounds in this archive:

unsorted_zynaddsubfxParameters20060615.zip   found here:

[http://zynaddsubfx.sourceforge.net/doc/instruments](http://zynaddsubfx.sourceforge.net/doc/instruments)

Use the 'open parameters' menu to load these multi-timbral patches,
not the banks! Place the expanded archive a separate folder, (named like aaa-zyn so it's first in the file requester), in
/usr/share/zynaddsubfx
some fabulous sounds are in there, so rename them to your needs!
Save your new creations with menu 'save parameters'.

Cheers

---

### Post by marcia on 2011-10-13
Thank you very much for the extra soundfont links. I will be eager to try them out.

Such fun!

Thanks.

Marcia

---

### Post by sgx on 2011-10-13
> **marcia said:**
> Thank you very much for the extra soundfont links. I will be eager to try them out.

Such fun!

Thanks.

Marcia
Just to make sure, these are not soundfonts, but banks of
sounds for zynaddsubfx (and its yoshimi variant)
After unarchiving the folders, copy them to

/usr/share/zynaddsubfx/banks 

the unsorted folder, is noted in the previous post.

Are you using the multi-timbral feature of zyn?

Click the little triangle widget to the right of '1'
just under the blue effect area. It will change to
the next highest number, 2 of a possible 16. Now click the empty
tickbox by 'enabled', to enable  a second sound.
Under MIDI Chn Rcv on the right, change it from 2 to 1,
so both sounds will play at once. Add more sounds, and
when happy, use the menu option

File-->Save All Parameters   to name and save it.
It will have a .xmz extension

Cheers



Cheers

---

### Post by marcia on 2011-10-15
Thank you for explaining about soundfonts and banks.

I had not tried the multi-timbral feature yet and I definitely will. I am truly a newbie with most sound apps, however I am looking forward to expanding my knowledge.

Thank you for the great tips.

Marcia

---

### Post by sgx on 2011-10-15
Another thing, when using multiple sounds in zynaddsubfx, there is
a button labelled 'Mode -Poly' under the Edit Instrument button.
You may need to click it, and change some sounds  from poly to mono mode, as they can overload the computer sound system. Using a sustain pedal too much, can also send so much midi data, that sounds lock up for a few moments.

Legato mode, is similar to mono mode, but notes sweep from one to the next,
instead of jumping. Various sounds and melodies will benefit from these choices.

Carefully choosing 3 or 4 sounds of different styles, can produce
elegant and beautiful results.

Arpeggios for rythm, pads for backround, and a lead with sweeping
motion, are good combos to invest in. A notebook will be handy to keep track of your favourite sounds, and use the 'save all parameters'
menu choice so you can reload the ones you like.

Did you know many experts consider this one of the worlds greatest
software instruments?

Cheers

---

### Post by sgx on 2011-10-15
Where to find the banks you copied to
/usr/share/zynaddsubfx? Its not obvious!

Use the menu  Instruments-Show Instrument bank.

A big empty panel will appear.
Click the little triangle widget by the 'Refresh Bank List' button.

All the banks should now appear in a list you can choose from.
Do this each time you want to use a different bank.

Cheers

---

