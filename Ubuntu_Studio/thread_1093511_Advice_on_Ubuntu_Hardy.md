---
title: "Advice on Ubuntu Hardy"
date: 2009-03-11
forum: Ubuntu Studio
---

### Post by djadamn on 2009-03-11
Hi im new to linux and Ubuntu studio. I currently on windows vista using Ableton Live 7 and Reason 4 with maudio oxygen 8 midi controller and maudio fasttrack pro sound card. I also want to start migrating to Ubuntu Studio, to learn Ardour. My question is will my sound card and midi controller work with linux? And does anyone know if I can still run Ableton and Reason if I had Ubuntu as my main OS and then ran windows on VMware?

---

### Post by thorgal on 2009-03-11
try a linux live CD to see if your h/w is supported (knoppix for example or maybe there's a Ubuntu studio live CD ??). I suspect it will (ALSA has a kernel module for USB interfaces - snd-usb-audio, if you fast track pro is USB class compliant, it should be supported).

Now, about the virtual machine, you have to realize that if you install MS windows in your linux host, VMware or virtual box will emulate a sound card (I know vbox emulate a sound blaster or Intel ICH audio). The purpose of the VM is not to drive your real h/w. Sure the apps you mention will install and run but not in connection with your h/w. The VM is all about virtuality (CPU and RAM). 

I toyed around with virtual box. It can output to pulseaudio. Pulseaudio can run concurrently with the jack audio server (needed for ardour). It worked reasonably well on a beefy machine (lots of RAM and CPU) on the output side of things (e.g. mp3 playback from VM to pulseaudio to jack). Performance-wise, it sucks (high latency, high power usage). Now, on the input side of things, if you feed the VM with some audio, process it through windows apps, and output it back to the linux host (pulseaudio and jack), you'll get the worst audio experience ever :lol:

---

### Post by Reeman on 2009-03-13
If the 64 studio (live) no install lets jack connect the usb sound devices you are in business. There is no driver from M-audio ..however this does not mean that it will not work. If jack sees the external ports through usb or firewire then you should be able to use Ardour and route your sources accordingly. Rosegarden will do the same thing if you enable jack when you load Rosegarden.... that way external midi should come to life. Unfortunately Ardour is not midi capable yet ...coming in version3 though.

As far as Ardour goes it is the most (gui centered) advanced multitrack audio recording software available in the linux world. However if you want to take the plunge and learn lots of command line stuff Ecasound is much more advanced than most people who only use visual guis realize. It can do much more than any of the Xgui based audio software available and the beauty is that you can write quick and dirty simple scrips to do repetitive tasks!(quite a few are already written) There is also the possibility of running simultaneous sessions doing different things at the same time....something that Xgui based stuff has extreme difficulty doing. If jack can connect to your usb devices then [[COLOR="RoyalBlue"]Ecasound[/COLOR]]("http://ecasound.seul.org/ecasound/") is a much more comprehensive and useful tool. It has been under development since 1999!  

When I want to do multitrack audio recording at high bit rates I do not even fire up an X session and have not for years. The reason for this is that the majority of X sessions like the ones used by Ubuntu etc...also clutter up the sound drivers with all sorts of unnecessary deamons and stupid sound servers that put locks on devices. 

Good old terminal based guis can do more than is necessary for simple audio tasks, and have the added bonus of not getting in the way of audio tasks!

---

### Post by propagation_of_sound on 2009-03-16
Have a look at this:

[http://www.kvraudio.com/forum/viewtopic.php?t=190021&view=previous](http://www.kvraudio.com/forum/viewtopic.php?t=190021&view=previous)

Also, there is no Ubuntu Studio Live CD, so you'll have to install with the alternate install DVD. 

You could, if you just want to install Ardour install normal ubuntu and then download Ardour or ubuntustudio-desktop which will download everything to make it into an ubuntu studio configuration. This is exactly the same, as Ubuntu Studio 8.10 doesn't have a realtime kernel, and if you want to use Ardour, I would stick with **8.04 Hardy** and use that until 8.10 has a realtime kernel which improves audio latency etc.

---

### Post by markbuntu on 2009-03-18
I don't think that 8.10 will ever get a rt kernel. Jaunty just went to a 2.6.28-2-rt kernel that does not work ( at least for me) and dropped the 2.6.27-3-rt kernel that did not work so I think it may be abandoned. 

Hopefully they can get the new rt kernel working in a reasonable amount of time. Anyway, for the time being 8.04 is your best bet for an rt kernel in Ubuntu which is really critical for recording and live work etc. Besides that, 8.04 has become very stable as all the bugs have been worked out.

---

### Post by Stochastic on 2009-03-18
> **markbuntu said:**
> I don't think that 8.10 will ever get a rt kernel. Jaunty just went to a 2.6.28-2-rt kernel that does not work ( at least for me) and dropped the 2.6.27-3-rt kernel that did not work so I think it may be abandoned.

Markbuntu, that rt kernel is still in development.  I have been partially successful running Jaunty-rt.  On, that note 2.6.29 is supposed to be in highly-active rt development, so the future does look good for the rt kernels.

---

### Post by thorgal on 2009-03-19
I am experimenting with 2.6.29-rc6-rt3 on my debian sid DAW. It works really good with the latest jack1_svn (the version that has the newly introduced sanity checks.

---

### Post by markbuntu on 2009-03-19
> **Stochastic said:**
> Markbuntu, that rt kernel is still in development.  I have been partially successful running Jaunty-rt.  On, that note 2.6.29 is supposed to be in highly-active rt development, so the future does look good for the rt kernels.

Well yes, I know the rt kernel is being actively developed. I just do not expect to see a working one in Intrepid since I doubt Intrepid will ever get a 2.6.29 kernel.

I would suspect that 2.6.29 will not be seen in Ubuntu until 9.10.

---

### Post by Stochastic on 2009-03-19
rt kernel state: hardy - works
jaunty - works for some, not for others, still in development
karmic - 'prolly gonna see 2.6.29 land and stick for the LTS (crosses fingers)
intrepid - is dead to us (us as in audio users)

Okay enough kernel development talk in a 'Advice on Ubuntu Hardy' thread (I know my hand's in the cookie jar too while I'm trying to close the lid).

---

### Post by djadamn on 2009-03-31
Thanks for advice. I will look into that stuff

---

