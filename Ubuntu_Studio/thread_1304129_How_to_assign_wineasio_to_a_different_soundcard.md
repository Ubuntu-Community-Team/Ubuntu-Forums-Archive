---
title: "How to assign wineasio to a different soundcard?"
date: 2009-10-29
forum: Ubuntu Studio
---

### Post by lavadisco on 2009-10-29
I installed wineasio, opened my pro audio program (Reaper via WINE) for the first time, and it worked with my laptop's onboard soundcard with no other tweaking! No winecfg or JACK Control or anything. Great! However...

I want wineasio to recognize my Edirol UA-25 USB audio interface instead. How do I do that?

---

### Post by AutoStatic on 2009-10-29
Then you have to set your UA-25 (great device BTW ;)) as the default in gnome-sound-properties (Sound Properties).

---

### Post by lavadisco on 2009-10-29
I did that, it didn't work.

---

### Post by AutoStatic on 2009-10-29
Sorry, I must've been low on cafeine ;)
You need to set up JACK for your UA-25 (I can provide some settings if you want to) and hook up wineasio through JACK. At least, that's what I recall the last time I used Guitar Rig.

---

### Post by lavadisco on 2009-10-29
Thanks, I'd be very grateful if you'd do that. Been reading up on Jack, but there is so much out there that it is a bit confusing. 

Do you find it odd that Reaper and wineasio worked with my onboard soundcard with no tweaking of Jack in the first place? How did that happen?

---

### Post by sgx on 2009-10-29
> **lavadisco said:**
> Thanks, I'd be very grateful if you'd do that. Been reading up on Jack, but there is so much out there that it is a bit confusing. 

Do you find it odd that Reaper and wineasio worked with my onboard soundcard with no tweaking of Jack in the first place? How did that happen?
Reaper opens using the wdm audio device by default, so it should work, but not likely at the low latencies provided by asio. 
Install qjackctl, and click everything, taking notes, and google for anything that is new or strange to you. Lots of hits/info out there!
Cheers.

---

### Post by AutoStatic on 2009-10-30
Check the attachment for the settings I'm using in Qjackctl for the UA-25. The only thing that might differ from your setup is the Interface address. If you click on the > you should have the option to select the UA-25.

---

### Post by lavadisco on 2009-10-30
> **AutoStatic said:**
> Check the attachment for the settings I'm using in Qjackctl for the UA-25. The only thing that might differ from your setup is the Interface address. If you click on the > you should have the option to select the UA-25.

Thanks! It worked. I did have errors with Jack at first, but once I added my login to the audio group with realtime permissions, everything was cool. 

One issue - I am not getting nearly as low of latency with this setup that I used to get on my Windows XP system. Will I get better performance if I switch to the realtime kernel? If I can get to 6ms, I'll be happy.

---

### Post by sgx on 2009-10-31
> **lavadisco said:**
> Thanks! It worked. I did have errors with Jack at first, but once I added my login to the audio group with realtime permissions, everything was cool. 

One issue - I am not getting nearly as low of latency with this setup that I used to get on my Windows XP system. Will I get better performance if I switch to the realtime kernel? If I can get to 6ms, I'll be happy.
The numbers are not important, and won't match equally on a different OS, so if you can't hear/feel latency, any numeric label it has is meaningless. :) But larger multi-track or heavily layered productions may need the benefits of the realtime setup. Cheers

---

### Post by AutoStatic on 2009-10-31
> **lavadisco said:**
> Thanks! It worked. I did have errors with Jack at first, but once I added my login to the audio group with realtime permissions, everything was cool. 

One issue - I am not getting nearly as low of latency with this setup that I used to get on my Windows XP system. Will I get better performance if I switch to the realtime kernel? If I can get to 6ms, I'll be happy.Good to hear that it works! A RT kernel will help lowering latency but 4ms is the lowest I can get. Very workable though.

---

### Post by lavadisco on 2009-10-31
Thanks guys. To record electric guitars well, I feel that I need 6ms latency or better. Sounds weird/late to me otherwise.

---

### Post by AutoStatic on 2009-11-01
> **lavadisco said:**
> Thanks guys. To record electric guitars well, I feel that I need 6ms latency or better. Sounds weird/late to me otherwise.Then you'll definitely need a real-time kernel, especially when you want to use any real-time effects.

---

### Post by eightdollarbeer on 2009-12-19
> **lavadisco said:**
> Thanks guys. To record electric guitars well, I feel that I need 6ms latency or better. Sounds weird/late to me otherwise.



/etc/security/limits.conf 
----add----
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

add yourself to the audio group

---

