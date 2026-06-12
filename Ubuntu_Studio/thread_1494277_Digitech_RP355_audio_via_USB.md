---
title: "Digitech RP355: audio via USB?"
date: 2010-05-26
forum: Ubuntu Studio
---

### Post by MIJ-VI on 2010-05-26
Has anyone here succeeded in recording & playing back audio via the RP355's USB port?

Also, has anyone tried this?:

"Control your Digitech effect pedal under Linux!
gdigi is tool aimed to provide X-Edit functionality to Linux users

Supported devices (list misses your DigiTech device? Please get in touch!):

    * RP250
    * RP255 - support in hg
    * RP355 - support in hg
    * RP500
    * RP1000 - support in hg
    * GNX3000
    * GNX4K"

[http://desowin.org/gdigi/](http://desowin.org/gdigi/)

Thank you.

---

### Post by MIJ-VI on 2010-07-02
*bump*

---

### Post by sgx on 2010-07-03
Sorry not to have an answer, but with all honesty, rakarrack 5.8
will far exceed the needs of most guitarists, and Falk and AutoStatic
both keep it updated in their nice PPAs.

If a cover band requires quick access to a specific modeled hardware,
Amplitube 3 works nicely in linux with wine/wineasio, but having done
hours of A/B testing with Guitar Rig, Amplitube, many excellent windows freewares, and my own hardware FX boxes, for general creative work, where you create what you like, I put rakarrack on top, and Guitarix, and Calf plugins are also excellent. 

To be precise, my basic use is to send rakarrack a compressed or clean + slight reverb guitar signal from my hardware, get the sound I'm after, and utilize the hardware soundsets if needed. And multiple rakkaracks are easy as pie. Rakarrack rewards deep exploration.

The rp355 has outputs that should work in any line-in, adaptors/cables  as needed, to get the best of both worlds.
Cheers

---

### Post by MIJ-VI on 2010-07-03
Hi sgx.

I'll give rakarrack 0.3.0-2 a try first since it's available as part of the Ubuntu Studio package set (I believe) which I installed a while ago, then I'll try the newer version from: [https://launchpad.net/ubuntu/+source/rakarrack/0.5.8-1/+build/1810595/+files/rakarrack_0.5.8-1_armel.deb](https://launchpad.net/ubuntu/+source/rakarrack/0.5.8-1/+build/1810595/+files/rakarrack_0.5.8-1_armel.deb)

I'll also try the Guitarix, and Calf plugins.

I'm looking for an all-Ubuntu effects processing/practice/home recording set-up for use with MIJ Fender VI. And since no hardware or software is tailor-made for these 30" scale E0 - e-tuned, six string bass guitars...

Thank you for your prompt and comprehensive post.

---

### Post by AutoStatic on 2010-07-03
> **MIJ-VI said:**
> I'll give rakarrack 0.3.0-2 a try first since it's available as part of the Ubuntu Studio package set (I believe) which I installed a while ago, then I'll try the newer version from: [https://launchpad.net/ubuntu/+source/rakarrack/0.5.8-1/+build/1810595/+files/rakarrack_0.5.8-1_armel.deb](https://launchpad.net/ubuntu/+source/rakarrack/0.5.8-1/+build/1810595/+files/rakarrack_0.5.8-1_armel.deb)That's an ARM build for Maverick Meerkat. If you want to try a newer version and you're on Lucid or Karmic, check my [PPA]("https://launchpad.net/~autostatic/+archive/ppa/+packages").
And gdigi, can't test it, I don't have any supported Digitech devices. But if you want I could try packaging it for you. Or maybe philip5 and/or falktx have it already.

---

### Post by MIJ-VI on 2010-07-04
> **AutoStatic said:**
> That's an ARM build for Maverick Meerkat. If you want to try a newer version and you're on Lucid or Karmic, check my [PPA]("https://launchpad.net/%7Eautostatic/+archive/ppa/+packages").
And gdigi, can't test it, I don't have any supported Digitech devices. But if you want I could try packaging it for you. Or maybe philip5 and/or falktx have it already.

Thank you for clarifying, and for your offer AutoStatic.

I don't own an RP355 yet and rakarrack may obviate the need to buy one for home recording use in favour of a decent audio interface.

During my struggles with Ubuntu Studio 9.10 I started [this thread]("http://www.talkbass.com/forum/showthread.php?t=599271") over at TalkBass with the aim of providing interested TB members with a centralized source of relevant links.

Bass guitar-->audio interface-->notebook running Ubuntu Studio-->headphones (played at sane volume levels) would be the ideal approach for me (and likely others as well) when it comes to piecing/tracking together ideas as time and circumstance allows.

---

### Post by AutoStatic on 2010-07-04
> **MIJ-VI said:**
> Bass guitar-->audio interface-->notebook running Ubuntu Studio-->headphones (played at sane volume levels) would be the ideal approach for me (and likely others as well) when it comes to piecing/tracking together ideas as time and circumstance allows.Then you should give Guitarix a try. Amazing little modelling amp that can also load Impulse Response files. The most recent version for Karmic is in my PPA.

A little example: [http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection-06302010.ogg](http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection-06302010.ogg)

The basslines are routed through Guitarix with an Ampeg 8x10 IR file loaded.

---

### Post by MIJ-VI on 2010-07-05
> **AutoStatic said:**
> Then you should give Guitarix a try. Amazing little modelling amp that can also load Impulse Response files. The most recent version for Karmic is in my PPA.

A little example: [http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection-06302010.ogg](http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection-06302010.ogg)

The basslines are routed through Guitarix with an Ampeg 8x10 IR file loaded.

I'll check out Guitarix once I get my 32 bit machine up & running again.

Thanks again.

---

### Post by MIJ-VI on 2010-07-12
> **AutoStatic said:**
> That's an ARM build for Maverick Meerkat. If you want to try a newer version and you're on Lucid or Karmic, check my [PPA]("https://launchpad.net/%7Eautostatic/+archive/ppa/+packages").
And gdigi, can't test it, I don't have any supported Digitech devices. But if you want I could try packaging it for you. Or maybe philip5 and/or falktx have it already.

Hi AutoStatic.

UPDATE: I've downloaded rakarrack (0.5.8-lucid~autostatic0) lucid from your PPA and tried it--and I'm *impressed!*

Thus I've decided to spring for an...

[IMG]http://futuremusic.com/news/images/Edirol_UA-25EX.jpg[/IMG]

...[Edirol UA-25EX]("http://www.rolandus.com/products/productdetails.php?ProductId=970") (which is [supported by ALSA]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Edirol") and [sells for the same locally]("http://www.long-mcquade.com/products/9536/Pro_Audio_Recording/A_D_D_A_Converters/Edirol/UA-25_-_2_i_o_USB_Audio_Interface.htm") as the [Digitech RP355]("http://www.long-mcquade.com/products/6506/Guitars/Guitar_Effects/Digitech/RP355_-_Multi_Effects_Processor.htm")).

However, I posted a link to [gdigi]("http://desowin.org/gdigi/") on this [TheStompBox.net discussion thread]("http://www.thestompbox.net/forum/showthread.php?p=74661#post74661") along with a link to this thread and a mention of your generous offer to package gdigi.

I then tried to package gdigi myself by copying & pasting the **Setup** instructions on gdigi's site into Terminal and running them.

Everything seemed to go well in Terminal (no error messages) but gdigi is nowhere to be found on my Acer Aspire 5517-1536 (64 bit Edubuntu 10.04) even after searching the file system with variations of gdigi's name.

So my question to you is: based upon these instructions...

**Setup:**
There're no distribution packages  available for gdigi (you're welcome to package it for your distribution  of choice).
In order to compile gdigi on Debian/Ubuntu system, issue  following commands:

sudo apt-get install build-essential libasound2-dev libgtk2.0-dev libglib2.0-dev libexpat1-dev
wget [http://d10xg45o6p6dbl.cloudfront.net/projects/g/gdigi/gdigi-0.1.8.tar.bz2](http://d10xg45o6p6dbl.cloudfront.net/projects/g/gdigi/gdigi-0.1.8.tar.bz2)
tar xvjpf gdigi-0.1.8.tar.bz2
cd gdigi-0.1.8
make
./gdigi

...would gdigi have been compiled as a binary application on my notebook's hard drive, and if so, where should I look for it?

Thank you.

---

### Post by sgx on 2010-07-13
Hi, run the command

sudo updatedb

Then, check in synaptic to see what it is called after being compiled. 

Then

sudo locate appYouLookFor


You can also read the makefile for clues.

Most user apps are in /usr/bin
user admin apps in /usr/sbin

system apps and admin apps in

/bin
/sbin

Cheers

---

### Post by isaacullah on 2010-07-13
there is no make install command for gdigi compilation. The binary, once compiled, is in the same directory you compiled it in, and does not get put in a directory that is in the system path. Thus to activate it, you have to type in an explicit path. For me, this is "/usr/local/src/gdigi-0.1.8/gdigi" because I compiled gdigi in the directory "/usr/local/src/gdigi-0.1.8/".

I have an RP155, and I was hoping it would work with gdigi because it supports the 255, which is very very similar. Alas, it seems I am having no luck. I get the following error: 

ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC1D0 failed: No such file or directory
snd_rawmidi_open hw:1,0,0 failed: -2

and a pop up that says "midi device not found". Interestingly, ALSA and Jack Audio seem to see the device, and know it by name. But even though there are controls for the audio input in the ALSA mixer, I can't get audio to come through via USB. Jack thinks the RP155 is only a MIDI device when it is connected by USB, but not as an input audio port. Plugging in direct from the line out of the RP155 to the line in of my computer (a brand new Sys76 PanP7 Laptop running Ubuntu Studio 10.04) receives audio, but no matter how I adjust the mix and levels on the RP155 and in ALSA, I get really bad background hisssss. Very bad. That's using either the headphone out or the regular out jack of th RP155, with the unit set to "mixer" mode. 

So far, the best solution I've found is to run the RP straight to my amp, which has a very clean "mixer in" port, and then to mic the amp to my mic in port on my laptop. Still get a small amount of hiss (the amp is quiet, but not ABSOLUTELY quiet). Not a perfect solution for me, by FAR. It would be really nice to be able to take advantage of the USB interface, as that was one of the major selling points for me. FWIW, it doesn't work that well on my old windows box either, but at least it DOES work over there. Oh Well, if anyone has any more experience or advice about this, I'd like to know!

---

### Post by isaacullah on 2010-07-13
> **isaacullah said:**
> 
I have an RP155, and I was hoping it would work with gdigi because it supports the 255, which is very very similar. Alas, it seems I am having no luck. I get the following error: 

ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC1D0 failed: No such file or directory
snd_rawmidi_open hw:1,0,0 failed: -2

and a pop up that says "midi device not found". 


Well, a further search brought me to the following post at gdigi's google groups page: [http://groups.google.com/group/gdigi/browse_thread/thread/2d697979e935e2f3](http://groups.google.com/group/gdigi/browse_thread/thread/2d697979e935e2f3)

This is exactly the error message I got, and the fix proposed there works for me perfectly! I chose RP250 compatability mode (I'm using a 155) as it seemed the closest to my actual device. It finds all my patches, and I seem able to use the interface to modify them. GREAT! At least I can use the USB to help edit my patches, as I find it SO MUCH easier to do so over a software interface than on the machine itself (knobs and buttons).

Still, I would like to know if anyone has any ideas about getting the audio to stream up/down USB, as it is supposed to be able to.

---

### Post by isaacullah on 2010-07-13
Well, a little more searching and I seem to have found a solution to all of my problems!!!!

First, I downloaded and installed (make) the DEVELOPMENT version of gdigi following the instructions on the gdigi site

> **Latest version:**
You can get latest version of  gdigi by checking project's mercurial repository

 hg clone [http://hg.atheme.org/users/desowin/gdigi/](http://hg.atheme.org/users/desowin/gdigi/) gdigi

This version has support for the RP1000, RP355, and the RP255. The 255 settings are the most similar to my RP155, so I had a much better interface with my device. Also, someone is working on compatability for the 155, so that'll be perfect.

Okay, now onto the USB audio itself. According to this thread ([http://ubuntuforums.org/archive/index.php/t-697158.html](http://ubuntuforums.org/archive/index.php/t-697158.html)) the RP units are seen as "USB Mixer" by ALSA, but to get the specific driver for your unit, the ALSA firmware library has to be upgraded. I used the commands they recommended:

> 
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install alsa-firmware-loaders


Now it works fine! The device shows up by name on the "inputs" tab of the system audio preferences dialog (System > Preferences > Sound). Selecting it's radio button automatically routes the sound from the RP unit. I am able to record with great fidelity in "sound recorder", but Audacity crashes upon stopping record mode.

Still not sure how to use JACK with it, as it shows up as a midi device under the ALSA tab, but maybe this is okay? Anyway, I have a good solution now for USB recording, so I'm not terribly worried about it anymore. It would be good to know for sure though!

---

### Post by isaacullah on 2010-07-13
Oh, I forgot to mention to important idiosyncracies:

1) If you unplug your RP unit, then plug it back in, it will no longer be found in the sound preferences dialog until you reboot. Best bet is to reboot, turn off the RP unit. Connect the USB, and then turn the RP unit back on.

2) You will NOT be able to record or get any sound unless the RP unit is selected to be BOTH the input AND the output device in the sound preferences dialog. The unit must also be set to the "Analog Stereo Duplex" setting under the "Devices" tab of the sound preferences dialog.

If all this is followed, then audio can be recorded via USB connection.

---

### Post by pjrodz on 2010-09-01
> **isaacullah said:**
> Oh, I forgot to mention to important idiosyncracies:

1) If you unplug your RP unit, then plug it back in, it will no longer be found in the sound preferences dialog until you reboot. Best bet is to reboot, turn off the RP unit. Connect the USB, and then turn the RP unit back on.

2) You will NOT be able to record or get any sound unless the RP unit is selected to be BOTH the input AND the output device in the sound preferences dialog. The unit must also be set to the "Analog Stereo Duplex" setting under the "Devices" tab of the sound preferences dialog.

If all this is followed, then audio can be recorded via USB connection.

thanks for this man! good stuff :)

---

### Post by MIJ-VI on 2010-11-07
I recently bought an RP355. If I succeed in compiling...

[http://desowin.org/gdigi/](http://desowin.org/gdigi/)

...into a properly functioning .deb archive I'll post it in a shared folder in my Ubuntu One account.

EDIT: I've successfully compiled and tested gdigi 0.2.0 (which produced an executable file, not a .deb) and it works beautifully with my RP355. :) It appears to use MIDI to control the RP' and can run concurrently with Audacity.

However, I've just learned that I can only share files stored in my Ubuntu One account via an e-mail address so I can't use the account as a file hosting service. :(

But the instructions in the above link are straight forward enough.

I'll be forwarding a well-earned donation to Tomasz Mo&#324; along with the suggestion that gdigi's device support list be expanded to include Digitech's BP series of multi-effects processors for bass...

[http://www.digitech.com/bass.php](http://www.digitech.com/bass.php)

...and that gdigi be given the ability to export configuration files to a hard drive.

More on the RP355
[http://forum.thestompbox.net/showthread.php?t=8645](http://forum.thestompbox.net/showthread.php?t=8645)

---

### Post by espsupreme on 2011-02-05
It seems to me that a lot of you are having trouble recording audio to your computer via digitech usb. Just so you all no digitech generally does not supply the usb cord so you have to buy it. once you are connected with the usb cable go to digitechs website and download the x-edit software and the drivers. im sure a lot of many of peoples problems start with what DAW they are using. I have guitar pro tracks 4 and with this software, recording via usb is very simple.first plug your guitar into the digitech and plug usb in to. depending on what you want the audio to playback through, like your amp or computer speakers or headphones that can cause problems too. i use my amp for playing through and for playback. you must be sure that your digitech is set as both input and the output device. i record using this method and software with the rp 355 and it sounds incredible! best of luck

---

### Post by mrob184 on 2011-04-16
I'm new to Unbuntu and have been playing with it for several weeks now. I've been wanting to hook up my RP355 to it but the Xedit software does not work in Linux.
I found the gdig software but I am unable to figure out how to install it. Could someone please give me a hand. Thanks.

---

### Post by MIJ-VI on 2011-04-16
> **mrob184 said:**
> I'm new to Unbuntu and have been playing with it for several weeks now. I've been wanting to hook up my RP355 to it but the Xedit software does not work in Linux.
I found the gdig software but I am unable to figure out how to install it. Could someone please give me a hand. Thanks.

Hi mrob184.

FROM: [http://desowin.org/gdigi/](http://desowin.org/gdigi/)

Download:
Version 0.2.0 was released 7th October 2010: gdigi-0.2.0.tar.bz2
( [http://sourceforge.net/projects/gdigi/files/gdigi/0.2.0/gdigi-0.2.0.tar.bz2/download](http://sourceforge.net/projects/gdigi/files/gdigi/0.2.0/gdigi-0.2.0.tar.bz2/download) ) <--EDIT

Contact:
You can reach me by sending email to [EMAIL="desowin@gmail.com"]desowin@gmail.com[/EMAIL]
If you're looking for help, have patch or similiar please check out gdigi mailinglist at google groups
There's IRC channel available. Server: irc.freenode.net channel: #gdigi

Changelog:
Changelog is available here

Setup:
There're no distribution packages available for gdigi (you're welcome to package it for your distribution of choice).
In order to compile gdigi on Debian/Ubuntu system, issue following commands:

sudo apt-get install build-essential libasound2-dev libgtk2.0-dev libglib2.0-dev libexpat1-dev
wget [http://sourceforge.net/projects/gdigi/files/gdigi/0.2.0/gdigi-0.2.0.tar.bz2](http://sourceforge.net/projects/gdigi/files/gdigi/0.2.0/gdigi-0.2.0.tar.bz2)
tar xvjpf gdigi-0.2.0.tar.bz2
cd gdigi-0.2.0
make
./gdigi

Latest version:
You can get latest version of gdigi by checking project's mercurial repository

hg clone [http://hg.atheme.org/users/desowin/gdigi/](http://hg.atheme.org/users/desowin/gdigi/) gdigi

--------

My simplified installation instructions which worked for me:

1) [FONT=Courier New]sudo apt-get install build-essential libasound2-dev libgtk2.0-dev libglib2.0-dev libexpat1-dev[/FONT]

2) Download gdigi-0.2.0.tar.bz2 by clicking its name on desowin's [http://desowin.org/gdigi/](http://desowin.org/gdigi/) page...

"Download:
Version 0.2.0 was released 7th October 2010: gdigi-0.2.0.tar.bz2 "

...or by using the URL for gdigi-0.2.0.tar.bz2 ( [http://sourceforge.net/projects/gdigi/files/gdigi/0.2.0/gdigi-0.2.0.tar.bz2/download](http://sourceforge.net/projects/gdigi/files/gdigi/0.2.0/gdigi-0.2.0.tar.bz2/download) ).

Either of these methods will result in gdigi-0.2.0.tar.bz2 being downloaded via Firefox into Ubuntu's Downloads folder.

3) Go to said Downloads folder, find gdigi-0.2.0.tar.bz2 and move it to your Home Folder.

4) Double-click gdigi-0.2.0.tar.bz2. It should open to reveal a folder named gdigi-0.2.0

5) Drag the folder named gdigi-0.2.0 out of gdigi-0.2.0.tar.bz2 into your Home Folder.

6) Launch Terminal, type [FONT=Courier New]cd[/FONT] then tap the <space bar> on the keyboard once and then drag the folder named gdigi-0.2.0 into the Terminal window and tap the <enter> key once. What you'll see in Terminal should look like this (except that your Home Folder will have a different name than mine):

[FONT=Courier New]ubuntu:~$ cd '/home/p4/gdigi-0.2.0' 
p4@ubuntu:~/gdigi-0.2.0$[/FONT]

7) Type [FONT=Courier New]make[/FONT] then tap the <space bar> once and then type [FONT=Courier New]./gdigi[/FONT] and tap the <enter key> once. This should produce a flurry of activity in Terminal for a few seconds.

8 ) Open the folder named gdigi-0.2.0 and the various files inside should now include a new, purple diamond-shaped one named gdigi .

9) Make sure your DigiTech RP355 is plugged into a USB 2.0 port on your computer (please read the RP355's owners manual first to learn the proper way to do this) via a fairly short & well-shielded USB 2.0 cable and then double-click gdigi. A window which looks like the one on [http://desowin.org/gdigi/](http://desowin.org/gdigi/) should open.

Please report back on whether or not these instructions worked for you.

Thank you.

---

### Post by mrob184 on 2011-04-17
Hi MIJ-VI!
 I have spent the last 3 days trying everything I could find on the net about gdidg and nothing could get it to install. I'm 100% sure that my inexperiance with Linux is to blame. 
Your straightforward install instructions were clear enough that even a newbee as myself could do it and it works perfectly.
I misspoke earlier when I said I had a RP355 I actually have a RP350. I run gdidg in RP250 compatability and it works perfectly, if I try RP355 mode it gets all wonky and does'nt work right.
Thank you so much for the instructions I really do appreciate it!
I've been really frustrated with Ubuntu lately over this install issue but this experiance has changed all of that and am starting to plan a new desktop computer build with Ubuntu Studio as the OS for my guitar room.
I have alot of micro$oft habbits to break. LOL.
Again, Thank you very much.

---

### Post by MIJ-VI on 2011-04-17
> **mrob184 said:**
> Hi MIJ-VI!
 I have spent the last 3 days trying everything I could find on the net about gdidg and nothing could get it to install. I'm 100% sure that my inexperiance with Linux is to blame. 
Your straightforward install instructions were clear enough that even a newbee as myself could do it and it works perfectly.
I misspoke earlier when I said I had a RP355 I actually have a RP350. I run gdidg in RP250 compatability and it works perfectly, if I try RP355 mode it gets all wonky and does'nt work right.
Thank you so much for the instructions I really do appreciate it!
I've been really frustrated with Ubuntu lately over this install issue but this experiance has changed all of that and am starting to plan a new desktop computer build with Ubuntu Studio as the OS for my guitar room.
I have alot of micro$oft habbits to break. LOL.
Again, Thank you very much.

*does a Monty Burns* Ex-cellent! :-)

One important function which gdigi cannot yet do is save custom settings as configuration files to a hard drive. Such an ability would be VERY useful to any RP series device user who does a variety of gigs and/or recording projects. (Wanna redo a guitar part six months later while using the *exact* same guitar tones that were used on the rest of the recording?)

I believe that the author of gdigi, [email]desowin@gmail.com[/email] was/is working on adding said feature. You may wish to shoot him an e-mail for an update.

A very useful thing that gdigi does for a Digitech RP unit in a home setting is that it allows for convenient and frequent parameter tweaks without needlessly wearing out the RP's rotary switches (thus potentially prolonging the unit's service life).

These Digitech RP amp modeller/multi-effects units are decent-sounding, well thought out units which reward those who are willing to experiment with different sounds. gdigi enables such experimentation with ease.

Saving configuration files as a library of parameter tweaks tailored to specific recording projects would be the icing on the cake.

One cool thing about these units is being able to cycle through various speaker/cab models to nail tones (or to better define a part in a mix) instead of fiddling with a lot of EQ nudges.

If my RP355 got stolen I'd replace it with another or an RP500. These things are truly a great bang for the buck--especially for GNU/Linux-using musicians. Before settling on a Digitech RP355 I looked for GNU/Linux support. AFAIK only Digitech's RP Series has it--and that's ONLY because of [email]desowin@gmail.com[/email]

Speaking of GNU/Linux:

[http://linuxmusicians.com/](http://linuxmusicians.com/)
[http://wiki.linuxmusicians.com/doku.php](http://wiki.linuxmusicians.com/doku.php)

---

