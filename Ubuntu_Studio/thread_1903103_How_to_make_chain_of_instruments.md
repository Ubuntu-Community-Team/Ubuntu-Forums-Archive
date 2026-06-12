---
title: "How to make chain of instruments"
date: 2012-01-01
forum: Ubuntu Studio
---

### Post by mmoraschi on 2012-01-01
Hallo everybody, and sorry for my english.
I play keyboard in a group. Ours songs are a bit complicated and I have to use nearly 10 instrument in each song.
I usualy play with soundfonts and vst.
I'm tring Lmms and is very nice but I need to create a song with 10 traks with the instruments needed and than switch throug them while I'm plaing ... and it seems impossible.
Does anyone know how to do it or tell me another software to do the same.
Thanks to all

---

### Post by jejeman on 2012-01-01
How do you play? Do you use midi contoler?
Why not separate instruments by midi channels, and then on controler change the channel while playing?

---

### Post by mmoraschi on 2012-01-01
Thank you for the answer, yes you are right ... it's possible to tell lmms : track 1 - midi ch1 track 2 midi ch 2... on my master keyboard i'll set user bank memory to do the same it's ok ... but.
Is a bit unconfortable maybe impossible to make this kind of operation while we are composing and i have to add an instrument to the song.
For example I've made a song with 5 intrument ... and i'm playing it with my friend ... the guitarrist say to me ... in the third part ... try to use a violin.... great, I have to add a track give the midi ch 3 and reopen all the instrument after to change the midi ch ... the third to the fourth 4 to 5 an5 to 6 ... it take a time.... so I'm searching another solution to do the same.
Faster
For example with fruity loop all tracks are midi omni but you hear only the selected track, when you send prg up yoa change the selected track .... if you want to add an instrument you have only to add a track in the right place to do the trick ... but i dont want to use wine and a cracked FL

---

### Post by pdxken on 2012-01-01
Don't know if this will work for you but it may be worth looking into.

genpo (in the repos) is a general pipe organ stop control program. It allows you to connect a controller channel to up to 32 different synth voices. One click voice change. It is setup using xml files. Install includes several sample files including a GM file in /usr/share/genpo/organs on my 11.10 system.

I have used it with qsynth using FluidR3_GM.sf2 as well several organ sound fonts. [http://genpo.sourceforge.net](http://genpo.sourceforge.net)

Ken.

---

### Post by mmoraschi on 2012-01-02
I'll give it a try for sure, maybe I'll have to renounce to the sound of zyn, but a good chain of sf2 is a good start point.
Thank you.

---

### Post by mmoraschi on 2012-01-02
I,ve installed genpo, I read the manual on th cli... but I havent found how to write (and where to put) a suitable .org file...
I've found the manual... it seems not be for me. I have to say that is a very powerfull system but I will have to write about 30 / 40 .org files... and if I have to make a change in a song... I need to open an editor to rewrite the definition... don't suite to my operational need.
Till searching the solution.

---

### Post by sgx on 2012-01-03
Hi, specify the kind of music you play, or if your band does
covers, or originals. Without knowing, that, for bread and butter cover band sounds, with multi-fx, a multi-timbral
IK Multimedia Sampletank can be used with 16 sounds on 16 channels, change the instrument(s) you want to hear to channel 1. Load more than one multi-timbral instrument for more variety. Zynaddsubfx will do for Multi-timbral synth sounds, and if you get all available soundsets, the variety is pretty good.. At least changing between sounds is easy. For a larger total number of sounds multiple instances of multi-timbral instruments, can yield lots of variety, if you have a powerhouse computer.

Until 1. ladish can save full projects, and 2. the types of sounds you need are available natively and easily in linux, you will need reaper, with saved projects holding suitable instruments assigned on each track. 

I would study the progress ladish has made in project management,
as I don't know what success stories can be expected. When it can faithfully reload a project with zynaddsubfx, hydrogen rakarrack, guitarix2, calf/invada plugins, fluidsynth, linuxsampler, and
qtracktor/ardour/muse/rosegarden, then native productions will be easier to manage, with a good range of instruments.
Cheers

---

### Post by mmoraschi on 2012-01-03
ok... I'm sorry, I think sgx tell me something that is maybe a solution but my bad english create some understanding problems.

I try to explain. My band make original instrumental songs. I usualy use soundfonts for piano violins and natural intruments and VST for synt and pad ... zyn is perfect.

So, can you explain what I have to do with wich software for doing these tasks.
-1) we want to make a new song ... I need for begin: pr g1 piano(sf2), prg2 organ (zyn), prg3 violins (sf2)
-2) our new song growup and modify so now I need: prg1 piano(sf2), prg2 brass (sf2), and then prg3 organ (zyn) prg4 violins (sf2).

Is it possible?
reading your post seem yes, but I dont understand what software I need and what I have to do.
Hope I can understand better. :)
Thanks a LOT!

---

### Post by mmoraschi on 2012-01-03
A bit of googling helped.
I try to explain.
You suggested two way.
1- install sample tank and use only this software
2- use zyn and ladish

what about sampletank? Is only for win so I need wine and wineasio to have low latency.. (and also I dont want to use cracked software) is the free version usable?

Zyn and ladish seems to be a little triky to program while I am in the studio for play.

---

### Post by jejeman on 2012-01-03
> **mmoraschi said:**
> Is a bit unconfortable maybe impossible to make this kind of operation while we are composing and i have to add an instrument to the song.
For example I've made a song with 5 intrument ... and i'm playing it with my friend ... the guitarrist say to me ... in the third part ... try to use a violin.... great, I have to add a track give the midi ch 3 and reopen all the instrument after to change the midi ch ... the third to the fourth 4 to 5 an5 to 6 ... it take a time....Why don't you just add it as 6th channel?

---

### Post by mmoraschi on 2012-01-03
You are right... but 10 sound each song... I'd like to have them in the right sequence otherwise... big mistake and big trouble... my friends start to insult me ... poor keyboardman.

---

### Post by jejeman on 2012-01-03
I don't see why can't you later, just when you play complete song, rearange it for playing. You dont need to have just one version of the project per song. One working version, and one finished version.

---

### Post by mmoraschi on 2012-01-03
Some work in the studio, some work at home... in my dreams :D, I'll try to explain to my wife.
Hey woman don't bother me I'm working to my song!
(no, no please dont hit me noooo soooorry mi little charming wife) 
For sure ... I'm bother all of you with my problems and I apologies if I can find a better solution (maybe sampletank) well, otherwise I will do like you told with LMMS.

---

### Post by sgx on 2012-01-03
layering up to 16 sounds in zyn or sampletank, is part of
their main features. But with just one keyboard musician,
all the notes will be the same. You can stir in a variety of
sound styles, to create sonic interest for each keypress,
even if the notes are unison, use pad, sweep, gated, tremolo, arpeggiated, hits/stabs (stacatto), legato/portamento, delay, phased,
flanged, etc plus try not to have all the EQ settings of the sounds
bunched up. So in a mix with brass, synth and
violins, adding a vibraphone might be more distinct than a clavinova.
A mix with rhodes, organ and accoustic bass, might have the
clavinova stand out more than the vibraphone.

The free sampletank has some good sounds, but I think it also supports
akai sample format, and CDs of those may be on ebay sometimes.

Spending time learning about the sfz textfile sound format, supported by linuxsampler, is a good idea, more sfz supporting instruments appear
in vst setups, of various quality, Alchemy, Dimension Pro,
Wusikstation, probably many more. Computer Music magazine made Alchemy Player their default sample playback software, look for more sfz
files arriving on the monthly magazine dvd.

---

### Post by mmoraschi on 2012-01-08
Time is passed and many try was made, I've worked on rosengarden that was realy close to do the trick ... but there is no way to change the selected track with my two master keyboard (roland A33 Behringer UMX61) Rosengarden need a numeric data on channel 82 and I'm able only to send a 0-127 (on off). I can use a rotary but is crazy to select an instrument this way.
I'm really sad about knowing that in linux there is no way to make a chain and modify it.
Thanks to all for help!

---

### Post by sgx on 2012-01-08
some definition examples, for clarity, should more posts follow

example, Project = all software and hardware used to record/play a song

example signal chain = the flow of a sound from it's source through various effects, preamps, amps, mastering gear, to speakers/recording device

example multi-timbral device, hardware or software that can play multiple and wholely different sounds at once, each of which can be on or off, in a saved preset, 'patch', or 'multi'. (jargon varies) Sampletank, and zynaddsubfx are examples of that.

Saving projects in linux is a goal of the Ladish project, and
ardour/qtracktor/rosegarden,muse, etc, have some capabilities,
but I do not know about them myself.

The term 'chain' as used by mmoraschi, seems to point to 'saveable projects'.
I take notes about sonic victories, and title things with names of key components
so when memory fails (the next day) I still have tracks to follow.
Anyone currently able to save projects, please describe your success!


Cheers

---

### Post by mmoraschi on 2012-01-10
thank you sgx!
I'll tell you my experiment.
The last try as i told was using rosengarden.
Rosengarden is very very close to my needs.
It can use soundfonts and zyn so I have all sound I need.
I can make "chain" using tracks .. is simple to add a track or rearrange them if I want, so for every song I have to play I can open a rosengarden's file and I have all instrument I want to use in the correct order for play.
The problem is that rosengarden doesn't accept the signal from my keyboard for change the selected track. (Fruity loops do it).

---

