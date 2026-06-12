---
title: "Can't connect MIDI keyboards to MIDI Through or Wine especially when Jack running"
date: 2014-06-21
forum: Ubuntu Studio
---

### Post by halfbeing on 2014-06-21
I am having trouble connecting midi devices when Jack is running. I have two midi keyboards. When Jack is not running I can connect them to MIDI Through in the graph in Qjackctl, but when Jack is running I can't. If I connect them when Jack is not running then the connection continues to work after Jack has been started. I can however connect the keyboards to, say, Hydrogen even if Jack is running.

On the other hand I have more difficulty connecting the keyboards to Reaper (running in Wine). If I try to connect them, whether or not Jack is running, I get an error message from Reaper (this has to be done within Reaper because Reaper MIDI is invisible to Qjackctl) saying the MIDI input could not be opened. I can however connect Reaper to MIDI Through. (This gives me a workaround of a sort, but it is still causing me headaches.)

I should also point out that this only occurs on one of my machines running 14.04. The other works OK. Any idea what could be causing this?

Many thanks.

---

