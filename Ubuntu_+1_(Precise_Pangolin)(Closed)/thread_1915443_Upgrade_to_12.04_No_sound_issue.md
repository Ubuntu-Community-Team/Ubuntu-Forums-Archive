---
title: "Upgrade to 12.04 No sound issue"
date: 2012-01-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by onilink422 on 2012-01-26
for all of us people testing the latest Alpha release of Ubuntu  12.04, most of us have been having a problem with no Audio. I have found  a temporary or permanent fix that I would like to share in order to  provide incentive for Alpha testers to keep Ubuntu 12.04. :)
 Follow these instructions..
 open a Terminal and do:
 'sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload'
And your problem should be fixed for now! Continue testing ubuntu 12.04 to make our Devs happy and look for other problems. :popcorn:

---

### Post by nothingspecial on 2012-01-26
Moved to Ubuntu +1

---

### Post by ScislaC on 2012-01-26
Didn't fix it here for me...

---

### Post by onilink422 on 2012-01-26
After you do this, go to your volume slider in the top panel and select sound preferences, and for hardware your sound card should now be supported. Also, I apologize for the wrong section post.
[Edit]
Restart might be required?
Also, try this apt-get gnome-alsamixer Tell me if you have any luck, I was able to get it working so you should as well.

---

### Post by ScislaC on 2012-01-26
Didn't fix... HOWEVER, using gnome-alsamixer uncovered that my sound is going through "bass speaker" rather than "speaker", so as long as I have that app open I can adjust volume and have sound. I'm curious if I can remap bass speaker to speaker.

---

### Post by onilink422 on 2012-01-27
Oh good, I am glad you got it working, maybe with some fiddling you can work around it.. Maybe something like you said. Remap bass speaker to speaker. Shouldn't be to hard with the Terminal. 
You could try :
sudo speaker-test  -c6 -l1 -twav
and you should hear noise in the Left and right Channels. 
Luckily Pulse Audio supports remapping, so you don't have to do anything elaborate.

---

### Post by Davide89 on 2012-01-28
It works!:D

---

### Post by A_T on 2012-01-28
I tried the OP's method but no change. Then I looked in pavucontrol and my output device was set to analogue headphones. Changed to analogue speakers and all was well.

---

### Post by makitso on 2012-01-28
This borked my virtualbox 12.04 install.  Just cycles between load window and full screen, never gets to login.

---

### Post by lidex on 2012-01-29
Probably shouldn't have to mess with alsa. What worked for me:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio indicator-sound
```
**Reboot.**

---

### Post by ScislaC on 2012-01-29
Still the same... interestingly pavucontrol doesn't show my regular soundcard and only shows the HDMI device. Still, gnomealsamixer's bass speaker slider gives me sound (no luck in remapping yet).

---

### Post by nevar1 on 2012-01-31
This worked for me until I rebooted... any idea how I can make it permanent?

---

### Post by nevar1 on 2012-01-31
This worked for me until I rebooted.. how can I make this permanent?

---

### Post by Actieman on 2012-02-02
Thanks, great! It did work for me!

I'm always a little bit cautious in upgrading to a new version of Ubuntu .. but I just can't help myself! Every problem can be solved so GO for it .. problem evolved and problem solved!

Thanks again!

---

### Post by superflymonkeyboy on 2012-02-10
The only thing that seems to be working is ```
sudo alsa force-reload
``` in terminal. This is only temporary though and I have to do this every time I switch on - as others above have also noticed. Anyone know of a permanent solution yet?
Cheers.

---

### Post by dino99 on 2012-02-10
The first place to go is: System Settings Sound , and check that your sound hardware is first recognized, then with the good settings. If its not the case, then check:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by prusswan on 2012-02-10
```

sudo alsa force-reload

``` works for me

but at the same time I expect this to be a trivial fix that should be applied ASAP

---

### Post by balloons on 2012-02-10
You guys may be happy to hear about some alsa stack updates that are getting ready to go into precise.. If you wish, check out the details here:

[http://www.theorangenotebook.com/2012/02/call-for-testing-alsa-1025.html](http://www.theorangenotebook.com/2012/02/call-for-testing-alsa-1025.html)

They are in the ubuntu audio dev ppa.

---

### Post by lidex on 2012-02-13
I had forgotten to add the part about removing your pulse config files:
```
rm -r ~/.pulse ~/.pulse-cookie 
```

---

### Post by prusswan on 2012-04-05
Just a heads-up for those still facing this issue, in my case I have discovered that it may have to do with pulseaudio not being able to access the audio hardware on startup for some unknown reason (This was a symptom for a few other pulseaudio related bugs).

If that applies to your case as well (sudo killall pulseaudio), confirm my report at [https://bugs.launchpad.net/bugs/933209](https://bugs.launchpad.net/bugs/933209)

---

### Post by DrSkylaser on 2012-04-18
> **onilink422 said:**
> for all of us people testing the latest Alpha release of Ubuntu  12.04, most of us have been having a problem with no Audio. I have found  a temporary or permanent fix that I would like to share in order to  provide incentive for Alpha testers to keep Ubuntu 12.04. :)
 Follow these instructions..
 open a Terminal and do:
 'sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload'
And your problem should be fixed for now! Continue testing ubuntu 12.04 to make our Devs happy and look for other problems. :popcorn:

This works for me, but the fix breaks awfully easily--even refreshing a webpage with video is enough to kill it.  Is there a more permanent fix?

---

### Post by ForrestBrandt on 2012-04-19
Hey all,
Been having this persistent problem where sound plays ok from my headphones but not from my onboard speakers.   
I've searched around on the web and tried various things but to no avail. 
I Even updated to 12.04 but it didn't solve the issue either.  

Here is the link from my output from SOUNDTROUBLESHOOTING ([https://help.ubuntu.com/community/So...otingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")) step 4:

[http://www.alsa-project.org/db/?f=71...a899237548e6f1]("http://www.alsa-project.org/db/?f=71a089123d2be85724a5dc78cda899237548e6f1")

---

### Post by cmccauley on 2012-04-20
> **DrSkylaser said:**
> This works for me, but the fix breaks awfully easily--even refreshing a webpage with video is enough to kill it.  Is there a more permanent fix?

I don't have a more permanent fix but I've found that ctrl-alt-f6 then ctrl-alt-f7 'fixes' it for me - sometimes needs a few attempts. Breaks eventually again.

---

### Post by rob22941 on 2012-04-22
sudo killall pulse audio worked for me, much thanks.

---

