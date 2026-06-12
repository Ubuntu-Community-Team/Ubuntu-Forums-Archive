---
title: "LADSPA plug ins to use with Jokosher?"
date: 2010-12-29
forum: Ubuntu Studio
---

### Post by keithpeter on 2010-12-29
Hello All

Newbie alert!

What packages do I need to install to get a few effects to use with the Jokosher sound editor? LADSPA effects work apparently. What Ubuntu repository packages are people using with Jokosher? All I'm picking up in searches is how  to avoid a bug with gstreamer.

Most of the ones I can see in the Ubuntu repositories expect or refer to Jack audio, i.e. Jack Rack. Do I just go ahead and install those but not Jack? 

This is all going on a netbook using 10.10 netbook remix...

Thanks very much

---

### Post by AutoStatic on 2010-12-29
Hello keithpeter,

Just open up synaptic and look for the **ubuntustudio-audio-plugins** package. That should pull in enough plugins to get you going :)

Best,

Jeremy

---

### Post by cchhrriiss121212 on 2010-12-29
You do not need jack to use LADSPA plugins. Install the package you want and the plugins show up automatically in Jokosher, I just gave it a quick test myself and it all works nicely.

I haven't tried Jokosher before today, I don't know why as it is a nice piece of software. Are you getting on OK with it?

---

### Post by keithpeter on 2010-12-29
Hello Chaps and thanks for the replies

@AutoStatic: ubuntustudio-audio-plugins wants to install jack2 &c. I'm trying to avoid that

@cchhrriiss121212: can you tell me the name of a package that contains one or more LAPSPA plug ins that I can install that won't install Jack? A nice mono reverb would be handy. Is there one in the Ubuntu repos?

I've barely got past the recording a couple of grunts from the built in microphone in Jokosher but it looks relatively easy which is what I need for this application. It'll be running on an asus EeePC and being used for workshops & playing about.

---

### Post by keithpeter on 2010-12-29
Hello again

[https://answers.launchpad.net/jokosher/+question/90094](https://answers.launchpad.net/jokosher/+question/90094)

following these instructions has provided a range of plugins. Jokosher recognises them after you delete the .gstreamer-0.10 directory in your home before restarting Jokosher.

They don't seem to work like in Ardour where you can alter parameters while playing the track, but its easier to use and is what I need for some 'open source magic' demonstrations. 

Thanks

---

### Post by AutoStatic on 2010-12-29
> **keithpeter said:**
> @AutoStatic: ubuntustudio-audio-plugins wants to install jack2 &c. I'm trying to avoid that.Then try installing the following packages:
[LIST]
[*]caps
[*]cmt
[*]fil-plugins
[*]invada-studio-plugins-ladspa
[*]rev-plugins
[*]swh-plugins
[*]tap-plugins
[*]calf-plugins
[/LIST]

Best,

Jeremy

---

### Post by keithpeter on 2010-12-29
> **AutoStatic said:**
> Then try installing the following packages:
[LIST]
[*]caps
[*]cmt
[*]fil-plugins
[*]invada-studio-plugins-ladspa
[*]rev-plugins
[*]swh-plugins
[*]tap-plugins
[*]calf-plugins
[/LIST]

Best,

Jeremy

Thanks, adding the extra ones now (Calf, rev, invada)

cheers

---

### Post by karlhutt on 2011-09-15
i intalled all the packages above and work fine, but still don't find a reverb effect on my Jokosher. any ideas?

---

