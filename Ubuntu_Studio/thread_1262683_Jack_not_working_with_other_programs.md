---
title: "Jack not working with other programs"
date: 2009-09-10
forum: Ubuntu Studio
---

### Post by g-raf on 2009-09-10
Which basically means that Jack isn't working at all.

I'm using ALSA (got rid of PulseAudio), Ubuntu Studio with the realtime kernel and running Jack in realtime. I'm using a USB soundcard (m-audio fast track pro). ALSA works perfectly with the soundcard - i'm listening to music on speakers thru the soundcard. 

However, other audio production programs that normally use Jack (Audacity, Hydrogen, ZynAddSubFX, Audacious) are not recognizing Jack as a host or I/O preference and Jack also doesn't recognize these programs in the control panel. 

I've had this problem for more than a week now and spending a lot of time trying to fix it. I'm suprised not to find others with the same problem online. If anyone has some ideas, please let me know. I'll give any info about my system and how it's set up. I've been getting the feeling that there is something that Jack needs but it doesn't have. Here are some screenshot links: 

[http://blog.jinbo.net/files2/72/giraffe/images/200909/100537155.png](http://blog.jinbo.net/files2/72/giraffe/images/200909/100537155.png)
[http://blog.jinbo.net/files2/72/giraffe/images/200909/100539145.png](http://blog.jinbo.net/files2/72/giraffe/images/200909/100539145.png)

I'm supposed to do a radio show tomorrow using Jack and Audacity, so now I'm in an emergency situation about trying to fix this.

---

### Post by kayosiii on 2009-09-10
This error most commonly applies when you have more than one version of jack installed....

---

### Post by g-raf on 2009-09-10
Ok, i just realized that in the Jack control panel, alsa_pcm is not on the "writable clients/input ports" section. That's probably the main problem here. I'm going to continue browsing the internet for the information i need, but if anyone has an idea, please let me know and it will surely save me time.

---

### Post by g-raf on 2009-09-10
> **kayosiii said:**
> This error most commonly applies when you have more than one version of jack installed....

How can i uninstall and reinstall a fresh Jack? I'm not very good at this stuff. Thanks for this help.

---

### Post by g-raf on 2009-09-10
I've just reinstalled Jack, ubuntustudio-audio, almost all the audio programs through synaptic and Jack's still not working. I've been trying to fix this problem for over a week now, but I'm almost considering moving to windows because i'm basically in a coma.

---

### Post by g-raf on 2009-09-10
Please help, i'm a newbie. I can give any info about my system. But i have no idea why Jack isn't working and it's a crisis for me.

---

### Post by variona on 2009-09-10
Sorry if I ask, did you start jackd before Audacity?

---

### Post by g-raf on 2009-09-10
Yes i start jackd before audacity. The problem is much more difficult and i'm stumped and desperate at this point. I'm not sure what i should change or how i should change it.

---

### Post by kayosiii on 2009-09-10
Actually which version of UbuntuStudio are you running....
And which kernel.
I am running Karmic (not yet released) and I was having difficulties with Jack and USB and the 2.6.31-rt kernel. The 2.6.29 based rt kernel works fine for me though.

So if you are running on a RT kernel try with the normal kernel and see if you have the same problems.

---

### Post by g-raf on 2009-09-10
I've been using both the rt kernel and the regular kernel on jaunty. I've tried so much to fix this, but nothing has worked. 

When i open the Jack "connect" panel, i have only "alsa_pcm" and "system" in the outputs, with only "system" in the inputs. Nothing else, no matter how many other programs i'm trying to use (usually hydrogen and audacity). Within those programs, Jack is not recognized as a sound host in the preferences. I've tried many things, but haven't found a solution yet. Keep making suggestions please, it will help me.

---

### Post by dawiba on 2009-09-10
I seem to remember reading somewhere recently, that Audacity won't show up in Jack until you actually hit record. Once you press record, Audacity connections are available in Jack. I'm sorry it's a bit vague as advice, my memory isn't what it used to be :sad:, but try hitting record and then checking your connections in Jack.

---

### Post by dawiba on 2009-09-10
It'd be useful if you could let us know what you've got when you click on the Jack 'setup' button.

I just plugged in an old USB card and got it to start okay with Audacity and Jack using the setup window, so I might be able to help with yours.

---

### Post by dawiba on 2009-09-10
This is great, I've got the whole thread to myself now!

Anyway, I started Jack and opened Audacity. Audacity didn't appear in the Jack 'connections' window. So I clicked on record and then looked in Jack's connection window while Audacity was running (recording) and now I had a 'Portaudio' connection. I played a bit of piano and it recorded and after I stopped, I was able to play it back just fine.

Maybe you should try this?

---

### Post by g-raf on 2009-09-10
> **dawiba said:**
> It'd be useful if you could let us know what you've got when you click on the Jack 'setup' button.

I have Jack on realtime, monitoring and force-16bit. The interface is on "Pro" (that's the m-audio fast track pro) with the input device as hw:0,1 (usb audio #1) which is the capture device for the fast track. Using the alsa driver.

---

### Post by g-raf on 2009-09-10
> **dawiba said:**
> I seem to remember reading somewhere recently, that Audacity won't show up in Jack until you actually hit record. Once you press record, Audacity connections are available in Jack. I'm sorry it's a bit vague as advice, my memory isn't what it used to be :sad:, but try hitting record and then checking your connections in Jack.

I've tried this, but unfortunately didn't work. I'm getting suspicious about my alsa settings. The "alsa_pcm" can't be found in the qjackctl connect panel "input ports." The "alsa_pcm" is in the output ports, but not the inputs.

---

### Post by dawiba on 2009-09-10
I'm not sure about your settings. I've attached a screenshot of the settings I used to get the USB interface working, in case you want to try those settings.

---

### Post by g-raf on 2009-09-11
Do you use Jack for audio production? The settings show that you have 69.7 msec latency which is pretty bad. Have you tried lowering the "frames/period" and using "force 16bit"? That might help quite a bit. I'm jealous that you have it working though. What about your ALSA settings? The asoundrc.conf or alsa-bas.conf - did you need to config those files for it to work? I have my USB soundcard set to hw:0...playback is hw:0,0 and capture is hw:0,1. Jack still isn't working and it's blowing my mind.

---

### Post by dawiba on 2009-09-11
Yes I do use Jack. I normally use a firewire interface though, I only plugged the USB interface in to try to help with your situation.

I disgree with your statement about my latency being bad. Latency being bad depends on what you do and the way you work. I don't use softsynths or vsti's. In terms of plugins, I generally only use a bit of compression and reverb although I will sometimes use other effects. Most of my effects are recorded along with the instrument from external sources. All my synth and piano parts are played in (badly!) from my keyboard, with any effects at the time. Same for any guitar and bass parts. It's actually quite an old fashioned way to work.

I monitor through my interface, which allows me to hear what I play with practically zero latency along with the playback. Working like this, in theory, my latency could be at the maximum possible value and it wouldn't make any difference to the way I hear things. So high latency in itself isn't bad, it just wouldn't suit you if you play virtual instruments.

I have messed around with frames/period and other settings, but because of the reasons I give above, I just leave Jack the way I find it as regards latency. I don't force 16 bit. I haven't edited any files and I try not to because I usually end up screwing up my system. What you see is stock UbuntuStudio settings at work.

I'm sorry I can't be of more help.

---

### Post by g-raf on 2009-09-11
I'm considering reinstalling Ubuntu Studio in order to get this stuff to work. This Jack problem has basically put my life in a standstill.

---

### Post by g-raf on 2009-09-13
> **g-raf said:**
> I'm considering reinstalling Ubuntu Studio in order to get this stuff to work. This Jack problem has basically put my life in a standstill.

And that's what i did yesterday! Problem solved. Got a fresh install, realtime kernel, Jack running with all the good programs now. Pretty simple solution.

---

