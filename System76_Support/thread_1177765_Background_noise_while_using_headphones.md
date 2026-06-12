---
title: "Background noise while using headphones"
date: 2009-06-03
forum: System76 Support
---

### Post by 982000971 on 2009-06-03
When I use headphones there is a constant static hiss and crackle even if I do not have any audio playing. Even if all volume controls are reduced to 10% or even muted. Sounds increase with activity (scrolling during web browsing, opening applications, etc.) but does not appear through laptop speakers without headphones.

I understand this is common, but is there a way to reduce or eliminate this? Running the latest Ubuntu on a Serval Performance.

---

### Post by thomasaaron on 2009-06-04
Mute anything related to your internal (or front) microphone.

---

### Post by 982000971 on 2009-06-04
Nada. I've experienced muting just about every combination possible. Tried switching sound servers as well. Sounds like I'm listening to the hardware operate :(

---

### Post by thomasaaron on 2009-06-04
I'm still not convinced it's not the internal mic.

Have you tried double-clicking your speaker icon and, in the resulting window, click the preferences button, and making sure all of the checkboxes are selected. 

If not, this may reveal some sliders related to the mic (mic boost, etc...). Mute the sliders under the Recording tab as well.

I've seen feedback through the internal mic many times. This sure sounds like it.

---

### Post by 982000971 on 2009-06-04
Yeah the Preferences thing is exactly what I tried before (made sure EVERYTHING was checked etc.) Is there a way to completely disable the mic? I don't use it anyway (though I would if the built-in webcam would ever work consistently!:shock:)

---

### Post by 982000971 on 2009-06-04
And I just discovered something related to my other thread "Touchpad doesn't work after upgrade" ( [http://ubuntuforums.org/showthread.php?t=1142128](http://ubuntuforums.org/showthread.php?t=1142128) ). Remember how I describe the static as increasing and corresponding to when I scroll with my web browser or open applications etc.? Well when I move my finger over my touchpad there is a similar static hiss which tells me my touchpad is not completely dead or unresponsive even under Ubuntu 9.10. Kind of a side note I guess, but I haven't received much of a follow up after our last email so maybe that will help?

---

### Post by thomasaaron on 2009-06-04
Sorry, I'll get the touchpad testing done tomorrow.
I'll check to see if I get the hissing too, while I'm at it.

Do you have your webcam working on that one under Jaunty?

---

### Post by 982000971 on 2009-06-05
Naw I got the webcam working a few versions ago after running through some tutorial posted in this forum. But subsequent upgrades broke it and I just gave up on it.

---

### Post by ashwat on 2009-06-05
bump. exact same problem.

---

### Post by thomasaaron on 2009-06-05
OK. I duplicated it. Here is the fix (for the touchpad)...

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

We'll get that worked into the driver.

---

### Post by woodbrick on 2009-06-10
Sorry was that last post about fixing the background noise problem? I have had the problem  for a while and have just been too busy to fix it. I am using pulse audio sound server on Intrepid. Bad noise starts up at bootup, ends at shutdown. 

I have followed this [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578") howto to no avail. Any suggestions?

---

### Post by thomasaaron on 2009-06-10
Woodbrick, what System76 model do you have? And are you really still using 8.04?

---

### Post by 982000971 on 2009-07-19
I'd like to reopen these discussions. I start school again in a month and that means hours upon hours spent in the library with my headphones on. I will kill myself if I have to listen to this annoying noise six hours a day!

I'll do whatever you guys want in terms of testing things out. I can record the noise for you with a mic, mess with all the sound settings, I'll do anything! Please help.

---

### Post by BoozeWooz on 2009-07-19
> **982000971 said:**
> I'd like to reopen these discussions. I start school again in a month and that means hours upon hours spent in the library with my headphones on. I will kill myself if I have to listen to this annoying noise six hours a day!

I'll do whatever you guys want in terms of testing things out. I can record the noise for you with a mic, mess with all the sound settings, I'll do anything! Please help.

Hello!

I had the same problem and it was very annoying!
But I found an easy solution: MUTE YOUR MIC.

You can do this with the Sound Mixer (I'm running Xubuntu, idk the name in the normal Ubuntu): just set the microphone to zero.

Or follow the instructions from "**[shaice]("http://forum.eeeuser.com/profile.php?id=31863")**"

> 
open terminal

Ctrl-Alt-T (in easy mode - or select Console from Full DEsktop Mode)

Then run alsamixer with the command

alsamixer

and turn off eMic (external mic) - the mixer is not mouse friendly, use arrows and then Q to exit (or Esc I don't remeber now).
[http://forum.eeeuser.com/viewtopic.php?pid=302942](http://forum.eeeuser.com/viewtopic.php?pid=302942)


Great succes!:popcorn:

---

### Post by 982000971 on 2009-07-21
Thanks, but I've tried that already. It isn't the mic.

---

### Post by thomasaaron on 2009-07-21
Please take screenshots of your sound control panel (the one you get when you double-click your speaker icon). Take shots of each tab and post them here. We'll have a look and see what we can figure out. 

My serval is out for review.

---

### Post by 982000971 on 2009-07-21
Screenshots or xvid capture (zipped), your choice :wink:

---

### Post by thomasaaron on 2009-07-22
OK, not to beat a dead horse here... but you don't have "Microphone" and "Mic Boost" muted.

---

### Post by 982000971 on 2009-07-22
It's not muted in the picture/video because I actually use the mic for Skype (and once we figure this out I'd like to return to the webcam issue, but that can wait).

I can do more pictures/video or you can just just trust me when I say I am 1,000,000% positive that my problem persists even when both "Microphone" and "Mic Boost" are muted.

EDIT: Meh, what the hell, here it is :)

EDIT2: In fact, I can mute every single thing on those first two tabs and still hear it.

---

### Post by thomasaaron on 2009-07-23
1,000,000% was good enough for me. :)

I'm going to have to wait until my Serval gets back to do testing. Hopefully it will be here in a few days.

---

### Post by 982000971 on 2009-07-23
Sounds good.

I've been scouring Google and trying to read up on this. Similar experiences seem to be caused by a bad ground wire (usually associated with either the power outlet or surge protector it is attached to). My problem persist even when not plugged into anything. So I've read it may be due to some bad ground soldering inside the laptop itself? To test this, whether or not the problem is isolated to the 3.5mm jack itself, I went and plugged in to every audio device I could get my hands on and sure enough I can hear the same fuzzy sound with just about everything (it is just WAY easier to hear while using headphones, which is what I use most often).

So I don't know if that means the jack itself is bad or if this is inherent in all Servals? Maybe the jack is just too close to components inside the case and there is interference? I'll wait for you to test some tings out on the Serval obviously, but worse case scenario do you think something like a USB to 3.5mm is plausible? [http://www.vpi.us/usb-audio.html](http://www.vpi.us/usb-audio.html)

---

### Post by thomasaaron on 2009-07-23
I'm pretty sure a USB device would not have the same problem.

---

### Post by jvik on 2009-07-23
I have the same problem. Well. For me it's a nettop. Acer Revolution. It's constantly (or well. Like every other minute) making these annoying scratching noises. Even if i mute the master channel it goes on. I have no clue what to  do. Please help me! :)

---

### Post by 982000971 on 2009-07-24
Hey jvik, why don't you be the guinea pig and buy that USB Adapter :D

---

### Post by 982000971 on 2009-07-29
Bumpity-bump-bump-bump!

Serval back yet?

---

### Post by thomasaaron on 2009-07-30
Just received our Serval back yesterday evening.

I've attached a tar.gz file with screenshots of how mine is set up. No hiss.

---

### Post by 982000971 on 2009-07-30
Thanks for checking. I mimicked all the settings from your screenshots, no dice. Still hear it. Am I to assume this means some sort of hardware defect.

If yes, the USB Audio solution I am having difficulty with. I purchased a "Syba SD-CM-UAUD USB Stereo Audio Adapter, C-Media Chipset, RoHS" (seen here [http://www.amazon.com/gp/product/B001MSS6CS/](http://www.amazon.com/gp/product/B001MSS6CS/) ). It is supposed to be plug and play (even for Linux) but it isn't. Not sure where to go in terms of settings to get it going...

---

### Post by thomasaaron on 2009-07-30
What are you listening to, exactly?

Do you get the background noise when you go to System > Prefs > Sound and click the "Test" button?

What is the output of...
cat /proc/asound/version
...?

I think you have to set the set the various dropdowns in System > Prefs > Sound to your USB device. If that doesn't work, I can get a USB headset in here to test with in a day or two.

---

### Post by 982000971 on 2009-07-30
What are you listening to, exactly?
>> FLAC files via Rythmbox and YouTube videos via Firefox (with no third party plugins to handle flash video player). To clarify, the sound continues to come out of the laptop speakers.

Do you get the background noise when you go to System > Prefs > Sound and click the "Test" button?
>> I have the exact settings as the picture you sent last post. So on autodetect all the tests work on my laptop speakers. If I use the dropdown to go through my other options (see attached video - can't print screen while using dropdown menu?) I can hear the test on my second selection, you will see an error on the first selection and this occurs for the other two dropdowns as well. So on the selection that I CAN hear the test I can also get audio through my headphones (WITHOUT the crackle noise!, but ONLY through Rythmbox, YouTube still emits through front laptop speakers?

What is the output of...
cat /proc/asound/version
...?
>> "Advanced Linux Sound Architecture Driver Version 1.0.18rc3."


So a few things. One, am I going to have to manually mute my Master volume then chance my sound playback device under Sound preferences for three separate dropdown menus EVERY single time I want to use my headphones? And repeat the process to go back to laptop speakers? And second, this essentially disables my Keyboard Shortcuts to control the volume since they are set to control Master on the "autodetect" (whatever that was). And we still don't have the flash video sound going yet? :P

Thanks, I await your reply. Please take solace in the fact that the support I have received in this forum will make me a repeat customer for life.

---

### Post by Eldera on 2009-07-31
Hi, 982000971.

I started learning Ubuntu by buying a Pangolin and have been reading this forum as a self-teaching exercise. 

I have read all your posts and feel sorry that you are having such a problem with noise. 

One thing I am curious about: you haven't mentioned what kinds or what brands of ear phones you have tried. I am guessing that being a student you could borrow phones from some of your buddies just to find out if they made a difference.

Good luck to you and TA in working this out.

Eldera

---

### Post by thomasaaron on 2009-07-31
You know, I was just looking through all of your previous posts on this thread to try and ferret out some golden clue when I found this post from you...

> Naw I got the webcam working a few versions ago after running through some tutorial posted in this forum. But subsequent upgrades broke it and I just gave up on it.

I've been working on the assumption that you are using a current SerP6. But the "versions" comment makes me think you are using something earlier. If so, I've been barking up the wrong tree. What model number does your System76 driver report?

---

### Post by 982000971 on 2009-07-31
Nope I'm old school. Serp1.

As far as headphones go Eldera, I've tried three different ones plus two different speaker systems.

---

### Post by thomasaaron on 2009-07-31
Back to the drawing board.

---

### Post by 982000971 on 2009-07-31
Ouch.

Added info to signature, let me know if there is anything else I can do...

---

### Post by 982000971 on 2009-08-03
So I'm wondering, now that we are barking up the right tree, does it sound like there is any hope?

I've been messing with the USB audio "solution" and it is kind of a pain. From what I've been able to see I have to ```
sudo asoundconf set-default-card default
``` every time I want to use the USB (then restart any programs that were open for it to take effect. Then ```
sudo asoundconf set-default-card Intel
``` to go back (Intel being laptop speakers, default being the USB device).

So that's not very convenient, and worse yet my shortcuts to control volume are rendered useless once switched to default. I can create two separate launchers to speed up this process but is there a way to make a single launcher to switch between the two as opposed to two launchers (one for Intel, one for default?) And further, could said script also change keyboard shortcuts from controlling Master on the Intel device to controlling Speaker on the default device?

If that could be accomplished, and if it is any less difficult than probing the original problem, then I would be content with that as a solution.

:popcorn:

---

### Post by thomasaaron on 2009-08-04
Well, I'm getting the same problem on the SerP1. So, at least we know it's an ALSA thing and not a hardware thing.

You could write a BASH script that detected which device was being used and then switched to the other one.

But do you not have the option in System > Prefs > Sound (in the pulldowns) to set the sound device to your USB headphones?

The way it's worked in our shop testing (albeit most likely not with the same model headphones you're using), there you set your sound device to the USB headphones and then highlight the channel that you want your sound keys to control in the "Default Mixer Tracks" text box at the bottom of the Preferences window.

---

### Post by 982000971 on 2009-08-04
Yes, that does do the trick. However, start to finish this takes a full 20 seconds -I timed it- so it's a total pain in the ***. Not ideal.

So does determining it's ALSA help us at all? Or am I S.O.L.?

---

### Post by 982000971 on 2009-08-05
P.S. it feels hit-or-miss getting USB audio from firefox. As far as I can tell all sounds will go through headphones, until I fire up a YouTube video and it blasts through the laptop speakers. I'm restarting firefox each time, so I'm not sure why...

EDIT: Audio from Mplayer = headphones. Audio from VLC or Mplayer (Xine) = laptop speakers.

---

### Post by 982000971 on 2009-08-11
*Bump*

---

### Post by thomasaaron on 2009-08-11
Except for one or two days, I'll be out of the office for two weeks. I'm not really sure what I can do on this one. It seems like it might be an ALSA regression. But I'll do some more testing when I return.

---

### Post by 982000971 on 2009-08-14
Okay, well if you think it is even possible to figure out the ALSA thing with the speaker jack that'd be cool. I'll bump this again in another 2 weeks just in case.

In the meantime I think I'll post my issues with the USB adapter elsewhere because it doesn't seem to work at all. If I can get that figured out, I'll let ya know.

---

### Post by 982000971 on 2009-08-15
Resolved USB Adapter issues with this thread [http://ubuntuforums.org/showthread.php?p=7789508](http://ubuntuforums.org/showthread.php?p=7789508)

So don't bother with the background noise issue unless you are feeling especially ambitious ;)

(And not to burst your vacation but in a few weeks I'm going to reopen the Serval webcam thread since it has yet to be fully resolved, sorry)

---

