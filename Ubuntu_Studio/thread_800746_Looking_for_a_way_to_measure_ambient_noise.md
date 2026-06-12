---
title: "Looking for a way to measure ambient noise"
date: 2008-05-20
forum: Ubuntu Studio
---

### Post by r8dhex on 2008-05-20
I'm trying to make a digital picture frame from an old laptop. To conserve power, I'd like it to only turn on the screen when the built-in microphone detects noise above a certain threshold, basically when someone is in the room.

I tried google, but I don't know exactly what to look for, I keep finding audio-editing programs or volume controls. Ideally, it would be a command-line tool that would return a 0-255 value, that I could script using bash, but I'm not sure if there are any.

---

### Post by Stochastic on 2008-05-20
If you're looking for command line based tools, then there's Chuck, SuperCollider, and a few other programming languages that deal with audio quite well, and can take command line args if needed.  There's also less specific languages that could be used if you grabbed the right libraries.  

Essentially you'll be looking at the incoming signal from the mic and checking its value to see if it's above threshold x.  You'll also probably want to insert some envelope following before you check its value to prevent quick on/off stuff.  Then you'll want to send out that yes/no data to your external code.  The sending of the message to a bash script part I'm not too sure of, you should look to see if you can find a MIDI or OSC tool that will listen for a signal and report any messages to bash.

In the end, what you're looking for is a custom built piece of coding.  I might be able to help along the way if you get in over your head.

---

