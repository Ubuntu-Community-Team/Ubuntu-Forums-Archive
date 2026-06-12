---
title: "Soft synth sounds and MIDI controller"
date: 2010-08-12
forum: Ubuntu Studio
---

### Post by Sylos on 2010-08-12
Hello all.

I have a reasonably old computer running ubuntu studio for recording guitar, drums sequenced on hydrogen etc. Recently I have decided I want to add some synth into the mix at times. I cant stand the thought of having some cheesey casio keyboard mid 90's sound (it just wouldnt work in the music I am trying to record) but I cant afford the money or space for a nice Korg Triton.

However, I have noticed you can buy a DVD for a few pounds that contains loads of Triton sounds. My question is, could I buy one of these DVDs and somehow put the sounds into a soft synth like Zynaddsub and just buy a little midi controller (eg. M-audio Oxygen 25 key) to control it.

I am quite new to the home studio scene and a complete dunce with MIDI so forgive me if this is a stupid question.

---

### Post by AutoStatic on 2010-08-12
> **Sylos said:**
> However, I have noticed you can buy a DVD for a few pounds that contains loads of Triton sounds. My question is, could I buy one of these DVDs and somehow put the sounds into a soft synth like Zynaddsub and just buy a little midi controller (eg. M-audio Oxygen 25 key) to control it.Hello Sylos, it depends how the Triton sounds are packaged. If it's a format Ubuntu can handle you could load the sounds in a suitable app, probably LinuxSampler, Specimen or Qsynth. You can't put it in ZynAddSubFX, that's a softsynth by itself that doesn't load and play samples.
Did you already try ZASFX by itself? Maybe you should give Yoshimi a try, or PHASEX, or amSynth. Maybe you don't need to buy a DVD at all ;) Yoshimi and PHASEX are both in my [PPA]("https://launchpad.net/~autostatic/+archive/ppa").

---

### Post by Sylos on 2010-08-13
Hello and thanks for the post.

I have tried doing some stuff with Zynaddsub but the I cant get the sounds Im looking for. Im trying to add a realistic sounding strings section (violins, cello etc) into it and anything I can create in zynaddsub sounds very fake.

I have tried PHASEX and that does produce some cool effects but again its not good at emulating a real world instrument (or at least not when Im controlling it.

I will see if I can give Yoshimi a try.

Any other suggestions?

---

### Post by AutoStatic on 2010-08-13
If you want to emulate a real-world instrument you might be better off with something like Qsynth, LinuxSampler or Specimen. Those apps are sample based. Qsynth can load Soundfonts, LinuxSampler loads GIG and SFZ files and Specimen can be used to play around with your own samples.
Yoshimi is a ZynAddSubFX fork but comes with a lot more presets, maybe you'll like some of the instrument patches of the Will J Godfrey collection that comes bundled with Yoshimi.

---

### Post by Sylos on 2010-08-13
Thanks man. I shall give Yoshimi and Qsynth a day in court and see what we get.

Cheers!

---

### Post by Sylos on 2010-08-17
Sorry to bother you again but Im trying to test out Qsynth but I cant seem to get any noise from it.

Im trying to connect the ALSA virtual keyboard to it through JACK but when connected there appears to be no sound. Ive tested the VKeyboard with Hex and it seems to work.

Is it possible to connect the VKeyboard to Qsynth and do I need to follow a special connection process?

Thanks,

---

### Post by AutoStatic on 2010-08-17
Hello Sylos, did you load a Soundfont in Qsynth? Qsynth doesn't make any sound by itself.

---

### Post by Sylos on 2010-08-17
Yeah I did load up two soundfonts that I downloaded in sf2. format. I think I set it up right but still no sound.

Are there any other settings I need to fiddle with.

PS: I seem to recall that in jackctrl I cant conncet Vkeyboard to Qsynth directly - the only option is to connect to FluidSynth - I assumed this was right as Qsynth is just a fluidsynth front end. Is that correct?

---

### Post by cchhrriiss121212 on 2010-08-17
Hi sylos, you are correct about fluidsynth, qsynth is just the GUI. Once you connect your midi to fluidsynth you should be able to get some sounds.

---

### Post by Sylos on 2010-08-17
Thanks for the post.
Im wondering whether Qsynth will only accept a MIDI input and not the ALSA Virtual Keyboard. Is there any reason that would be the case. 

Have you had success using Qsynth without the MIDI device?

Many Thanks.

---

### Post by cchhrriiss121212 on 2010-08-17
I've only used qsynth with my novation, but you should be able to connect the virtual midi keyboard to it just like anything else.
Does fluidsynth show up in the ALSA tab? It might be that you have one thing set to use jack midi and another set to use ALSA midi. Check your preferences.

---

### Post by raboofje on 2010-08-17
QSynth shows green flashing 'leds' when it receives MIDI input - do you see them?

Did you connect 'qsynth' to 'system' in the 'audio' tab of qjackctl?

---

### Post by Sylos on 2010-08-18
Hi and thanks for the posts.

raboofje: I have connected VKeyboard to Qsynth via jack and I do get the little green light next to Qsytnh1 to flash when I click on the Vkeyboard keys but still no sound. Am I missing some other Qsynth setup?

cchhrriiss121212: My Jack window shows VKeyboard in the ALSA readable clients section and Fluidsynth in the writable clients section.

When I start and conect the two progs together the JACK audio tab already shows that Qsynth is connected to the system and reconnecting it has no effect.

I cant figure  it out. Maybe the soundfonts are bad?

---

### Post by madeinfamous on 2010-08-18
allo Sylos,

not enough to select a soundfont, you need to go to channel and assign some sound :)

here's a pic of what i mean: [https://sites.google.com/site/nueusx/qsynth_channel.jpg]("https://sites.google.com/site/nueusx/qsynth_channel.jpg")

hope that help.

---

### Post by Sylos on 2010-08-18
Hello there and thanks for the post.

Having tried some other soundfonts I have discovered that it was the soundfonts that were not working. Currently around half of the soundfonts are working. Is this a common thing or am I maybe missing something to open some of them.

I am using the Hardy version of Ubuntu Studio so things are a little out of date. I followed a guide to install a CLI prog to deal with sfArk files but it seems that none of the sf2 files extracted from the sfarks work. Other sf2 files got from rar archives and zip packs have varied results - some work some dont.

Any insight gratefully received.

Thank you all for your patience and help.

---

### Post by Sylos on 2010-08-24
Ok, so I have now solved my problems and have achieved what I wanted to do. For anyone who may  be wondering how to 'cheat' your way into some nice synth instruments without splashin out a 2k on a flash synth heres my solution.

1. Find a friend who is willing to sample you his flashy expensive keyboard sounds and get them saved as WAV files.
2. Use SWAMI to input these samples into sf2 soundfonts.
3. Load them into Qsynth and connect the virtual keyboard using Jackctrl.
4. Select the sound you want in the 'channels' section of Qsynth.

For me this has provided the sounds I need (for now).

Many thanks to all the people who have read this post and helped me out in my dunce like stumble towards a solution.

Cheers

---

### Post by rpkopreski on 2011-01-18
Hi Sylos, I would love to benefit from your "dunce-like-stumble" as I feel I may be in worse shape than you.  I have started learning swami 2.0 and successfully loaded a suite of .wav samples and arranged them into an "instrument."  However, I am having trouble saving the work as a .sf2 file that may be read by qsynth.  Can you explain how you did this? Thanks!

---

### Post by rpkopreski on 2011-01-18
Okay, nevermind I figured it out finally using this spanish tutorial ([http://www.musix.org.ar/wiki/index.php/Swami-tutorial](http://www.musix.org.ar/wiki/index.php/Swami-tutorial)).  Thanks to google for the translation!  Basically I had to assign the instrument (drag and drop or copy and paste) to a preset. Choose a bank and channel for the preset and then save including the .sf2 extension.

---

### Post by Sylos on 2011-02-03
Sorry for the lack of reply - old thread - havent been checking it.

Swami is a complete pain to get your head around - so unintuitive. Its awful really. I had exactly the same problem as you figuring out how to get it to work.

Do you get any sound from your Swami? - appears to not be supported for my 10.04 system

---

### Post by rpkopreski on 2011-02-03
I have Swami-2.0 working fine for my system (10.04).  I actually am very happy with how full-featured it is for FOSS.  This is great software that has allowed me to have new freedoms in music creation.  It shows up in patchage (or qjackctl alsa connections) as a fluidsynth engine that I connect my midi keyboard to.  I will be posting any soundfonts I create with it at my blog: overhauser.blogspot.com.

---

### Post by Sylos on 2011-02-04
> **rpkopreski said:**
> I have Swami-2.0 working fine for my system (10.04).  I actually am very happy with how full-featured it is for FOSS.  This is great software that has allowed me to have new freedoms in music creation.  It shows up in patchage (or qjackctl alsa connections) as a fluidsynth engine that I connect my midi keyboard to.  I will be posting any soundfonts I create with it at my blog: overhauser.blogspot.com.

Dont get me wrong - I think the standard of the prog and what it can do is commendably high. Its the user interface and the way things have to be input and saved that bugs me. I spent ages trying to work out how to use it.

As for the sound I think I may have an older version of Swami - I havent used it in a while so I will have to investigate and see if there is a newer build.

Cheers

---

### Post by stephenstop on 2011-06-26
Hey autostatic i have been trying to figure out how to "unpackor whatever" yoshimi fo awhile,i downloaded a tar.gz{i t6hink that was named) but i cannot figure it out.I went to the launchpad site but i could not find any header that said "signing keys",and chance you could help me find it or somin.I have 10.o4 ubuntu and I use zynaddsubfx but I was told Yoshimi was more awesome.

Also I have tried using qsynth as well although I do have soundfonts but i don't really  like any of em and all the sites i have been sent too didn't have real sounding samples.I downloaded fluid synth as well but I cannot "unpack" or "compile" it.Ive read articles,watched tutorials and spent hours reading and trying but I cannot  figure it out.

I would really appreciate the help,I am having a hard time figuring lots of the music programs so your help,i would be so gratreful

---

### Post by cchhrriiss121212 on 2011-06-26
Hi stephenstop, you do not have to compile programs on Ubuntu. Compiling is not a bad way to install software, but you should always go through software centre first. If you cannot find what you want in the software centre, try using a PPA like this one which is for music software:
[https://launchpad.net/~falk-t-j/+archive/lucid/+index?start=300&batch=75]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/+index?start=300&batch=75")

If you already have qsynth installed you don't need fluidsynth, they are the same thing. As for a better sounding soundfont, try looking up squidfont orchestra or sonatina. sf2 is kind of a dead format now, with most new stuff being sold as VSTs, but there are still a few good ones out there.

---

