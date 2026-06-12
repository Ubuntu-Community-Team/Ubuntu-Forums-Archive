---
title: "MUSE-&gt;QSynth-&gt;SF2 working not properly"
date: 2015-03-02
forum: Ubuntu Studio
---

### Post by snakeRU54 on 2015-03-02
Hello to everybody.
I've got a issue in my ubuntu-studio.
I cant add a sound_font file more, than three in one project.
So, step-by-step:
1. Start Jack.
2. Start QSynth.
   2-a. Add a sound_font file, assigned to some channel.
3. Start Muse.
4. Open project in Muse, add a MIDI-track.
   4-a. Select a channel, wich give me a needed instrument.
5. Working in a pianoroll on that track, have a instrument, listen a sound.
Repeat staps from 4 to 5, two times.
In this moment I've got a three MIDI-track's, three music instruments and perfect sound. Well, how can be a perfect sound from Sound Fonts.
Go on.
6. Making a step "2-a" in four time - add a four SF2 in QSynth.
In that moment I'm discovering: the fourth SF2 "rewrite" a previous SF2. And now I've got a ONE (fourth) instrument, working on two MIDI-tracks (last added and previous added).
Illustrating:
Tracks: 1. Bass. 2. Drums. 3. El_guitar. 4. Harmonic.
Sounds: 1. Bass. 2. Drums. 3. Harmonic. 4. Harmonic.
That's it. To fix that i must delete a SF2 of "guitar" and "harmonic", after that I must re-add guitar in QSynth again and re-assign the channel in Muse.

What's wrong?
Who is guilty - MUSE or QSYNTH?
What... tinnnn-TIIINNNNNN can I dOOO-oooo... :guitar:
Someone, help me, please.

---

### Post by marseille2 on 2015-03-03
It's hard to tell from your set-up (without a screenshot), so I'm curious... Is there a particular reason why you aren't just loading soundfonts into Muse via the DSSI plugin? Are you routing Qsynth to other apps as well... or just Muse?

---

### Post by snakeRU54 on 2015-03-10
> **marseille2 said:**
> It's hard to tell from your set-up (without a screenshot), so I'm curious... Is there a particular reason why you aren't just loading soundfonts into Muse via the DSSI plugin? Are you routing Qsynth to other apps as well... or just Muse?

Thanks for your responding.

OK, I'll show you the screenshot's, a little later.
Particular reason? maybe, because in "windows" I've worked in "Sonar" with SoundFonts. And i dont know, how to do by the another way - DSSI Plugin.
Only QSynth, Jack and Muse.

On the next day I know a new issue.
The sound in my project is gone.
-There was a many steps to find a reasone...-

Finely, I created a new project with one MIDI-track and assign a one file.SF2, as early, and go to pianoroll. And then I've found a very funny effect.
Click by LMB on the piano - I hear sound, everything is OK.
Holding the LMB and sliding on piano up-n-down - sound is presented, but volume is fade out (slow or fast - that depended from the "speed of cursor moving" and time between MIDI-event's).
If I slow-down or stop-to-slide - sound are fading in.

So, it seems, my old project have a three MIDI-track, who have a so many MIDI-events, that's because sound is not presented.
But why?!!!

Yes, I'm understand, there is no miracle. 99% - the reason in my own "curve hand's".
But I dont remember, how I changed a some settings.
All was working well... Oh... Almost well))))

That's it, I dont have a more news.
Let's wait a incoming screenshot's.

---

### Post by marseille2 on 2015-03-10
[**[COLOR=#000000]snakeRU54[/COLOR]**]("http://ubuntuforums.org/member.php?u=1972223"), check this [video]("https://www.youtube.com/watch?v=11VWsbeT35s") out. It taught me how to use Muse in less than 7 minutes. It quickly teaches us how to set-up midi connections, and how to load synth plugins and soundfonts.

But I had some midi problems with Muse, too. Every now and again, Muse goes a little haywire and starts hanging on midi events with certain soundfonts. For me, it's usually a never-ending note with a specific soundfont ... that seems to stick, and over-ride any attempt to change the SF2. 

I thought maybe I had some bad SF2 files... since I have a few that do work really well Muse. And normally, I load soundfonts right into Muse's DSSI plugin, using Fluidsynth (Qsynth with no GUI).

Long story short... I've given up on Muse for the last few months. I think there's a new, updated version, but for me, Ardour works the best. I also like Rosegarden since I can easily write, and see the notation of a composition. I just don't think the sound quality is as good as the Muse version in UbuntuStudio 14.04 ... but IMO neither can compete with Ardour. 

So for musicians familiar with ProTools, Ardour will have a familiar feel and provide the quality they need. I highly recommend it, if Muse keeps acting buggy!

---

### Post by snakeRU54 on 2015-03-11
> **marseille2 said:**
> [**[COLOR=#000000]snakeRU54[/COLOR]**]("http://ubuntuforums.org/member.php?u=1972223"), check this [video]("https://www.youtube.com/watch?v=11VWsbeT35s") out. It taught me how to use Muse in less than 7 minutes. It quickly teaches us how to set-up midi connections, and how to load synth plugins and soundfonts.

But I had some midi problems with Muse, too. Every now and again, Muse goes a little haywire and starts hanging on midi events with certain soundfonts. For me, it's usually a never-ending note with a specific soundfont ... that seems to stick, and over-ride any attempt to change the SF2. 

I thought maybe I had some bad SF2 files... since I have a few that do work really well Muse. And normally, I load soundfonts right into Muse's DSSI plugin, using Fluidsynth (Qsynth with no GUI).

Long story short... I've given up on Muse for the last few months. I think there's a new, updated version, but for me, Ardour works the best. I also like Rosegarden since I can easily write, and see the notation of a composition. I just don't think the sound quality is as good as the Muse version in UbuntuStudio 14.04 ... but IMO neither can compete with Ardour. 

So for musicians familiar with ProTools, Ardour will have a familiar feel and provide the quality they need. I highly recommend it, if Muse keeps acting buggy!

Pre-scriptum. Sorry, I forgot my screenshot's at home and cant show them today. By the way, after watching "your" video screenshot's are unnesessary.

O, BIG thanks for your link to the video. it's a really help for me. Today I'll try this way. I believe very much, what is working way.

About ARDOUR. I using him only for voice-record (reading the audiobook). If ardour supporting the MIDI - it will big lucky for me. Almost happines.

P.S. Unfortunately, in Russia not so easy to find a correct manual about some software in russian language. When read manual in english, sometimes I lost the meaning of text, because my english not good enough. So, if you can give me a link at correct, step-by-step, manual - I'll be a very grateful.

---

### Post by marseille2 on 2015-03-11
I'm glad the Muse video worked out for you! 

I haven't really watched video tutorials for Ardour, but the first few minutes of [this one]("https://www.youtube.com/watch?v=89fuAeCAfDY") shows us how to lay down a midi track, and load a soundfont. The narrator uses [Calf Rack]("http://calf.sourceforge.net/") to do it... which I like ... and use to load soundfonts in Fluidsynth, and other effects, too. There's also Jack Rack... but I don't use it much.

If you want to try Ardour, choose Ardour3 ... but you may want to think about installing this version: **Ardour3.5.403**.

The version of Ardour3 in Ubuntu repositories has a known bug that loses tracks. I installed the updated version from [KX-Studio]("http://kxstudio.sourceforge.net/Repositories:Applications"), but we can also install the package on Ardour's [website]("https://ardour.org/download.html"), or [compile]("https://community.ardour.org/s/source") it (*if we know how*). 

Note: If you install from a repo outside of UbuntuStudio, don't forget what you did, before a system upgrade... so you don't take the chance of breaking your system. I can't say what's the best course of action, but if I upgrade ... I've might remove the KX-Repos and any apps I've installed from it, then reinstall it after the upgrade.

---

### Post by snakeRU54 on 2015-03-11
> **marseille2 said:**
> I'm glad the Muse video worked out for you! 

I haven't really watched video tutorials for Ardour, but the first few minutes of [this one]("https://www.youtube.com/watch?v=89fuAeCAfDY") shows us how to lay down a midi track, and load a soundfont. The narrator uses [Calf Rack]("http://calf.sourceforge.net/") to do it... which I like ... and use to load soundfonts in Fluidsynth, and other effects, too. There's also Jack Rack... but I don't use it much.

If you want to try Ardour, choose Ardour3 ... but you may want to think about installing this version: **Ardour3.5.403**.

The version of Ardour3 in Ubuntu repositories has a known bug that loses tracks. I installed the updated version from [KX-Studio]("http://kxstudio.sourceforge.net/Repositories:Applications"), but we can also install the package on Ardour's [website]("https://ardour.org/download.html"), or [compile]("https://community.ardour.org/s/source") it (*if we know how*). 

Note: If you install from a repo outside of UbuntuStudio, don't forget what you did, before a system upgrade... so you don't take the chance of breaking your system. I can't say what's the best course of action, but if I upgrade ... I've might remove the KX-Repos and any apps I've installed from it, then reinstall it after the upgrade.

Ow, thank you very much!!!
Now I must to run away, go home.
Today I'll try all that stuff.

---

