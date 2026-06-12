---
title: "Behringer UCG102 Guitar Link"
date: 2010-04-18
forum: Ubuntu Studio
---

### Post by lordofmiscreation on 2010-04-18
Does anyone have experience with the Behringer UCG102 guitar link?  The short of it is, I'd like to use the ucg102 in Reaper if possible. As far as recording guitar in reaper I am extremely flexible, any DAW where I can import a .wav or mp3 file and record more than one track at the same time over the imported track suites me.   The million dollar question is which one will read my Behringer UCG102.  It shows up as an ALSA USB Audio Codec I believe. I've heard you can use Jack, but the tutorial was hard to follow, it involved turning off audio devices in order to locate the proper alsa usb codec. Being inexperienced, I'm a little sketchy about that and am hoping to find another way.  Audacity does, it doesn't apply effects in real time so I have to run my guitar through my amp, my amp headphone jack to the ucg102. It's not great, but it gets the job done and is good enough because this computer's limited amount of Ram and processor speed will serve it's purpose as a writing tool. I plan on getting a powerful box without integrated graphics and sound so I can get a really good recording, but all in good time.  I have a couple issues with audacity, but Ill try something to solve it here in a bit. If I load a track in audacity I can't record a second because the latency correction moves it before 0? I'm going to try setting the latency correction to 0 and see what happens. A bypass solution was convert the symphonic track to an mp3 with reaper, play it through the gnome player because it's a really lite player and record the guitar tracks one at a time, converting each take to a .wav, load them up in Reaper and mix with the symphonic track. A little time consuming, but it does work. Any tips would be appreciated.  From what I can tell EnergyXT2 can also read the codec, but when I try to set it as an input, the input does not support recording. I think it's because it is not associated with wineasio on my box? I still have a lot of reading to do with this program and may be able to find a solution. If anyone has experience with how to set that up I'd appreciate it, a viable link or tutorial would be equally awesome.  I believe ardour also reads the codec. Upon starting ardour it allows me the option to record and analog or usb project. If I unplug the ucg102 analog is my only option. To me this means there is promise with ardour. I know nothing about ardour, but I'm trying to change that. If anyone knows a quick tutorial on how to inport a .wav or mp3 and set up the UCG102 as an input so I can record guitar over it I'd really appreciate it.  If anyone knows a way to get a multi-track recording with this set up please let me, any tutorials you've read, anything.  I'm trying expand my knowledge base as much as possible when it comes to recording in linux, thanks.

---

### Post by AutoStatic on 2010-04-19
Hello lordofmiscreation, the UCG102 is a class compliant USB 1.1 device so it should work out of the box. Could you post the outcome in a terminal of **aplay -l** and **arecord -l** ? And in your case it is best to use JACK. And which manual did you follow? Turning off audio devices? That's really not necessary.

---

### Post by lordofmiscreation on 2010-04-20
I'd be happy to upload any information which would be useful.
Upon typing aplay -1 in the terminal I received this message.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
megatron@ubuntu:~$ 

arecord -1

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
megatron@ubuntu:~$ 

I did quite a bit of hunting before I discovered this thread.  It seemed to work for them and was intriguing.  There method was aimed at not having to configure jack each time, however in my case, I'd rather deal with the nag of configuration over corrupting.  Once I have a better understanding of how the code is written I'd consider taking a crack at it.  

[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

Right on, thanks for the quick response, I'm really getting into Ubuntu Studio.

---

### Post by AutoStatic on 2010-04-20
> **lordofmiscreation said:**
> I did quite a bit of hunting before I discovered this thread.  It seemed to work for them and was intriguing.  There method was aimed at not having to configure jack each time, however in my case, I'd rather deal with the nag of configuration over corrupting.  Once I have a better understanding of how the code is written I'd consider taking a crack at it.  

[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)First, thanks for the info. And modifying your */etc/modprobe.d/alsa-base.conf* is an option, but you could also tell JACK directly to use the UCG102 by manually entering 'hw:default' in the 'Interfaces' field of the Setup window of QjackCtl. 'default' is the name of your card according to the output you posted that Ubuntu assigns to it.

I've attached a screenshot of the Setup window of QjackCtl with what I think would be appropriate settings to start with. Could you give it a go?

---

### Post by lordofmiscreation on 2010-04-21
No problem

I typed it in manually, the mistake I made in my earlier attempts were trying to adjust the input device instead of the interface.


Just out of curiosity when I hit the horizontal arrow next to the interface this it gave me access to this list.  

hw:0       HDA INTEL
hw:0,0     ALC888 ANALOG
hw:1       USB AUDIO CODEC
hw:1,0     USB AUDIO
default

would hw:1 be an option as well by any chance.

[IMG]http://i1000.photobucket.com/albums/af122/elblogger/Screenshot.png[/IMG]

---

### Post by AutoStatic on 2010-04-21
> **lordofmiscreation said:**
> would hw:1 be an option as well by any chance.Yes, that's the same device. But chances are the ID might change when you start using other USB peripherals and then JACK won't start anymore.

---

### Post by lordofmiscreation on 2010-04-21
Rock and Roll brother, I can handle that lol.  Thanks a lot for helping me out man, I've been dying to get the audio up and going on this system.  So far Ubuntu Studio is the best operating system I have used, the sight and sound capabilities are exceptional.

---

### Post by AutoStatic on 2010-04-21
You're welcome. So get that Rakarrack and Guitarix and noodle the blisters on your fingers :)

---

### Post by zander1013 on 2010-04-24
so did you get the beringer ucg102 to work?

---

### Post by sgx on 2010-04-25
> **zander1013 said:**
> so did you get the beringer ucg102 to work?
Hopefully he blistered his fingers jamming, and can't type for a couple more days :)

(not wishing him the pain, but hoping he has it working!)

---

### Post by marconbr on 2010-12-06
I have a Behringer UCG102 Guitar link and I can't use it in ubuntu 10.04 (64bits).

I've already installed qjackctl and configured the interface either as default and as hw:1, but still nothing happened. I've also changed the sample rate, but still there ain't no sound.

I'm pretty much a newbie in using audio devices in ubuntu, so any advice will be welcome.

---

### Post by Pablo_F on 2010-12-07
Hi, 

Please, can you give the termninal output of 

lsusb 

and your hardware-software audio configuration with alsa-info? This command will do it:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Upload the info and give the URL please.

Cheers, Pablo

---

### Post by marconbr on 2010-12-07
Hey Pablo, here goes the output of lsusb:
> 
$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08bb:2902 Texas Instruments Japan 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 002: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

My alsa-info was uploaded in the following address:

[http://www.alsa-project.org/db/?f=d551570e0bdee004f06532a429f8c7c311cf24eb](http://www.alsa-project.org/db/?f=d551570e0bdee004f06532a429f8c7c311cf24eb)

Cheers,
Marco

---

### Post by kaizen666 on 2011-08-03
man I can't get this thing to work at all.

what exactly am I supposed to be doing to get the sound card working.

I know there is a .exe file on the cd that came with it, but I don't want to play this through wine.

how can i make the usb port pick up the guitar? 

sorry if i'm being a bit slow, but i been working on this for a few hours now :P
so i think i followed everything correctly on the ubuntu page, I changed the config file to having the # in front of the options thing and did the 2 ports one for my computer sound card and the other for the guitar(USB) one

edit: i replaced the config file the way it was before i tinkered about with it. Now I have tried to do it through the jacks settings that have been mentioned here.  Still nothing, although there is a little white noise coming from the speakers now which could be better than what i was getting before which was nothing.  The cable is new, just got it, any other settings i need to be looking at?...2nd edit- got the noise out now, although there is a time delay, is this because i'm using hw:0 as my output and hw:1 as input?

---

### Post by sgx on 2011-08-04
ps ux will show the running processes, if pulseaudio shows up

killall pulseaudio (or whatever name it goes by)

I would try to get jackd working, in the qjackctl gui,
it is crucial to set the periods/buffer to 3 for a usb device. 
The qjackctl gui wiki is

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

I would read the links from bottom to top, the bottom one may be all
you need for now.

When you start qjackctl, go to the setup page, on the right you see

Input device >
Output device >

click the > widgets, and your card should appear, so select it
for input and output. But not all devices offer outputs, so you can
choose your motherboard soundchip or another soundcard for playback,
and the Guitar Link for input.

A Fender Mustang 1 usb amp/interface is $99 or less, provides
great usb and line-level signals, that work great with rakarrack,
calf plugins, guitarix etc.

Cheers

---

### Post by kaizen666 on 2011-08-04
thanks for the info, i did finally get it working through rakarak(sp) but the other apps don't do anything, so guessing it's just a case of learning how to use those which isn't relevant to this post.

i can confirm though that the bit of advice sgx gave me there was a lot clearer than all the other stuff i read on the net so far, so thanks.

the input/output thing just changes whether i play through pc or the headphone jack it seems.  i am reliably informed by many of my muso friends that delay is inevitable on any system like this, so bang go the fast solos for me :( unless someone has come up with a no delay programme. might try the fender options once i've got some cash, but it's off-topic so won't ask here.

peace:guitar:

---

### Post by sgx on 2011-08-04
Hi, in qjackctl, lower the Frames/period setting in the Setup panel,
go lower and lower, and if you get stuttering or clicks/pops, go back to the previous good setting. The setting has a low of 16, each setting doubles that, up to 4096. Try 256 or 128, and go from there.

Linux will get you great low latency guitar recordings, ignore
the windows/mac fanbois :popcorn:

The input device decides what you will record from, the output
device decides which soundcard will >be< the output. If nothing is connected to the devices you selected, recording or playback doesn't happen. Its similar to selecting a soundcards asio driver in windows,
but much more flexible.

Guitarix is good for experienced player who will craft their sound.
Calf Plugins are an excellent group of fx plugins, start their gui with
the command calfjackhost from the terminal, or a sound menu item.
Cheers

---

### Post by kaizen666 on 2011-08-08
hahaaaa....EXCELLEEEEENT!!!! (sorry for the dated Bill+Ted reference)
:D:D:D

sgx...ty so much, almost no noticeable delay...I set it at 128 and its GREAT, I can even manage to get some quite complicated rhythm techniques coming out also now as well as doing some pretty fast fingerlicks (for me anyway)..

TY so much,:guitar:

---

### Post by sgx on 2011-08-08
One great thing about linux, is there is always something to discover.
So much is locked away in mac/windows, that we get to tinker with.

[http://www.youtube.com/watch?v=43ES7p4ejX0](http://www.youtube.com/watch?v=43ES7p4ejX0)

Here are some videos of ardour, and more on the sidebar, like
Hydrogen, a great drum machine/sample player.

Glad things are working! :D

---

