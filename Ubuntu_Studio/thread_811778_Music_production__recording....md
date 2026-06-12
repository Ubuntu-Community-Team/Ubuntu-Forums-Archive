---
title: "Music production / recording..."
date: 2008-05-29
forum: Ubuntu Studio
---

### Post by Shugs81 on 2008-05-29
reet.... still a bit green around the gills so to speak... Just upgraded to Ubuntu Studio... not had a proper play with anything yet... Just wondering... is there any way to have a Line 6 X3 Live to interface with jack or whatever? I'm plnanning to buy a firewire card but am planning to use the laptop to record live gigs so it's gonna be a biggie.... hopefully not rackmount but see waht's permitting...

anyhow... back to the line 6 issue....

Not bothered about Monkey or gear box... just wondering if there's a way to plug it in USB and record that way?:guitar:

any help much appreciated... if i ever meet y'all i'd get a round in....:lolflag:

---

### Post by robeast on 2008-05-29
Plug it in and see what happens (if you already have one). I haven't read anything about it working or not.

---

### Post by Shugs81 on 2008-05-29
will have alook tomorrow... didn't get chance tonight.... was just wondering cause it classes itself as an asio soundcard.... like i say the aim is to be able to hook the laptop up to record gigs... just hoping i can find a decent firewire card that covers all of the  channels i need...

have seen things stating that jack supports asio with a -a argument but will find out tomorrow...

---

### Post by warbread on 2008-05-30
Taking a quite Google around the web, I can't find any posts either way about it.  In my mind, this is a good thing, as if there were problems, someone would be on some forum complaining.  I'm putting all my chips on "it'll work".  Let us know here so we'll have something for people to search for.


400th post!

---

### Post by joegiampaoli on 2008-05-30
Firewire is still choppy, I use a boss GT8 it doesn't have usb but it does have a digital line out, but I still go raw stereo outputs to line in in soundblaster and to tell you the truth quality is pretty good.

---

### Post by Shugs81 on 2008-05-30
lookin at getting the Edirol FA-66 pretty good bang for the bucks and also has spdif in/out as well as the std line in / xlr connections... and i may have talked the mrs into getting one!!! bonus!!!

planning to effectivly do line recording but need some kind on interface for the laptop so it'll work... will try to get something done tonight... even if it's to the mic in on the laptop... was hoping to just use the pedal cause i'm getting a new amp delivered on monday and was gonna use it to test it.... but we shall see what kind of jury rigging i can get sorted gonna have a look through the ardour forums about USB soudcards... may be able to manage something that way.... latency isn't really gonna be an issue for the recording as i'll probs add the effects on afterwards altho if i could get it working it records a clean line and an effects line... oh decisions decisions.....

---

### Post by joegiampaoli on 2008-05-30
If you have line in it will be best but  if mic is the only option for now just disable the mic boost switch when recording because that's a high impedance interface and can get really noisy, also use low out levels in your fx pedalboard, that thing is a PA, and if it has a mode where you can tell it you are connecting to a line in it will be best, that way amp/cab simulation will be enabled and you can mix the stereo outputs with a special cable that has two rca to a 3.5 mm, just get to 1/4" adaptors to place them int the rca side so you can plug them into your pedalboard. The rest will just depend on equing everything nicely to eliminate any type of hiss.

Anyway  usb or firewire will someday work well under linux for audio. Running real time kernel will always be a plus for this, or configuring your /etc/security/limits.conf to enable realtime jack will also be a big help, you dont want xruns during recording.

Good luck!

---

### Post by Shugs81 on 2008-05-30
this is apparently something peeps are working on!!!!

looks like support for older models but not this newest one yet....

may help someone... also links to a site about how to write alsa drivers!!

[https://sourceforge.net/forum/?group_id=200399](https://sourceforge.net/forum/?group_id=200399)

---

### Post by robeast on 2008-05-30
Many firewire and usb interfaces work very well with linux thanks to the efforts of the ALSA project and FreeBoB/FFADO. The Edirol FA-66 is one of them, so if it looks like it has what you need for the price you want then you can buy it with confidence.

---

### Post by Shugs81 on 2008-06-01
Looks like the line 6 ain't a viable option as a stand alone.... unless there's some way to interrogate the usb via ardour or jack....

need to look into stuff a bit more... still tempted with the eridol.... can't really afford it haveing just bought a new guitar, amp, 2 sets of bass strings, laptop, rebuilt 2 computers and a playstation 3 all in the last 3 months (totalling around £2500!!!) think i need to wait at least a week or so.... :p ... if the eridol is definatly compatible then it'll be on my shopping list!!

think it may help to learn how ardour & jack work!!!

---

### Post by joegiampaoli on 2008-06-01
I say yes, first learn JACK and Ardour and get what you need as you go along, that's what I'm doing, necessities will pop up as you go along, and then that's when you can decide to purchase what you might need.

---

### Post by Shugs81 on 2008-06-01
FFADO!!!!!!! Just realised.... I was using the website as a guide before but couldn't find it again!! woot!! 

While i remember.... which is the most reliable way to record through an external soundcard? firewire or USB? I know in windows usb has a tendency to drop now and then and firewire was a million times better... is it the same via linux?

---

