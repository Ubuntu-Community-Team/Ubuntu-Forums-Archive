---
title: "Nooblet needs some help (Envy24 control related)"
date: 2011-04-07
forum: Ubuntu Studio
---

### Post by Musicjunkie4537 on 2011-04-07
I'm using ubuntu 10.4 with a partial upgrade to ubuntu studio, just to give you the heads up.

I'm using an M-Audio 2496 soundcard if that helps as well

So I was messing around in the Envy24 control playing with sample rates because when I pressed a different sample, it made a tone and all the tones went together musically, 

So as I was messing around making this beat, I hit the S/PDIF at the bottom, then tried clicking on another sample rate, but the actual rate stayed at S/PDIF.  I have tried a bunch of things like  enabling the onboard soundcard to see if it would kick it out of its 'stuck' state, but that didn't work,  I tried a different Ubuntu installation and the Envy24 control isn't stuck there, but I still haven't figured out how to get audio output from that installation

I'm a serious noob when it comes to computer programming and software, but musically thats where my mind is at.  Because of this Its kiiled my productivity and I really would love some help.

I hope to God this isn't gonna be a hardware problem.  Does anyone know what may have happened?  Is this a bug in the Envy24 control? If so, how do I fix this

---

### Post by Pablo_F on 2011-04-07
Hi, 

Try removing and reinstalling the package named "alsa-tools-gui" via Synaptic (envy24control is part of this package).

Cheers, Pablo

---

### Post by Musicjunkie4537 on 2011-04-07
Thanks for the advice, Pablo, unfortunately, I tried a regular removal and a complete removal, and when I open up the envy24 control its still stuck at S/PDIF as the sample rate.  Any more suggestions? :P

---

### Post by Pablo_F on 2011-04-07
I don't know what happens. It is beyond me.

I suggest you run the alsa-info script. This command will do it at once:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Upload to the internet and copy the URL provided.

Then, ask in the alsa-user mailing list, explaining your problem and giving the URL. You can subscribe from here: 

[http://www.alsa-project.org/main/index.php/Mailing-lists](http://www.alsa-project.org/main/index.php/Mailing-lists)

Cheers, Pablo

---

### Post by sgx on 2011-04-08
> **Musicjunkie4537 said:**
> I'm using ubuntu 10.4 with a partial upgrade to ubuntu studio, just to give you the heads up.

I'm using an M-Audio 2496 soundcard if that helps as well

So I was messing around in the Envy24 control playing with sample rates because when I pressed a different sample, it made a tone and all the tones went together musically, 

So as I was messing around making this beat, I hit the S/PDIF at the bottom, then tried clicking on another sample rate, but the actual rate stayed at S/PDIF.  I have tried a bunch of things like  enabling the onboard soundcard to see if it would kick it out of its 'stuck' state, but that didn't work,  I tried a different Ubuntu installation and the Envy24 control isn't stuck there, but I still haven't figured out how to get audio output from that installation

I'm a serious noob when it comes to computer programming and software, but musically thats where my mind is at.  Because of this Its kiiled my productivity and I really would love some help.

I hope to God this isn't gonna be a hardware problem.  Does anyone know what may have happened?  Is this a bug in the Envy24 control? If so, how do I fix this
Hi, in the envy24control profiles tab, type a name into the first box, and press save active profile.
This file will get saved as ~/envy24control/profiles.conf  (not in a typical .folder!)
It is a file that looks much like /etc/asound.state and with similar elements.

I have a pci maudio 24/96, in profiles.conf,
sections  control.40 thru control.43, the last lines of each section are

name 'H/W Playback Route'
value 'PCM Out' 

in control.36 and 37, the last line is

value '48000'

your file should reflect your config choices at the time you save the profile.
Make some changes, and save other named profiles, to verify that the save system is working.

also, check in /usr/sbin for alsaconf and alsactl
If both are present run this command to configure the maudio card

sudo alsaconf

In envy24control Hardware Settings S/PDIF tab, I have

Consumer ticked, not Professional, and

Copyrighted
No emphasis
PCM encoder
Original

as the options

In Patchbay/Router all 4 of the top row items are ticked

Cheers

If all fails, power off, remove the card, reboot, uninstall the envy24control and config files, power off, reinstall card, reboot, and start fresh...

I can almost smell the damp air of Redmond just thinking about it :o

---

### Post by horaz on 2011-07-12
> **sgx said:**
> Hi, in the envy24control profiles tab, type a name into the first box, and press save active profile.
This file will get saved as ~/envy24control/profiles.conf  (not in a typical .folder!)[...] 

Ok, I found it. I opened it. And I saw... I don't know. Strange things. Like this:
#########################
Control.3 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		name 'IEC958 Playback Mask'
		value ffffffffffffffffffffffffffffffffffffffffffffffff0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
################################

I don't know if it's normal. I'll attach a copy, if it can help. I got the SAME problem: s/pdif stuckked. More, "sudo alsaconf" doesn't exist. :(

Can you help me?

---

