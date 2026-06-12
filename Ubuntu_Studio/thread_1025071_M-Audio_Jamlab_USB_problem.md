---
title: "M-Audio Jamlab USB problem"
date: 2008-12-29
forum: Ubuntu Studio
---

### Post by TTC1 on 2008-12-29
Hello,

I posted this in the Multimedia & Video section but no one has answered yet.
Then I realized here was the Studio distro section.

So I'm reposting my problem here. Hopefully someone will be able to help me out.

Here goes:

I just installed Ubuntu-Studio a few days ago and I am using this M_audio Jamlab USB interface as my main sound module.

My problem is that I only have one channel operating (having sound)
I remember ansewring a question, at the install time, about sound devices, it was asking me if I wanted 1 or 2 devices, or something like that. I wasn't sure and answer with 1. I have the feeling that it is related somehow.

Now, after quite a bit of searching thru the internet, I came up with someone having the same problem but within a Mandriva distro.
He kinda tracked down the problem to the amixer config.

My result of "amixer -c0 contents":

numid=1,iface=MIXER,name='PCM Playback Switch'
; type=BOOLEAN,access=rw------,values=1
: values=on
numid=2,iface=MIXER,name='PCM Playback Volume'
; type=INTEGER,access=rw---R--,values=2,min=0,max=319,step=0
: values=77,158
| dBscale-min=-127.50dB,step=0.39dB,mute=0
numid=3,iface=MIXER,name='Mic Capture Switch'
; type=BOOLEAN,access=rw------,values=1
amixer: Control hw:0 element read error: Invalid argument

numid=4,iface=MIXER,name='Mic Capture Volume'
; type=INTEGER,access=rw---R--,values=2,min=0,max=292,step=0
: values=255,264
| dBscale-min=-127.99dB,step=0.50dB,mute=0

Now, if you look at numid=2 you see values=77,158
If I change the value 77 to 158 the second channel comes into action.
But, obviously it is only temporary and upon next reboot it reverts back to its original setting at 77.

In Mandriva, he used the file /etc/rc.local to put in the change.
I just can't find that file in Ubuntu. I'm assuming Ubuntu is using another file to register these settings.

I haven't had any luck so far finding where the hell these settings are saved in Ubuntu.

Another thing that puzzles me.
When I boot into Windows (I'm dual booting on this machine), my USB interface makes some initialization noises that come out from both channel but when I boot into Linux, I hear noise from only one channel.
I have a feeling that the drivers may have been compiled into the kernel with the wrong info in them.

Anyways, anyone can help me out with this here?
I am not very knowledgeable with Linux. I know my way around within Windows but Linux is another beast to master.

Thanks for any help.

---

### Post by Nunu on 2010-01-07
Don't know if this will help but its worth a shot

[http://forums.m-audio.com/showthread.php?211-JamLab-Alsa-driver](http://forums.m-audio.com/showthread.php?211-JamLab-Alsa-driver)

Please let me know if it worked for you

---

### Post by AutoStatic on 2010-01-07
Hello TTC1, there are several possibilities to work around this. I would personally avoid using /etc/rc.local for this.

1. You could create a little startup script in your home directory with the following lines in it:
```
#!/bin/bash
amixer -c0 cset numid=2 100%
```
Name it **jamlab** for example. Make it executable with the terminal command **chmod +x /home/youraccountname/jamlab**
And then have this script executed everytime you log in by adding the script to your startup applications (System - Preferences - Startup Applications)

2. You could create a new *asound.state* file. This is the file that holds your mixer settings. First you have to make sure the JamLab has the right mixer settings, you've already done that successfully, and then you have to save that state with the terminal command **alsactl store -f $HOME/Desktop/asound.state**
This will create a file *asound.state* on your Desktop. Now copy this file to your */etc* directory:
[B]sudo cp /etc/asound.state /etc/asound.state.orig
sudo cp /home/youraccountname/Desktop/asound.state /etc/asound.state[/B]

I'm not 100% sure if the 2nd possibility will work though but I think it should.

---

