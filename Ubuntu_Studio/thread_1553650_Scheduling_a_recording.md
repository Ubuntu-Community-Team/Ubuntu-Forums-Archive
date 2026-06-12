---
title: "Scheduling a recording"
date: 2010-08-15
forum: Ubuntu Studio
---

### Post by rmcellig on 2010-08-15
I have a radio hooked up to my PC that I use to record my radio shows from. I use Audio Hijack Pro on the Mac to do this because with AHP I can set schedules for when to record the shows. For example, Every Sunday at noon, AHP starts to record my show from the radio. I have other radio shows that I record during the week using the scheduling feature of AHP.

Is there anything in the Ubuntu world that would allow me to do the same thing be it a cron job or an app with an easy to use GUI (my preference. Being a Mac user, I am pretty new to the Bash shell and am still struggling through the various commands etc...

Thanks so much for helping me with this!!

---

### Post by cchhrriiss121212 on 2010-08-17
Audacity has a timed record feature, but it doesn't seem to offer a persistent weekly schedule. Maybe useful if you don't mind setting it every week.
It also has sound activated recording based on input levels which might do the job.

---

### Post by lukeiamyourfather on 2010-08-17
You could use cron and GStreamer with ffmpeg. Use cron to schedule recordings, GStreamer to grab the audio, and ffmpeg to encode it to whatever you want. Not sure of an application with a GUI but there might be one out there for performing this kind of task.

---

### Post by FakeOutdoorsman on 2010-08-17
Forum member andrew.46 has a nice guide showing how to [record a scheduled internet radio show](http://andrews-corner.org/ftgws.html).  The script is straightforward and also shows how to use it with cron.

---

### Post by andrew.46 on 2010-08-18
Hi FakeOutdorsman,

> **FakeOutdoorsman said:**
> Forum member andrew.46 has a nice guide showing how to [record a scheduled internet radio show](http://andrews-corner.org/ftgws.html).  The script is straightforward and also shows how to use it with cron.

I have been running that script for a long time now and it still feels like Christmas every week when I wake up and see that beautiful radio broadcast downloaded, transcoded and ready to play :).

Andrew

---

