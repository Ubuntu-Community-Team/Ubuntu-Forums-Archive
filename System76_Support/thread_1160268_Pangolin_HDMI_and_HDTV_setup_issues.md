---
title: "Pangolin HDMI and HDTV setup issues"
date: 2009-05-15
forum: System76 Support
---

### Post by Sea Lint on 2009-05-15
I have  pangolin running 9.04. I have been unable to get my hdtv to display my desktop. Here's what i have tried:

Nvidia Server X Config, detect displays = samsung hdtv detected; configured as twin view.

Tried pressing Fn F7 to switch to display = no joy.

Noted someone else having to save to x conf file, tried to do this, but got an error message saying  'Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

This same person mentioned disabling default screen and retrying = no joy.

I also tried to dowload the new system 76 drivers and it says that the utitlity only suports up to 8.10... Is this correct?

I am still kind of a newb to Ubuntu. Thanks for your help!

---

### Post by thomasaaron on 2009-05-15
> Noted someone else having to save to x conf file, tried to do this, but got an error message saying 'Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

That's because you must run nvidia-settings as root. So open a terminal and then run...

sudo nvidia-settings

> I also tried to dowload the new system 76 drivers and it says that the utitlity only suports up to 8.10... Is this correct?

You need to download the most recent version of the driver.

> The System76 Driver comes installed on your system and is located in your menu at System > Administration > System76 Driver. Any updates to the System76 Driver will be detected by Update Manager. 

If you have performed a fresh Ubuntu installation, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update


I got your voicemail, but haven't been able to test yet. If someone else can provide some instructions, that will be great. Otherwise, I'll post back here a little later today with instructions.

---

### Post by Lee_Machine on 2009-05-15
Type sudo nvidia-settings

to be able to change your X-config

Have you tried the Clone Display option?

Lastly make sure you are Clicking Apply to save your settings.


Does this help?

---

### Post by thomasaaron on 2009-05-15
Yeah, I checked that on my HDMI monitor. It looks like all is working well, but I never get a picture on the monitor.

I'll check it's menu settings to make sure it doesn't have some sleep mode enabled.

---

### Post by thomasaaron on 2009-05-15
D'oh! There is a bloody toggle switch on this monitor that goes from VGA > DVI > HDMI. Once I put it on HDMI, everything worked as expected. So, Lee_Machine's instructions should work perfectly.

---

### Post by Sea Lint on 2009-05-16
> **Lee_Machine said:**
> Type sudo nvidia-settings

to be able to change your X-config

Have you tried the Clone Display option?

Lastly make sure you are Clicking Apply to save your settings.


Does this help?

I can now save the xconfig, but i am still unable to pull the screen up on the TV.

Is the clone display option your talking about under the position drop down menu?
I tried this but it didn't want to save this selection. Always came back as absolute or right of. tried saving to xconfig and restarting x (I assume this means closing the window and opening it up again via terminal) and "apply"

Still not having any luck. I wonder if it has something to do with 1080i vs 1080p?

It also says in a black box with a triagle/ruler cannot set config settings for crtc 321 when i switch to the other screen (pressing FnF7).

Any thoughts? Again, i really appreciate your time! Thanks!

---

### Post by thomasaaron on 2009-05-16
I don't think you have to push the Fn-F7. You should be able to do it all through...

sudo nvidia-settings

The "clone" setting is in the position drop-down. There is another setting there that (I don't have an nvidia machine at home with me right now) that says Twin View. You should use that as well.

If you are detecting the TV, but not able to pull up a picture on it, check the TV's buttons and/or menu settings. You may have to specify that it gets its image from the hdmi port.

---

### Post by Sea Lint on 2009-05-19
I talked with one of my buddies and he seems to think that it may be because my hdtv is a CRT 1080i and not a LCD hdtv. He says CRTs don't do per pixel rendering that the LCDs do, so the TV may not be able to display the picture. Does this make sense to anyone, and can someone confirm/deny this theory?  Thanks!!!

---

### Post by thomasaaron on 2009-05-20
CRT's can be problematic...
[http://ubuntuforums.org/showthread.php?t=483285](http://ubuntuforums.org/showthread.php?t=483285)
...but, typically, you can get *some* type of output.

You could try manually configuring your xorg.conf file. Make sure you save a back-up of your old one in case you have to revert back to it (and you probably will).

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If it doesn't work, you can revert with...

> sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo reboot -h now

Here is an example of how your CRT would fit into the file...
[https://answers.launchpad.net/ubuntu/+question/34525](https://answers.launchpad.net/ubuntu/+question/34525)

---

### Post by miniyak on 2009-05-27
im having a similar issue, i've got the external screen on. but there is all ways an issues in the form of one of the following-

 -using the correct resolution for the external
 -unresponsive input: mouse gets stuck on one screen apps open on the other or just stops working all together...
 -changes resolution on laptop

what i'm looking for is the external to act like a second monitor (using its own resolution) that i can move my mouse to and put separate applications on (separate X screen right?)

Unfortunately the nvidia settings app has proven to be a little confusing to me... or may be just misleading. Is there a good reference that im missing out on anyone knows of that would help me out?

Is this how the the graphics(UI) are supposed to act? if so i feel bad for any newcomers buying from s76, i have feeling they would just see it as broken, :( when it really just needs to be tweaked correctly

---

### Post by thomasaaron on 2009-05-28
miniyak,

When each monitor is of a different resolution on a spanned desktop set-up, the xserver calculates a *virtual* resolution large enough to contain *both* monitors. That is why you don't get the proper resolution on one of the monitors.

I've not had much luck either with the separate x screens. That's not a System76 thing. It is more a limitation of the xserver/nVidia.

If anyone has had better luck with it, though, I'd sure love to hear about it too.

---

### Post by miniyak on 2009-05-28
really? hmm cloning is fairly useless when your working with 720p display.(coming from 1680*1050) If thats the way its supposed to work i guess it works fine... ill have access to a 1080p display tomorrow, so maybe that will make me more happy bout the whole situation.

Originally I had assumed out of the box functionality for these sorts of things went along with getting the system pre-installed, but as always assume seems to stand for as$(of)u&me and i ended up paying 400 extra dollars and more then a few hours of my time.

 i am happy with s76 in general in regards to service and product build quality, but if i had known of some of these issues at the time of purchase my buying decision would been different. Maybe i would have got the gazelle or darter (if eSata gives me a hard time i going to say hp refurb from ubid would have been worth it...) , however with the pangolin the screen upgrade is amazing and i am pleasantly surprised with how light it is

sorry, off topic... i'll write a review when i get the chance

I may have just asked this(sorry), but if anyone has good reference to tweaking the nvidia settings or just setting up dual monitors in general please post link. At one point ill be willing to invest the extra time to make this work

---

### Post by thomasaaron on 2009-05-29
> Originally I had assumed out of the box functionality for these sorts of things went along with getting the system pre-installed, but as always assume seems to stand for as$(of)u&me and i ended up paying 400 extra dollars and more then a few hours of my time.

I do understand what you are saying, but it functions exactly like it is supposed to out of the box. This is essentially the state of development for desktop spanning in Ubuntu.

I too can think of ways it could be done better. And, in fact, it is much better now than it was a year ago. I imagine it will continue to improve and become more competitive with proprietary operating systems. However, we do not add functionality to Ubuntu (after all, we're not Ubuntu developers). But we do strive to make Ubuntu work on our machines.

---

### Post by miniyak on 2009-05-29
ok... i just tested the pangolin out on a LG 1080p. 

heres what i expected to happen- cloned 1650*1050 via hdmi would show up crisp yet not fix to screen. in other words my laptop screen with in the space of  a 1080p display

heres what actually happened- on the external display my cloned laptop screen was still larger then the display size (just enough to hide the panels) and the quality was distorted.

i know the quality of this monitor is better then what i saw because i have couple other sources to compare to, both performing better then the pangolin. One is unsurprisingly the PS3, the other however is my old desktop.... a Dell Dimension 2350 using a p4 2.2gz, 512ram, cheap intel graphics, running 32bit hardy, via a VGA cable!?... granted this was not full screen(an inch wide black bar on right side) it was very good quality though, plus i could access the top panel... Its my understanding that TV manufactures place limits on full vga resolution to encourage HDMI adoption. Uninhibited by this nonsense, im sure every thing would have displayed properly. With a 7 year old economy dell deal!

with that understood, im going to say that the hdmi port on the pangolin is pretty much useless until the software(gui for setting up X screens and changing resolutions) and what seems like poor driver performance gets worked out.

Out of curiosity im going to try with a vga cable instead and see if i get better results

Another thought occured to me, is audio over hdmi possible with the pangolin?

---

### Post by miniyak on 2009-05-29
wow on the 1080p LG lcd the vga worked great compared to the hdmi . fit the screen even. all though i have a feeling that the dell was doing the native resolution per square inch however.(if that makes any sense) So, i would still say the dell looked better. LCDs look bad at anything other then their native resolution IMHO. plasmas and dlps seem to fair better with that sort of thing.

i also just tried with VGA and HDMI on 50'LG 720p plasma. Both failed to display

---

### Post by thomasaaron on 2009-05-29
HDMI Audio out is still problematic in Jaunty. It does not work yet.

---

### Post by silvertuna on 2009-08-11
thomasaaron,

is there a fix coming? 

is this a issue that System76 can address by updating the Alsa driver?

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1367781.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1367781.html)

[http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html](http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html)

Pan4 64bit Jaunty nVidia180 Alsa 0.9.14

---

### Post by thomasaaron on 2009-08-11
I think it is an ALSA regression. Lee_Machine had it working pre-Jaunty. But I'm out of the office for a couple of weeks, so I won't be able to test until I return.

Have you tried going to Switches in your volume control and enabling IEC958? I think someone said that was necessary for audio over HDMI.

---

### Post by jbelmonte on 2009-08-11
> **thomasaaron said:**
> ... I'm out of the office for a couple of weeks, so I won't be able to test until I return. ...

How will this forum function without you? :(

---

### Post by thomasaaron on 2009-08-11
:lolflag:

Actually, FIRST I'd like to say...

[SIZE="7"]THANK YOU!![/SIZE]

...to all the folks who help me here. This community is really the best one I've ever seen, and always happy to help. I've solicited tutorials, advice, etc... from a number of folks here. It's really great to come in on Monday morning and see that some of the questions are already answered.

SECOND, *THIS* week I'm going to OpenSource World Conference in San Francisco. So, I'll still be answering email and checking forums between sessions.

But the following week, I will be on vacation. (First one in three years.) And I *don't* expect to be able to answer email and form posts during that week. Carl and Mandy will handle sales questions and critical support issues via email while I'm on vacation.

But anything that requires much testing probably will end up having to wait until I get back.

---

### Post by Lee_Machine on 2009-08-13
So I tried to get Audio over HDMI working again, but no dice. What I did was...

1) Install a daily build of Ubuntu 9.10 (20090813)

2) Install newest Nvidia driver (185.18.31)

3) Install newest AlSA Driver (1.0.20) Which is the default, but I did anyways. 

4) I even tried a daily build of ALSA, and it still didnt work. 

I give up :lolflag:

There are somethings they changed in Ubuntu 9.10 with the GUI for how sound preferences work. I don't really like it, it's confusing :confused:

But I prefer CLI anyways, and aplay -L does not show any Nvidia HDMI outputs like it should.

Although I do like how it shows what applications are using sound resources, and you can dictate priority (The new sound Preferences UI :guitar:




Lastly for the S76 dev guys the Track-pad does not work properly. Moving the mouse does, but Horizontal Scrolling, and tapping the middle for clicking does not. But It's probably too early for you guys to care, it's just an unstable build. :lolflag:


##EDIT##

Never mind it works just fine, it is disable by default. Just have to go into Trackpad settings....Maybe that should be enabled with the S76 driver? Also there are two new options, "Disable Trackpad while typing", and "Two-Finger Scrolling" 

Disable Trackpad while typing works GREAT!!!! :) , but not Two-Finger Scrolling :(

---

### Post by gpstar on 2009-08-13
HDMI audio has been working fine for me on my Bonobo. I had to change a few things. Here's a screenshot of my settings.

---

### Post by betrunkenaffe on 2009-08-18
Lee Machine: Did you have HDMI audio working in Interpid? What settings did you use?

This is one of those "I'll be testing at work" things since I don't have HDMI tv here :) Wanted to play some movies off comp while working.

---

