---
title: "Any experts in recording and processing radar signals?"
date: 2009-06-21
forum: The Cafe
---

### Post by tashirosgt on 2009-06-21
I have a crackpot.... well, let's say "imaginative" idea for an open source project that I call "Passive Radar Detection At Home".  Are there any experts on recording and processing  radar data on the forum who could comment on it?   If so, I'll post it.  (If not, I shall maintain my mask of sanity.)

---

### Post by Pogeymanz on 2009-06-21
This sounds neat. I'm not an expert at all on the subject, but please don't be shy. It's sounds like a lot of fun.

I hope someone who knows about it comes soon!

---

### Post by richg on 2009-06-21
Buy a wideband spectrum analyzer. Look on ebay. 
Find antennas that will cover say 400 mmhz up to say X band or K band. Do a google search for those frequency bands. There are quite a few radar bands. You will need quite a lot of hardware.
I spent some years working at a NASA radar site using 420 mhz, S band, X band, Ku band radars. While in the Navy, I operated wideband spectrum analyzers looking for many kinds of RF signals. 
Be prepared to spend some money if you are serious about this issue and not just blowing smoke.

Rich

---

### Post by HermanAB on 2009-06-21
I don't want to discourage you since you could learn a lot by pursuing your idea, but this is definately a hard and expensive problem.

---

### Post by grappler on 2009-06-21
I'd like to encourage you not to be put off by the preceding two correspondents. For one thing, since you've talked about passive radar, you won't be working at any of the conventional radar frequencies - L, S, X, C, KA, ... In fact there's almost no energy at these frequencies. You'd want to be working in a standard broadcast range such as TV or cell phone though the latter would probably have too many low power transmissions to be useful.  


Given the speed and dynamic range of modern AD converters you'd be able to work mainly in the digital domain. You'll need to correlate the direct signal with the reflected one - some good directional antennas would come in useful. After that it's all digital processing.

Of course it depends what you want: detect and track close by airplanes? Not difficult. Find humans at a kilometer? Forget it!

---

### Post by tashirosgt on 2009-06-21
I suppose I'm forced to show my hand. I've discussed versions of the idea on other web forums.  Based on those experiences, this is a revised statement.

Passive Radar Detection At Home

                                 The objective of &#8220;Passive Radar Detection At Home&#8221; is to collect radar data and make archives of it available on the web. Web pages of the project would display the current data in a visual format. These maps would not be a &#8220;real time&#8221; maps. They would have a time lag similar to the lag in weather radar maps on the web. People who want to do detailed research could download the archives as numerical data and analyze or display it in other ways.
 

 This project is unrelated to the maps of airline traffic that are currently available on the web. Those maps are based on the FAA's "Aircraft Situation Display To Industry" (ASDI) data. As I understand that data, it is not based on radar detection, but rather on the transponders carried by the aircraft.
 

 The maps of "Passive Radar Detction At Home" would not necessarily identify airline flights by their number.  They might not even be able to identify individual targets by a symbol. They might look like weather radar maps. The numerical data underlying the maps would be available to the public for further processing. People might figure out various ways to recognize targets in the data or coordinate the data with ASDI data.
 

 What is the use of doing this? Data is always a neat thing to have!  Perhaps it could be used to investigate aircraft disappearances or accidents. On the other hand, I suppose some government agencies would argue that public access to such data would be a bad thing and try to censor it.
 

 The method of collecting radar data is suggested by the &#8220;SETI At Home&#8221; project and also by a paper on &#8220;Passive Radar Detection&#8221; on the website of the National UFO Reporting Center.  The data could be used to investigate UFO incidents.  I would welcome the participation of UFO investigators, but investigating UFOs is not the only goal of the project.
 

 &#8220;Passive Radar Detection&#8221; is a well known idea. In such a system, you don&#8217;t build any equipment to emit radar signals. Instead you use &#8220;public&#8221; sources of signals like commercial radio stations or radar transmitters belonging to other people. You put some antennas near the sources to get a reference signals. Ideally, you put other antennas in places where they only get these signals if they are reflected from aircraft. Or you may have receivers that filter out the direct signals. By doing computations that compare the reference and reflected signals, from several transmitters you can find aircraft locations.
 

 &#8220;SETI At Home&#8221; is socio-technical project. Signal data (received from space) is collected at a central location. The data is sent out over the web to people who volunteer the use of their computers. It is processed and the results are sent back to a centralized location.
 

 The idea that I call &#8220;Passive Radar Detection At Home&#8221; is a reverse-analogy to &#8220;SETI At Home&#8221;. Recruit volunteers all over the world to attach radar receivers to their PCs. They will collect the signal data and send it back to a central location. At the central location, the data is organized and stored. Some processing of the data is done to produce the current radar maps.
 

 Hopefully, a volunteer's radar receiver could be a simple device, not a big scanning dish. The PC would run software to transmit data about received signals over the web to the central location. It might also do other simple functions. For example, if the job of the volunteer site is to receive reflected signals, the software could decided when it was worthwhile to send information over the web vs when the site is only seeing empty sky.
 

 Data would include a time stamp since the central site can&#8217;t rely on getting the information instantaneously. This means that each volunteer site would need to have an accurate clock.  Let me emphasize that the central site is not trying to analyze the data within milliseconds of receiving it. Nor does data about a received signal have to be processed within milliseconds of the time the signal is emitted from a radar. A computer analyzing the data can look at the time stamps and see that a signal was emitted at a certain time and that another signal was received milliseconds afterward. A computer might be analyzing the data minutes or hours after the data was recorded.  Furthermore the data doesn't have to collected every second of the day.  It could consist of "snapshots" of the sky. Perhaps a second or two of data could be recorded every few minutes.
 

 Since this is a socio-technological idea, some the &#8220;socio&#8221; aspects are interesting to discuss. However, at the moment, I&#8217;m mainly interested in whether the technological side is feasible.
 

 I suspect that radar specialists will take a dim view of it. The business of having dispersed receivers that may turn off or on, each one possibly having different specs - it just sounds like bad design.  It might be more interesting to mathematicians and computer scientists who like the challenges of noisy data.
 

 I request that people who provide technical objections to the feasibility of this project make clear whether their objections are to "Passive Radar Detection" in general, or to the particular case of "Passive Radar Detection At Home".

---

### Post by grappler on 2009-06-22
Just one slight issue with the previous post - radar engineers are always interested in noisy data since the challenge for them in many circumstances is to extract very small signals reflected from small distant targets. Receiver noise is a significant problem in this situation. And then there's clutter ...

In this context the challenges are that you have no control over the illuminator and that you do not want to spend lots of money on the receiver but  on the other hand you don't require high performance.

---

### Post by geekygirl on 2009-06-22
Is it just me, but why do I think of the movie 'The Philidelphia Experiement'?

lol

---

### Post by HavocXphere on 2009-06-22
Interesting project idea.:biggrin: I'm not entirely convinced that it is feasible though.:-|

I'll have a go at thinking it through...

Standard radar measure the time between sending the signal and receiving an echo thereby working out the distance. And the direction in which the spinning radar setup is pointing gives direction.

You don't have this time difference since you can't know when the active radar is sending out a pulse. You could work this out by using a directional antennae as suggested above or by timing it (assuming constant pulses). Either way it would have to be *very* accurately timed. However this does not "fix" the problem. In this setup, the original pulse and the echo you receive travel different distance, so the exact time split between original path and reflection's path is not know.

You don't need that split *if* you know the exact direction that the reflection is coming from. With active radar this is easy - its wherever the radar is currently pointing.

You can't really use a spinning radar setup because you might miss an echo, i.e. you'd have to monitor all/many directions simultaneous. I've got no idea how one would do that :confused:...but I'd imagine it would cost big bucks.

---

### Post by tashirosgt on 2009-06-22
The data would be time stamped.  If you have a receiver at a known location monitoring the transmitter you could compute when the transmitter emitted a pulse.  A computer analyzing the data could compare emitted and received signals to get range data since it would know the times  - (I know, it wouldn't be a simple as that phrase makes it sound.)

Since my background is in mathematics and programming, I tend not to be bothered about the problems of analyzing the data.  What worries me is that you could not record and transmit the data ( since that is outside my expertise).  

I don't know what part of a radar signal contains the actual information.  For example, suppose you have a 2 GHz signal.  What would you need to record about the emitted and received signal besides the time?  Is the signal modulated?  Would you only need to record data that could reconstruct the shape of the "envelope" of the wave?  Or must you record the details of the wave down to the shape of each cycle of a 2 GHz signal?  

(i.e. Imagine active radar based on DSP instead of analog signals.  How would it digitize its data? ) 

I agree that the normal kind of Passive Radar Detection doesn't use directional information. Yes, the remark about the "scanning dish" is unnecessary.   Whatever "standard" home receiver is proposed for "Passive Radar Detection At Home",  electronics hobbyists would come up with all sorts of enhancements and modifications to it.  The programmers for the central analysis site would be kept busy accommodating new formats of data.

---

