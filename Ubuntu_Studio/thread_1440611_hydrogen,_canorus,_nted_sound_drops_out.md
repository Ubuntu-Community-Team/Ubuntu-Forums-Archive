---
title: "hydrogen, canorus, nted: sound drops out"
date: 2010-03-27
forum: Ubuntu Studio
---

### Post by dcroxton on 2010-03-27
I discovered Hydrogen a few days ago and enjoyed playing it.  Everything worked out of the box.  Then, when I went back to it yesterday, I got no sound.  I can export a .mid file and play it, but I get no sound in the hydrogen application.

This is very frustrating, because I am obviously missing no software packages, or else it would never have worked in the first place.  Obviously midi is working, because I can play midi files.  I tried purging Hydrogen and re-installing, but with no better luck.

I had this same problem some time ago with Canorus and Nted.  For some reason, sound just seems to drop out of these applications.  I could only make wild speculations as to why.

I'm running Ubuntu 9.10, 32 bit.  Any help would be appreciated.

Sincerely,
Derek

---

### Post by sgx on 2010-03-28
Hi, disconnect from the net, shut all sound apps off, do a ctrl-alt-backspace xorg reset, then

start jackd: jackd -d alsa -r 44100
then start qjackctl, 
make sure your qjackctl settings are for your soundcard,
start hydro, making sure hydro is connected in both the audio and alsa tabs in qjackctl
load a kit, load a pattern, load a demo song etc hit the play button,
remember there is a little button switching between song mode, and pattern mode.
The panel opened by the menu Tools-->preferences has a restart button, and options to choose the jack sound server, or other ones.
Sometimes a requestor can open behind the main hydro screen, deeking the user into thinking the app just froze, so minimize or drag the gui to check.

If still no luck, try zynaddsubfx, connecting in qjackctl as per the above instructions, it has a Virtual Keyboard (abbreviated on its button)
and when pressing a key by mouse or querty you should see action in its gui, and hear the default sound. If zyn works and hydro does not, we must dig deeper.
Cheers

---

### Post by AutoStatic on 2010-03-28
> **sgx said:**
> do a ctrl-alt-backspace xorg resetctrl+alt+backspace has been disabled since Jaunty 9.04.

@dcroxton, are you using JACK? What are your settings in Hydrogen (Tools - Preferences - Audio Settings)?

---

### Post by sgx on 2010-03-28
> **AutoStatic said:**
> ctrl+alt+backspace has been disabled since Jaunty 9.04.

@dcroxton, are you using JACK? What are your settings in Hydrogen (Tools - Preferences - Audio Settings)?
Sorry to mislead, I'm on another distro until I get a new motherboard,
had no idea that Ubuntu changed a nearly universal xorg reset.

Here is a workaround, to restore it, or use a Ubuntu recommended alternative,

[http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html)

 and a lively debate about the keycombo being changed.

Using konqueror, Opera, zynaddsubfx, audacity, and lots of wine based audio plugins, there is room for tons of beta-misbehaviour, that quickly gets resolved by resetting X. Some things are just good luck!

---

### Post by dcroxton on 2010-03-28
Thanks for the helpful responses.

I followed the instructions for running jackd, and it got hydrogen working.  No amount of changing settings could get nted or canorus to play sound, however.

Then I rebooted.  Without running jackd, not only hydrogen, but also nted and canorus worked.  Very strange.

Hydrogen has audio driver = auto and midi driver = PortMidi.  Canorus has MIDI out pointed to Timidity port 0.  It doesn't work when Hydrogen is running, even if I change to another Timidity port.  However, Canorus and Nted can co-exist on port 0.

I'm clueless about what's going on, but I'm happy that it at least works now.  Does anyone have any explanation?  Given the way sound has disappeared in the past, I expect I'll be back here in the future at some point (although at least now I know how to start jackd, which might solve the problem).

Sincerely,
Derek

---

### Post by sgx on 2010-03-29
> **dcroxton said:**
> Thanks for the helpful responses.

I followed the instructions for running jackd, and it got hydrogen working.  No amount of changing settings could get nted or canorus to play sound, however.

Then I rebooted.  Without running jackd, not only hydrogen, but also nted and canorus worked.  Very strange.

Hydrogen has audio driver = auto and midi driver = PortMidi.  Canorus has MIDI out pointed to Timidity port 0.  It doesn't work when Hydrogen is running, even if I change to another Timidity port.  However, Canorus and Nted can co-exist on port 0.

I'm clueless about what's going on, but I'm happy that it at least works now.  Does anyone have any explanation?  Given the way sound has disappeared in the past, I expect I'll be back here in the future at some point (although at least now I know how to start jackd, which might solve the problem).

Sincerely,
Derek
Hi, part of it is there are several audio systems installed, and
each being best in their own eyes, they often fight to be king. Some apps work in more than 1. You might
find and compare any configuration files in a text editor, (don't save them if they are binaries), look in /usr/share, /usr/include, /etc,
/home/user (look for 
.textfiles or in .folders bearing their name, or their gui toolkit folders
(.gtk, .qt, .fltk etc) or .alsa  .esound .pulse  for sound system info ...looking for signs of conflict, or things in common.
And google them with alsa, and other relevant terms.

Timidity needs a soundset. It has a config file to choose one. Google
fluidr3.sf2 timidity, and the instructions to download, choose and configure that sound font, it may even be in the repos, or installed, but not yet selected in the textfile config. There is also a dedicated timidity soundset
Cheers

---

### Post by sgx on 2010-03-29
heres an article on linux scoring software, look in the comments too

[http://www.linuxjournal.com/content/music-notation-software-linux-progress-report-part-2](http://www.linuxjournal.com/content/music-notation-software-linux-progress-report-part-2)

---

