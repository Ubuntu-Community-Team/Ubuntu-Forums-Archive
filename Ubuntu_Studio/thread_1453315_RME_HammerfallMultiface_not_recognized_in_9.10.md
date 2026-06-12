---
title: "RME Hammerfall/Multiface not recognized in 9.10"
date: 2010-04-13
forum: Ubuntu Studio
---

### Post by sonicolonic on 2010-04-13
I am getting so frustrated with Linux audio OSes right now. Used to use DeMuDi ok but not really in a productive way, then switched to 64Studio 2.1, tried to switch to 3beta3 with some kind of driver conflict that crashes at boot, and so here I am at Ubuntu Studio. Everything was going great until I realized it's not detecting my HDSP card. I was trying to get pulse to go through jack, with limited success, when I noticed it wasn't an option. I'd tried assigning soundcard indexes and tried at least one other pci slot, disabled onboard audio, so now it's the only soundcard. 

So, so, so, so sick of 99% functionality from an OS except for the one critical component.

I've tried so many different things to get the pulse/jack combo to get everything playing through jack, I have no idea if I messed up the chances of sanely getting the HDSP card to work.

lspci sees it but nothing else does. That's all the info I can really offer right now. irq seems to be 20. 

Any leads from here? I've got no problem getting my hands dirty as I've already broken 2 OSes this week. 

I was really looking forward to going to bed early tonight and getting up early and recording all day, but instead I put in an 8 hour shift at this blasted computer trying to figure this mess out... getting sick of spending my time like this and might revert to 64Studio 2.1 if this doesn't work out. 

~Brian

---

### Post by cchhrriiss121212 on 2010-04-13
> lspci sees it but nothing else does.
Does that mean that you get nothing from aplay -l?
I would not recommend trying to get pulse and jack working together. What is it you need pulse for?

---

### Post by sonicolonic on 2010-04-13
aplay -l shows my on-board audio and that's it. 

I don't need pulse so I tried to uninstall it last night but couldn't do a complete uninstall. I went through and picked only the packages that didn't want to remove the ubuntustudio-desktop package. Just went through and uninstalled some more pulse related packages.

I don't know squat about pulse but when I realized US used it and that some people got it to play nice with jack (sometimes) I thought I'd try it. 

I might just try reinstalling US with just the hdsp installed, maybe it'll detect it and then I'll just add my ice1712 card later. 

Thanks for replying. 

~Brian

---

### Post by trulan on 2010-04-13
By default, Pulse Audio is suspended when Jack is started (that is, if you start Jack from Jack Control[qjackctl]).  I've found that actually trying to get Pulse to output to Jack results in a pretty unstable audio system.  But using Jack Control and letting it suspend Pulse works great for me except it sometimes makes the volume buttons on my laptop quit working.  But I can live with that.

If you really want to avoid Pulse Audio, you can either disable autospawning of the process (I've never done it, but I've read about it), or you could try a distro such as AVLinux that doesn't use Pulse at all.  Unfortunately 64studio hasn't seen much development lately, so it's not the best option right now (as you discovered.)

---

### Post by sonicolonic on 2010-04-13
Thanks for the reply. That info helps me reasess my approach. More likely now to stick with US if 64Studio is going to take forever, or try something else completely. 

This is embarassing to admit, but I'd been doing all of this troubleshooting without the Multiface breakout box plugged in, because jack will see/list the card without the box... (or at least that's what my fried brain has been telling me)... ](*,) ](*,) ](*,) ](*,) but now that it's attached, jack sees it. 

SO... Now I'm just looking at the host error light that won't turn off. I've tried power cycling the system but no luck. Time to do more searching. 

I think I ran across something about preventing the autospawn when I was trying to run pulse through jack. I'll have to find that again.

~Brian

---

### Post by sonicolonic on 2010-04-13
Here it is!!

[http://kijjaz.exteen.com/20091117/rme-hammerfall-multiface-firmware-not-loaded-in-ubuntu-9-10](http://kijjaz.exteen.com/20091117/rme-hammerfall-multiface-firmware-not-loaded-in-ubuntu-9-10)

Worked like a charm... meaning now I get to actually test it.

~Brian

---

### Post by AutoStatic on 2010-04-14
[https://help.ubuntu.com/community/UbuntuStudioPreparation#Disabling%20PulseAudio](https://help.ubuntu.com/community/UbuntuStudioPreparation#Disabling%20PulseAudio)

---

### Post by sonicolonic on 2010-04-14
. . .

[http://ubuntuforums.org/showpost.php?p=9119965&postcount=41](http://ubuntuforums.org/showpost.php?p=9119965&postcount=41)

You got anything anything else you'd like to share Jeremy? hahaha. Don't hold back, I'm all ears.... errr, eyes.

~Brian

---

