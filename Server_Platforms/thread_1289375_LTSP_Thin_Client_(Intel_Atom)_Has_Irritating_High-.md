---
title: "LTSP Thin Client (Intel Atom) Has Irritating High-Pitched Sound"
date: 2009-10-12
forum: Server Platforms
---

### Post by AlexanderDGreat on 2009-10-12
Hi, I have an LTSP Server running on Ubuntu 9.04.

My thin client is an Intel Atom INTEL D945GCLF2, but I noticed there's a high-pitched irritating buzzing sound coming from the speakers. It's as if the processor is making this because it fluctuates every time I do something.

What can possibly cause this?

How can I disable this?

Any ideas?

Help Me! It's Really Annoying!

---

### Post by kpholmes on 2009-10-12
i got a intel atom 330 little pc i got from newegg for about 100 bucks, the think rocks. 

well if i read it correctly its the speaker thats making that noise? if it is a speaker then just rip the sucker out, (thats probably not the best advice) but its something i would do. haha.

has it always made that noise since you installed ubuntu?

if you can, try and figure out if its a hardware problem, or the mobo is flipping out cause theres something on the software side.



p.s. for a quick test with the software, pop in a live cd.:guitar:

---

### Post by AlexanderDGreat on 2009-10-12
Hi kpholmes, thanks for answering.

Nope, it's not the speaker because I plugged in a lot of GOOD working speakers and earphones on the front and back JACK ports, but it's still there.

Every time I move the mouse or do some processing, sound goes: "zzzzz, eeeeee, zzz, wweeee, eeellleeee". I've tried disabling all sounds to make it disappear, but unfortunately it's coming from the MAIN PCM SOUND of the computer.

Is this a motherboard issue? Is it grounded?

OK I'll try what you said from the LiveCD, but what do I do if the sound still exists from the LiveCD?

I'll come back soon.

Thanks for your idea!

---

### Post by cariboo on 2009-10-12
I would suggest check your grounds, between the mb and the case, also make sure the p/s is grounded properly.

---

### Post by AlexanderDGreat on 2009-10-12
Thanks cariboo907, I'll do what you say, and come back here.

---

### Post by kevin11951 on 2009-10-12
Every time I try to set up an Ubuntu ltsp server, the clients always make that buzzing noise.  I have no idea how to fix it, but I can tell you it has nothing to do with hardware errors.

---

### Post by AlexanderDGreat on 2009-10-13
> **kevin11951 said:**
> Every time I try to set up an Ubuntu ltsp server, the clients always make that buzzing noise.  I have no idea how to fix it, but I can tell you it has nothing to do with hardware errors.

Hi kevin11951, so it's part of the hardware itself?

How can I mute it, or KEEP IT TO MINIMUM LEVEL? Is there a problem with the speakers? Or my sound preferences?

Thanks.

---

### Post by kevin11951 on 2009-10-13
> **AlexanderDGreat said:**
> Hi kevin11951, so it's part of the hardware itself?

How can I mute it, or KEEP IT TO MINIMUM LEVEL? Is there a problem with the speakers? Or my sound preferences?

Thanks.

At the moment, I have no idea what is causing it.  What model router are you using?

---

### Post by AlexanderDGreat on 2009-10-14
> **kevin11951 said:**
> At the moment, I have no idea what is causing it.  What model router are you using?

Hi kevin, I'm using a DLINK - DL524 router. Would that affect the irritating high-pitched sound? I'm going to ask the experts at irc.freenode.net #ltsp for more info on this. I have 5 thin clients all, Intel Atoms, so far this is the only problem I couldn't solve. We couldn't play music or watch videos because of this weird-electric sound. By the way, did you notice if you stop moving your mouse, the sound shuts up?

---

### Post by kevin11951 on 2009-10-14
> **AlexanderDGreat said:**
> Hi kevin, I'm using a DLINK - DL524 router. Would that affect the irritating high-pitched sound? I'm going to ask the experts at irc.freenode.net #ltsp for more info on this. I have 5 thin clients all, Intel Atoms, so far this is the only problem I couldn't solve. We couldn't play music or watch videos because of this weird-electric sound. By the way, did you notice if you stop moving your mouse, the sound shuts up?

On my clients, the sound starts the second the sound server starts.  It sounds like white noise, and keeps on going until the sound server is shut off (along with the computer).  

The reason I asked you about the router, is because I have a linksys wrt54gs v7.2, and thought maybe I was trying to push too much data through at once, so the sound was getting messed up.

---

### Post by AlexanderDGreat on 2009-10-14
So it's coming from a sound server? Would you mind bringing this up in the LTSP channel? It sounds to me you have more experience in servers, I'm practically new, and has a very basic setup, though I can hear that "white noise" as well.

They were suggesting about the monitor refresh rate? And the other is hardware problem, but 5 clients can't be a hardware problem. I think it's a bug.

---

### Post by AlexanderDGreat on 2009-10-16
Hey Kevin, so what do you do with the noise? Do you turn off the speakers? I assume you can't watch YouTube videos, or play music, correct?

Me, I just turn off our speakers and whine in frustration...

---

### Post by kevin11951 on 2009-10-16
> **AlexanderDGreat said:**
> Hey Kevin, so what do you do with the noise? Do you turn off the speakers? I assume you can't watch YouTube videos, or play music, correct?

Me, I just turn off our speakers and whine in frustration...

Yup, that sounds about right :)  I will try to get on irc sometime tomorrow.

---

### Post by AlexanderDGreat on 2009-10-16
Sorry double post!

---

### Post by AlexanderDGreat on 2009-10-16
Hi kevin, are you using a PS/2 mouse? Today, I tried a USB mouse and the Friggin Sound disappeared!

---

### Post by AlexanderDGreat on 2009-10-19
Hi kevin, how's it going? Can I ask a question from you? Do you have any other problems with your Intel Atom besides the irritating high-pitched sound coming from the PS2 mouse?

My Intel Atom thin client is very noisy, when LDM starts, I can hear the fan. Do you experience the same? Do I just need to replace my casing? My celeron thin clients are very quiet, and I can play mp3s and videos. Thanks for reading.

PS I've muted ALL volumes in my Intel Atom client, but the noise isn't part of it so it stays. It's like the sound of falling rain, a wind, or a spinning fan.

---

### Post by AlexanderDGreat on 2009-10-20
The wind noise problem is solved, I just installed mplayer as a local app! Thanks for all those who read my problem.

---

### Post by frederickjh on 2010-02-05
Hi all!  

I recently upgraded my Ubuntu LTSP Intrepid to Jaunty to Karmin, and now I am having a strange problem with the sound. As soon as the client machine says 

" Starting LTSP Client . . . " 

the speakers start putting out white noise (like an FM radio not tuned to any station).

I went on the LTSP irc channel and got the following advice:

> (07:16:06 PM) vagrantc: set your *VOLUME= parameters...
(07:16:06 PM) frederickjh: This white noise can not be muted on any audio channel and only stops when the client shuts down.
(07:16:20 PM) Gadi: frederickjh: try adding MIC_VOLUME=0 and FRONT_MIC_VOLUME=0 to your lts.conf
(07:16:26 PM) vagrantc: frederickjh: it's probably picking up from the mic and generating a feedback loop
(07:16:38 PM) frederickjh: Ok will try.
(07:17:03 PM) vagrantc: and it will considerably reduce the pain in your ears to lower VOLUME=20

I then added the lines 

MIC_VOLUME=0
FRONT_MIC_VOLUME=0 

under the [Default] section header in lts.conf   This is located in /var/lib/tftpboot/ltsp/i386/

However if you have a different architecture client machine the i386 part will change.

I found your post when trying to find a fix and though I would post so others can find the answer too.

Frederick

---

