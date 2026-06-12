---
title: "Be Lazy and clever: Control your house with voice !!"
date: 2009-06-15
forum: The Cafe
---

### Post by frenchn00b on 2009-06-15
Hi Guys,

Is there some of you using speech recognition too for your Server and House? 

I have now it working, for regular commands with the Linux box. It is cool with the headset.

I advice it, and you can impress your friends visiting you. 

Happy Tux!!

---

### Post by t0p on 2009-06-15
> **frenchn00b said:**
> Hi Guys,

Is there some of you using speech recognition too for your Server and House? 

I have now it working, for regular commands with the Linux box. It is cool with the headset.

I advice it, and you can impress your friends visiting you. 

Happy Tux!!

I don't need to do this.  My gf can recognize my speech.  ;)

---

### Post by frenchn00b on 2009-06-15
> **t0p said:**
> I don't need to do this.  My gf can recognize my speech.  ;)

Not bad,... I will propose my girlfriend. I hope I get as much luck as you :)

---

### Post by linuxguymarshall on 2009-06-15
I have my computer automated but nothing else. What application can you recommend for doing other things. I am moving in about a month and a half and would like my new room to be voice controlled lights, fan, music, etc.

---

### Post by frenchn00b on 2009-06-15
> **linuxguymarshall said:**
> I have my computer automated but nothing else. What application can you recommend for doing other things. I am moving in about a month and a half and would like my new room to be voice controlled lights, fan, music, etc.

You need for that a second pc with xp, with you computer and headset, with noice cancelling, Otherwise forget: DNS10

---

### Post by linuxguymarshall on 2009-06-15
I was hoping for something more open-source and ran on Linux as I plan to buy a nettop and let it run this. 

Anyone know of an open-source, voice recognition program? I can probably reprogram it to fit my needs I just need the voice recognition part.

---

### Post by AICollector on 2009-06-15
WHat speech recognition program are you using?

---

### Post by andras artois on 2009-06-15
I'd rather see a remote controlled in a none web based way from mobile phones to control things like that. Just my 2 fiddy,

---

### Post by ~&#730;JaZ&#730;~ on 2009-06-17
> **frenchn00b said:**
> Hi Guys,

Is there some of you using speech recognition too for your Server and House? 

I have now it working, for regular commands with the Linux box. It is cool with the headset.

I advice it, and you can impress your friends visiting you. 

Happy Tux!!


Hi!

Could you pls describe exactly how you did that? Pls...I really wish to do something like that...or even bather to control everything in my room with my cell phone...so any help pls?!

---

### Post by frenchn00b on 2009-09-07
[Innovative voice recognition, PoweredbyLinux] Talk to your Server and control electrical devices

XP machine (forget vmware,it is cycling too much):
- Buy Dragon naturally speaking
- buy a plantronics designed for skype headset
- install this xp machine

Linux power machine:
- Get Debian or Slackware, make it as "server install"
install stuff for home controlling, home linux control, electricity, heating, plugs...
put it the gsm SMS sending / receiving to control it remote, even in the car via a simple SMS
- Install a VOIP on the XP so that you can talk to your Server via Phone call (unfortunately there is only SKYPE. Linux community is passive. Not doing anything for having a remote voice command control via Phone calling (voip))
- Install the Samba, share a file call commandsmyserver.txt
sleep it and tail it

- Make few trials, on xp, onpen the dragon pad.
talk and say "File, Save"
Example:
"Mysuperpc turn off the light in the lounge. file save"
"Mysuperpc command elinks "google.be". file save"

And the Magic occurs, you can control the lights of your house
and read your emails through festival(texttospeech) for those lazy or overworked businessmen (like me)
For talking


So question:
- What is doing Linux? Why no one is working on that.
That could make really a lot of money.

I mean I would pay for saving time, sure. Voice recognition permits to save x5 x10 times more time.
We would need a super computer, to whom we could ask question. An A.I. would be perfect.
So projects or sleeping like always?

Author: French00b, always there for creating new ideas, to be followed.

---

### Post by frenchn00b on 2009-09-12
[http://www.youtube.com/watch?v=cOf1XQyxyHU](http://www.youtube.com/watch?v=cOf1XQyxyHU)


> Voximp

Voximp is an application, with which programs can be spawned and key/mouse presses simulated, all from just speaking a few words.
Installing

If you’re using archlinux, get a PKGBUILD here.
For all of you unlucky enough not to be using arch:

    * Grab the .tar.gz here
    * Extract it
    * mv voximp.py /usr/bin/voximp
    * copy everything from sample_configs to ~/.config/voximp/
    * rename voximpconf.py.sample to voximpconf.py
    * run voximp in a terminal, enjoy!

Troubleshooting
It’s really very innaccurate…

    * open up ~/.config/voximp/voximpconf.py
    * remove/comment out anything which you don’t need (I’d definitely suggest the bit which adds every letter)
    * follow the instructions to regen the language model

How do I regenerate the config file?

Once you’ve edited the config to your satisfaction, run voximp -c which will create a corpus.txt in the current working directory, and give you some instructions. Follow these instructions.
Nothing is picked up

Seems to be a bit of an issue – the fun of linux + microphones.
A possible solution follows:
list all audio capture devices with arecord -l
for me, this give the following output

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: default [AK5370 ], device 0: USB Audio [USB Audio]
Subdevices: 0/1
Subdevice #0: subdevice #0

As I want to use the USB microphone, I can see that I want device 0 on soundcard 1.
I then edit /usr/bin/voximp, and replace alsasrc in line 54 with
alsasrc device="hw:0,1"
Replace hw:0,1 with your specific card/device combination

---

