---
title: "recording MIDI and audio in LMMS"
date: 2010-11-15
forum: Ubuntu Studio
---

### Post by toolmania1 on 2010-11-15
Hello,  I just installed LMMS.  I checked their wiki, some other sites I googled, and some youtube videos.  I cannot find how to record MIDI in LMMS.  Anyone know how?  I am running Ubuntu 10.10.  I just got it installed within this past week or two.  I really like it.  I used to use FL Studio.  I was really excited about LMMS.  I just want to be able to record.  Also, if this answer is know too.  How we can record audio?  In FL Studio in Windoze, I used to be able to use 'Edison' to record audio from my keyboard.  Thanks in advance, toolmania1

---

### Post by toolmania1 on 2010-11-16
So, after 43 views this morning, I am guessing that this cannot be done?

I thought I saw someone else post that they were able to record.  I tried to message them, but I don't have 75 points yet.

---

### Post by Peter7K on 2010-11-16
I would check out Tools > Settings > MIDI Interface and check out what you can do with those settings.  I don't have a MIDI keyboard so I can't really see the potential options.

---

### Post by sgx on 2010-11-17
I have tried lmms many times over the years, and it always has crashed in flames within minutes. It's an ambitious project, but to easily record both audio and midi in linux, I find Reaper in a wineasio setup to be the most stable, and easiest to learn. Some are using the FLS in the same manner, there is a long thread here telling the tale. If your hardware
is 'wineasio friendly' it may be worth a weekend in the config cage to get it working.

[http://ubuntuforums.org/showthread.php?t=1260057](http://ubuntuforums.org/showthread.php?t=1260057)

Cheers

---

### Post by Pablo_F on 2010-11-17
qtractor is another option.

---

### Post by toolmania1 on 2010-11-18
Well, I actually have read the above listed thread before.  I also have read things about WINE.  I really enjoy having such a safe system in ubuntu.  I left windows for this reason as well.  I read with WINE, you can open yourself back up to the windows viruses and such.  I don't want to deal with that stuff anymore.  Do you guys have an opinion on this matter? ( Pablo, sgx, or anyone else )

---

### Post by Peter7K on 2010-11-18
Well using WINE... you have an isolated little contained box of good ol' Window$.  Pretty much the only way you could get a virus would be opening internet explorer and going to malicious sites, etc.  If that were to actually happen, you could just delete your .wine folder and start fresh (you'd have to reinstall REAPER, etc.).  Audio has come a long way on linux over the past few years (developing at an incredible speed), but it's still not quite ALL the way there yet, and some proprietary options are superior still.  And of course, if you want to really stick it to the proprietary people you could just torrent the app (i'm totally kidding of course).

---

### Post by toolmania1 on 2010-11-18
Hmmm.

Well, I will have to know a lot about WINE before I do that.  I have heard it mentioned in several posts.  I have not studied it yet.  In the meantime, I am going to stick with what I can get through Ubuntu and learn about them.  Maybe they do enough.  I only want to goof around anyways.  It's not like I am Dr. Dre.  Or am I?  muwaaa hahahaha ( Dr. Evil laugh )

j/k

;)

---

### Post by toolmania1 on 2010-11-22
I have also read that by combining many of the audio resources in Ubuntu, you can get done what you need.  So, I was wondering, can any of these record what LMMS puts out:

Rosegarden, Audacity, Muse.

Oh, and are there any other packages that could record what I would play in LMMS?
:)
Thanks

---

### Post by JayPeeJay on 2011-02-13
I am sure you have probably figured this out by now, but since this thread only points you towards WINE I will reply.  You can indeed record midi in Lmms.  I would need to know more about your setup to figure out why it isn't working for you.

You can also, by using Jack, record the output from LMMS (route it to Audacity or Ardour to record an audio track, route it to JAMIN to master it, etc.) or you can simply go to Project--> Export to "bounce" a track into a .wav or .ogg (you will need another program to compress it to mp3).

As far as recording audio directly into LMMS without using another program and then importing the file into the audio file processor, well.. that's what I am trying to figure out.  That is how I found this post.

---

### Post by cedicon on 2011-11-21
As of version 0.4.12, LMMS 'records MIDI' input from the keyboard in its 'Piano Roll' function. It does not, however, export MIDI files (ie. "*.mid"), only *.WAV & *.OGG files ("bouncing", etc.). 

Also, LMMS does not *record* MIDI CC data, like knob & fader controls found on many MIDI keyboards and MIDI controllers. This is actually how I found this post. I was hoping that there might be some hidden, secret way to write the CC data from an assigned knob/fader on my MIDI keyboard to an automation track, but nope. NOPE.

If you are looking for a way to record the raw sound of your soft synth or sampler in LMMS to a file that can then be imported into the song editor, pattern editor, etc., then JayPeeJay had it right with using JACK to connect the output of LMMS to the system 'capture' channels. That way you can record the sounds routed to the system 'capture', or input (same thing), with any program that records audio. (my personal preference being Audacity)

Qtractor, currently 0.5.1, is another program that is useful for MIDI sequencing and recording. With Qtractor you can export *.mid files as well as audio files. You can also map MIDI CC controls to the mixer, plugins, etc. Now that automation has been implemented, there is an option to 'Record', so it appears to me that Qtractor can record MIDI CC data and write it to automation.

JayPeeJay, AFAIK, you cannot record audio directly into LMMS. You can only import sound files into the Audio Processor instrument.

---

