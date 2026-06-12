---
title: "Help with fast digital accelerometers &amp; more"
date: 2013-01-19
forum: The Cafe
---

### Post by flyingsliverfin on 2013-01-19
Hi all!
Last year I did a project in which I used piezoelectric sensors to measure vibrations. I shifted the signal into the positive range with an op-amp and converted to digital with an ADC. With this setup i could read a 12-bit data word from the ADC in about 12 microseconds (The signal changes from reading 100 to 300 in 80 microseconds, so its a decent speed for the application)
 This year, I'm planning on making an evolution of the project, but didnt want to mess with all the electronics and instead focus on the programming, which means opting for a digital accelerometer [preferably]. However, I can't seem to find any that can output data more than 6 KHz (which comes out to one data every 167 microseconds - more than a factor of 10 larger). 
 Is my best bet going back to the old piezoelectric sensors, looking longer for a sufficiently fast digital accelerometer, or getting an analog accelerometer and ADC'ing that? I'm mostly looking to avoid the op-amp because it doesn't make sense to me and somehow changed the signal last time (didnt affect results but still bugged me). 
extra info: Another downside of the piezoelectric sensor was that it picked up lots of interference even with coax as i ran it to the ADC breadboard

thanks!

---

### Post by flyingsliverfin on 2013-01-19
I was just talking with my father and I suppose i have a fundamental misunderstanding of 'bandwidth'. I had assumed bandwidth of digital sensors was equal to the maximum output data rate. Really, for these sensors it is the fastest (sine) wave that can accurately be measured, correct?
I'm left wondering what the point of having a digital sensor with a 1KHz bandwidth that has a maximum data output rate of 800/second? (I think i came across one like this in the multitudes i read up on today ;))

---

