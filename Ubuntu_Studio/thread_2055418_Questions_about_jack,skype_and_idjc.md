---
title: "Questions about jack,skype and idjc"
date: 2012-09-09
forum: Ubuntu Studio
---

### Post by fractalman on 2012-09-09
I am trying to get skype audio to stream through idjc in ubuntu studio 12:04,  i have been googling and reading guides for the last 5 days and absolutely nothing is working

i deleted pulse audio so skype wouldn't default to it everytime i open it

 i have followed the guide on the idjc homepage but it's not working.
 i added myself to the audio group
 i made a file called .asoundrc and placed it in the home folder  but when i load skype i    cannot see the option for idjcvoip     
--------------------------------


i have added the jack-alsa-bridge package,

[http://www.penguinproducer.com/2011/11/jack-alsa-bridge-kit/](http://www.penguinproducer.com/2011/11/jack-alsa-bridge-kit/)

i have placed the .asoundrc file in my home dir and i can see the plug ins in skype but i cannot see skype in jack and everytime i try a test call it just says 'playback problem'  and i cannot get any audio through them

the package includes 4 files called jackloop.sh 1-4  
where am i supposed to put these file?  
do they go in the home directory, an alsa directory or a jack directory, which one? 

 i have set the permissions to executable

-------------------------------------------------------


 i am also missing jack plug in support  when i run   find /usr/lib/alsa-lib | grep jack  i get nothing back  but when i try and compile from source or binary it won't let me and says i am missing a package called alsa, i can't find 'alsa' in synaptic

-----------------------------------------

so far i have not been able to get skype directly into idjc so i thought i'd see if i could achieve it as described in this link

[http://www.penguinproducer.com/2012/01/streaming-podcast-with-skype-workflow/](http://www.penguinproducer.com/2012/01/streaming-podcast-with-skype-workflow/)

 it's a bit longwinded and i could probably miss a few steps out  but i'm getting all sorts of problems doing it this way as well

in the guide he says there is a 'custom' option in claudia, i cannot see this option, i have klaudia installed from medibuntu repositories

-------------------------

i tried this simple guide to get used to jack

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

in jack conections audio tab, all i have is system,  when i connect the keyboard to zynaddsubfx  i can see the signal is making it to zynaddsubfx  but there is no sound coming out of my speakers
------------------------------

i apologise for so many issues in one post but i didn't want to start loads of threads,

i'm running ubuntustudio 12:04 on 2.5g ram 3200hz 32 bit with an amd64 athlon chip using the motherboard audio

```

0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe028000 irq 23
phi@BLACK47B:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
phi@BLACK47B:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```any help would be much appreciated

---

### Post by fractalman on 2012-09-09
ok this is how i have jack configured - see attachment.


When i open a programme i have audio and can hear stuff fine but as soon as the jack server starts i have no sound,

i can no longer start a jack server from the terminal using jack -d alsa 

i cannot get skype to show up in gladdish

mixx will not play nicely with gladdish, as soon as i try and add it to my room it just crashes mixx immediately and constantly says inactive

gladdish is refusing to save any of my studio set ups and connections, it still saves my projects but in the studio everything remains disconnected on loading

i have also added the ubuntu-extras-audio package and disabled pulse and stopped it respawning

any ideas?

---

### Post by fractalman on 2012-09-10
I have tried downloading a new copy of studio and trying a fresh install but nothing has changed.  i still have no sound through jack, when i try starting jack from a terminal using jack -d alsa then i get told i am missing the package 'jack'.  on installing the package 'jack'  i am told the ogg module is missing,  not only is the module missing but my window manager has now decided to stop functioning, it might have even un-installed itself i don't know and i can't be bothered to find out,  i really have had enough of this now.  i want something that just works, no messing about in the system, no days on end looking online for solutions and help, i want to start an app and it works, obviously i am not going to get this with linux, 

 from all the posts online it seems jack is too hit and miss too take seriously, what i don't understand is how such an unreliable package has been deamed acceptable for the repo's?  sure... some people have had great success with jack , but there is very little documentation aimed at the novice computer user, some of us don't have computer science degrees,  nor do we actually want them,  we want to be able to switch our pc on just have the thing damn well work with no issues. 

 it's a shame linux hasn't sorted this issue out by now, as someone posted in another thread, windows and apple got it right nearly ten years ago!! 

  i really wanted to use linux for the audio stuff but i think i am probably going to have to use windows now.   i really love the fact linux has more power, is more efficient and a lot more secure but i don't want to have be spending all day under the bonnet trying to get it to work, it's just glitch after glitch after glitch.  nor do i want to be installing a new copy every 6 months. or even 2 years for lts for that matter.  why not make it 5 years for lts and stop all the 6 month public releases, have a seperate site for anyone who wants to test and play about if people want it they will go and get it    

i have a copy of 11:04 that works without any issues as a normal o/s but everything since has gotten more and more problematic,  the ubuntu team have spent too much time trying to make it look nice at the expense of reliability 

apologies for the rant but i'm seriously disapointed and even more so at the thought of having to re-install windows!

---

### Post by jejeman on 2012-09-10
First, Skype is not JACK aware application. So, one can not really expect it to work with JACK.

Try to increase the frames 2.677 latency is preety low. I use 5ms, thats with 128 frames.

---

### Post by fractalman on 2012-09-10
Thanks, i know Skype is not jack aware, hence the jack-alsa bridges and the asoundcr file.  it's not just skype that isn't playing audio through jack, it's everything, i have sat here and tried plenty of combinations that don't include skype and none of them produce any sound when the jack server is active,

---

