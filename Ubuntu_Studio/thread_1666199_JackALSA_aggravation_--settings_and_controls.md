---
title: "Jack/ALSA aggravation --settings and controls"
date: 2011-01-13
forum: Ubuntu Studio
---

### Post by mgoldey on 2011-01-13
Folks:

I've been having a lot of aggravation using Jack/ALSA and Ardour, all  having to do with settings and controls.  I'm obviously using it wrong or missing some package that would make it work better for my workflow.  But what?  I've been slogging through outdated documentation and help threads for Jack/ALSA, and I'm  hoping that someone can please cut to the chase and set me straight.  

SPECS:  

Lucid, RT kernel, running headless on an Atom DM-510 mobo and an Audiophile 2496  soundcard.  2.6.31-11-rt kernel and everything is up to date.    Everything works just fine, once I get it running.  

USE: 

Here how I use this DAW:  I use Ardour to record playback of DAT and  cassette tapes through the Audiophile, which I then export to .wav format and work on in  Wavelab on a different machine.  All I'm doing is recording two-channel  PCM audio from a single source through the Audiophile card.  No clips,  no mixing, mastering, bitrate conversions, etc., etc.  No playback,  either.  Just capture, and export to .wav and copy the file to another  machine.  

THE USUAL IRRITATING WORKFLOW:

Because Jack is set to run in Duplex (-D) mode, jackd shuts down after 10 seconds  with the normal "jackd watchdog timeout" unless I turn a DAT machine on  and plug it into the Audiophile card.  Naturally, Ardour stops working  as well.  Thus, to export an Ardour session to .wav, I have to find a  DAT that's set to the same bitrate as the session and plug it into the  soundcard.  Otherwise, jackd craps out.  

Worse, qjackctl doesn't quit, it crashes and it's  process windows  freeze.  That freezes Ardour as well.  Qjackctl can't be closed except  via a kill  command.  That might have been OK for version 0.1, but it's obviously not how jackd is intended to be used.  

Change the Jack settings, you say?  Read on . . . .

Some context: I don't run a patchbay or anything that could be always on  to feed signal to the audiophile and keep Jack happy.  It's obviously not OK for me to constantly shift cables  around or  turn the stereo on and off, just to provide an electrical connection to the soundcard.  I can't imagine jackd was designed to require that, either:  could you imagine a professional studio where  something is always being switched around, and Jack quits unless you  do in within 10 seconds?  

SETTINGS SNAFUS:

One solution is to change Jack to playback only.  There are two problems with this.  First, there's nothing  *ever* plugged into the Audiophile outputs, since the DAW isn't used for playback.  But even if I broke down and plugged the output into something, jackd crashes before I can make any changes to the settings via  qjackctl, like going from Duplex to Playback only to Record only.  It's a wonderful(?) design feature(?) that you have to make  changes, save them, and restart Jack all within a 10 second window.   Mostly, I can't do it fast enough.  

Jack defeats me at every turn.  It ignores changes to my ./jackdrc and /etc/jackrc.  For example, there's no -R flag in my ./jackdrc and it's set to -p1024 but Jack runs in  RT with 256 ports shown in qjackctl. What config is it pulling?  (Try googling for an answer to that!)  Worse, qjackctrl over-writes ./jackrc each time it crashes.  So,  changing -D to -P wouldn't matter anyway.  Occasionally, I am fast enough to uncheck  the box for "save settings to file" on the Misc tab of qackctl and  restart jack before it crashes.  But this just can't be how it's  supposed to work:  a race against the clock to get every setting right in 10 seconds, or a complicated command line and restart throughout the day?  Again, maybe for version 0.1, but itt's not 2007 any more.
  
It seems to me that the Audiophile should be  enough to feed Jack whatever Jack wants so that Jack will shut up and  leave me alone, without external hardware being powered on.  Sounds like a mix/patching problem, eh?   Enter Alsamixer. 

ALSAMIXER MADNESS:

I'm not wed to alsamixer, but it seems to be the appropriate package for hardware level control, and a lot of people with similar Jack problems report changing alsamixer to solve their woes (e.g., to playback only).  

The gnome-alsamixer package has no  documentation that I can find.  (Here's where the 2007-era forum posts  get thick and three years out of date).  At best, I can untick the "rec" box which means . . . what?   The attachment shows my gnome-alsamixer panel.  Clear as mud.  

/usr/bin/alsamixer, in turn, has no options to change recording v.  playback.  Better yet, it reports that it's using  "Advanced Linux Sound  Architecture Driver Version 1.0.20" while dpkg reports another version"ii   alsa-utils                           1.0.22-0ubuntu5".   (alsamixer is part of the alsa-utils package).  The usual fix  for that sort of thing -- reinstall the package -- yields this gem:

"The following packages will be REMOVED:
  alsa-utils ubuntu-desktop"

Yes, that's what I want to do.  I want to uninstall my desktop.    :roll:

Bottom line is, this sort of endless futzing around to do the simplest tasks cannot be right.  I must be missing some obvious step or piece of software that would tie Jack to the Audiophile in a way that prevent endless crashes, quits, etc.  

Can you help?  Here are some specific questions:

1) Is there any sort of dummy or internal connection that will allow Jack to service  a piece of software running on the same machine, without having a live  input or output to/from the soundcard?  

2) If not, can jackd be set to timeout after 60 seconds, instead of 10?  That would give me a fighting chance of actually changing settings.

3) Any idea why alsamixer seems to be 2 versions behind the repository-installed packages?

If you've read this far . . . thank you!

---

### Post by cchhrriiss121212 on 2011-01-13
Sorry to hear you have been having so much trouble. As far as I can see, you don't really need jack or Ardour at all. Try installing Audacity then use it to capture your audio input. 

Or you could use [arecord]("http://alsa.opensrc.org/index.php/Arecord") from the command line if you like. Like this:
```
arecord -f cd test
```
This will create a WAV file named test.wav in your home folder at 44.1kHz/16bit depth in stereo. It will use the default soundcard unless you specify otherwise.

---

### Post by Pablo_F on 2011-01-13
Hi, 

Lots of things. I will try to help in some of them.

I run lucid with a m-audio audiophile 2496. Same kernel as you.

> 3) Any idea why alsamixer seems to be 2 versions behind the repository-installed packages?

Drivers and utils are different pieces of software. Don't worry about this. Your alsa drivers version works. You don't need to reinstall alsa-utils. BTW, ubuntu-desktop is just a metapackage. 

Anyway: DON'T USE alsamixer for your card. You have a specific tool to access the snd-ice1712 cards:
[B]
envy24control[/B]

(from alsa-tools-gui package)


> 1) Is there any sort of dummy or internal connection that will allow Jack to service a piece of software running on the same machine, without having a live input or output to/from the soundcard? 

The dummy driver


I don't know what happens with your jack and I am not familiar with DAT. It could be something wrong in your card settings (envy24control).

You can always ask for help in #jack or #ardour or #ubuntustudio channels in irc.freenode.net.

---

### Post by mgoldey on 2011-01-13
Thanks, I'd forgotten about Envy24Control.  

Sure enough, setting the rate on the card to the same rate as the Jack session lets Jack run w/o a physical input.

Thanks, too, for the suggestion that Ardour and Jack are overkill.  I agree that in some ways they are.  But, I've had a lot of bad luck transferring DATs only to discover, after working on the transfer for a few hours, that there are dropouts, static, etc.  I wanted something designed to work in real time, report Xruns, show me a waveform in real time, etc.  Ardour seemed like the way to go.  It would be perfect if only it would do one of two things:

1) Stop recording after a pre-determined time, or
2) Let me delete the end of the session waveform (so I can go to sleep and reduce a 10 hour recording session to 2 hours, before export to .wav)

---

### Post by cchhrriiss121212 on 2011-01-13
In this case Audacity would be a better choice. In theory it should have *less* chance of going wrong as it is a simpler recording chain. You can set Audacity to stop recording after a certain time with Transport>Timer Record.

---

### Post by Pablo_F on 2011-01-13
Audacity is not as good as ardour as a jack client. 

You can do both things:

> 1) Stop recording after a pre-determined time

A little tricky, but here it is:

Install gnome-scheduler and pyliblo-utils

replace /usr/share/gnome-schedule/at.py with the attached file in 
[https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/617873](https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/617873)

In ardour, Options -> Misc options: Use OSC 

(BTW, Stop recording at xrun detect could be useful for your needs too)

Now, in Applications -> System tools -> Scheduled tasks, New, a task that launches one time:
Select day and time. The task is:

send_osc 3819 /ardour/transport_stop


> 2) Let me delete the end of the session waveform (so I can go to sleep and reduce a 10 hour recording session to 2 hours, before export to .wav) 

If the edit point is the mouse, you only have to point to somewhere in region and press "S" to split it in two, then delete the region you don't need, just click and and delete. Or you can trim the region by dragging the mouse while pointing to the coloured zone at the bottom.  

Cheers! Pablo

---

### Post by mgoldey on 2011-01-18
Thanks, guys, for the reply.  With your help, I've got the aggravation level down to something tolerable.  I'm going to play with the Ubuntu scheduling functions next.

---

