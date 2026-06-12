---
title: "MIDI foot controller - getting started"
date: 2012-02-09
forum: Ubuntu Studio
---

### Post by Ansible on 2012-02-09
I'm wanting to use an old guitar effects pedal to control various programs in ubuntu studio.  The equipment/software I'm using:

- digitech rp10.  its a guitar effects pedal with midi in and out ports.  I just want to use the midi functions for now.
- echo audiofire4.  
- sooperlooper.
- guitarix.

I have sooperlooper and guitarix connected using qjackctl and that's fine.  I can play my guitar through that and make loops and etc using the mouse to control things.  Its the midi part that I'm clueless about.  I'm a midi noob basically.  

Sooperlooper has a 'learn' function in its midi preferences.  I was kind of hoping I could just plug everything together, hit 'learn' and then hit a pedal on the controller and sooperlooper would detect it.  I've got the pedal and the audiofire connected via 2 midi cables but it doesn't 'just work' so far.

I guess one point of failure could be the pedalboard itself.  Maybe I need to put it into some special mode to send midi events.  Hard (for me) to tell from the manual.

Another would be that sooperlooper doesn't show up on the midi tab in qjackctl.  guitarix does, though, along with the audiofire4.  Does this mean that sooperlooper can't get midi events through the audiofire4 unit?

Do I need to wire devices together on the MIDI tab in qjackctl in order for midi events to be passed between programs/devices?

Is there some other way that sooperlooper does midi communication besides jack, and is it possible to get it going through that other system, if it does exist?

---

### Post by jejeman on 2012-02-10
> **Ansible said:**
> Do I need to wire devices together on the MIDI tab in qjackctl in order for midi events to be passed between programs/devices?

Is there some other way that sooperlooper does midi communication besides jack, and is it possible to get it going through that other system, if it does exist?Yes, you need to connect midi ports in jack.
There are two realms of midi in linux. Alsa realm and jack midi realm. They are separated but can be connected. So, it just depends on what you need.
To connect this realms one can use program: a2jmidid

If you list for us all the ports you have, at the moment, in ALSA and MIDI tabs we can say to you what to do.

---

### Post by Ansible on 2012-02-10
a2jmidid was the key!  With that I was able to connect sooperlooper and my pedal board, finally.  thx for the help.

---

