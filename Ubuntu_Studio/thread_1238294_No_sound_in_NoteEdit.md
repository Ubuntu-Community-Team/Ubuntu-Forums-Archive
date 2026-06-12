---
title: "No sound in NoteEdit"
date: 2009-08-12
forum: Ubuntu Studio
---

### Post by JoeBlow9878 on 2009-08-12
Hello everybody!

I am trying to get NoteEdit to function correctly.  I am not sure if I am posting in the right section.  I have read this : [http://noteedit.berlios.de/faq.html#q3](http://noteedit.berlios.de/faq.html#q3) but I cannot figure out how to play a MIDI file with kmid.  Where is kmid found?  I have installed TiMidity, but still no sound.  :sad:  (The notes turn red like they should.)

Any help would be greatly appreciated.  I am using Ubuntu 9.04 on VirtualBox 3.0.2

Thanks!

Joe

P.S.  I can play midi with MoviePlayer, and when I hover my mouse over the .midi icon, I can hear the midi.

---

### Post by JoeBlow9878 on 2009-08-12
Hello again.

I have only succeeded in making the problem worse.  :cry:  Now I have no sound whatsoever.

Any help would be very much appreciated!

Joe

Edit : My sound is working again!  But I still can't get it to work with NoteEdit.  Midi is working, just not NoteEdit.

---

### Post by JoeBlow9878 on 2009-08-14
Bump!

Hello.  I still have the same problem.  In case it helps, I thought I would add the result of /sbin/lsmod

Here it is :

Module                  Size  Used by
binfmt_misc            16776  1 
vboxvideo              10240  2 
drm                    96424  3 vboxvideo
agpgart                42696  1 drm
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
vboxvfs                52128  0 
lp                     17156  0 
ppdev                  15620  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
pcspkr                 10496  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
psmouse                61972  0 
serio_raw              13444  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              18448  0 
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
vboxadd                81792  8 vboxvfs
parport_pc             40100  0 
parport                42220  3 lp,ppdev,parport_pc
pcnet32                41092  0 
mii                    13312  1 pcnet32
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

Thanks for any help on this issue!

Joe

---

### Post by JoeBlow9878 on 2009-08-18
Hurray!  I finally have sound working in noteedit!  :razz:

I guess I didn't look hard enough before posting :oops: .  Here is the link for anybody with this problem in the future : [http://ubuntuforums.org/showthread.php?t=770148](http://ubuntuforums.org/showthread.php?t=770148)

Joe

---

### Post by QwUo173Hy on 2010-06-03
Thanks Joe, that solved my problem. For others, to save you browsing the entire thread, here's the helpful post.
[http://ubuntuforums.org/showpost.php?p=6334754&postcount=9](http://ubuntuforums.org/showpost.php?p=6334754&postcount=9)

---

