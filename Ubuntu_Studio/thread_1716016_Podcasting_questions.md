---
title: "Podcasting questions"
date: 2011-03-27
forum: Ubuntu Studio
---

### Post by SPW06 on 2011-03-27
Hello all,

I would like to start a semi-professional podcast in about the next 6 months. I plan on using a laptop (for the ability to record anywhere) with a M-Audio mixer to provide power and a interface to a couple of mics. Occasionally, I will conduct interviews over Skype. For post-production purposes recording should take place with separate channels  for each mic, the output from the Skype call, and for sound bites queued up in VLC or something. There would need to be a separate virtual audio device which would combine the input from the mics and the sound bites, so the interviewee can her it via Skype. How could this setup be accomplished with Ubuntu (Studio)?

First and foremost, I don't want to start a flame war. I used a MacBook as my primary machine for about three years. I have since sold that MacBook to help fund a high-end desktop for software development, testing, and vitalization, with a windows partition for gaming. From my experience with all 3 OSes, I have found that OS X, with the addition of SoundFlower and wiretap studio, makes a sound configuration painless. That said, I am not impressed with Apples cost to hardware quality ratio. Of all of their machines, the 11'' MacBook air seems well suited to the task it terms of portability and cost. I'm also not crazy about the fact that the Air only has one USB port. However, for about the same amount of money, I can get a much more powerful, flexible laptop in the form of a Lemur UltraThin from System76.

So, I'm taking a closer look at Ubuntu (Studio). I know that SoundFlower it really just a simplified JACK port. However, most of the tools I have seen for JACK on Ubuntu seem overly complex by comparison. Can anyone explain to me which tools I would need and how they work? Or at least a practical tutorial?

Finally, I know that Ubuntu Studio comes pre-loaded with all the tools I would ever need, including tweaks to let audio tools operate in "real time". I also know that some of these tweeks may worsen laptop power usage. Should I use Ubuntu Studio or plain old Ubuntu?

---

### Post by zettberlin on 2011-03-28
> **SPW06 said:**
> Hello all,

I would like to start a semi-professional podcast in about the next 6 months. I plan on using a laptop (for the ability to record anywhere) with a M-Audio mixer to provide power and a interface to a couple of mics. Occasionally, I will conduct interviews over Skype. For post-production purposes recording should take place with separate channels  for each mic, the output from the Skype call, and for sound bites queued up in VLC or something. There would need to be a separate virtual audio device which would combine the input from the mics and the sound bites, so the interviewee can her it via Skype. How could this setup be accomplished with Ubuntu (Studio)?


With the exception of Skype, all of this and more can be done in Ardour2, wicht comes with Ubuntu Studio). It is the perfect broadcasting studio. Its alternatives(like Traverso or Qtractor) all run with Jack also. So Jack is the foundation whenever you want to do audiowork in a more like basic manner.

Skype, well -- it is proprietary and not really intended to be used in professional audiowork. But I am sure, that there are tricks to incorporate its audio-ports into a Jack-session. Basically all audio produced under Linux can be routed to Jack, regardless if the application is written to support Jack or not. But in some cases performance suffers as you do that and the solutions can mean unusual 1-2h of reading howtoes and applying them ;-)

> **SPW06 said:**
> 
...

 However, most of the tools I have seen for JACK on Ubuntu seem overly complex by comparison. Can anyone explain to me which tools I would need and how they work? Or at least a practical tutorial?

You put it perfectly right: they "**seem** overly complex by comparison". At first glance I should add :) Once you have the system running you will find, that Jack is easier to operate than wirering your USB-interface. Do not block yourself by searching for strange mysteries in it: it is just a virtual patchbay that operates automatically most of the time and gives you easy-to-use tools to adapt such automatisms by hand. All logical and written in the tongue of musicians/soundtechs.


> **SPW06 said:**
> 
Finally, I know that Ubuntu Studio comes pre-loaded with all the tools I would ever need, including tweaks to let audio tools operate in "real time". I also know that some of these tweeks may worsen laptop power usage. Should I use Ubuntu Studio or plain old Ubuntu?

You should use Ubuntu Studio with the generic Kernel. You do not need hard Realtime for your tasks, so you can set Jack to run with say 512 Frames/Period and 3 Periods. This would translate to approx. 30 Milliseconds Latency, unacceptable for musicians but perfectly OK for radio-production.

If you really experience too much power-usage/heat you can allways revoke realtime-permissions by moving all the files in the folder /etc/security/limits.d to a backup-folder (on your desktop, on a USB-stick -- you choose) and restart.
Without these files you will have to start Jack without realtime and memory-locking. both options can easily be unchecked in the configuration-panel of Qjackctl.

---

### Post by SPW06 on 2011-03-28
> **zettberlin said:**
> 
Skype, well -- it is proprietary and not really intended to be used in professional audiowork. But I am sure, that there are tricks to incorporate its audio-ports into a Jack-session. Basically all audio produced under Linux can be routed to Jack, regardless if the application is written to support Jack or not. But in some cases performance suffers as you do that and the solutions can mean unusual 1-2h of reading howtoes and applying them ;-)

I don;t like the idea of using Skype either. However, it's semi-ubiquitous, cross-platfrom, and easy to use. Idealy, I'd prefer something browser-based so the interviewee would not need to install anything. DimDim once provided such a service, but they have now been aquired by Salesforce.com. There is an open source version, but a suspect the project may slowly die now that DimDim will no longer support it.

GNU free call seems perfect as a Skype alternative; too bad it's still in the planning stages :p

Would Firefox be any easier with JACK? If so, Does anyone know of a service like DimDim, which would alow for a cross platform (Windows, Mac, Linux), browser based metting with VoIP without the need for additional software (with the acception of Adobe Flash)?

> **zettberlin said:**
> 
You should use Ubuntu Studio with the generic Kernel. You do not need hard Realtime for your tasks, so you can set Jack to run with say 512 Frames/Period and 3 Periods. This would translate to approx. 30 Milliseconds Latency, unacceptable for musicians but perfectly OK for radio-production.

If you really experience too much power-usage/heat you can allways revoke realtime-permissions by moving all the files in the folder /etc/security/limits.d to a backup-folder (on your desktop, on a USB-stick -- you choose) and restart.
Without these files you will have to start Jack without realtime and memory-locking. both options can easily be unchecked in the configuration-panel of Qjackctl.

Do I need to select the kernel at install? Do you think heat and power preformance would be an issue with my (simple?) solution?

---

### Post by zettberlin on 2011-03-28
> **SPW06 said:**
> I don;t like the idea of using Skype either. However, it's semi-ubiquitous, cross-platfrom, and easy to use. Idealy, I'd prefer something browser-based so the interviewee would not need to install anything. DimDim once provided such a service, but they have now been aquired by Salesforce.com. There is an open source version, but a suspect the project may slowly die now that DimDim will no longer support it.

GNU free call seems perfect as a Skype alternative; too bad it's still in the planning stages :p

Would Firefox be any easier with JACK? If so, Does anyone know of a service like DimDim, which would alow for a cross platform (Windows, Mac, Linux), browser based metting with VoIP without the need for additional software (with the acception of Adobe Flash)?


[QUOTE=SPW06;10611029]
Do I need to select the kernel at install? 

NO, get the generic Kernel automatically provided by the installer, it will work for the things you plan to do.

> **SPW06 said:**
> 
Do you think heat and power preformance would be an issue with my (simple?) solution?

Trouble is or can be: IF any application running with Jack will need full force all cycles, it will get it, for as long as it wishes to get it. Certain FX-Plugins can do that, there is badly programmed audio-software out there also. If you can spot such evildoers, you could replace them with an alternative (if there is any).

I recommend you try. Everything SHOULD work OK. If it does not (if you run into heat-trouble that is) you can allways increase frames/period in Qjackctl and force your CPU to run slower.

---

