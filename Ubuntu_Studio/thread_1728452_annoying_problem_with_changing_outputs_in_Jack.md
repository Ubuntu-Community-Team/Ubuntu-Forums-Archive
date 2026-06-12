---
title: "annoying problem with changing outputs in Jack"
date: 2011-04-13
forum: Ubuntu Studio
---

### Post by m3x1c0 on 2011-04-13
Ok so I had Jack all set up to play nice with my external sound card/ interface but I was away from my house today without my interface and wanted to do some mixing to some recordings in Ardour. Unfortunately no matter what I do I cannot get ANY sound out of Ardour using my laptops internal hardware. Ive been playing with settings and digging in forums for hours and cannot figure it out. When I export the audio to Flac a timer will run but no sound will happen. Here is my current Jack configuration but keep in mind ive been changing it for hours, (hopefully ill be able to get my sound card working again)

[[img]http://farm6.static.flickr.com/5026/5617760628_16422b30c5_z.jpg[/img]](http://www.flickr.com/photos/61715305@N05/5617760628/)
[Screenshot](http://www.flickr.com/photos/61715305@N05/5617760628/) by [xavcorral](http://www.flickr.com/people/61715305@N05/), on Flickr

Once I get this set up right I'll be sure to save the configuration!

---

### Post by zettberlin on 2011-04-14
> **m3x1c0 said:**
>  I cannot get ANY sound out of Ardour using my laptops internal hardware. 


I fail to see anything wrong in your config and jack seems to run perfectly OKish.

Have you checked the mixer?

```
alsamixer -c0
```

---

### Post by m3x1c0 on 2011-04-15
> **zettberlin said:**
> I fail to see anything wrong in your config and jack seems to run perfectly OKish.

Have you checked the mixer?

```
alsamixer -c0
```

just did. levels are up and using the appropriate sound card

---

### Post by nightmorph on 2011-04-15
Set Ardour to perform (software) monitoring rather than have the (nonexistent) hardware perform the monitoring. It's in the top right settings menu, under "monitoring." I had the same issue when I first tried using my laptop's Intel HDA chip. Anything sent to Ardour didn't come out the speakers until I enabled Ardour monitoring.

---

### Post by m3x1c0 on 2011-04-15
> **nightmorph said:**
> Set Ardour to perform (software) monitoring rather than have the (nonexistent) hardware perform the monitoring. It's in the top right settings menu, under "monitoring." I had the same issue when I first tried using my laptop's Intel HDA chip. Anything sent to Ardour didn't come out the speakers until I enabled Ardour monitoring.

tried that. still no dice. what is interesting is that jack monitoring cannot be clicked because it is shaded out. check out my connections:

[[img]http://farm6.static.flickr.com/5142/5622488637_4a37b6f2d2_z.jpg[/img]](http://www.flickr.com/photos/61715305@N05/5622488637/)
[Screenshot-2](http://www.flickr.com/photos/61715305@N05/5622488637/) by [xavcorral](http://www.flickr.com/people/61715305@N05/), on Flickr

When I connect the individual tracks on the left (such as solo guitar etc.)to system playbacks I do get sound which is encouraging but why doesnt the sound come from the master? please excuse me if I'm missing something here?:-k

---

### Post by Pablo_F on 2011-04-15
The tracks' output ports must be connected to the master bus. There is an option when you start ardour (advanced options). By default, all tracks connect automatically to the master bus. 

You can also use the mixer window in ardour to connect inputs and outputs of tracks and buses.

Cheers, Pablo

---

### Post by m3x1c0 on 2011-04-15
> **Pablo_F said:**
> The tracks' output ports must be connected to the master bus. There is an option when you start ardour (advanced options). By default, all tracks connect automatically to the master bus. 

You can also use the mixer window in ardour to connect inputs and outputs of tracks and buses.

Cheers, Pablo

Well thank you your solution using the mixer window worked heres what it looked up upon start up:


[[img]http://farm6.static.flickr.com/5028/5623392166_069b6483b8_b.jpg[/img]](http://www.flickr.com/photos/61715305@N05/5623392166/)
[Screenshot-4](http://www.flickr.com/photos/61715305@N05/5623392166/) by [xavcorral](http://www.flickr.com/people/61715305@N05/), on Flickr

as you can see on the bottom of each individual track above the comment button there is no assigned output and even though the tracks are playing, the master shows no activity. After clicking each individual track and assigning them to master out all is well! After saving the session everything is ready to rock right at start up! no more need to fiddle with Jack control hopefully. I will test the configuration with my interface later on and then tackle the xruns I'm getting. I checked the Autoconnect options (Options>Autoconnect) and the option to connect inputs to master bus was already checked but despite this I had the earlier issue. This is probably because I somehow messed with the configuration while trying to figure out Jackrack earlier and saving the session saved that configuration. Still, a newbie probably will not realize that these configuration changes override what Ardour is told to do automatically so I thought I would discuss it.

Thanks for the help fine sirs!

---

### Post by Pablo_F on 2011-04-16
Cool. 

Well, a new track will autoconnect to the master and I think ardour does the right thing remembering manually made connections and disconnections. 

OTOH, as you will have realised, when using ardour it does not make much sense using jack-rack, as ardour can load the same effects (ladspa plugins) and more (lv2 plugins, which jack-rack cannot load).

Cheers! Pablo

---

### Post by m3x1c0 on 2011-04-16
> **Pablo_F said:**
> Cool. 

Well, a new track will autoconnect to the master and I think ardour does the right thing remembering manually made connections and disconnections. 

OTOH, as you will have realised, when using ardour it does not make much sense using jack-rack, as ardour can load the same effects (ladspa plugins) and more (lv2 plugins, which jack-rack cannot load).

Cheers! Pablo

I totally agree that ardour is doing the right thing, I just thought I'd mention it as a noob such as I might not think about it. And yes Jack-rack was a monstrous headache until I figured out Ardour could do it so smoothly! I cant wait for the summer (as I will have a job, currently in university) to purchase Harrison DSP. this Is a wonderful program!

---

