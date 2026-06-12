---
title: "No sound from Hydrogen w/Jack"
date: 2009-03-29
forum: Ubuntu Studio
---

### Post by homerj742 on 2009-03-29
Hey, Just installed Ubuntu 8.04.1 

I have an M-Audio Delta 44 being used as my sound card (I also have a built in Intel soundcard which I never use). 

I can startup jack, go into connections, and connect the "systems" plug in my guitar and I hear sound. 

However, when I open up hydrogen and connect it to "systems" I get no sound!

I also can't get sound from amorak, or audacious. Please help! Thank you!

Is this a "pulseaudio" issue? should I just remove it and use alsa?

---

### Post by Stochastic on 2009-03-29
This is probably not a pulseaudio issue, pulseaudio is suspended whenever jackd is started.

Can you post a screenshot of the Hydrogen audio preferences and the qjackctl preferences?

The lack of sound through amarok and audacious, is that only when jackd is running, or all the time?

---

### Post by homerj742 on 2009-03-29
I only know how to use the Jack GUI. 

I solved the audacious and amarok problems by going into preferences and selecting it to use ALSA as opposed to "Autodetect". 

Here are the Screenshots below. Please let me know if you need anything else. and of course, thank you so much for your help.

[IMG]http://img.photobucket.com/albums/v32/homerj742/Screenshot-Connections-JACKAudioCon.png[/IMG]

[IMG]http://img.photobucket.com/albums/v32/homerj742/Screenshot-Preferences.png[/IMG]

[IMG]http://img.photobucket.com/albums/v32/homerj742/Screenshot-Setup-JACKAudioConnectio.png[/IMG]

---

### Post by Stochastic on 2009-03-29
Okay, first thing to try is uncheck the 'connect default output pair' in hydrogen.  Then restart both hydrogen & jack.  There's an issue with that option often being too fast then locking things out after it fails.  Not having this option checked means you'll have to manually connect Hydrogen and the soundcard in qjackctl (the jack GUI).

If that doesn't work, change the buffer size in hydrogren to match the frames/period size in qjackctl.

post back with your results.

---

### Post by homerj742 on 2009-03-29
Results:

1) Unchecking "connect default output pair" option didn't work. I did manually connect hydrogen in qjackctl. 

2) The buffer size in hydrogen doesn't go under 100. So I set it to 128, as well as the "Frames/Period" option in qjackctl. Restarted both programs and still no sound. 

I welcome anymore suggestions. Thank you very much!

---

### Post by Stochastic on 2009-03-30
Hmm, this is strange.  Is hydrogen the only jack app that doesn't make sound in jack?  Which other apps have you tested?

Can you try Hydrogen with the 'enable track outputs' and see if those output sound?

Can you also open a terminal, type ```
hydrogen
``` press enter, connect the output of hydrogen in jack, then copy the results to this forum?  Please post the results inside code tags either with the # button in the web editor, or by using the word code contained in square braces [  ] then with a closing version of the same tag [/  ] at the end of the output.

Lastly, and this is really just to cover all the bases, can you post a screenshot of hydrogen (including the mixer window) *as it's playing a demo song*.

---

### Post by thorgal on 2009-03-30
is your onboard chip disabled in the bios ?
If not, you may have an issue with the ALSA indexing of your sound cards.

---

### Post by homerj742 on 2009-03-30
> **Stochastic said:**
> Hmm, this is strange.  Is hydrogen the only jack app that doesn't make sound in jack?  Which other apps have you tested?

Can you try Hydrogen with the 'enable track outputs' and see if those output sound?

Can you also open a terminal, type ```
hydrogen
``` press enter, connect the output of hydrogen in jack, then copy the results to this forum?  Please post the results inside code tags either with the # button in the web editor, or by using the word code contained in square braces [  ] then with a closing version of the same tag [/  ] at the end of the output.

Lastly, and this is really just to cover all the bases, can you post a screenshot of hydrogen (including the mixer window) *as it's playing a demo song*.


I have tested Ardour, and it worked just fine in playback and recording. So far, hydrogen is the only thing giving me an issue. I will post all of the above once I return home from work. Thank you!

---

### Post by thorgal on 2009-03-30
can you connect hydrogen to ardour and monitor things in ardour ? (or even record ?)

---

### Post by homerj742 on 2009-03-30
Oh, I also like to mention a "shutdown" problem. The computer doesn't completely shutdown when I choose the "shutdown option". It seems to shutdown all the services just not the PC itself.

---

### Post by Stochastic on 2009-03-30
> **homerj742 said:**
> Oh, I also like to mention a "shutdown" problem. The computer doesn't completely shutdown when I choose the "shutdown option". It seems to shutdown all the services just not the PC itself.

It's best to start a new thread for each separate issue.

---

### Post by homerj742 on 2009-03-30
> **Stochastic said:**
> Hmm, this is strange.  Is hydrogen the only jack app that doesn't make sound in jack?  Which other apps have you tested?

Can you try Hydrogen with the 'enable track outputs' and see if those output sound?

Can you also open a terminal, type ```
hydrogen
``` press enter, connect the output of hydrogen in jack, then copy the results to this forum?  Please post the results inside code tags either with the # button in the web editor, or by using the word code contained in square braces [  ] then with a closing version of the same tag [/  ] at the end of the output.

Lastly, and this is really just to cover all the bases, can you post a screenshot of hydrogen (including the mixer window) *as it's playing a demo song*.

1) The enable track outputs didn't bring about any soud. 

2) here is the code when launching hydrogen from the terminal:

```
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH

Hydrogen 0.9.3 [Jan  6 2008]  [http://www.hydrogen-music.org]
Copyright 2002-2005 Alessandro Cominu


Compiled modules:  (FLAC) (LASH) (Jack) (Alsa) (OSS) (LRDF)

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8
Warning: error loading locale: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8.qm
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Kik_04.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Kik_04.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Kik_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Kik_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Kik_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Kik_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Kik_04.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Kik_04.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/SN_B_04.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/SN_B_04.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/SN_B_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/SN_B_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/SN_B_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/SN_B_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/SN_B_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/SN_B_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Flr_Tom_04.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Flr_Tom_04.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Flr_Tom_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Flr_Tom_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Flr_Tom_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Flr_Tom_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Flr_Tom_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Flr_Tom_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Mid_Tom_04.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Mid_Tom_04.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Mid_Tom_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Mid_Tom_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Mid_Tom_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Mid_Tom_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Mid_Tom_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Mid_Tom_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Hi_Tom_04.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Hi_Tom_04.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Hi_Tom_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Hi_Tom_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Hi_Tom_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Hi_Tom_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Hi_Tom_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Hi_Tom_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Cl_HH_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Cl_HH_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Cl_HH_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Cl_HH_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Cl_HH_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Cl_HH_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Op_HH_04.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Op_HH_04.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Op_HH_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Op_HH_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Op_HH_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Op_HH_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Op_HH_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Op_HH_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Rd_Cymb_04_bell.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Rd_Cymb_04_bell.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Rd_Cymb_03.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Rd_Cymb_03.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Rd_Cymb_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Rd_Cymb_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Rd_Cymb_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Rd_Cymb_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Szl_Cym_03_bell.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Szl_Cym_03_bell.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Szl_Cym_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Szl_Cym_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Szl_Cym_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Szl_Cym_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Crsh_Cym_02.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Crsh_Cym_02.flac not found
[ERROR]     FLACFile_real   	[load] file YamahaVintageKit/Crsh_Cym_01.flac not found.
[ERROR]     SongReader   	[readSong] Error loading sample: YamahaVintageKit/Crsh_Cym_01.flac not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[ERROR]     LocalFileMng   	[getDrumkitDirectory] drumkit "YamahaVintageKit" not found
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/lib/hydrogen/plugins
[LadspaFX::getLadspaFXGroup]
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/lib/hydrogen/plugins
cannot lock down memory for RT thread (Cannot allocate memory)
[WARNING]   JackDriver   	[setBpm] 100
[WARNING]   JackDriver   	calling jack_transport_locate(0)

```

3) And here's a screen shot with the kick,snare, and closed high hat filled out completely.

[IMG]http://img.photobucket.com/albums/v32/homerj742/Screenshot-Hydrogen093-BriansBeatsR.png[/IMG]

---

### Post by homerj742 on 2009-03-30
> **thorgal said:**
> can you connect hydrogen to ardour and monitor things in ardour ? (or even record ?)

I tried this too, and still got nothing. Thank you for the suggestion though!

---

### Post by homerj742 on 2009-03-30
See the "volume" icon to the left of the Tempo reader, under the +/- buttons. I clicked on that and heard the metronome. 

But can't hear the drums. 

[IMG]http://2.bp.blogspot.com/_-moPD4TOaU8/SGM_8HtYLyI/AAAAAAAAAHE/Zf79pWShQ0M/s1600/Transport.png[/IMG]

I also "unmuted" all the tracks in Hydrogen (duh! lol) still no sound however:

[IMG]http://img.photobucket.com/albums/v32/homerj742/Screenshot-1.png[/IMG]

---

### Post by thorgal on 2009-03-30
er... from the terminal output you posted above, it looks like your drumkit is simply not found ... so hydrogen has no sample to play (?). I know, it sounds like a really dumb problem, but better check that you do have a drumkit loaded ...

---

### Post by homerj742 on 2009-03-30
*Slaps forehead* lol

Well that was it! As you can tell I'm not that well versed in hydrogen. Thank you both so much for all of your help. I really appreciate it! Does this board have any sort of "reputation points" system?

---

### Post by Stochastic on 2009-03-30
> **homerj742 said:**
> *Slaps forehead* lol

Well that was it! As you can tell I'm not that well versed in hydrogen. Thank you both so much for all of your help. I really appreciate it! Does this board have any sort of "reputation points" system?

The only way to pay us back is to stick around and help others who have this same problem.  That's right - you're here for life now  -  muahahaha :evil:

But no, the board used to have a 'thanks' option for useful posts but the servers/databases were getting too strained to handle them all.  At the time of their deletion the staff claimed they'd try to bring the feature back sometime soon.

P.S. for future issues reading the terminal output can be very insightful.

---

### Post by thorgal on 2009-03-31
hey! I'm glad things worked out for you, sometimes it's just as simple (but unexpected) as that :D

About the "point" system, I don't see the usefulness of such a system. Ppl like stochastic or me are dwelling in places like this for a good reason: it is an expression of gratitude for the many open-source developers who, against many odds, decided it was a good thing to release their work for free. So it is only fair that "power users" (if that means anything) help newcomers.

---

### Post by homerj742 on 2009-03-31
Well thank you again. I really do enjoy posting on this board and hope to contribute more as I learn. 

I will definitely keep an eye on the terminal in the future!

Thank you!

---

