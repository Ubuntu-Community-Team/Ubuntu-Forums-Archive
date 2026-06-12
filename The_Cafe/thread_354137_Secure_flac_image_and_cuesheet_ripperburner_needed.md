---
title: "Secure flac image and cuesheet ripper/burner needed"
date: 2007-02-05
forum: The Cafe
---

### Post by VCSkier on 2007-02-05
I've been looking and dreaming of a cd ripping/burning utility that is comfortable in the gnome environment since I left Windows over a year ago.  I used to use EAC to rip and encode losslessly compressed images and cuesheets, and Burrrn to burn them back to exact duplicates.  It was beautiful, and I never had to worry if a cd got damaged, because I always had a perfect copy archived.  Now, in linux, I can't find any acceptable alternatives.

I would even be willing to compromise on the secure part; a good cdparanoia ripper would give accurate enough results for me, without the secure guarantee that EAC offered.  But, I do need a system that allow me to maintain all the gaps between and before tracks though, hence the use of images and cuesheets.  Ideally, I would like to be able to encode the cd images to flac, and then embed the cuesheet in it, and then at a later time, be able to decode and rip it easily.

Please feel free to suggest ideas of methods or applications I could use, or even other places I could make requests.  Thanks.

---

### Post by MetalMusicAddict on 2007-02-05
Have you tried Grip? See the link in my sig. Its a work in progress. I dont know if it does cue sheets but its honestly the best thing we have in linux. You can run EAC in WINE.

---

### Post by Jussi Kukkonen on 2007-02-05
I know this is not what you asked for,  but if you are ready to use a command line app, *abcde* is a wonderful ripper/encoder/tagger that is very modifiable for your needs -- my setup currently rips, encodes to flac, gets tags from cddb, calculates replaygain and moves the files to my music directory with one press of a button on my media box remote.

Abcde can use several backends, like paranoia or cdda for ripping. The setup naturally takes a little more time, but if you are going to rip lots of CDs like I do, it's definitely worth it.

---

### Post by VCSkier on 2007-02-06
I've tried both grip and abcde in the past, and both are good programs, just not what I'm looking for particularly.  abcde does most of the things I want and is a very good ripper, probably the one I'm going to be using until something better comes along, but I've been having some difficulties with it, and it's interface isn't necessarily the easiest for newbies like myself to manage.  I just haven't had the time to spend working with it yet.

Grip on the other hand, while I'm sure it's great for alot of users, its quite a bit lacking for my needs.  FWIW though, it does have a very nice interface, something that I would love if abcde had.

I just wish that more users and/or developers would show alittle interest in quality audio tools; it seems to me like everyone's attention and time is going into all of these "yet-another-itunes-clone" audio players, and its quite a bit discouraging.  IMHO, from what I've seen, abcde is the best we have, and *i don't think* its even being actively developed currently...

edit (my rambling continues)...  If we had programs to compete with EAC and foobar2000, I think linux userbase would grow to bring in alot of audio junkies (those guys over at hydrogenaudio.org :) )  I guess our problem here is in a way recursive and self defining.  We don't have these programs because we don't have many audio-minded users asking for them, and we don't have many audio minded users asking for them, because we don't have many programs to convince audio-minded users to switch to linux.  What are we to do...

---

### Post by bonejob on 2008-03-28
I know I am coming late to this party, but I have been frustrated by the same issue in Linux and I have found a solution that is acceptable to me, at least.

I just downloaded and installed (through WINE) the latest 0.99 beta of EAC. It installed and configured without a hitch. It even automatically found my FLAC encoder! (Older versions required one to manually point EAC to the desired encoders.)

I just pull the album info from FreeDB, and tell it to rip a compressed CD image with cue sheet; Bada Boom, Bada BING!

The only caveat of course is, make sure you install whatever codecs you want - LAME, FLAC, FAAC, OGG - BEFORE you install EAC. EAC can't find what isn't there!

NOW my only problem is finding a Linux media player that supports playback from cue sheets. Foobar2000 does, and it will install through WINE, but sadly, it is not very stable running in Linux. 

Anyone with a suggestion for a native Linux media player with cue sheet support?

---

### Post by solarin_kb on 2008-04-03
I suggest using Amarok.  It has a superb interface even if it is KDE.  It will automatically read your cuesheet and allow you to even skip through tracks using it (even though you have one large mp3 instead of broken up tracks).

---

### Post by maxim99 on 2008-07-01
I'm interested in finding an application that will be able to do what the original poster was trying to accomplish. Mainly the part where it is trying to burn the the CUE/WAV combination recreating the gaps and pre-gaps.

I looked a few months back and you can see my findings here:

[http://fedoraforum.org/forum/showthread.php?t=183662](http://fedoraforum.org/forum/showthread.php?t=183662)

I did not have much luck.

---

### Post by maxim99 on 2008-08-20
I have found that for the most part the cue is not needed depending on how the original WAV is pulled off of the disc.

Given the following scenario the cue is not needed, simply removing the gaps is enough to produce an audio experience identical to the original.

Things to take into consideration here are the gaps between tracks, the tracks themselves, and the placement of both together. Almost all CDs start out with atleast a two second gap infront of the first track, this is unavoidable as far as I know. What can be done with the rest of the gaps is up to the user ripping the CD. The most common scenario is to *append* the gap to the *previous* track. So the gap that is at the end of track one and before track to will be appended to the end of track one. If this is done for all of the tracks, then in order to create the same waveform again on another CD, burn all of the tracks together *without* gaps at all. This is done because all of the gaps are actually appended to the previous track. The audio experience will be the same, the only difference is that there will be no "negative" time displayed when changing tracks on the CD player.

If a user must produce a CD including the original gaps then they are out of luck in the Linux market, the option (and demand) simply isn't there. They must use Windows and (as far as I know) must use ExactAudioCopy in order to do this.

Here is a neat little tutorial that explains this concept:

[http://www.digital-inn.de/exact-audio-copy-english/16964-gap-cue-sheet-101-simple-tutorial-dummies-like-me.html](http://www.digital-inn.de/exact-audio-copy-english/16964-gap-cue-sheet-101-simple-tutorial-dummies-like-me.html)

---

### Post by ghindo on 2008-08-20
I realize this thread is old, but people are definitely missing out on Rubyripper as a viable secure ripper.  It has both cuesheet and log support, and supports FLAC, mp3 and ogg.  Check out my sig for more.

---

### Post by VCSkier on 2008-08-21
Thanks for the "heads up" regarding RubyRipper.  I had checked it out in the past because of it's secure ripping and had been disappointed with it's lack of other features, but now if it can handle cuesheets and ripping to a single file, I think this might be my solution.  I'm quite excited.  I used your tutorial (thanks again ghindo) to install and I'll be testing it out (hopefully) soon.  I still wish there was a program that would take an encoded flac image (single-file) and cuesheet and generate indiviual mp3's, one per track.  In the mean time though, assuming RubyRipper does indeed now support single-file ripping and cuesheets, I'll just do two seperate rips, one to a single-file flac, and then another to seperate mp3's.  I'll post back with what I find!

---

### Post by k.eight.a on 2008-10-28
@ **maxim99**: I must laugh. :lolflag: I have recently the same difficulties as you > [see]("http://ubuntuforums.org/showpost.php?p=6045449&postcount=5").
Anyway I was able to burn an Audio CD image in one *PCM Wave* file with CUE sheet without any problems.
Now I want to burn a project of separate *FLAC* tracks and a CUE sheet and it tells me the same error, so I wanted to find out where the problem lies. :?: :D

@ **VCSkier**: Cheers to another *HydrogenAudio.org* member! ;)

---

### Post by VCSkier on 2008-10-28
It seems there is progress being made, albeit slow.  As I mentioned before, RubyRipper has the basic features I want implemented (secure ripping to a single FLAC file with cue sheet generation), but there is a [bug]("http://code.google.com/p/rubyripper/issues/list") (issues 248 & 236) standing in the way of success.  Unfortunately there seems to be only one developer for RubyRipper, with a long list of todo's at the moment.  If anyone here has some experience with ruby, I'm sure he would apprecieate some help.

Oh and yes, I was once very active on HydrogenAudio.org.  But since linux changed the way I used and viewed computers, I don't find myself logging in over there nearly as much.  It's a shame though.  At one point, I believe I was up to over 2 posts a day average, and they even started up a "Non-Windows Audio Discussion" forum at the [request]("http://www.hydrogenaudio.org/forums/index.php?act=ST&f=25&t=47475") of me and some other linux users.  Things [didn't turn out]("http://www.hydrogenaudio.org/forums/index.php?s=&showtopic=47475&view=findpost&p=446666") as planned.  Who knows though, as RubyRipper comes to maturity, hopefully some other helpful tools will come up beside it and linux will garnish the attention of more of the audiophile world.

---

### Post by k.eight.a on 2008-10-28
I'm quite happy with RubyRipper, it suits good for my needs. I'm a beginner so first I wanted just secure MP3 ripper. It generates CUE sheet for the MP3 files so it is OK, but I've never heard of MAREO or REACT for Linux that can create both lossless and lossy files in one step. I don't have any clue if there is any powerful transcoder for Linux like Multi Frontend and others for Windows are.

Still I'd love to realize were is the problem with burning my separate FLAC tracks and CUE sheet. :D
*Pregap out of range* drives me insane because I understand most of the CUE sheet generation but I lack the useful tools that can help me to spot the problem.

I've also posted to the HA linux thread although it is almost two years since the last post. I think there will be more and more GNU / Linux users out there and sooner or later such a category will be needed at HA. Searching is more complicated when there is no dedicated category for non-Windows users.

---

### Post by VCSkier on 2008-10-28
k.eight.a, have you tried burning with another application, like K3B?  It sounds to me like the burning program you are using may just not like cd's with pregaps, but I'm no expert.

---

### Post by rotwang888 on 2008-10-28
One cool thing about Rubyripper I didn't see mentioned here is that it can output more than one format in one go.  IE flac and LAME Mp3.  As far as coverting individual mp3s from a single flac file, I think the easiest thing is to install foobar with Wine.  I assume you know what to do from there.
  And here's another vote for a foobar2000 equivalent for Linux.  I'm spoiled and everything else falls short.  Each time I think I can live with a player I run into something like lack of gapless flac playback, no way to browse by folder structure, etc..

---

### Post by miche11 on 2008-11-24
Hi, putting up the topic, with any big news...
I got at this step, and ie I still can't find a solution to do what i do under windows with nero:
i got an EAC copy of my albums, can open the .cue file (same whether flac or ape, having the plugins it works out fine) and through nero burn a virtual image.
From that, i can _Mount_ it (all virtually, no physical support needed), let it play and even download the covers !!! 
Then simply have a rip with all the tags in a uniform format.
Questions (about 4 weeks looking for this, running Kubuntu 8.10 right now):
- how to burn a virtual image (.iso) of .ape + .cue files ? 
i downloaded the k3b mac-ape plugin, tried to burn an image (a .iso virtual image), it gave back splitted wav files, one for each track (thus loosing the original cue tracklist)
- how i mount it on a virtual device ?
(ok, nice, i know already the solution, it's a trap question :))
- then comes the play, like for a normal audio cd. this can be managed by every player, and eventually also the covers can be downloaded (important fot the ipod!)
- how to rip this cd in lossy format (say, mp3): i didn't even look for an answer, since this's the point number 4.

or perhaps the whole procedure is a little heavy, and you could give me some advice to do all that in a smart way ?

---

