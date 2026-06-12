---
title: "How to fix your Audio EQ! - Audacious"
date: 2009-03-03
forum: Tutorials
---

### Post by Nano_ext3 on 2009-03-03
Ok, for all who trouble with audacious in Ubunutu, this seemed to work to fix the EQ:

1. Download the Winamp preset EQ's
2. Open up terminal
3. wget [http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz)
4. To install the presets for the Audacious media player type:
   gunzip -c winamp_presets.gz > ~/.config/audacious/eq.preset

Restart Audacious.  Now heres the sticker.  What I think happens is Audaciou's Pre-Amp (to the left on EQ), is pushing too much Hz (?) through the audio channel.  Now, I do use the ALSA mixer, as nvidia's fails to work by default on my 8.04 machine.  I don't believe it matters if your using ALSA or not, I believe this to be tied to linnux + sound cards in general.

Select a Winamp preamp, and turn on the EQ to ON.  WOW! Its loud and fuzzy you say!  Well turn the Pre-amp down slightly until the tinnyness and garble subsidees.  Many a times I just turn off the preamp.

I am quite certain the preamp messes with the EQ in terms of the Base dB's (decibel) frequency.  Think of if you've ever used Adobe Premiere, raising the dB too high and what, tiny crackly , or fuzzy audio! The same goes for a guitar amp, turn up the pre-amp (your amp) too high, then plug in a external effect pedal and turn up the sound and voila, crackly shitty audio.

Please reply if help is needed or if you have better methods.  This worked for me to use the eq as I want.  If you have trouble with anything else try going to your sound prefs. and using the ALSA mixer.



Note!!!:  If you use Ubuntu / Debian, I specially added the "Gnome-Alsamixer" to my arsenal as well.  This allows you to change Master, and sub level audio tracks without the terminal.  This will let you bump up you base master volume without destroying anything.  The default audio applet on the top gnome panel bar only raises it so much.  Find this program in Add/Remove Programs, or do "sudo apt-get install gnome-alsamixer "



Cheers!


Nano

---

### Post by ibuclaw on 2009-03-03
Nice HowTo.

You could perhaps re-edit it and replace some cusses here and there to make it more family friendly.

Regards
Iain

---

### Post by Nano_ext3 on 2009-03-03
Will do thx for the input.

---

### Post by damnthatdog on 2010-03-30
[I]Hello,

Let me get something straight. 

To get the eq presets you do step no. 3, right?

Well,after I type the command I get the following message

 [I]--2010-03-30 12:34:19--  [http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz)
Resolving [www.xmms.org](www.xmms.org)... 200.35.148.194
Connecting to [www.xmms.org|200.35.148.194|:80](www.xmms.org|200.35.148.194|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-30 12:34:20 ERROR 404: Not Found.[/I][/I]

Well, what am I doing wrong?

Tnx

---

### Post by damnthatdog on 2010-03-30
Ok...found them on 

*[http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz](http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz)*

Installed and it works

---

### Post by ozwoofer on 2011-11-14
ok so i am having the same problem as damnthatdog...


--2010-03-30 12:34:19-- [http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz)
Resolving [www.xmms.org](www.xmms.org)... 200.35.148.194
Connecting to [www.xmms.org|200.35.148.194|:80](www.xmms.org|200.35.148.194|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-30 12:34:20 ERROR 404: Not Found.


but i have tried and tried and i dont understand what i am doing wrong. i am putting in the terminal but nothing is happening. ahhh so frustrating! can anyone help?

cheers

---

### Post by CSchultz on 2012-09-02
There is an other Method to load Winamp Presets into audacious-player:
go to the Windows-Partition eg: /windows/C/Documents and settings/Username/Appdata/Winamp/ and there is a file named "Winamp.q1". 
Now you go to audacious into the EQ-Window and klick on _**Preset>Import>Winamp-Standard**_ in the upcoming File select Dialog selct the "Winamp.q1" file and it works. 
Have a look to Preset>Load>Preset and all Winamp-presets are shown and working...
Enjoy the Music.
Christoph

---

