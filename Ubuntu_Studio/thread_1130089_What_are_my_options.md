---
title: "What are my options?"
date: 2009-04-19
forum: Ubuntu Studio
---

### Post by hitsynth on 2009-04-19
Does anyone know what music production software is available for the linux platform? My personal workstation is running Ubuntu and I prefer that to windows, but I haven't seen any real music production software for linux that I could use instead of the ones available for windows and mac. Any ideas?

---

### Post by pbpersson on 2009-04-19
Check out the software included in the Ubuntu Studio collection

---

### Post by pietjanjaap on 2009-04-19
[http://distrowatch.com/](http://distrowatch.com/)
There are more linux versions with music programs, these you can ofcourse download/install in ubuntu.

---

### Post by hitsynth on 2009-04-19
thank u, i will check these out, does anyone know of any software that handles vsti's?

---

### Post by eric71 on 2009-04-20
For MIDI recording with VSTi's your best bet is Rosegarden using vst-dssi (see [http://breakfastquay.com/dssi-vst/](http://breakfastquay.com/dssi-vst/) ). I used to have good luck with that, but admittedly I do not use a lot of MIDI and VSTi's. Vst-dssi also provides the ability to load vsts in stand-alone dssi hosts like jack-dssi-host, and connect them to any Jack capable program, like Ardour or Audacity.

I've never used it, but if you like Fruity Loops/FL Studio type programs, LMMS is supposed to be good and can handle Windows VSTi's. [http://lmms.sourceforge.net/home.php](http://lmms.sourceforge.net/home.php) 

Also, although not open source or technically free, Reaper works very well with Wine and Wineasio on Linux, and is probably the most reliable Vsti host you can use with Linux.

And another I have never tried, fst, which is the basis for Ardour's new VST hosting ability. It is discussed in this tread: [http://www.linuxmusicians.com/viewtopic.php?f=24&t=868](http://www.linuxmusicians.com/viewtopic.php?f=24&t=868)

---

### Post by kayosiii on 2009-04-20
How do you like to produce music.... There are different approaches and people have different priorities here are some examples....

1) You do most of your sound outside the computer and want to mix down something that sounds professional. You know rock, jazz, folk etc.... Ardour would be the first thing I would look at, It is actually very descent software. (alternatively for mixing stuff you create inside the computer).

2) You do most of your sounds outside the computer and maybe a few synth sounds. You want to rapidly prototype by recording parts as loops and then play other parts on top of them. Freewheeling is a great program for doing this though you might want to start out with some video tutorials.

3) You have some sort of music theory background and want to compose pieces note by note using notation, then Rosegarden is not too shabby. you will also want to load in a few soft synths. Maybe hunt for some good soundfonts and gig files....

4) You are fairly advanced computer wise and want to really experiment sound and compositon wise doing mostly synthesis stuff then maybe look at cmusic or pure data.

5) You want to put music together out of repeating loops -- then lmms is probably your best bet (though I can't vouch for this one through experience)... 

Best of all you can mix and match all software with each other.... as well as other utility programs like drum machines (hydrogen), synths (zynaddsubfx,amsynth,qsynth,whysynth),meters.

I can't comment specifically at levels of functionality vs current versions of commercial software. But what you can do with a system that is properly setup is pretty amazing.... Is it better for you? That will depend on what you need and what sort of a budget you have...

---

### Post by QwUo173Hy on 2009-05-20
I have the same question as the OP really. I'm surprised Audacity isn't on your list kayosiii - I want to record my band one instrument at a time and then mix it. I was going to use Audacity, would you recommend this?

Thank you,
Jarlath

---

### Post by raboofje on 2009-05-22
> **jarlath said:**
> I want to record my band one instrument at a time and then mix it. I was going to use Audacity, would you recommend this?

Ardour is a very good choice here, too.

---

### Post by QwUo173Hy on 2009-05-22
Thank you - I'm experimenting with Ardour now.

---

### Post by Musicologynut85 on 2009-05-28
Everyone keeps suggesting Rosegarden, and I've tried using that as well as just learning lilypond.

However, as a music student, lilypond does not offer the full functionality that I require. It would be nice were I just engraving music from a handwritten score; however for actual composing or doing work where I need the ability to quickly make adjustments and get immediate feedback lilypond does not work, and Rosegarden is just not powerful enough.

I've been using Sibelius 5 in WINE without a problem, and love it. Actually, I think it is running faster and with better sound support than it did when I was running it on Windows XP. For me, I need (and regularly use) the full functionality of the program; however, YMMV.

-Jeff

---

### Post by kayosiii on 2009-05-28
@Musicology Nut -- Lilypond is specifically an engraver, Not really an interactive playback tool. Yes Rosegarden does have limitations but it is the currently the best native tool available for interactive composition using music notation. (I am looking forwards to seeing some of the current development like being able too see multiple parts on the same staff, I would be interested at which other limitations you were coming up against) 

@Jarlath -- Audacity to me is a wave file editor that can do some multitracking, it's major weakness as far as a multitrack program is that all effects are applied destructively. In a program like Ardour the effects applied in realtime and you can use Automation curves to adjust effect parameters as the track plays (and even record them from a control surface if you have one). 

Audacity does fit into my sound arsenal as a wave file doctoring program. Mostly for it's noise removal and repair tools. The other tool I can recommend for this is Gnome Wave Cleaner.

---

### Post by QwUo173Hy on 2009-05-28
kayosiii, thank you. That frames it nicely. I'll have a look into Wave Cleaner also. Ardour is going very well for me.

---

