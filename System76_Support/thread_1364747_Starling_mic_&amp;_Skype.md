---
title: "Starling mic &amp; Skype"
date: 2009-12-26
forum: System76 Support
---

### Post by bvandev on 2009-12-26
Has anyone had success using the internal mic on the Starling?  

I purchased a Starling in early November, installed Skype through Medubuntu and after one small configuration change got Skype and the Sound Recorder to work.  We then purchased one for my son that we gave him yesterday, but have been unable to get Skype to work.

Some facts:
Both Starlings are running 9.04.

Medubuntu seems to have dropped Skype from the repository.  Sudo apt-get install skype yielded a message that the package was not known.  I confirmed the problem by uninstalling skype from the original (sudo apt-get remove skype).  I then tried to install it again and got the same message, that the package was not known.

Skype (installed from the Skype site) shows only pulseaudio as options in the sound device screen.  I've never seen this before.

Anyway, any help would be much appreciated.

---

### Post by bvandev on 2009-12-27
Update:

I got the microphone to work using the Sound Recorder, but not Skype.

I also confirmed that Skype can no longer be installed using "sudo apt-get install skype" after loading the medibuntu repositories.  Basically, the instructions on the System76 site ([http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)) for installing skype no longer work.  The skype installation command results in this message:

bill@system76-netbook:~$ sudo apt-get install skype
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate

I'll try the static package from the Skype site next.  Some forums suggest this as the best option.

Any help would be appreciated.

Thanks.

---

### Post by bvandev on 2009-12-27
Still no success.  I have now tried the .deb package from Skype and the static package.  I've manipulated the HDA Intel, Capture:HDA and Capture: Monitor HDA sound controls, all to no avail.

Please note, the Skype Audio Options page only lists Pulse Audio.  In the past (I've been installing Skype on Ubuntu for a few years now) all of the audio options would be listed.  Now they cannot be changed. 

Thanks for any help anyone can offer.

---

### Post by riseringseeker on 2009-12-27
> **bvandev said:**
> Update:

I also confirmed that Skype can no longer be installed using "sudo apt-get install skype" after loading the medibuntu repositories.  Basically, the instructions on the System76 site ([http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)) for installing skype no longer work.  The skype installation command results in this message:

bill@system76-netbook:~$ sudo apt-get install skype
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate


Hmm, if I try to install skype (it's already there), I get this instead:

user@computer:~$ sudo apt-get install skype
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.

Are you sure the "Other Software" in "Software Sources" has both medibuntu sources checked?

---

### Post by bvandev on 2009-12-27
Yes.  However, if you remove it(sudo apt-get remove skype) and try again, I don't think it will be there.  I have two Starlings.  I installed Skype on the first through medibuntu back in November.  Two days ago, when I couldn't get it to install on the new Starling, I removed it and tried to reinstall.  This yielded the message in my last post.

Hey, I'd love to be wrong on this one.  

Does you mic work?  What settings do you have?

Thanks for replying.

---

### Post by Teasdale on 2009-12-27
I tried Tokbox on my Starling, which seems a lot like Skype, and I could see and hear everyone else but neither my mic nor my camera worked. The Tokbox box said they were "disabled." I could see that my camera was working just fine, but I don't know what's required to get it working with Tokbox. 

So it may not be just Skype.

---

### Post by bvandev on 2009-12-27
I seem to have solved the problem by installing a back-level version of Skype.  Here is what I did:

1.  Uninstalled Skype:  sudo apt-get remove skype
2.  Just for good measure:  sudo apt-get autoremove
3.  Installed the old version from this link

[http://download.skype.com/linux/skype-debi...0.72-1_i386.deb](http://download.skype.com/linux/skype-debi...0.72-1_i386.deb)

This is version 2.0.0.72-1.  

4.  Started Skype->Options->Sound Devices
5.  Changed the Sound In and Sound Out to HDA Intel, clicked Apply
6.  Opened the volume controls - right click on volume and choose Volume Controls.
7.  Choose HDA Intel (Alsa Mixer) from device list.
8.  Selected Recording tab and set Mic Boost to about half and Capture to about 7/8ths.  (Note, the mute button showed the "not" sign. Ignored this.)
9.  Set the Capture (pulseaudio) to the top also, but I doubt this mattered.

Hope this helps others with the same problem.

---

### Post by Mark.ST on 2009-12-28
Hi bvandev,

Thanks for sharing. I have a few comments and questions..
(I'm not a Starling user BTW, my computer is Lemur Ultrathin that came with Ubuntu 9.10 Karmic (64bit).)

I could download the older version of skype with the following link (your link seems to be truncated. Hope mine is fine):
[http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)

and after removing the current version of skype with

```
sudo dpkg -r skype
```

I could install the older version of skype with the following command:

```
sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
```

But the problem is I couldn't get the sound to work. I tried different combinations of HDA Intel options, but none seems to work. Could you attach a screenshot of your Sound Devices setting?

Also, under Karmic, there is no Volume Controls (right-clicking volume icon in the system tray shows only "Mute" and "Sound Preferences"). How can I "Choose HDA Intel (Alsa Mixer) from device list"(Step 7)? Do I need to install some package?

---

### Post by bvandev on 2009-12-28
Hi Mark,

I'm not sure how to do it in Karmic.  The audio tools, or at least the interfaces, have changes substantially.  The only advice I can suggest is to experiment (trial and error) with the settings in the preferences option of the sound applet (right click and choose Sound Preferences).  

At the very least it may provide you some insight into what settings to try in Skype.  

You may also want to install pavucontrol (sudo apt-get install pavucontrol).  This will provide configuration tools for pulseaudio.  

Sorry I can't be of more help.

---

### Post by riseringseeker on 2009-12-30
> **bvandev said:**
> I seem to have solved the problem by installing a back-level version of Skype.  Here is what I did:

1.  Uninstalled Skype:  sudo apt-get remove skype
2.  Just for good measure:  sudo apt-get autoremove
3.  Installed the old version from this link

[http://download.skype.com/linux/skype-debi...0.72-1_i386.deb](http://download.skype.com/linux/skype-debi...0.72-1_i386.deb)

This is version 2.0.0.72-1.  

4.  Started Skype->Options->Sound Devices
5.  Changed the Sound In and Sound Out to HDA Intel, clicked Apply
6.  Opened the volume controls - right click on volume and choose Volume Controls.
7.  Choose HDA Intel (Alsa Mixer) from device list.
8.  Selected Recording tab and set Mic Boost to about half and Capture to about 7/8ths.  (Note, the mute button showed the "not" sign. Ignored this.)
9.  Set the Capture (pulseaudio) to the top also, but I doubt this mattered.

Hope this helps others with the same problem.

bvandev was correct, Skype is no longer in the medibuntu repositories, but don't know the a reason for that.

I don't know why you would install an older version though.  Skype .deb files for [[COLOR="Blue"]32bit[/COLOR]]("http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb") and [[COLOR="Blue"]64bit[/COLOR]]("http://www.skype.com/go/getskype-linux-beta-ubuntu-64") are both available on the skype site.  (Click on appropriate version)

I reinstalled the 64bit version and it works fine.  I would guess the 32bit does as well, but there is no reason that I know of to force the install of the 32bit version on a 64bit system.

I *did* have to do a bit more than "completely remove" skype in synaptic (or purge from the cli).  I had to manually remove a skype directory or two in /etc or /user (I forget), otherwise it would fail to install, saying it could not overwrite a current file.  

I just did ```
locate skype |
``` and went and removed anything left over other than in my home directory.  When I fired up skype, all my contacts were still there since I hadn't touched the ~/.skype directory.

I had some other sound troubles that prompted me to install a couple of things from the repositories, which also made me wonder why they weren't included by default, given that pulse is the default sound scheme.

```
sudo apt-get install padevchooser pavucontrol
```

The only glitch is that one cannot have the "ring" come over the speakers and the conversation over the headset.  They will both be over one or the other, but you cannot "split" them as you could before.  

My reading tells me this is a skype implementation problem, not a pulse audio fault.  Skype simply did not split out the two (three actually, if you count the mike - I have three mikes on my Wild Dog) to make them individually controllable.

---

### Post by Tart on 2009-12-30
> **riseringseeker said:**
> 

I don't know why you would install an older version though.  Skype .deb files for [[COLOR="Blue"]32bit[/COLOR]]("http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb") and [[COLOR="Blue"]64bit[/COLOR]]("http://www.skype.com/go/getskype-linux-beta-ubuntu-64") are both available on the skype site.  (Click on appropriate version)



For some reason on Starling newer versions of skype do not allow you to select specific audio device for input and output. I had problems with that. 

bvandev Thank you very much for your post!!

---

### Post by riseringseeker on 2009-12-31
> **Tart said:**
> For some reason on Starling newer versions of skype do not allow you to select specific audio device for input and output. I had problems with that. 

bvandev Thank you very much for your post!!

As I covered in my post, the latest version of skype does not separate the inputs and outputs under pulse.  There is a fix coming from Skype, supposedly anyway.  It was an admitted oversight on their part.  It's a function of PulseAudio that allows the choice.

Skype works fine, you just have to have all the audio coming or going from one device, you cannot (currently) have it ring over one device, and hear the conversation over another.  

Install PulseAudio Device Chooser and PulseAudio Volume Control and you will indeed be able to choose which device that is.  

```
sudo apt-get pavucontrol padevchooser
```

Just click on Applications->Sound and Video->PulseAudio Device Chooser  This will put an new icon at the top.  Click on it, go to volume control, choose the "playback" tab (for output) or "input devices" to choose the mike and do a test call on skype, see what I mean.

---

### Post by thomasaaron on 2009-12-31
OK, here is how I get Skype working in Ubuntu Netbook Remix 9.04...

You're going to need to download Skype from skype.com. Get the 8.10+ 32-bit version for Ubuntu.

I have no idea if this will work with the pulseaudio volume control. I'd recommend removing it, if you've installed it, and just using the default sound preferences window that you get when you click the speaker icon.

(Thanks to marshmallow1304 for this part...)

Open a terminal and run this command...
```
gksudo gedit /etc/pulse/client.conf
```

In the resulting text editor, change...
> 
; autospawn = yes

...to...

> autospawn = no

Now, make sure skype is completely closed (click the icon in the upper bar and select Quit).

Run this command...

> killall pulseaudio

And now, restart Skype. Set up both your volume controls and your skype options according to the screenshots I've attached.

(NOTE: Doing it this way, you will have to run...

killall pulseaudio

...every time before starting Skype. If you want to make it permanent, go to Start-up Programs and create a start-up program that uses...

killall pulseaudio

...as its command. Then reboot.)

Let me know if you need further assitance.

---

### Post by bvandev on 2010-01-02
Hmmm.  Sorry, but I like the other solution better.  All I needed to do was install the prior version and it works fine, without the need for hacks.  

As near as I can tell, the only thing added in the new version was pulseaudio support, which you are disabling in your solution.  So I'm not sure of any benefit to having the newer version.  

I also tried out riseringseeker's solution with the pulseaudio controls, but was unable to get it to work.  I'm also a little confused as to why he/she installed the 64-bit version.  Was this a solution for the Starling?  Aren't we using 32-bit machines?

That said, the more options people have the better.  So thanks for the info.

---

### Post by riseringseeker on 2010-01-02
> **bvandev said:**
> Hmmm.  Sorry, but I like the other solution better.  All I needed to do was install the prior version and it works fine, without the need for hacks.  

I'm a believer in someone using what works for them and what makes them happy - even if it means windows.

> As near as I can tell, the only thing added in the new version was pulseaudio support, which you are disabling in your solution.  So I'm not sure of any benefit to having the newer version.  

There are a few additions in the new version, such as text messaging to cell phones, and a couple of other minor items, but if these are unimportant to you, there is no reason to change versions if you are happy with what you have.

> I also tried out riseringseeker's solution with the pulseaudio controls, but was unable to get it to work.  I'm also a little confused as to why he/she installed the 64-bit version.  Was this a solution for the Starling?  Aren't we using 32-bit machines?

I'm a he, and as I said, I don't have a Starling.  Both my System76 machines are 64bit (Daru1 and Wild Dog).

What failed?  If you're not interested in having the latest version it's a moot point, but am curious.

> That said, the more options people have the better.

Couldn't agree more.  Just wish karmic had kept making some of the changes I like to make as easy as previous versions, but that's a rant for another thread.

>   So thanks for the info.

Anytime

---

### Post by bvandev on 2010-01-02
Quote:

What failed? If you're not interested in having the latest version it's a moot point, but am curious.


I've already removed the new version and the pulseaudio tools, so I'm going from memory.  Also, I've never seen the 64-bit version of these tools, so I'm not sure what I was supposed to see.  

Now that the disclaimers are out of the way, the pulsesudio volume controls offered no options for choosing devices, at least none I could see.  They were strictly volume controls and each was set to the max.  I looked into the "manager" tool from the pulseaudio applet dropdown, but could find nothing in there to help either.  Next I tried the standard Sound configuration, but capture was already set to pulseaudio. I suppose I could have changed that to alsa as a test, but didn't.  

Anyway, the general forum reading public now has three paths to tread when trying to get Skype working, so the thread has worked out fine.

Thanks for your comments and input.

---

### Post by riseringseeker on 2010-01-03
> **bvandev said:**
> Quote:
I've already removed the new version and the pulseaudio tools, so I'm going from memory.  Also, I've never seen the 64-bit version of these tools, so I'm not sure what I was supposed to see.  

I doubt the 64 and 32 bit versions have much difference.  If I get bored some time sitting in a hotel room I may try to force the install of a 32 bit version just to see.  I run 64 because that's what my system is.  Someone running 32 should stick with it - if anyone here wants to chime in that is running one (or more) of each, please do.

> Now that the disclaimers are out of the way, the pulsesudio volume controls offered no options for choosing devices, at least none I could see.  They were strictly volume controls and each was set to the max.  I looked into the "manager" tool from the pulseaudio applet dropdown, but could find nothing in there to help either.  Next I tried the standard Sound configuration, but capture was already set to pulseaudio. I suppose I could have changed that to alsa as a test, but didn't.  

I am not overly fond of how PA does this, but it does work once you figure it out.  IMHO, you should be able to choose the device without the application running, but for whatever reason, the developers did not do it this way.

When an application that is producing sound is running - and **only** when it is running a new item appears in the "Playback" tab, otherwise the only thing there is "System Sounds", or at least, that's all I see.  

If one makes a test call with skype, the new item shows as in the attached screenshot, when the test call is in progress, and **only** when it in progress can the device for playback be chosen.  If I wanted to change it from the headset, (which is what is shown) to the speakers, I would just click on C-Media_USB (etc) and choose another device.

You can also for example set another device as a fall back, so if in my usage the USB headset is not plugged in, it falls back to using the speakers - an improvement over the old system from my point of view.

Just to be clear, one gets to what the screenshot is showing by opening Applications->Sound and Video->PulseAudio Volume Control.



> Anyway, the general forum reading public now has three paths to tread when trying to get Skype working, so the thread has worked out fine.

Agreed!

---

### Post by malanciault on 2010-01-07
Running Ubuntu 9.10 and had this problem where I could not get the option to select the input and output sound in the Skype options. It was always PulseAudio. I've read a little bit about this on the net and there are a few complex solutions to this but they were all too painfull for me. 

I uninstalled the latest version of Skype and re-installed the older on as mentionned by bvandev and it works perfectly:

> I seem to have solved the problem by installing a back-level version of Skype. Here is what I did:

1. Uninstalled Skype: sudo apt-get remove skype
2. Just for good measure: sudo apt-get autoremove
3. Installed the old version from this link

[http://download.skype.com/linux/skyp....72-1_i386.deb](http://download.skype.com/linux/skyp....72-1_i386.deb)
Thanks!!

---

### Post by riseringseeker on 2010-01-08
> **malanciault said:**
> Running Ubuntu 9.10 and had this problem where I could not get the option to select the input and output sound in the Skype options. It was always PulseAudio. I've read a little bit about this on the net and there are a few complex solutions to this but they were all too painfull for me. 

Choosing the device in PA instead of Skype is complex?   :confused:

> I uninstalled the latest version of Skype and re-installed the older on as mentionned by bvandev and it works perfectly:


Thanks!!

Hey, as long as it's working for you and you're happy with it, that's the bottom line.

---

