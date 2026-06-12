---
title: "Getting sound nice in screencapturing is also difficult."
date: 2011-06-24
forum: Ubuntu Studio
---

### Post by Aisaka_Tiger on 2011-06-24
This is another one of those topics that's kind of been embarrassing for me, since I know so little of what I'm doing. I get the feeling I would cause people to facepalm and sigh out of my utter new-being.

Prepare to hear something... uneducated.. again. I'm an absolute beginner at Linux. So I was just finished getting pretty much every emulator possible to work for Linux, Dolphin and PCSX are both working quite fine. I wanted to make a video of what I've done. I don't have a working microphone right now, but I can still capture video. In Windows I'd tended to use Camtasia or sometimes FRAPS. And uploaded a few videos, it'd be cool to upload and say "hey, these ones I did in Linux!". But it's been a little harder, especially with the sound and grabbing it from internal instead of external sources.

So far I've tried RecordMyDesktop, XVidCap, and Istanbul. So far I've had the best luck with Istanbul. Both with internal audio recording(the programs I'm using, and not a microphone), and easily and conveniently saving the files.

At first, the sound didn't record at all. So I look to the help files and things and found that messing with the preferences should fix things. Turns out the "input" was on very low, and when I put it above %50 or so, it would start to record sound. But it would still be very fuzzy and not of a good quality at all. It also would appear it would only work for "front microphone", despite the fact no microphone is plugged into the computer at all. It's "internal audio analog stereo", after all. Which obviously means by microphone it somehow means internal sound. But it doesn't want to pick it up well.

Just to give an example of what I'm talking about, here's a download link of one of my screencaptures in Istanbul.
[http://www.mediafire.com/?qjnb7jj9wf5a9fp](http://www.mediafire.com/?qjnb7jj9wf5a9fp)
Don't worry, it's not copyrighted. It's a short capture of a youtube video by a youtube user who has made free dubstep songs on their channel. They would definitely not mind. It's also a very tiny file, almost disturbingly so.

Anyway, this is another of probably quite over the top in terms of not-knowing-what-you-are-doing topics today. But I do know the very bare minimum, so please bare with me. I've done a bit of searching, but I don't exactly know how to fix this internal sound pickup problem. If I'm going to screencapture emulation, it would be kind of bad to have sound. And I'd hate to rely on an external microphone. I am planning on making Let's Play videos, but not immediately and I don't want to rely on that.

Thank you for your time.

---

### Post by Pablo_F on 2011-06-25
Hi, 

You might need to access your soundcard controls at a lower level (alsa mixer). 

For a reliable but non graphical interface, in a terminal: 

alsamixer

If you prefer a graphical interface, there are several of them. I suggest gamix (software center).

For a text only interface (useful for give info that you can paste here or anywhere, so others can help you see what is wrong), in a terminal:

amixer

Make sure that the interface is the right one, in case you have more than one. List your audio interfaces with this command:

cat /proc/asound/cards

---

### Post by akavir on 2011-06-25
For my video review site I use xvidcap.  It seems to be the best at video, but not so good for sound.  Posting in the Ubuntu Studio forum I assume you are using it and have JACK?  I use JACK capture to create a seperate .wav file and then merge them in a video editor.  Sometimes it may be a bit tricky to align, but this is the method that works for me.

---

