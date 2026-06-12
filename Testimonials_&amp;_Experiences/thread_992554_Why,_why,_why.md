---
title: "Why, why, why?"
date: 2008-11-24
forum: Testimonials &amp; Experiences
---

### Post by RockinDolphin on 2008-11-24
Please, someone, *please* tell me *why* Ubuntu seems to always have to be somekind of jigsaw puzzle just to be able to get at least *moderate* internet browsing? (Enter 'enjoyable experience' here...)

I finally got sound to work, only to be stymied when I logged-on to MySpace to see if I could hear some music from people's profiles so I would know that *that* aspect of the browser was working correctly.

Only I get the message "Oops! In order to listen to this, you will need to enable JavaScript and install Adobe Flash 9 or greater." (Now, as I was highlighting this statement to post here, the hidden words "Get Flash Now!" mysteriously appeared where they were hidden until I high-lighted the *non-hidden* text in order to copy/paste it here. What gives?)

I know people are going to laugh, but I have been using Linspire Linux for the past 3-4 years and it did things straight out of the box that Ubuntu wouldn't do, or wouldn't do easily. It became such a thorn in my side to deal with people in the forums who just don't seem to 'get it' to the point where I was warned of my language from a thread because I became irate at the seeming lack of attention to detail concerning Linux when it comes to new users. 

I tried Kubuntu because Linspire is based on KDE, from my understanding, so I thought I should stick with it, but it is entirely un-usable, in my opinion, and needs to go back to the shop.

Ubuntu seems to do better, but there is still this ad-lib/ad-hock way you have to pull your hair out and do crazy command-line acrobatics just to be able to get a modicum of functionality. 

I thought Linspire and Ubuntu teamed together to work on the CNR package client to make downloading updates more simpler. I guess Ubuntu has Synaptic, but I'm still new to this distro and am not conversant with all the different apps. 

If there are certain aspects of programs, like Firefox, that have been gutted of certain functionality for whatever reason, why can't someone put an easily noticeable... *notice* where people can be made aware of this fact and then click a button to install the missing components? It seems that would take the liability, or whatever the case may be, away from Ubuntu and out it on the user, but that option doesn't seem to be there. Instead, one must spend at the very least thirty minutes trying to figure-out what is going-on.

Furthermore, I still see a lack of intuitiveness in Ubuntu's GUI that would aid people in learning the ins-and-outs of this OS.

I'm sorry for this rant, but this is the *exact* reason I gave-up on Ubuntu and went and bought Linspire. Yeah, Linspire had it's issues, too, like I had marginal use of my printer ('Couldn't print graphics...), and I had a perfectly good scanner that has been a paper-weight because it won't function under Linux, but I was otherwise able to use Linspire right out of the box. I was told by a guy at a computer store that Ubuntu was really impressive, now, but it seems I'll have to spend an inordinate amount of time to get it to work before I will get to see this for myself.

My computer, by the way, is an older black-box/'custom' machine with an AMD Duron 1GHz processor, 2Gig of RAM, 320Gig HD, Voyetra Turtle Beach sound card, and ATI Radeon 9200SE (128Meg internal RAM which seems to never get used under Linux. I'll have to go get an NVidia card someday...)

I'm about to try the link for the Flash Player plug-in, now that I know that it's there, but just hidden, and see what happens, unless if I have to do that command-line stuff that I detest and can't for the life of me figure why a person has to seemingly be forced to become a computer programmer/hacker just to be able to do such things that are made simple in Windows. 

We shall see.

Thanks!

~Kenny

---

### Post by stoogiebuncho on 2008-11-24
For the flash issue, Adobe offers a .deb file at their website that will install on your Ubuntu box with a mere double-click.

---

### Post by RockinDolphin on 2008-11-24
Yep. 'Should've guessed it. 'Broken dependencies', or some such, so the plug-in won't install and I'm being told to do command-line stuff that I don't understand. 

I'm starting to get that tingling in my scalp like I want to rip something apart, again...

~Kenny

---

### Post by stoogiebuncho on 2008-11-24
It tells you that you have broken dependencies when you try to install the .deb file?  Or when you're doing something else?

Have you tried installing flash any other way before trying this?

---

### Post by diablo75 on 2008-11-24
Applications>Add/Remove

Change the filter to "All available applcations", and search for "restricted"

Check off Ubuntu Restricted Extras, click Apply.

Viola!

---

### Post by RockinDolphin on 2008-11-24
[COLOR="Red"]"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."[/COLOR]

This is what I get when I try to un-select plug-ins/programs...

I don't know what I've done. I was trying to download some plug-ins to see if they would fix the problem, which they promptly did *not* and now it looks like I may have broken something.

---

### Post by RockinDolphin on 2008-11-24
[COLOR="Red"]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]

This is what I get, now...

Thanks for your help.

~Kenny

---

### Post by diablo75 on 2008-11-24
> **RockinDolphin said:**
> [COLOR="Red"]"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."[/COLOR]



Close whatever synaptic/program installation manager you have open, and then open a terminal window (applications>accessories>terminal).  Paste in:

```
sudo apt-get update  && sudo apt-get install -f
```

The && is used to daisy-chain multiple commands next to each other to be run in sequence, fyi.

> **RockinDolphin said:**
> [COLOR="Red"]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]

This comes up because you are trying to run two package management softwares (likely add/remove and aptitude at the same time).  This is why you want to close add/remove before pasting that text into a terminal.

---

### Post by RockinDolphin on 2008-11-24
I cannot tell that I am running two apps at the same time, and I cannot remember how to get the task manager up so I can see if this is the case and end that process.

---

### Post by RockinDolphin on 2008-11-24
I am wondring if I should just start over and re-install Ubuntu. 'Might be quicker, I don't know...

~Kenny

---

### Post by laffinet on 2008-11-24
> **RockinDolphin said:**
> I am wondring if I should just start over and re-install Ubuntu. 'Might be quicker, I don't know...

~Kenny

No need for that. What windows do you have open currently ?

---

### Post by PoopyTheJ on 2008-11-24
System-Administration-System Monitor will show you running processes. Or if you've closed everything and can't seem to find what's running try CTRL+ALT+BACKSPACE to restart X.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You are using sudo right? Anyways for flash it's "sudo apt-get install flashplugin-nonfree". Most of the things you'll need for quick and simple setup can be found in the Synaptics Package Manager just be sure to enable the Universe and Multiverse repo's and you should be able to get everything very easily. When I performa new install I make sure to get all updates, enable the repos then get wine, flash, sun-java, firestarter (easy firewall) Xine, and oh Deluge, though Deluge I've found is much better to get from the eluge website than the repos as it never works correctly for me from the repos. I can understand your aggravation with the way Ubuntu does things, but I have to say if you can relax, take a deep breath and give it some time to learn the way things work it actually is easier to deal with than windows or any other OS I've used. but it did take me some time to become accustomed to the way it operates and what is required to do things. Give it 30 days at least before you give up and realize it will take a bit of time. I think you'll be well satisfied.

---

### Post by diablo75 on 2008-11-24
Trust me, I don't think you've screwed anything up.  It's even possible that when you tried to run apt-get from the terminal that your update manager was in the middle of checking for updates.  Checking for updates, installing and uninstalling software is and can be handled by more than one program.  Synaptic Package Manager, Update Manager, apt-get (in terminal) and Add/Remove all pretty much do the same thing.  But in order for them to work, no two of these can be running simultaniously.

If I were you, I would close all windows (except for firefox), open a new Terminal window, and re-paste in the code I mentioned in my previous post.  In fact, I've modified it a little to save you more time:

```
sudo apt-get update  && sudo apt-get install -f && sudo apt-get install ubuntu-restricted-extras
```

If the above goes through with no errors, then you should have flash, java and a bunch of other useful multimedia plugin's installed and at your disposal.

---

### Post by pgatrick on 2008-11-24
If you're having trouble installing flash through the package manager or a .deb, you might try just downloading the tar.gz file from adobe, unzip and put libflashplayer.so in /usr/lib/mozilla/plugins /usr/lib/firefox/plugins /usr/lib/iceweasel/plugins (whichever of those you have). Should just work, and no messing with broken dependencies or anything.

---

### Post by PoopyTheJ on 2008-11-24
diablo75 this "sudo apt-get install ubuntu-restricted-extras" gives me flash, java and other plugins? Like Codecs? Seriously? Awesome, wish I had found that little command earlier. ;)

---

### Post by Perfect Storm on 2008-11-24
Also check medibuntu, for googleearth, libdvdcss2, w32codecs etc. if you need such stuff.

[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by ryanhaigh on 2008-11-24
Also if you post the exact error message that you are getting it is more likely that people on the forum will be able to help you out.

Well that will teach me for not pressing the post button for an hour after I write the response.

---

### Post by RockinDolphin on 2008-11-25
Okay,

I re-installed Ubuntu. Before doing anything else, I went to the MySpace page where I know a person had an on-line audio player... (Props to Phuture Primitive!)

[http://www.myspace.com/phutureprimitive](http://www.myspace.com/phutureprimitive) 

I clicked on the invisible hot-link to Adobe and downloaded what I needed. The download and installation went without a hitch...

I then closed FireFox and downloaded the updates it was screaming at me that it had. I re-booted the computer afterward.

I went to 'Sounds' in the Control Panel and selected the device/driver for each instance because I did that before and was able to get sound.

I would get the test sound, but couldn't get the music playing from the MySpace page. I went to a FAQ concerning cound issues and read it. I tried a few things and have discovered this:

[COLOR="Red"] sudo modprobe snd-cs4630
[sudo] password for kenny: 
FATAL: Module snd_cs4630 not found.
 [/COLOR]

So, it seems I am close, but how do I get it to install the driver? I think it's telling me how, but I'd like to double-check with you guys.

Also, thank you to everyone who has tried to help!

~Kenny

---

### Post by RockinDolphin on 2008-11-25
Okay. I tried what the FAQ said to do and it looks like my driver just isn't in the computer... :( It *is* supported as it's a (Voyetra) Turtle Beach-Santa Cruz, driver: CS4630...

So, how do I get it into my 'puter?

---

### Post by diablo75 on 2008-11-25
> **RockinDolphin said:**
> I went to 'Sounds' in the Control Panel and selected the device/driver for each instance because I did that before and was able to get sound.

I would get the test sound, but couldn't get the music playing from the MySpace page. 

What did you change in the Sounds applet in your "Control Panel" (You mean System>Preferences>Sound)?

And you said, "I would get the test sound."  As in just now?  Or before you reinstalled Ubuntu?  Because if your getting test sounds out of your speakers, you probably don't have a driver issue.

---

### Post by jimreynold2nd on 2008-11-25
To the original poster: Read the article in my signature, especially Problem number 1, number 3a, 3b (especially the Lego part), number 7, and the conclusion.

---

### Post by RockinDolphin on 2008-11-25
I was able to get the tone both before I re-installed Ubuntu, and after, but it's saying that my driver isn't loaded... I'm not getting sound from MySpace. I *did* get music off of Amazon from clicking on a button to hear a song-clip (Which it downloaded and played in a separate player, which is rather asinine...) 

It just isn't working right and it looks like the driver isn't even on the version (Ubuntu 8.10) that I downloaded...

~Kenny

---

### Post by spawn. on 2008-11-25
GOOGLE and patience saves lives and time. lol. I can't recall how many times I had to install Ubuntu or Windows Vista/XP. But it gets easier to troubleshoot the more problems you encounter. I had to learn my way around Linux the hard way. But now my friends think I'm some tech support guy, all I do is GOOGLE.

---

### Post by jimreynold2nd on 2008-11-25
> **spawn. said:**
> GOOGLE and patience saves lives and time. lol. I can't recall how many times I had to install Ubuntu or Windows Vista/XP. But it gets easier to troubleshoot the more problems you encounter. I had to learn my way around Linux the hard way. But now my friends think I'm some tech support guy, all I do is GOOGLE.

Love it :guitar:

---

### Post by diablo75 on 2008-11-25
> **RockinDolphin said:**
> I was able to get the tone both before I re-installed Ubuntu, and after, but it's saying that my driver isn't loaded... I'm not getting sound from MySpace. I *did* get music off of Amazon from clicking on a button to hear a song-clip (Which it downloaded and played in a separate player, which is rather asinine...) 

It just isn't working right and it looks like the driver isn't even on the version (Ubuntu 8.10) that I downloaded...

~Kenny

You are not having a driver issue.  You have a sound configuration problem with flash.  If you're able to hear audio from an mp3 clip you downloaded off of Amazon, that means your sound card is working.

What you need to understand is that Ubuntu (or rather, Linux) works with many different sound management systems, the latest being Pulse Audio, and before that others such as ALSA and OSS.

So again, WHAT did you change in System>Preferences>Sounds?  If possible, please open this panel up, press the PrintScreen button to take a screenshot, save it, and attach it to your reply.

---

### Post by RockinDolphin on 2008-11-25
I switched everything from 'Auto Detect' to "Sound Fusion CS46xx CS46xx (OSS), but it isn't working now for MP3's. I get the 'tone' on everything but 'Sound Capture'...

---

### Post by RockinDolphin on 2008-11-25
I ran the hardware tester and it keeps picking up the on-board audio chip and not the Turtle Beach. Kubuntu *was* smart in that it had a way to click which one you preferred, but I don't see where you can do it with Ubuntu...

Also, Alsa Mixer isn't giving me the mixing board GUI...

---

### Post by RockinDolphin on 2008-11-25
> **jimreynold2nd said:**
> To the original poster: Read the article in my signature, especially Problem number 1, number 3a, 3b (especially the Lego part), number 7, and the conclusion.

I'm sorry, I'm not sure I'm understanding what you're directing me to do.

~Kenny

---

### Post by diablo75 on 2008-11-25
1.  Change everything in your Sound settings to Pulse Audio.

2.  Click Applications>Add/Remove

3.  Search for "PulseAudio"

4.  Check off all items with the word "PulseAudio" in the title and then click the Apply button in the bottom right.

5.  Click System>Preferences>PulseAudio Preferences

6.  In PulseAudio Preferences, click on the Simultanious Output tab.

7.  Check off the box that says "Add virtual output device for simultaneous output on all local sound cards"

8.  For good measure, restart the PC completely.

9.  Test your sound completely (play an MP3 file on amazon, check flash again)

---

### Post by RockinDolphin on 2008-11-25
Okay. I think it's fitzed...

I went into the BIOS and disabled the on-board audio chip. At this moment I'm listening to 'Darkness' by Phutureprimitive...

I just fired-up Amarok and listened to that guy tell me that I'm using Amarok Fast Forward, so I can listen to MP3 files, now. Cool!

'Cept I feel like I'm not getting full volume, but I'll try experimenting with different settings and see which works best.

Thanks, All!

~Kenny

Addendum: 'Oleander' by Phutureprimitive sounds awesome through my vibrating headphones! YEAH!

---

### Post by RockinDolphin on 2008-11-25
Ummm...

Nothing from the CD player/CDROM. 

Just when I thought it was all together. At least it's getting there...

~Kenny

---

### Post by RockinDolphin on 2008-11-25
Finally figured-out how to use the Master Volume Control and was able to select an 'input' that worked. I now have CD.

---

