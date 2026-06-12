---
title: "serval temp sensors"
date: 2008-07-09
forum: System76 Support
---

### Post by majoridiot on 2008-07-09
tearing into set-up on my new serval (GREAT unit- highly recommended) but having issues trying to get lm-sensors
working.  sensors-detect can't find any sensors beyond nvidia i2c...

anyone got pointers to save this idiot a bit of time?

---

### Post by thomasaaron on 2008-07-10
Yep. I'm not having much luck getting it running either. This one will take some work.

---

### Post by pauper on 2008-07-10
Check this link to find out current driver support status for your chip.
[http://www.lm-sensors.org/wiki/Devices]("http://www.lm-sensors.org/wiki/Devices")

According to aforementioned website, i2c-* are the proper "bus drivers" for
nVidia, and there are no "sensor chip drivers" so far.

 
From their FAQ ([http://www.lm-sensors.org/wiki/FAQ/Chapter2]("http://www.lm-sensors.org/wiki/FAQ/Chapter2")):

"Which modules should I insert?

sensors-detect will tell you. Take the modprobe lines it recommends and paste
them into the appropriate /etc/rc.d/xxxx file to be executed at startup.

You need one module for each sensor chip and bus adapter you own; if there
are sensor chips on the ISA bus, you also need i2c-isa.o. for each type of
chip you own."


Try their FAQ/mailing list support.
[http://www.lm-sensors.org/wiki/FeedbackAndSupport]("http://www.lm-sensors.org/wiki/FeedbackAndSupport")

P.S. You might as well try nvclock utility
[http://www.linuxhardware.org/nvclock/]("http://www.linuxhardware.org/nvclock/")

---

### Post by Naenyn on 2008-07-17
> **thomasaaron said:**
> Yep. I'm not having much luck getting it running either. This one will take some work.

I am interested in this as well. Hope you're able to come up with something!

---

### Post by thinman1189 on 2008-07-21
I just got my serval today and I haven't had any luck getting temp or fan to work either.

Any update on this?

---

### Post by majoridiot on 2008-07-22
> **thinman1189 said:**
> I just got my serval today and I haven't had any luck getting temp or fan to work either.

Any update on this?

thomasaaron has only been aware and working on this for a week or so (post #2)... i'm being patient while
they sort it out.

still loving the serval.  a really solid machine :)

---

### Post by thomasaaron on 2008-07-22
I've still not been able to figure it out. Sorry for not updating sooner.
As best I can tell, lmsensors doesn't support the Serval's hardware.

---

### Post by majoridiot on 2008-07-22
> **thomasaaron said:**
> I've still not been able to figure it out. Sorry for not updating sooner.
As best I can tell, lmsensors doesn't support the Serval's hardware.

bummer. :(

is anyone @ system76 following up with the lmsensors guys to see about compatibility, and what we
could do to help get the hardware supported?

---

### Post by pauper on 2008-07-22
Verbatim from [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)
> If you would like us to support a chip **not** listed below, or listed as
'not planned', please [contact us](http://www.lm-sensors.org/wiki/AuthorsAndContributors). Please indicate if you can help in
development, testing, or donations. We don't have much spare time, so the more
help you can provide, the better your chances to get a chip supported fast.

---

### Post by majoridiot on 2008-07-22
> **pauper said:**
> Verbatim from [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

i'm more than willing to throw some donations their way and help with serval testing if system76 can
get the ball rolling by providing the needed info directly to the devs.

i'll bet i'm not alone on that... ;)

---

### Post by asmiller-ke6seh on 2008-07-22
I have temp sensors working on my SERP2: GPU (147 degress F), Hard drive (120 degrees F), Core 0 (153 degrees F), and Core 1 (151 degrees F).
-----------------------------------------------------------------
found at: [http://www.techthrob.com/tech/linuxsensors.php](http://www.techthrob.com/tech/linuxsensors.php)
-----------------------------------------------------------------

Technology: Enabling Temperature Sensors in Linux

Introduction

Most computers these days come with a myriad of sensors to monitor the temperature of your computer. These sensors are generally located on the processor and the motherboard, and you might also have sensors on your video card. On top of that, all S.M.A.R.T-enabled hard drives have built-in temperature monitoring. 

The temperature of your computer is a vital thing to keep track of - heat and computers don't mix very well. Unfortunately, Ubuntu doesn't setup your computer's sensors automatically; but you can follow these steps to enable the temperature sensors in your computer in Ubuntu, or any other version of Linux. While sensor-monitoring is somewhat hardware dependant, this guide will work for most users. It involves heavy use of the command-line, but don't worry - I will walk you through it step-by-step. 


1. Installing the sensor libraries
First thing's first - you need to install the libraries that allow Linux to read your sensors. To do this, install the lm-sensors library, by running the command:

sudo apt-get install lm-sensors
This will install the libraries for your motherboard's sensors. For your hard-disk sensors, you'll want to install hddtemp:

sudo apt-get install hddtemp
In Ubuntu, the install will ask you several questions. First it will ask if it should run SUID root, select "yes." It will then ask you for an interval for logging the temperature to a file; since we are going to have an applet display our system temperatures for us, this isn't necessary, so most users will be fine leaving the default of '0' and pressing enter; if you wish to log this data, however, I'd recommend a value between 2 and 10 seconds. Next, it will ask if it should run as a deamon; select yes, and leave the default values for hostname and port. Finally, it will ask if you wish for it to run on startup - select "yes."


2. Running sensors-detect
Now that your sensor libraries are installed, you need to detect your sensors! Run the command:

sudo sensors-detect
Which will probe your system for sensors. Answer "YES" to all questions! Don't just hit enter, type "YES", because at the end there will be a question for which the default answer is "no", and we'll want to answer in the affirmative.

The sensors-detect program will scan yur system, and then give you a summary, stating which sensors it has found. It will then say: I will now generate the commands needed to load the required modules. After you hit ENTER to continue, it will ask, Do you want to add these lines to /etc/modules automatically? (yes/NO) This is the question we want to make sure we answer YES to.


3. Loading the modules
Since we answered YES to the previous question, our sensor modules will be loaded by default the next time we start up. But since we don't want to have to reboot, we're going to use the information we got from the sensors-detect script to load the modules ourselves, this time only. Right above the last question will appear a list of modules that you should load, in the form of:
#----cut here----
# Chip drivers
smsc47m1
#----cut here----

You may have more, or different, items listed - that's fine! What we want to do now, to load these modules, is use the modprobe command, as follows:

sudo modprobe [module name]
So, in my case, I would type: 

sudo modprobe smsc47m1
If all goes well, you should be returned to the command-line, without any output.


4. Monitoring the sensors!
Wow, that was a lot of work! Now, let's see the rewards. On the command line, you can simply run the

sensors
command; this will output the information from your motherboard's sensors.

However, we'd rather have a graphical interface for checking up on our hardware, so let's install an applet for our Gnome desktop to keep an eye on our system's temperature. Run the command:

sudo apt-get install sensors-applet
to install the applet. Now, add the applet by right-clicking on your desktop panel, selecting "Add to Panel," and you will now see a "Hardware Sensors Monitor" applet in the System & Hardware section. Click and drag this to your panel to add it.

The applet will now say that you haven't enabled any sensors; right click on the applet and open its preferences. The first screen is for general settings:

(image omitted)

The options here are self-explanatory; for update interval, choose a value between two and ten seconds. The second screen is where you can enable your sensors to be displayed in the applet:

(image omitted)

Here we have my hard drive, /dev/sda, enabled. Simply check off the sensors you want to enable, and they will appear in your panel!


Conclusion

Hopefully by now, you'll see icons in your panel, with thermometers and temperature readouts, keeping you apprised of the status of your system's hardware. You'll notice that when doing intensive operations, various parts of your system will increase in temperature; this is normal, and this applet will help you keep an eye on things so nothing overheats. 

-----------------------------------------------------------------

---

### Post by pauper on 2008-07-22
> The temperature of your computer is a vital thing to keep track of -
heat and computers don't mix very well.

lm-sensors is nice thing to have, but don't overestimate or misinterpret its
purpose. It simply prints the current readings of temperature, fan speed,
and voltage, if properly supported. You won't miss much, unless you eager to
mess with your fan speeds ("man fancontrol"). I mean how often do you check
your body temperature, heart rate, blood pressure?

Be sceptic about the readings. There is always a room for miscalibration and
error: the figures might seem right or on the contrary, but as it turns out
it might not be the case.
[http://www.swiftnets.com/troubleshooting.htm](http://www.swiftnets.com/troubleshooting.htm)

Anyway, if something goes wrong libsensors will shutdown your computer. Well,
the same thing *supposed to happen* on the hardware level when the
processor reaches critical temperature range with or without any help from
software. What's the tradeoff? Hearing some bell once in a while, implying
that "G*ddamn, I'm cooking, shut me down now!" Think of it as backup.

I've already posted [here](http://ubuntuforums.org/showpost.php?p=5410034#postcount=2) that if you follow some sane maintenance&care
guidelines your computer should do well without any fancy applets.

---

### Post by asmiller-ke6seh on 2008-07-23
Pauper,

I read the article you referred to - one significant thing: that article was making reference to the lack of a temperature sensor in the AMD chips; my Serval has an Intel chip. Additionally, reference is made to the thermocouple-based sensor being calibrated to better than a tenth of a degree ... pretty darn accurate in my book.

Taking that into account, why would you want to rain on someone's parade? If I'm missing your point, maybe you can point me in the right direction.

---

### Post by pauper on 2008-07-23
The post #12 is addressed to the people who [color=red]aren't able[/color] to use lm-sensors
at this point of time. Don't feel neglected. It is not essential, as in
"absolutely necessary". Move on for now and come back later or provide support
to the maintainers.

quot homines tot sententiae

---

### Post by asmiller-ke6seh on 2008-07-23
> **pauper said:**
> The post #12 is addressed to the people who [color=red]aren't able[/color] to use lm-sensors
at this point of time. Don't feel neglected. It is not essential, as in
"absolutely necessary". Move on for now and come back later or provide support
to the maintainers.

quot homines tot sententiae

There are as many opinions as there are men.

Did I read the title of this thread correctly? Something about SERVAL temp sensors? With the instructions provided in Message #11, I think that ALL Serval owners can have Temp Sensors -- so there is no need to feel neglected...is there?

What does "at this point of time" mean? I would say "at this point" or "at this time".

---

### Post by thomasaaron on 2008-07-24
asmiller-ke6seh,

I don't think that will work for the poster, (but maybe it will). His Serval is a different motherboard/chipset/etc... than yours.

Best
T

---

### Post by majoridiot on 2008-07-24
opinion or not, temperature monitoring is *very* important to me at times- especially in a laptop.

while i do not constantly monitor my body temperature as (i hope) sarcastically mentioned, i **do** check
it when i am not well.  since the hardware exists, it should not seem unreasonable to have the same *ability*
to do so on the serval when needed.

in an effort to bring this more on-point to the original post and avoid devolving into an opinion-based
flame war that is just pointless...

Q: does system76 have any plans to address this issue by providing the required info to the lm-sensors 
developers and/or by working on a fix themselves?

Q: is there anything serval owners can do to help speed this process?

---

### Post by thomasaaron on 2008-07-24
I've passed the issue on to our R&D department.

You might want to contact the lmsensors folks yourself as well. This might help to add to the sense of urgency on their part, and they can direct you to whatever info they need.

As an organization, we can't really pursue every third-party software developer out there to make sure their stuff works on our computers. In most cases, stuff like this gets accomplished via community effort.

---

### Post by majoridiot on 2008-07-24
> **thomasaaron said:**
> I've passed the issue on to our R&D department.

You might want to contact the lmsensors folks yourself as well. This might help to add to the sense of urgency on their part, and they can direct you to whatever info they need.

As an organization, we can't really pursue every third-party software developer out there to make sure their stuff works on our computers. In most cases, stuff like this gets accomplished via community effort.

i'm happy to contact the devs and help get this hardware included. can you provide a complete 
list of the serval sensors we're dealing with, so the devs can provide feedback on what 
they need from there?  it would save time tracking down the info and would be accurate the 
first time.

---

### Post by thomasaaron on 2008-07-24
Unfortunately, I do not have that list. Perhaps R&D will.
The lmsensor devs may be able to guide you into extracting that info from the system.

---

### Post by asmiller-ke6seh on 2008-07-24
> **thomasaaron said:**
> asmiller-ke6seh,

I don't think that will work for the poster, (but maybe it will). His Serval is a different motherboard/chipset/etc... than yours.

Best
T

thomasaaron: Wow...to think that maybe my SERP2 has a capability that other Serval Performance systems might not have ... quite ironic considering that, until only recently, we were not sure that the built-in webcam in the SERP2 would be supported.

Say, Majoridiot: did you try the installation routine I copied in Message #11? I would be interested (as I am pretty confident thomasaaron would be) to know if you tried it, and what kind of results you had.

---

### Post by majoridiot on 2008-07-26
> **thomasaaron said:**
> Unfortunately, I do not have that list. Perhaps R&D will.
The lmsensor devs may be able to guide you into extracting that info from the system.

if r&d can provide a list, that would be ideal.

i'm glad to help as much as possible on this, but don't have time to run
down the info that they've undoubtedly got laying around somewhere ;)

---

### Post by thinman1189 on 2008-07-28
I'm quite concerned about my temp at the moment. If I run something like WoW in Wine for more than an hour, the bottom left portion of the laptop (left of the touchpad) becomes extremely hot to the point that I'm getting blisters...

---

### Post by thomasaaron on 2008-07-28
[http://forum.notebookreview.com/showthread.php?t=246748](http://forum.notebookreview.com/showthread.php?t=246748)

Interesting thread. The thermal sensors depend on the CPU you have. And the newer penryn chips use a digital instead of an analog sensor, which might be what is thwarting lm-sensors.

Here are some good places to contribute / follow this issue, as there are already bug reports dedicated to it and the solution is being actively developed already.

[https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/205730](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/205730)
[http://lists.lm-sensors.org/pipermail/lm-sensors/2008-January/022323.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2008-January/022323.html)

Looks like there is already a patch being worked on and tested, so a fix will probably come down via an update from Ubuntu in the near future. (Although, there is a fair chance it won't be available before Intrepid.)

---

### Post by majoridiot on 2008-07-28
> **thomasaaron said:**
> [http://forum.notebookreview.com/showthread.php?t=246748](http://forum.notebookreview.com/showthread.php?t=246748)

Interesting thread. The thermal sensors depend on the CPU you have. And the newer penryn chips use a digital instead of an analog sensor, which might be what is thwarting lm-sensors.

Here are some good places to contribute / follow this issue, as there are already bug reports dedicated to it and the solution is being actively developed already.

[https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/205730](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/205730)
[http://lists.lm-sensors.org/pipermail/lm-sensors/2008-January/022323.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2008-January/022323.html)

Looks like there is already a patch being worked on and tested, so a fix will probably come down via an update from Ubuntu in the near future. (Although, there is a fair chance it won't be available before Intrepid.)

thank you very much for this info, thomas- and for continuing fast and friendly support!

---

