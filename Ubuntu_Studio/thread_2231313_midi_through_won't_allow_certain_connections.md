---
title: "midi through won't allow certain connections"
date: 2014-06-24
forum: Ubuntu Studio
---

### Post by halfbeing on 2014-06-24
Hello,

I've got two areas of misbehaviour on one of my Ubuntu Studio systems and I think they are related to each other.

First of all I have difficulty connecting certain things to MIDI through when Jack is running. To be specific, I cannot connect either of my MIDI keyboards to MIDI through in either direction (using qjackctl) when Jack is running. However I can connect them when Jack is not running. I can also connect applications such as Hydrogen both to the MIDI keyboards and to MIDI through whether or not Jack is running.

Secondly I cannot connect any MIDI port to Reaper (running in Wine), using Reaper's MIDI preferences, whether or not Jack is running. However I can do it on my other Ubuntu Studio system. The error messages are of the form "The following MIDI inputs could not be opened: a2jmidid - port".

There are workarounds for most of the problems this causes, but not all of them, so I would be very grateful if anyone could help me work out why my MIDI is being so uppity.

---

### Post by CrocoDuck on 2014-06-30
Hi! Sorry for the late reply, I didn't see this :oops:.

You have to install a2jmidid.

```
sudo apt-get install a2jmidid
```

refer to a2jmidid documentation for usage. You can have info online and from man page:

```
man a2jmidid
```

[This]("http://ubuntuforums.org/showthread.php?t=2232111") could interest you.

---

