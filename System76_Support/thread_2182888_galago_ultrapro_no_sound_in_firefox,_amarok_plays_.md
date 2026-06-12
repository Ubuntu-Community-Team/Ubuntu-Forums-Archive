---
title: "galago ultrapro no sound in firefox, amarok plays ok"
date: 2013-10-22
forum: System76 Support
---

### Post by jono1515 on 2013-10-22
So I have a Galago Ultrapro that I upgraded to 13.10. I have Ubuntu, Kubuntu and Xubuntu all installed and the problem I'm having is the same in each. Basically, I can play music in Amarok but I can't get audio in Firefox or Parole Media Player. I can get audio in Dragon Player though. So it's not just a flash issue. I have actually uninstalled flash and installed lightspark for my browser plugin because I couldn't even get youtube videos to play at all with the adobe flash plugin. Now they play, just without sound. Has anyone else had a similar problem and if so what did you do to fix it? I'm getting close to doing a clean install but I really don't want to go through the pain of copying all my files back over to the laptop, especially if it's not even guaranteed to help at all. Thanks for any suggestions.

Jono

---

### Post by jono1515 on 2013-10-23
Ok I have it fixed. After some googling I took a guess that maybe it was a problem with alsa letting multiple applications play sound at a time. I uninstalled lightspark and reinstalled adobe flash player manually (downloaded the tar.gz file from adobe directly and copying libflashplayer.so to ~/.mozilla/plugins/). This page - [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash) suggested installing alsa-oss with sudo apt-get install alsa-oss and then making a firefoxrc file at /etc/firefox/firefoxrc that contained the following - FIREFOX_DSP="aoss"

At that point I could play youtube videos with audio if I hadn't opened amarok first. However, to get audio to play in amarok I had to close both programs and then open amarok. So any time I wanted to switch which program could play audio, I'd have to close both programs and then restart the one I wanted to play audio. 

Further searching revealed this at the alsa project page ([http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc)) 
creating a .asoundrc file or /etc/asound.conf file with the following in it -
pcm.!default {
	type plug
	slave.pcm "dmixer"
}

pcm.dmixer  {
 	type dmix
 	ipc_key 1024
 	slave {
		pcm "hw:1,0"
		period_time 0
		period_size 1024
		buffer_size 4096
		rate 44100
	}
	bindings {
		0 0
		1 1
	}
}

ctl.dmixer {
	type hw
	card 0
}

The only change I made was to change "card 0" to "card PCH" 

I can now play audio in multiple programs at the same time without having to shut any and reopen them. Hope this helps someone.

---

