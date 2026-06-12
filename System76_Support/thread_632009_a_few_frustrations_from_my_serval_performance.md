---
title: "a few frustrations from my serval performance"
date: 2007-12-05
forum: System76 Support
---

### Post by Squish on 2007-12-05
when i got my serval it was mostly fine, minus a bug here and there. Eventually it started getting iffy after a few days. My suspicions were that it was caused by compiz, my soundcard (trying to get record to work), and my basic gui.
It came to a point when i could not for the love of me log into my account regularly and access the internet. the only failsafe that worked was the rescue system as root, and the failsafe terminal.

I tried all I could to use the system 76 driver to restore my system, the first time it worked.
I was able to log in. I rebooted, and the problem appeared again. for the life of me i couldnt diagnose the problems i was experiencing, so I backed up my data and re-installed ubuntu off a fresh 3dbit gutsy disk.
Yes its working now, and i even got the system76 drivers installed, however i have no idea what they actually do, if anything. Anyways, i cannot get my soundcard working and its being a hassle.

Is there a quick fix?

Otherwise, could you offer a suggestion for a differant soundcard that I could use instead? To be honest, i want something better anyways, but i dont know much about laptop soundcards. I heard x-fi drivers came out, are they any good, can i get a x-fi into my laptop?

my card is the ALC268
Judging by all the trrouble i have read about this card, I would suggest you get something else. 
Nothing seems to work for me...

---

### Post by thomasaaron on 2007-12-05
First, yes the System 76 driver is important to your computer. It configures the sound as well as some other things.

Second, your sound card is integrated. You can't swap it out. That said, the 268 is a good card. A lot of people have had difficulty getting it configured, but ALSA has great support for it if you know where to look for answers.

However, the reason your sound does not work after re-installing and running the driver is because of either one of two things:

1. You used Update Manager to bring your system up to date after you installed Gutsy. Update Manager has a bug that hoses gstreamer pretty badly. 

or

2. You do not have it configured correctly. 

If you provide more info on what you are experiencing exactly (error messages, etc...) we can more accurately help you get it up and running. Particularly, does your speaker icon have a little red slash through it? Or if you go to System > Preferences > Sound and hit the first test button, do you get an error message about gstreamer? If either of these is the case, email me at support, and I'll send you a debian file that will fix your sound perfectly.

If these are not the case, let me know how you have your sound controls set up (i.e. how do you have it set up under each tab when you double-click the speaker icon), and we'll get you up and running.

---

### Post by Squish on 2007-12-05
I am using the newest serval performance - the piano black one
Gutsy 7.10
No I didnt partition it with the LVM - I wouldnt know how


Basically I went to sound (on this install), pressed test, and got this
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

Thing is, I cant even detect any devices even after installing a ton of differant alsa drivers, etc...

I did try one thing, a solution where you swap a .ko from one place to another - I used this command (which probably wasnt smart considering I didnt back up the one replacing.)

```
 sudo tar xvjf alsa-driver-hg20071205.tar.bz2
cd alsa-driver-hg20071205/
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
sudo mv kernel/sound/pci/hda/snd-hda-intel.ko ubuntu/media/snd-hda-intel/snd-hda-intel.ko 

```
hmmm, maybe I should have made a copy instead - ill try that

Anyways, I dont mind doing one more fresh install - but i do believe I did do the install of the drivers before the system update. I have gotten the gstreamer errors before like you said, which left me a bit confused because I wouldnt know what gstreamer would have to do with anything.

Anyways
Is it at all possible to use a 64 bit ubuntu, or is it ill advised.
The only reason i ask is becuase I have 4 gigs (which really only turns out to be 3.1 gigs), and I heard having a 64 bit operating system helps with ram management over 2 gigs.
Really, I am actually at a loss of what it really does...

---

### Post by thomasaaron on 2007-12-05
OK. Basically what happened is that Update Manager hosed gstreamer.
You have two options:

1. The new System 76 driver is coming by Friday. This will fix your sound again, as it addresses this very problem.

2. You can email me at support, and I'll point you to a .deb file that we created to fix this problem. All you have to do is download it and install it and you'll be good to go.

Best,
Tom

---

### Post by Squish on 2007-12-05
you guys are faaaantastic.
I guess Ill wait till friday then.

---

### Post by gobbles414 on 2007-12-06
**Hi Squish,**

I am anxious to read your impressions of the Serval. What do you like about it? What do you not like about it? What configuration did you choose?

**Hi Tom,**

I have been helping my friend to switch to Linux and she has chosen to go with either the Gazelle, Pangolin, or Serval. You and I chatted on the phone for a few minutes yesterday about this. She wants to add audio to presentations, so it is critical that her audio work consistently. Also, she is new to Linux and BTO laptops, so I really want for her to have a good first impression. Here are some questions about the Gazelle, Pangolin, and Serval, and Ubuntu Gusty:

(1) Could you please provide more information about the Gusty update bug, such as a Launchpad entry? Are there any workarounds to that bug currently, such as Synaptic or apt-get? I have not run into any update problems with my Asus G1 and Gusty. (2) Do all three laptops require a driver CD? Everything but the webcam on my Asus G1 works perfectly with the drivers provided by Ubuntu. (3) Do all three have dual-layer DVD burners? The product pages are unclear about that. (4) Are all three laptops Santa Rosa...? I assume yes because they can accommodate 4GB of RAM...

Thank you both!

---

### Post by thomasaaron on 2007-12-06
> (1) Could you please provide more information about the Gusty update bug, such as a Launchpad entry? Are there any workarounds to that bug currently, such as Synaptic or apt-get? I have not run into any update problems with my Asus G1 and Gusty. 

I don't have any more info on the bug at this time. In fact, I don't completely understand it. We've put a fix in our system 76 driver that should work around the bug. When upgrading to Gutsy or freshly installing it, I've found it best to update the system via:
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

> (2) Do all three laptops require a driver CD? Everything but the webcam on my Asus G1 works perfectly with the drivers provided by Ubuntu. 
The System 76 Driver is a python app that applies model-specific patches.
It is necessary on all three computers. It comes installed on the system and can be downloaded if you want to restore the system.

> (3) Do all three have dual-layer DVD burners? The product pages are unclear about that. 

The drives are not dual layer.

> (4) Are all three laptops Santa Rosa...? I assume yes because they can accommodate 4GB of RAM...

They are all Santa Rosa.

---

### Post by gobbles414 on 2007-12-06
Tom,

Wow... thank you for providing such a rapid response! Score 1000 bonus points for awesome customer service! I now understand the update bug and driver situations.

Would it be at all possible for you to fulfill a special request for a dual-layer drive in one of your laptops? Once my friend gets comfortable with Ubuntu Linux, she may want to start authoring DVDs on behalf of an organization in her community. It is possible that these DVDs might not fit on a single layer DVD. I realize that you could not provide full technical support for such a drive. But I think that my friend will want dual-layer, especially for a laptop as expensive as the Serval.

Thanks again for your time.

---

### Post by thomasaaron on 2007-12-06
I wish we could, but right now we're limited to the configuration options on the website.

Hope that is not a -750 points. :)

---

### Post by Squish on 2007-12-07
perhaps DYI instructions?


The laptop hardware as of this point is superb. My only critique is that the screen isnt swivel, but that doesnt matter to me anyways - a luxury of some sorts. I think piano black isnt my style (purely an aestetics thing) so I wish I went for gazelle, which looks sharper than a mac. 

The software I do have critique, as per a few of the following notices

1: 64 bit operating system please - this actually is not really a bad thing, considering most apps are 32, minus a few - xine... plus software that isnt 64 bit is essential, such as wine or java. However, if one hopes to move to x-fi, their drivers are only 64 bit... x-fi...
2: The auto flash install is broken, so you have to compile it from source, which is fairly easy if you can nav a command line.
3: Partitioned with a wierd extended format. I read that this is neccessary for the sleep to work, but it was a hassle trying to back things up for awhile because my desktop crashed, and i tried using gparted in knoppix to save my stuff, but it couldnt detect it.
4: The system 76 driver i think needs a more thorough explanation to what it actually does... it is very vague, and I cant help but wonder if I am installing something on top of another.
5: The sound is good, but it hardly takes advantage of my 200 dollar headphones. But thats linux audio drivers for you...
6: I wish there was something that would let me record from my mic, or my vid camera - i dont think the drivers let you. Some documentation for that would be nice.
7: Perhaps a guide to how to actually bring back my computer to a system 76 clean install.


Most of my issues concern the Ubuntu operating system, and any laptop I am sure would attribute to this.
Anyways, my laptops up on craigs list at a highway robbery price of 2750, if someone happens to buy it, I am getting a gazelle!

---

### Post by thomasaaron on 2007-12-07
> 1: 64 bit operating system please - this actually is not really a bad thing, considering most apps are 32, minus a few - xine... plus software that isnt 64 bit is essential, such as wine or java. However, if one hopes to move to x-fi, their drivers are only 64 bit... x-fi...

We're looking into it, but it could be a while before we offer 64-bit. Lot's of R&D to do before being able to actually ship it with our products. No ETA.

> 
2: The auto flash install is broken, so you have to compile it from source, which is fairly easy if you can nav a command line.

What are you referring to (auto flash install)?

> 3: Partitioned with a wierd extended format. I read that this is neccessary for the sleep to work, but it was a hassle trying to back things up for awhile because my desktop crashed, and i tried using gparted in knoppix to save my stuff, but it couldnt detect it.

It uses LVM formatting. Gparted doesn't support LVM.

>  4: The system 76 driver i think needs a more thorough explanation to what it actually does... it is very vague, and I cant help but wonder if I am installing something on top of another.

Ask and ye shall receive:
[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)
You should check out knowledge76.com. It has a lot of information on it.

> 5: The sound is good, but it hardly takes advantage of my 200 dollar headphones. But thats linux audio drivers for you...

ALSA. You've gotta love it. You've gotta hate it.

> 6: I wish there was something that would let me record from my mic, or my vid camera - i dont think the drivers let you. Some documentation for that would be nice.

You can record from your mic.
You can download your video camera too. There are a number of Linux apps for doing this. Carl was telling me about one he was messing with the other day. I'll ask him what the name was. But some other customers may be able to make recommendations.

> 7: Perhaps a guide to how to actually bring back my computer to a system 76 clean install.

Once again, ask and ye shall receive:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by gobbles414 on 2007-12-07
Tom and Squish,

Thank you both for your input. I have learned a lot. As I have told my friend, a laptop such as the Serval really should have the options for a dual-layer burner, 802.11n networking (draft obviously), and a higher resolution screen. Personally, I would rather wait until the N's specs have been finalized before switching from 802.11g.  And I know because of a purchase I made recently from another BTO website that the higher resolution screens are very difficult for laptop manufactures to obtain right now. Since my friend wants her new laptop ASAP, she would have to order the lower resolution screen anyway.

Any idea what System76's reasoning is regarding the single-layer versus dual-layer DVD burner? I am under the impression that dual-layer burners have gotten rather inexpensive. Is it a Linux-compatibility issue? Don't worry Tom, it is only minus 100 bonus points for the single-layer burner. :) I consulted with my friend last night and she doesn't seem to think that any of her DVDs will be longer than 2 hours. But just for my information -- I am considering purchasing from you when my current laptop dies -- iis there a particular brand/model of dual-layer burner that will be compatible with the current System76 drivers?

---

### Post by thomasaaron on 2007-12-07
I'm sure there is a compatible dual-layer. I'll  ask R&D about it. We had dual-layer on a previous line-up of machines.

I think the reason we don't have them right now is a combination of procurement and demand. I imagine they will be available again at some point in the fairly near future. But I just don't have an ETA on it.

---

### Post by gobbles414 on 2007-12-07
Tom,

Thanks as always for your quick and informative reply. You've re-earned those 100 bonus points. :lolflag: I'd really appreciate learning about the dual-layer compatibility once you hear back from R&D.

---

### Post by Squish on 2007-12-07
> **thomasaaron said:**
> We're looking into it, but it could be a while before we offer 64-bit. Lot's of R&D to do before being able to actually ship it with our products. No ETA.



What are you referring to (auto flash install)?



It uses LVM formatting. Gparted doesn't support LVM.



Ask and ye shall receive:
[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)
You should check out knowledge76.com. It has a lot of information on it.



ALSA. You've gotta love it. You've gotta hate it.



You can record from your mic.
You can download your video camera too. There are a number of Linux apps for doing this. Carl was telling me about one he was messing with the other day. I'll ask him what the name was. But some other customers may be able to make recommendations.



Once again, ask and ye shall receive:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

Flash Installer:
Enter a flash site - A bar comes down "Additional plugins are required to display the plugins on this page" - Click button to the right "Install Missing Plugins" - "Please wait while Plugin Finder Service 2 finds blah blah blah" - 2 options: Gnash, Flash - Click flash and you will either get these:
1: IF ITS ALREADY INSTALLED: "Package 'flashplugin-nonfree' is already installed" (Then why did it not work?) 
2: IF IT IS NOT ACTUALLY INSTALLED: Goes through the motions of installation, and says that changes were successfully applied. If you look at the terminal though, it distinctly says it was not installed. Now my computer though thinks it is... The same thing happens if you do it from add remove

If I install it from source, as soon as I get to the enter a valin directory for instal, /usr/lib/mozilla WILL NOT WORK DESPITE IT SAYING IT DOES. It makes the whooooole situation hopeless.

The mic is a common problem I have had with ubuntu in the past - nothing detects or captures it properly. I tried video with ekiga, but it gave me some error message. I gave up pretty quickly.

hey, A module update... maybe this will fix my flash...

Well, talk to you later

---

### Post by gobbles414 on 2007-12-08
Squish,

Regarding your mic problem: On a normal Ubuntu system, you can right click on the speaker icon and select *open volume control*. You should then see a bunch of volume sliders and some tabs. Believe it or not, there are actually lots more sliders to be had if you select *edit => preferences*. Experiment with the different tabs and sliders until you find an option that works on your system. You can also use the *file* menu to switch to-and-from Alsa to OSS.

I am sure that Tom can advise you better than I can regarding your Flash issue on System76 hardware. But a few of things to try/remember: (1) installing the *ubuntu-restricted-extras* using the command line or Synaptic will install lots of codecs, including Flash. (2) According to [a page about Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash") at the Ubuntu Community Documentation website, there is currently a bug in the Flash installer. Is this the bug the Tom was describing to us earlier? NOTE: This bug was caused by Adobe, not Ubuntu Linux or System76. (3) The current workaround to the Flash bug is to enable *proposed updates* in *system => administration => software sources*.

Does any of this help you?

---

### Post by Squish on 2007-12-08
None of that helps me, although I do appreciate it.

I have never actually had my sound record working well on ubuntu - only on suse believe it or not, was I ever able to get my record function to work. 
Sound is such a fickle thing....

Adobe is being the biggest pain I have ever faced in awhile, because even when I do get it installed, firefox will not use it. When I use it on swiftweasel, or another mozilla, its 2 white bars in a grey box giving me weird instances.

And I still cannot detect sound devices - and I just did another fresh install, without updating, and bringing the computer back to factory settings. Funny thing is, when I restored to my original settings, the sound wouldnt detect any devices at all.

anyways, whens that deb you spoke of coming out, you said friday, but its not here. This is slightly embarrassing not being able to get my computer to work nicely...

Huh... sorry, I am not being an angry costomer, and by no means do I blame system76. Ubuntu is a great operating system, but it still needs to come some way imo.

---

### Post by thomasaaron on 2007-12-10
Hi, Squish.

Regarding Flash, see the instructions on this thread:
[http://ubuntuforums.org/showthread.php?t=634442](http://ubuntuforums.org/showthread.php?t=634442)

Regarding sound, send me an email at support(at)system76(dot)com and I'll send you the latest System 76 driver, which will bring your alsa to where it needs to be.
Then it will just be a matter of setting up your volume controls correctly.

---

### Post by Squish on 2007-12-10
I actually did end up solving flash in my own method

Quite easy actually after I did it this way

I got automatix to install swiftweasel, and then I went to a flash site, and used the swiftweasels plugin finder to find and install flash

worked without a hitch... Funny how that works eh???

---

### Post by gobbles414 on 2007-12-10
Hi Squish,

Automatix has a reputation -- deserved or not -- for creating more problems than it solves. Did you have Automatix installed before your problems began? While I have used Automatix in the past, it has been quite awhile since I have had to resort to using such a program. The Synaptic Package Manager has gotten really good.

---

### Post by Squish on 2007-12-10
Im actually quite impressed with it - it wasnt what was causing my problems if that was what you were wondering, not by a long shot.

I didnt have it installed, until very recently, but it was nice because I now have google earth - to which I wish there was actually a deb folder - It clogs up my home folder, and I cant hide it or links get broken - anyways, no problems so far...

But who knows, I have eaten my words before:popcorn:

---

### Post by gobbles414 on 2007-12-10
Squish,

By deb folder, do you mean a normal folder? The .deb extension is sort of like a .exe file in Windows, but just for installing programs. I think that Google Earth has a hidden folder in your home directory. There is an option to enable hidden files in the view menu.

---

### Post by gobbles414 on 2007-12-10
Tom,

Any news from your R&D department yet about dual-layer DVD burner compatibility? Thanks as always.

---

### Post by Squish on 2007-12-10
Sound works, but I cant get record to work.


This laptop does have built in microphones right, I see 2 above the screen right?

Are these recognized as front mic? Should I check alsa mixer again??

---

### Post by Squish on 2007-12-10
its working, I sudo'd the alsamixer, and changed the input to front mic

---

### Post by gobbles414 on 2007-12-10
Squish,

Strange that you would have to *sudo* the mixer! Oh well, what ever works... :lolflag:

---

### Post by Squish on 2007-12-11
seldom second thought of sorts

heck, sometime I find myself sudo'ing to a new directory, as in

sudo cd /home
Anyways, the mic slightly sucks as far as it goes for quality, is that a driver thing, or a hardware thing?

---

### Post by thomasaaron on 2007-12-11
It is an alsa thing.

Tweaking it usually requires fine tuning the "Digital" slider. Also, the new System 76 driver might help some. It re-does alsa.

---

### Post by gobbles414 on 2007-12-12
Hi Tom,

I know that I am not yet an official System76 customer. But I would really like to know what your R&D people have to say about the dual-layer DVD burner. Also a new question... What functionality could my friend expect to lose on her Serval if she choses not to install the System76 drivers? Isn't most of the hardware on the Serval already supported in Ubuntu 7.10?

---

### Post by thomasaaron on 2007-12-12
OK. I'm an idiot. We didn't have them specified on our website as dual layer, so I 
A**-U-ME-D that they were not dual layer.

Turns out they are.

Here are the specs for the drives on the Gazelle, Pangolin and Serval.
DVDRW Multi (8x DVD+/-R, 4x DVD+/-R DL, 8x DVD+RW, 6x DVD-RW, 5x DVD-RAM)

I've got to check on the Darter.

---

