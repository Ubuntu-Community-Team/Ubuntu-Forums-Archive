---
title: "Midi in Ubuntu Studio 9.10....."
date: 2009-11-09
forum: Ubuntu Studio
---

### Post by dawiba on 2009-11-09
....really isn't that great, which is sadly the same as Jaunty in my experience.

Overall, I've found this version of Studio (9.10) to be really good. The kernel seems to be really stable, setting up and hooking up my firewire interface was very simple and the audio programs and plugins are great. If only midi was better!

I tend not to use softsynths like Hexter or ZynaddsubFX. I like to record midi as I play my external keyboard, then playback the midi to trigger it's sounds. I'm using a firewire interface and I use a2jmidi (nice to see it included in the install). Using midi through firewire i.e. the actual process of getting midi into and out of the computer is fine like this, it's the programs that are the let down.

I can only speak for myself here, but perhaps the programs for recording midi should be reviewed and those that don't come up to scratch taken out of the default install.

I tried SEQ24 first. The issue when you would select 'new' at the initial screen and the program would then disappear, has been resolved thanks to this version being later than the version in Jaunty. So that's good. I can get SEQ24 to record midi. So that's good. However, it seems to be completely random as to when or if it will play back the midi and trying to get it to sync with Ardour has proved impossible for me so far (frequently results in SEQ24 crashing). This is a shame as SEQ24 should be a good program for me and the way I use midi.

I tried Muse, but try as I might, I couldn't get it to record midi. I tried every connection possible in jack control and tried every different setting in Muse I could imagine, but nothing happened (apart from Muse crashing). Muse seems to cater for softsynths, but not external sounds. So I gave up.

In Jaunty I had tried Rosegarden, but it made my keyboard behave a bit erratically sometimes, and it became a pain having to constantly reset sounds and channels. Also it sometimes didn't sync too well with Ardour. So I didn't download it this time.

I have downloaded Qtractor and it seems to work fine for midi so far, including choosing (and remembering) channels as well as playing in sync with Ardour. Making connections was easy and it seems to work well with jack. So here's hoping it stays stable for me to use.

I realise this is only personal experience, but overall, trying to use midi in Ubuntu Studio with the default programs is a frustrating experience (as it was in Jaunty). This is even more true because I was able to find a perfectly good program in the repositories and also because the audio side is very well catered for in my experience.

So, does anyone know if Qtractor will be included in the default install in 10.04? If not, why not?

Does anyone have any other midi programs that they've used successfully?

---

### Post by AutoStatic on 2009-11-09
Hello Dawiba, you already mentionned Qtractor and I think it's the easiest and best tool to work with Midi. And it's in the repo's, version 0.4.2, so no need to download seperate debs, unless you want to use the latest version (0.4.3).

---

### Post by variona on 2009-11-25
About Rosegarden: If you define your Midi Devices 
[http://www.rosegardenmusic.com/tour/midi/](http://www.rosegardenmusic.com/tour/midi/) 
and save them as a "Standard Studio", which includes some work, but only once. Afterwards it is quite comfortable to choose the instruments you like. You can import the Standard Studio Definition File to all your previous Rosegarden Files.
What troubles me is that Rosegarden looses is connection to Jack quite freqently, therefore losing Jack Transport capability. This makes a restart of Jack and then Rosegarden necessary. 
I wil try other Jak parameters today - if this fixes something I'll tell you. (My doubts: Jack works really fine, Ardour stays connected while Rosegarden complains.)
Muse doesn't start at all.
Qtrator will be tested today (haven't heard of it yet)


Setup Overview:
---------------
Audio: Ardour
Midi: Rosegarden 
Sync: Ardor and Rosegarden via JackTransport

UbuntuStudio9.10-64bit
RME DIGI96PAD
M-Audio Midisport2x4
AMD64X2 Processor

---

### Post by dawiba on 2009-11-25
> **variona said:**
> About Rosegarden: If you define your Midi Devices 
[http://www.rosegardenmusic.com/tour/midi/](http://www.rosegardenmusic.com/tour/midi/) and save them as a "Standard Studio", which includes some work, but only once. Afterwards it is quite comfortable to choose the instruments you like. You can import the Standard Studio Definition File to all your previous Rosegarden Files.

That's what I had done, more than once, but Rosegarden would send messages to my keyboard and re-set channels and instruments. I assume it was the program and not my keyboard as QTractor doesn't seem to cause the same issue. I got fed up (I do very easily when I'm just trying to make music :)) and ditched Rosegarden as there were other choices. I don't doubt it works for many people, but not for me so I moved on. QTractor is working absolutely fine, although I don't use the audio side of the program at all.

Like you, Muse wouldn't work for me and SEQ24 is still a bit of a mystery. I can make it work, but it seems to have a mind of it's own. Both these programs rule themselves out for me.

I just feel that midi isn't quite as good (easy to use) as it could be, particularly for people like me (amateur, home user, light user) who don't really want to use the terminal too much and find it a bit of a pain to be constantly re-setting things when you just want to put down some ideas. I seem to remember reading somewhere that Ubuntu was Linux for human beings ;).

The modular approach has advantages but can also have it's disadvantages. I guess I was just expressing a little dissatisfaction with my experience of midi using this method. I also felt that the programs that come with UbuntuStudio were letting it down, especially in light of the fact that there *_is_* a program (QTractor) that works fine but you have to go and download it.

Sorry for the long winded reply and thanks for your input.

---

### Post by variona on 2009-11-25
Qtractor looks pretty promising, the interface is almost self explanatory. Only thing I didn't find out is: how do you save your setup for the next new project?

Say you have 3 MIDI Buses (sic!) to connect three external devices, each with  complete with banks and programs. I just didn't find a way to make something like a Standard Template. There are some things I miss in Qtractor -but I'll keep an eye on it. 
My Rosegarden problem was tediously solved by trying a lot of Jack parameters, only to find out that using the -u parameter is not good for me!(--unlock Unlock libraries GTK+, QT, FLTK, Wine)

---

### Post by dawiba on 2009-11-25
[QUOTE=variona]I just didn't find a way to make something like a Standard Template[/QUOTE]

I think when you create a song and then go to save, you have the option in a drop down menu to save as a song file or a template file.

---

### Post by variona on 2009-11-26
Yes, now I have found it, also the option where you tell QTractor to use the template. A final question: How (or where) do you set up your banks and programs, on the project homepage it says Cakewalk like instrument definition file, but it's been aeons since I used Cakewalk. I also found a dialog to import *.ins files - but I don't know how to create them. I tried in the buses and via track properties, alas I didn't succeed.

An idea to the behaviour of your keyboard you described: maybe you had controller events in your Rosegarden segments which you were not aware of? Maybe QTractor can't (yet) handle them.

Thanks for the hint on templates!
Variona

---

### Post by dawiba on 2009-11-26
My keyboard has a built in hard drive, audio inputs and sequencer so I can record audio and midi, use effects and mix, and export a song all from the keyboard. At least that what it says in the manual ;). In real life, I can do this but it's not quite as straight forward as it sounds. But it does mean that I can load up a whole load of instruments/sounds in my keyboard.

So, when I get an idea, I usually load up an empty song on the keyboard and do the same on the computer. Then I'll start recording audio on the computer. As I'm messing around, I'll have ideas for instruments and will turn to my keyboard and, for example, load a piano and assign that to midi channel 1. Then I'll create a track in QTractor and assign that to midi channel 1. Now I'll record just the midi and use that during playback (once I've sorted the mistakes :)) to trigger the audio from my keyboard.
-
I'll repeat the process assigning a different midi channel to each instrument/track. I've never needed more than the basic 16 midi channels for anything I do. I imagine for soft synths, something similar would be possible when you create a midi track to decide which channel you want for each synth from within the track window that opens when you create a new track.x

---

### Post by variona on 2009-11-27
For anyone who likes to know how to make Instrument Definition Files *.ins :
[http://www.tweakheadz.com/how_to_build_a_cakewalk_ins_file.htm](http://www.tweakheadz.com/how_to_build_a_cakewalk_ins_file.htm)
In most cases you won't have to as there are many available on the Internet. Just in case you have exotic or old midi synths. I got lucky in 3 out 4. Editing the 4th from my *.rgd file just took about 10 min. (As soon as I knew what to do;)
@dawiba Thanks.

---

### Post by mdrake36 on 2009-12-28
This seems like as good as place as any to jump in.
I love using Midi for all kinds of compositional tricks myself.
I am new and haven't had a chanec to play with rosegarden but I have succefully been introduced to VSTi and its Midi interface within Jaunty.
I got into it to try Hexter and it has been a great experience.
I want to install Ubuntu Studio as so as possible to take advantage of the Low Latency kernel.
Anything pertaining to Latency I should know?
Also from using tons of shareware interfaces I have started learning about System Exclusive messages and these messages can be disabled in some interfaces.
These messages may be resetting your keyboard.

---

### Post by dawiba on 2009-12-28
@mdrake36 - thanks for the reply, but I'm using QTractor very happily just now, so I've dropped Rosegarden.

---

### Post by mdrake36 on 2010-01-04
I was suprised not to see Qtrackor included w/ Karmic Studio. I finally got it all fired up and don't see rosegarden either unless it is called Linux Studio now. I am so trying to get Qtrackor because it does boast SysEx management. The Karmic Studio is a marked improvement over the Juanty as far as Midi use goes. I am still wrestling with the full impilcations of RT(realtime Kernel) Wish I could be certain I am utilizing it.

---

### Post by AutoStatic on 2010-01-04
Qtractor is included with Ubuntu Studio 9.10.
To check if you're using the RT kernel: System - Administration - System Monitor and the 'System' tab.
Or in a terminal: **uname -r**

---

### Post by dawiba on 2010-01-04
Well I revisited SEQ24 today and managed (after a few failed attempts) to get it to work consistently with no problems at all :). I also tried out Hydrogen for the first time today and once I sorted out the connection (by default, it wanted to try to connect every output to Jack which resulted in errors), it worked just fine. So I downloaded some extra kits and I'll give both programs a spin on my next wee project.

I also opened up Ardour and managed to get all three programs to sync to Jack controlled from Ardour, which is pretty much perfect for me.

So I guess I'm going to have to review (upwards) my original comments. SEQ24 does take a bit more setting up than QTractor for example, but it seems to be working great for me now. Fingers crossed it stays that way :)

---

### Post by mdrake36 on 2010-01-05
I have this basic Qtribe step sequence generator, I found on sourceforge.
In QJackctl I can see the the MIDI connection "out" but all my I/O Patches for my midi sound card fall under ALSA is there a a way to populate my ALSA midi connections in the same MIDI field. Why would the Midi ports fall under ALSA and Not MIDI abitrarily?
Just read thee above;Maybe Ardour would manage this better?

---

### Post by thorgal on 2010-01-05
> **mdrake36 said:**
>  is there a a way to populate my ALSA midi connections in the same MIDI field?

sure, it's a "daemon" called a2jmidid. It exposes legacy ALSA MIDI ports to the jack MIDI graph. So all your ALSA MIDI ports will show up in the jack MIDI tab.

[http://www.pubbs.net/linuxaudio/200912/70463/](http://www.pubbs.net/linuxaudio/200912/70463/)

---

### Post by mdrake36 on 2010-01-06
WoW, Can't wait to give it a shot. Thanks for the heads up.:guitar:
 
I almost understand the permissions for RT. I checked out the UbuntuStudio controls tab where Raw 1394 box can be selected. what do I select to assign permission to lock down memory and permission to enable realtime scheduling.
Please recommend an article.
My latency problems coming from Juanty are ten fold improved in Karmic but I want to be part of the Reatime compliant Club before I delve into more advanced sequencing , sample based Midi to Audio & DSSI Recordings. Possibly even trying out Soundfonts in the future.
Right Now I am Concerned with a Stable HexterDssi + Simple sequencer i.e. Seq24 or Hydrogen. 
Ultimately when I select Realtime in the Jack Control Qjackctl Jack refuses to start.
-Awesome Project everyone-
 
I think Karmic UbuntuStudio is the coolest Toy ever created next to the Tyco Turbo Hopper
and nobody ever gave me a TurboHopper to try. Infact I think I settled for a Radioshack RC that I ran through a puddle which immediately there after would only go in reverse. But now that I am comparing Karmic studio to RCs I would have to put in a class with the Tamiya Grass Hopper(w/ Monster Brushless Motor) Rather than a Kids Toy like the Turbo Hopper. Its Cool,New,Reissued & Classic?!

---

