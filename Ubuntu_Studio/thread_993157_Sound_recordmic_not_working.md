---
title: "Sound record/mic not working"
date: 2008-11-25
forum: Ubuntu Studio
---

### Post by abhinav90 on 2008-11-25
Hi 
i am on Hardy using a dell latitude laptop, my sound is working fine

USING INTEL HDA SOUND CARD
even my analog loopback is working so when i connect my electric guitar or mic to my laptop i can hear the sound from the speakers, but when i try and record anything using sound recorder or audacity or ardour it doesnt work. audacity keeps saying that your sound input device is not properly adjusted.

Pls Help!

---

### Post by superoptimo on 2008-11-25
Hi. Until this morning I finally discovered how to get running my Intel HDA sound card with Audacity. 

I also was very angry with linux programmers for this little audio problem, for designing these audio applications very badly. But then  I could make Jack working fine and now I'm very happy with my linux box again :)

I've just found the clue for configuring jack from this guy ([http://ubuntuforums.org/showpost.php?p=6249431&postcount=9](http://ubuntuforums.org/showpost.php?p=6249431&postcount=9)). Thanks

So here are the steps for recording audio with JACK on a HDA INTEL SOUND CARD:

At first, you have to install JACK and QJackCTL, from Synaptics or from command line:
```
sudo apt-get install qjackctl
```

Start the Jack Connection control:
[IMG]http://farm4.static.flickr.com/3206/3059834838_8938f204b5.jpg?v=0[/IMG]

Then go to setup and set the parametes as shown on this picture:
[IMG]http://farm4.static.flickr.com/3161/3059019241_8e089120ce.jpg?v=0[/IMG]

Take a carefully look about the latency parameters. Set the number of periods per Buffer to 3, and frames per period to above of 128. Also disable the realtime checkbox. That is the unique configuration that works on the majority of computers and laptops, specially Dell.

It would be nice that the JACK guys publish a comprensible tutorial for setting the parameters for the most common hardware profiles, specially for on-board audio devices. Most tutorials are only configured for high-end audio boards like Creative Labs or sound blaster, but not for the common user.

At last set the Audacity preferences on the IO audio configuration for using the Jack sound server.

---

### Post by picturefreedom on 2008-11-25
thanks, i will try this, i also have an intel sound card.

---

### Post by AbdRahim on 2009-07-09
Audacity has no Jack choice.

---

